---
title: "FTP server problem."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-24
Hi there,

I have tried to follow below tread to set up a basic FTP server, but it still doesn't seems to work.

[http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd](http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd)

I get below error message when I try to start it:

anders@anders-laptop:~$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                           [fail] 

and I get below result when I do the syntax check.

anders@anders-laptop:~$ sudo proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/ftp>: deferring resolution of path
 - <Directory /home/ftp/download/*>: deferring resolution of path
 - <Directory /home/ftp/upload/>: deferring resolution of path
 - IPv6 getaddrinfo 'anders-laptop' error: No address associated with hostname
anders-laptop - 
anders-laptop - Config for Anders haXXor FTP:
anders-laptop - /home/ftp/upload/
anders-laptop -  Limit
anders-laptop -   AllowAll
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUseranders@anders-laptop:~$ sudo proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/ftp>: deferring resolution of path
 - <Directory /home/ftp/download/*>: deferring resolution of path
 - <Directory /home/ftp/upload/>: deferring resolution of path
 - IPv6 getaddrinfo 'anders-laptop' error: No address associated with hostname
anders-laptop - 
anders-laptop - Config for Anders haXXor FTP:
anders-laptop - /home/ftp/upload/
anders-laptop -  Limit
anders-laptop -   AllowAll
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUser
anders-laptop -  AccessGrantMsg
anders-laptop - /home/ftp/download/*
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUser
anders-laptop -  AccessGrantMsg
anders-laptop - /home/ftp
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUser
anders-laptop -  AccessGrantMsg
anders-laptop - Limit
anders-laptop -  AllowUser
anders-laptop -  DenyAll
anders-laptop - AllowOverwrite
anders-laptop - AuthAliasOnly
anders-laptop - UserAlias
anders-laptop - DeferWelcome
anders-laptop - DefaultServer
anders-laptop - ShowSymlinks
anders-laptop - TimeoutNoTransfer
anders-laptop - TimeoutStalled
anders-laptop - TimeoutIdle
anders-laptop - DisplayFirstChdir
anders-laptop - ListOptions
anders-laptop - RequireValidShell
anders-laptop - TimeoutLogin
anders-laptop - RootLogin
anders-laptop - ExtendedLog
anders-laptop - TransferLog
anders-laptop - UseFtpUsers
anders-laptop - AllowStoreRestart
anders-laptop - UserID
anders-laptop - UserName
anders-laptop - GroupID
anders-laptop - GroupName
anders-laptop - Umask
anders-laptop - DirUmask
anders-laptop - MaxClients
anders-laptop - MaxClientsPerHost
anders-laptop - MaxClientsPerUser
anders-laptop - MaxHostsPerUser
anders-laptop - AccessGrantMsg
anders-laptop - ServerIdent
anders-laptop - DefaultRoot
anders-laptop - DefaultRoot
anders-laptop - MaxLoginAttempts
anders-laptop - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
Syntax check complete.

anders-laptop -  AccessGrantMsg
anders-laptop - /home/ftp/download/*
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUser
anders-laptop -  AccessGrantMsg
anders-laptop - /home/ftp
anders-laptop -  Limit
anders-laptop -   DenyAll
anders-laptop -  Umask
anders-laptop -  DirUmask
anders-laptop -  AllowOverwrite
anders-laptop -  AuthAliasOnly
anders-laptop -  UserAlias
anders-laptop -  ShowSymlinks
anders-laptop -  DisplayFirstChdir
anders-laptop -  ListOptions
anders-laptop -  RequireValidShell
anders-laptop -  RootLogin
anders-laptop -  TransferLog
anders-laptop -  UseFtpUsers
anders-laptop -  AllowStoreRestart
anders-laptop -  MaxClients
anders-laptop -  MaxClientsPerHost
anders-laptop -  MaxClientsPerUser
anders-laptop -  MaxHostsPerUser
anders-laptop -  AccessGrantMsg
anders-laptop - Limit
anders-laptop -  AllowUser
anders-laptop -  DenyAll
anders-laptop - AllowOverwrite
anders-laptop - AuthAliasOnly
anders-laptop - UserAlias
anders-laptop - DeferWelcome
anders-laptop - DefaultServer
anders-laptop - ShowSymlinks
anders-laptop - TimeoutNoTransfer
anders-laptop - TimeoutStalled
anders-laptop - TimeoutIdle
anders-laptop - DisplayFirstChdir
anders-laptop - ListOptions
anders-laptop - RequireValidShell
anders-laptop - TimeoutLogin
anders-laptop - RootLogin
anders-laptop - ExtendedLog
anders-laptop - TransferLog
anders-laptop - UseFtpUsers
anders-laptop - AllowStoreRestart
anders-laptop - UserID
anders-laptop - UserName
anders-laptop - GroupID
anders-laptop - GroupName
anders-laptop - Umask
anders-laptop - DirUmask
anders-laptop - MaxClients
anders-laptop - MaxClientsPerHost
anders-laptop - MaxClientsPerUser
anders-laptop - MaxHostsPerUser
anders-laptop - AccessGrantMsg
anders-laptop - ServerIdent
anders-laptop - DefaultRoot
anders-laptop - DefaultRoot
anders-laptop - MaxLoginAttempts
anders-laptop - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
Syntax check complete.

i have manually created a user called: **userftp** with a home dir: **/home/ftp** and shell **/bin/false**

I have also created the download and upload directories as per given instructions. They are located at **/ftp/download **and **/ftp/upload**

I copied the proftpd.conf from the other page and tries to modify it, this is my proftpd.conf

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias anders userftp

ServerName			"Anders haXXor FTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/ftp

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>

Can anyone help me as I am now stuck? Cheers

---

### Post by dcstar on 2008-03-24
> **lover_of_sc said:**
> Hi there,

I have tried to follow below tread to set up a basic FTP server, but it still doesn't seems to work.

[http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd](http://ubuntuforums.org/showthread.php?t=79588&highlight=gproftpd)

I get below error message when I try to start it:

anders@anders-laptop:~$ sudo /etc/init.d/proftpd start
 * Starting ftp server proftpd                                           [fail] 

and I get below result when I do the syntax check.

anders@anders-laptop:~$ sudo proftpd -td5
Checking syntax of configuration file
 - mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
 - parsing '/etc/proftpd/proftpd.conf' configuration
 - <Directory /home/ftp>: deferring resolution of path
 - <Directory /home/ftp/download/*>: deferring resolution of path
 - <Directory /home/ftp/upload/>: deferring resolution of path
 **- IPv6 getaddrinfo 'anders-laptop' error: No address associated with hostname**
..............
Can anyone help me as I am now stuck? Cheers

Do a search for disabling IPv6.

---

### Post by lover_of_sc on 2008-03-24
Hmmm, read a few posts and it does seem to be rather complicated for a linux noob like myself. How would I do this in the easiest way? Also, not to sure if I understand why this would help, would it cure the highlighted issues as well? 

- mod_ctrls/0.9.4: binding ctrls socket to '/var/run/proftpd/proftpd.sock'
- parsing '/etc/proftpd/proftpd.conf' configuration
[B]- <Directory /home/ftp>: deferring resolution of path
- <Directory /home/ftp/download/*>: deferring resolution of path
- <Directory /home/ftp/upload/>: deferring resolution of path[/B]
- IPv6 getaddrinfo 'anders-laptop' error: No address associated with hostname

---

### Post by Cresho on 2008-03-24
8(

---

### Post by lover_of_sc on 2008-03-24
Hmmm, what...?

---

