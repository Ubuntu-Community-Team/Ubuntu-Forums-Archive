---
title: "Sharing between Ubuntu and XP problem"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by Tristan9669 on 2005-08-14
On ubuntu I can access shared folders on a xp computer, but when I share a folder on ubuntu and try to access it from the xp computer, it asks me for a login and password. Weird thing is I'm stll able to access the same shared folder thats on the ubuntu computer and play a movie through my Xbox (with Xbox Media Center which is compatiable with both Windows and Samba netorking). I dont understand whats the problem, I followed the instructions from [here](http://ubuntuguide.org/#sharefolderstheeasyway) and I also edited the smb.conf to security = user on line 76. Does anyone know whats the problem.
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
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


[Shared]
path = /home/tristan/Shared
available = yes
browseable = yes
public = yes
writable = yes

```

---

### Post by h4rdc0d3 on 2005-08-16
>  I also edited the smb.conf to security = user on line 76

Why? That step was outside "the easy way".

---

### Post by kvn864 on 2005-09-10
Tristan
Did you figure it up? I'm having the same problems.
Thanks.

---

### Post by sneax on 2005-09-10
me too - i haven't used smb a lot yet so i'm not used to configuring it

i will rtfm some more ;)

---

### Post by patrick295767 on 2005-10-06
Is folder sharing only made by changing the smb.conf ?

---

### Post by brentoboy on 2005-10-06
if you edit the smb file, make sure and restart samba

sudo /etc/init.d/samba restart

You need to add a samba user.  Your linux user list is not automatically added to your samba user list.

sudo smbpasswd -a <username>

You must add users that have an equivelent user in linux to be mapped to (same username).
then, you will be able to supply a username/password from the windows box.

---

### Post by patrick295767 on 2005-10-06
Hi, 

(I have a disk with 4 partitions : fat16, windowsnt, data_disk_ntfs, linux+swap )

i tried to use the vmware as regular user ($) (not root)
but the vmware is telling me that it cannot access the physical harddisk /dev/hda (cos of rights).
Unfortunaltly, I have to do so (use the vmware for whole /dev/hda harddisk) otherwise, if I use vmware on only one partitions or two partitions (ntfs), I got the error message 
Grub Loading 
Error 17
So, the only way i found was to use the physical harddisk /dev/hda, to do vmware of my windows ntfs partition. 
If you have additional information concerning the vmware and its use with one or 2 ntfs partitions (os nt and data), please let me know how to do this. 
Thanks 
Pat'

---

### Post by patrick295767 on 2005-10-06
[QUOTE=patrick295767]Hi, 
(I have a disk with 4 partitions : fat16, windowsnt, data_disk_ntfs, linux+swap )
i tried to use the vmware as regular user ($) (not root)
but the vmware is telling me that it cannot access the physical harddisk /dev/hda (cos of rights).
Unfortunaltly, I have to do so (use the vmware for whole /dev/hda harddisk) otherwise, if I use vmware on only one partitions or two partitions (ntfs), I got the error message 
Grub Loading 
Error 17
So, the only way i found was to use the physical harddisk /dev/hda, to do vmware of my windows ntfs partition. 
If you have additional information concerning the vmware and its use with one or 2 ntfs partitions (os nt and data), please let me know how to do this. 
Thanks 
Pat'[/QUOTE]

wrong thread ... oups

---

### Post by EnderTheThird on 2005-10-06
Ooooh, I didn't know the media extender worked with Linux!  I hope the same applies for the 360, so I don't need to use Windows MCE2005 all of the time.

---

