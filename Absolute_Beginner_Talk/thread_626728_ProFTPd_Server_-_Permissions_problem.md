---
title: "ProFTPd Server - Permissions problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by mrhinman on 2007-11-29
Okay, I've read through tons of posts about this subject, but nothing seems to be working for me.  I've installed Drake 6.06 with a GUI, WebMin, ProFTPd, etc.  I've set everything up and I can see the FTP server no problem.

The problem I'm having is loading files into Dreamweaver, editing them, and then writing them.  Writing always gives me a permissions (550) failure.  I have tried setting folder permissions in addition to altering ownership of the folder, etc. (BTW it's in /var/www/apache2-default).

I have a group set up as "ftp" and a user set up as "ftpuser", and it's all in the config file:

> #
# /etc/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 
TransferRate RETR 4096

ServerName			"DSI SERVER"
ServerType			standalone
DeferWelcome off

MultilineRFC2228		on
DefaultServer on
ShowSymlinks on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayFirstChdir .message
ListOptions "-l"

DenyFilter			\*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd		off

# Uncomment this if you would use TLS module:
#TLSEngine 			on

# Uncomment this if you would use quota module:
#Quotas				on

# Uncomment this if you would use ratio module:
#Ratios				on

# Port 21 is the standard FTP port.
Port 21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances			30

# Set the user and group that the server normally runs at.
User ftpuser
Group ftp

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022
# Normally, we want files to be overwriteable.
AllowOverwrite			on
DefaultChdir /var/www/

# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
# It is on by default. 
#DelayEngine 			off

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayFirstChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>
<Global>
DefaultChdir /var/www/
AllowOverwrite on
DefaultRoot /var/www/ ftp
</Global>


Some ideas would be helpful!

Oh, here's my ls-l:
> drwxr-xr-x 3 ftpuser ftp 4096 Nov 29 10:14 apache2-default

---

### Post by mrhinman on 2007-11-29
Oh, and through all the changes I've managed to screw up my permissions on my phpMyAdmin folder - now it's inaccessible through the web... grrrr....

---

### Post by mrhinman on 2007-11-29
Can anyone offer some assistance on this subject?

---

