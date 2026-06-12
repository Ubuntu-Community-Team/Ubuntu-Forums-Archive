---
title: "ProFtpD Problems"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by DaleHUtch on 2008-03-26
I've got a problem with ProFtpD. It's probably something in my conf file but I'm a "Noob" and need some expert help.

The problem I am having is I am unable to upload or create directories. I have set up a user and can successfully log into my server.( I use WSFTP on an XP box to FTP into my Ubuntu 7.10 LAMP).

Once logged in I can see the folders I created using the same account locally. Since I can create files and directories locally I think I have my permission correct on the server. 

I think it is in my ProFtpD conf file. I must have a permissions section either not included or not set up right. I have posted it below.

Any help would be appreciated.

DH

--------------------------------------------------------------------

# This is a basic ProFTPD configuration file (rename it to
# 'proftpd.conf' for actual use. It establishes a single server
# and a single anonymous login. It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName "stargate-ftp"
ServerType standalone
DeferWelcome off

ShowSymlinks on
MultilineRFC2228 on
DefaultServer on
AllowOverwrite on

TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 1200

DisplayLogin welcome.msg
DisplayFirstChdir .message
ListOptions  "-l"

DenyFilter \*.*/

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
#PersistentPasswd off

# Port 21 is the standard FTP port.
Port 21

# To prevent DoS attacks, set the maximum number of child processes
# to 30. If you need to allow more than 30 concurrent connections
# at once, simply increase this value. Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User proftpd
Group nogroup

# Normally, we want files to be overwriteable.
<Directory /*>
# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask 022 022

AllowOverwrite on
</Directory>

# here are my improvements

# chroot for all users of the group www-data
DefaultRoot ~ www-data

# grant login only for members of the group
<Limit LOGIN>
DenyGroup !www-data
</Limit>

# disable root login and require a valid shell (from /etc/shells)
<Global>
RootLogin off
RequireValidShell on
</Global>

# increase
UseReverseDNS off
IdentLookups off

# Logging formats
LogFormat default "%h %l %u %t \"%r\" %s %b"
LogFormat auth "%v [%P] %h %t \"%r\" %s"
LogFormat write "%h %l %u %t \"%r\" %s %b"

# activate logging

# every login
ExtendedLog /var/log/ftp_auth.log AUTH auth

# file/dir access
ExtendedLog /var/log/ftp_access.log WRITE,READ write

# forr paranoid (big logfiles!)
#ExtendedLog /var/log/ftp_paranoid.log ALL default

---

### Post by nitro_n2o on 2008-03-26
I have followed this tutorial once [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) and it works just fine, have a look at it  you might find what you are missing

---

### Post by DaleHUtch on 2008-03-26
Thanks!

I found my problem...

It is file permissions...

Here's my real problem....

What would be the best (most secure) chmod command I can issue on my  /var/www  directory ( and subdirectories)  to allow my user group (www-data) full access but to restrict apache viewers read execute access? I assume PHP files need execute.

I was thinking 755??

Thanks?

---

