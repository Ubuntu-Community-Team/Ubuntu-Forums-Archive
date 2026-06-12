---
title: "Problem configuring samba"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by leep on 2007-04-23
Hi,
I've a problem configuring on my machine, hope someone could help me. Here is the scenario:

/dev/sda0 -> root filesystem
/dev/hda0 .. 1 -> 1st IDE HD
/dev/hdb0 .. 6 -> 2nd IDE HD
/dev/hdc0 .. 1 -> 3rd IDE HD

I want to share the folder called "condivisa" on "/dev/hdb6". I tried to chmod it to 777 but nothing changes:

```
sudo chmod -R 777 condivisa
```

does not change directory permissions:

```
drwxrwx--- 26 root plugdev 8192 2007-04-23 22:32 condivisa
```

I want to configure this directory as a read/write directory for everyone. I edited smb.conf following the instruction found on this tutorial [http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Dapper#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29) but I was not able to make it work.

Here is my smb.conf file:

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = hotservices

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;  security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[condivisa]
   comment = Cartella condivisa
   path = /media/hdb6/condivisa
   public = yes
   writable = yes
   available = yes
```

On a second pc, with the same installation and same smb.conf, I was able to make samba run as I want.  The only difference is that on "pc2" I was able to chmod 777 the shared directory. Any idea? I really can't understand how to solve this problem...
Thank you in advance,
S.

---

### Post by leep on 2007-04-24
Any advice?

---

### Post by dstew on 2007-04-24
Try chmod without the -R option.
Also, you have not uncommented your security setting. Uncomment it and set it to user or share, as desired.

---

### Post by leep on 2007-04-30
Thank you for your reply, it does not work, anyway.
There isn't any way to chmod a dir in a "mounted" HD?

---

### Post by dstew on 2007-05-01
I am thinking about your chmod attempt that failed. Do you get any error message after the command? You can get more info about what chmod is doing by using the -v or -c options:```
sudo chmod -vR 777 condivisa
```

---

### Post by leep on 2007-05-01
Thank you for your reply. Here is what I get:

```
simone@hs01:/media/hdb6$ sudo chmod -v 777 condivisa
il modo di `condivisa' è diventato 0777 (rwxrwxrwx)
simone@hs01:/media/hdb6$ ls -la
totale 44
drwxrwx---  6 root plugdev 8192 2007-04-30 22:37 .
drwxr-xr-x 10 root root    4096 2007-05-01 13:18 ..
drwxrwx--- 26 root plugdev 8192 2007-04-25 00:23 condivisa
drwxrwx---  5 root plugdev 8192 2006-12-23 14:03 transfer
drwxrwx---  4 root plugdev 8192 2007-04-30 22:37 .Trash-francesca
drwxrwx---  2 root plugdev 8192 2007-04-25 12:05 .Trash-simone

```

It says that permissions have been changed, but if I list directory, I can see that no change has been saved.

---

### Post by dstew on 2007-05-01
Bizarre. The only thing I can think of is that some process changes the permissions back before you list the directory. Try to boot in recovery mode, and change the permissions again.

---

### Post by leep on 2007-05-02
I tried, but nothing changed. I also tried to chgroup to the folder, but obtained an operation not permitted error. Maybe editing the way the drive in auto-mounted in fstab?

---

### Post by Gammell on 2007-05-02
> **leep said:**
> I tried, but nothing changed. I also tried to chgroup to the folder, but obtained an operation not permitted error. Maybe editing the way the drive in auto-mounted in fstab?

What filesystem is hdb6? If it's a non linux filesystem lik eFAT32 or NTFS, as I understand it you can only set the privileges at mount and for the whole drive.

---

### Post by dca on 2007-05-02
Did you: 
 
smbpasswd -a USERNAME   and   then  smbpasswd -e USERNAME   at the command line?

---

### Post by leep on 2007-05-03
It's a fat32 drive. I tried to change fstab like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dfbbf0b3-04ee-47ea-8617-481a020a4994 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=1E28-14D0  /media/hda1     vfat    defaults,utf8,umask=0777,gid=46 0       1
# /dev/hda5
UUID=1F52-14FC  /media/hda5     vfat    defaults,utf8,umask=0777,gid=46 0       1
# /dev/hdb5
UUID=460E-2523  /media/hdb5     vfat    defaults,utf8,umask=0777,gid=46 0       1
# /dev/hdb6
UUID=0C35-AF04  /media/hdb6     vfat    defaults,utf8,umask=077,gid=46 0       1
# /dev/hdc1
UUID=460A-B12F  /media/hdc1     vfat    defaults,utf8,umask=0777,gid=46 0       1
# /dev/hdc2
UUID=4596-66EA  /media/hdc2     vfat    defaults,utf8,umask=0777,gid=46 0       1
# /dev/sda2
UUID=cc168a05-a9f2-41f2-bce9-87fa20c9a00d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Is umask correct? This should solve my problem. Or not?

---

### Post by leep on 2007-05-03
And finally, I did it.
The problem was not in smb.conf, but in fstab. The one I posted above is wrong, the correct umask is "000". Setting umask=000 gave me writing permissions on my folder on hdb6, giving me the ability to configure it as a samba folder.
Thank you so much for your help and advices.
Simone

---

### Post by leep on 2007-05-03
It seems that I did not solve.
My Ubuntu laptop can now access the share, my windows pc can't...

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOTSERVICES

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;  security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom




[Condivisa]
	comment = Condivisa
	path = /media/hdb6/condivisa
	available = yes
	browsable = yes
	public = yes
	guest ok = yes
	writable = yes
	create mask = 0777

```

---

### Post by dstew on 2007-05-04
If hdb6 is a vfat file system, permissions in the linux style are not used. You have to give the permissions in the mount instruction in your /etc/fstab file. I notice that the umask in your /etc/fstab file for hdb6 is 077, but it should probably be 0777. Have you tried this?

---

### Post by leep on 2007-05-04
I changed it to "000" 'cause vfat notation is different from ext3. And it works, now i can set my dir as "samba shared", and I can create and edit any file on hdb6.

Trying to connect using samba, i'm able to read/write files on "condivisa" share if connecting from another ubuntu machine, but i'm asked for a password anytime I try to access using a win xp computer. I think that the problem, now, is in smb.conf (I remember that a deprecated command to allow each and every user to read/write on smb shares exists, but cannot remember what it is, nor can find it on internet...).

---

### Post by Gammell on 2007-05-04
K, two things. First, a little house keeping. The reason you put "umask=000" is that your setting a mask, not the permissions. Masks come up elsewhere, so I just want to point out the difference. Permisisions are calculated by subtracting the masks from a set of full permissions, so as follows:

Permissions = 777 - Umask

So if you want everyone to be able to read write, 000 is right. (Just to be a bit more confusing, the line in your share definition "create mask = 0777" is right... I know, not very consistent).

Now, samba. I assume you want all users to create files as the same account? (Actually, since it's VFAT, I don't know if you have a choice.). So, change the following lines:

Uncomment and change to "share".
```
####### Authentication #######
;  security = user
```

Uncomment
```
####### Authentication #######
;   guest account = nobody
```

Then, in your share definition, add
```
	guest only = yes
```

Now, what this configuration **should** do (I think):
Since it's using **share** security, client computers on the network (your Windows boxes) are not required to send user/pass pairs (and, when they do, the information is ignored). Samba allows everyone to access the share and has to decide on it's own who these people "are" locally (under what local user they will be creating files, reading permissions). However, since you're on a VFAT drive, it doesn't really matter. So to save Samba a lot of headache, we've essentially short circuited the process by setting up a guest account, and telling Samba that only guests can connect to your share. This means that Samba won't try and guess what local user each connecting client should act as, it will instead make them all guests immediately. And this should work for what I think you want (I hope).

Relevent sections from [man smb.conf](http://www.die.net/doc/linux/man/man5/smb.conf.5.html)
> guest only (S)
    If this parameter is yes for a service, then only guest connections to the service are permitted. This parameter will have no effect if guest ok is not set for the service.

    See the section below on security for more information about this option.

    Default: guest only = no 

> 
    SECURITY = SHARE

    When clients connect to a share level security server they need not log onto the server with a valid username and password before attempting to connect to a shared resource (although modern clients such as Windows 95/98 and Windows NT will send a logon request with a username but no password when talking to a security = share server). Instead, the clients send authentication information (passwords) on a per-share basis, at the time they attempt to connect to that share.

    Note that smbd ALWAYS uses a valid UNIX user to act on behalf of the client, even in security = share level security.

    As clients are not required to send a username to the server in share level security, smbd uses several techniques to determine the correct UNIX user to use on behalf of the client.

    A list of possible UNIX usernames to match with the given client password is constructed using the following methods :

        *            If the guest only parameter is set, then all the other stages are missed and only the guest account username is checked. 
        *            Is a username is sent with the share connection request, then this username (after mapping - see username map), is added as a potential username. 
        *            If the client did a previous logon request (the SessionSetup SMB call) then the username sent in this SMB will be added as a potential username. 
        *            The name of the service the client requested is added as a potential username. 
        *            The NetBIOS name of the client is added to the list as a potential username. 
        *            Any users on the user list are added as potential usernames.

    If the guest only parameter is not set, then this list is then tried with the supplied password. The first user for whom the password matches will be used as the UNIX user.

    If the guest only parameter is set, or no username can be determined then if the share is marked as available to the guest account, then this guest user will be used, otherwise access is denied.

    Note that it can be very confusing in share-level security as to which UNIX username will eventually be used in granting access.

    See also the section NOTE ABOUT USERNAME/PASSWORD VALIDATION. 

---

### Post by leep on 2007-05-08
Thank you very much, I'll try tonight.

---

