# Nexus Repository Manager OSS 3.xpen
The world's first and only universal repository solution that's FREE to use.

Manage these formats:
 Bower Docker Git LFS Maven npm NuGet
 PyPI Ruby Gems Yum Apt Conan R
 CPAN Raw P2 Helm 
 
* [Download](https://www.sonatype.com/download-oss-sonatype) - Download
* [Documentation](https://help.sonatype.com/repomanager3) - Documentation
* [Repository](https://github.com/sonatype/nexus-public) - Repository

## Disclaimer
This configuration example shows a typical case inside an organization. If you need more information, go to the official site.
Requirements covered:
* Enterprise Proxy
* LDAP Authentication
* Automatic Backup 

## Table of Contents

- [Install and Run](#install-and-run)
- [LDAP Integration](#ldap-integration)
- [HTTP and HTTPS Request and Proxy Settings](#http-and-https-request-and-proxy-settings)
- [Configure and Run the Backup Task](#configure-and-run-the-backup-task)
- [License](#license)



### Prerequisites

Nexus Repository Manager requires a Java 8 Runtime Environment (JRE) from Oracle.

```
$  java -version
java version "1.8.0_60"
Java(TM) SE Runtime Environment (build 1.8.0_60-b27)
Java HotSpot(TM) 64-Bit Server VM (build 25.60-b23, mixed mode)
```

## Install and Run

### Unix-like platform like Linux use:

```
$ cd NEXUS_HOME/nexus/bin
$ ./nexus run
```
### Windows requires a / in front of the run:

```
$ cd NEXUS_HOME/nexus/bin
$ nexus.exe /run
```

## LDAP Integration
Nexus Repository Manager OSS has a Lightweight Directory Access Protocol (LDAP) Authentication realm which provides the repository manager with the capability to authenticate users against an LDAP server.

### LDAP Connection and Authentication
Go to "LDAP feature view". “LDAP Feature View”, is available via the LDAP item in the "Security section" of the "Administration main menu".
The following parameters allow you to create an LDAP connection:
* Name: enter a unique name for the new configuration.
* LDAP server address: enter Protocol, Hostname, and Port of your LDAP server.
* Protocol: valid values in this drop-down are ldap and ldaps that correspond to the Lightweight Directory Access Protocol and the Lightweight Directory Access Protocol over SSL.
* Hostname: the hostname or IP address of the LDAP server.
* Port: the port on which the LDAP server is listening. Port 389 is the default port for the ldap protocol, and port 636 is the default port for the ldaps.
* Search base: the search base further qualifies the connection to the LDAP server. The search base usually corresponds to the domain name of an organization. For example, the search base could be dc=example,dc=com.

### User and Group Mapping
* Base DN: corresponds to the collection of distinguished names used as the base for user entries. This DN is relative to the Search Base. For example, if your users are all contained in ou=users,dc=sonatype,dc=com and you specified a Search Base of dc=sonatype,dc=com, you use a value of ou=users.
* User subtree: Check the box if True. Uncheck if False. Values are true if there is a tree below the Base DN that can contain user entries and false if all users are contain within the specified Base DN. For example, if all users are in ou=users,dc=sonatype,dc=com this field should be False. If users can appear in organizational units within organizational units such as ou=development,ou=users,dc=sonatype,dc=com, this field should be True .
* Object class: this value is a standard object class defined in RFC-2798. It specifies the object class for users. Common values are inetOrgPerson, person, user, or posixAccount.
* User filter: this allows you to configure a filter to limit the search for user records. It can be used as a performance improvemen
* User ID attribute: this is the attribute of the object class specified above, that supplies the identifier for the user from the LDAP server. The repository manager uses this attribute as the User ID value.
* Real name attribute: this is the attribute of the Object class that supplies the real name of the user. The repository manager uses this attribute when it needs to display the real name of a user similar to usage of the internal First name and Last name attributes.
* Email attribute: this is the attribute of the Object class that supplies the email address of the user. The repository manager uses this attribute for the Email attribute of the user. It is used for email notifications of the user.
* Password attribute: it can be used to configure the Object class, which supplies the password ("userPassword"). If this field is blank the user will be authenticated against a bind with the LDAP server. The password attribute is optional. When not configured authentication will occur as a bind to the LDAP server. Otherwise this is the attribute of the Object class that supplies the password of the user. The repository manager uses this attribute when it is authenticating a user against an LDAP server.


## HTTP and HTTPS Request and Proxy Settings
The repository manager uses HTTP requests to fetch content from remote servers. In some cases a customization of these requests is required. Many organizations use proxy servers for any outbound HTTP network traffic. The connection to these proxy servers from the repository manager needs to be configured to allow it to reach remote repositories. All this can be configured in the HTTP configuration available via the System section of the Administration menu, “Configuring HTTP Request Settings”.

* User-agent customization: the HTTP configuration in User-agent customization allows you to append a string to the User-Agent HTTP header field. This can be a required customization by your proxy servers.

* Connection/Socket timeout and attempts: the amount of time in seconds the repository manager waits for a request to succeed when interacting with an external, remote repository as well as the number of retry attempts to make when requests fail can be configured with these settings.


## Configure and Run the Backup Task
To configure and run a new task for database backup, review the steps in Configuring and Executing Tasks. The form for this task includes an additional field called Backup location, which requires you to enter the path to a directory where you want to store backup data. "Manual Admin - Export databases for backup Task with Directory Location".

* Access log: login and usage information among repository manager users
* Analytics: event data and overall repository manager usage
* Auditing: a record of repository manager configuration changes as well as asset or component additions and removals
* Component: all related data that make up components within the repository manager
* Configuration: general administrative configurations such as scheduled tasks, email server configuration
* Security: all user and access rights management content

## License

This project is licensed under the GNU GPLv3 - see the [LICENSE.md](LICENSE.md) file for details
