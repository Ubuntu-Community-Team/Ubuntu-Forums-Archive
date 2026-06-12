---
title: "::samba help::"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-08-14
I am having a problem with samba. I installed samba on my Ubuntu box which is running breezy. I configured samba and hoped that all would work. Everything seems to be running but I cant connect to my Ubuntu box with my Windows box. I get a connection was refused error message. When I check on Ubuntu I can see my windows box in the network servers section it displays its name. If I try to connect to it it wont let me. Does anyone know if there is something that you need to configure on windows to allow samba to run. I have been reading other threads but I cant find what I am looking for. By the way I evne disabled the firewalls on both computers just in case that was the problem but I still get the same errors. I would appreciate any help. Thank you.

---

### Post by taner on 2006-08-15
post your /etc/samba/smb.conf and /etc/fstab here

---

### Post by Iowan on 2006-08-15
> **grim918 said:**
>  When I check on Ubuntu I can see my windows box in the network servers section it displays its name. If I try to connect to it it wont let me. Does anyone know if there is something that you need to configure on windows to allow samba to run.You'll need to have a share defined on the Windows box...

---

### Post by grim918 on 2006-08-16
Here is my /etc/samba/smb.conf file:
> 
global]
    ; General server settings
    netbios name = grim_smb_server
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = grim
    force group = grim



Here is my /etc/fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I followed the instructions on the thread
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


How do I define a share on the Windows box.If there is another way to get samba working please let me know. I'm anxioux to know. Thank you for your help.

---

### Post by lerrup on 2006-08-16
I'm having the same problem, anyone?

---

### Post by zheek on 2006-08-16
> Everything seems to be running but I cant connect to my Ubuntu box with my Windows box. I get a connection was refused error message.

Have you tried setting the samba password for the windows user on the linux machine?

# smbpasswd -a <username>
New SMB password:
Retype new SMB password:
Added user <username>

(Where <username> is the username you use on the windows machine to connect to the linux machine)

---

### Post by taner on 2006-08-16
in control panel --> User accounts / Turn on the guest accounts

then right click to my computer select manage / go to local users and groups then select users and you will see the users in the right section click with right button on guest and select set password. set password
try to connect again your windows box.

if you want to connect from your ubuntu to your windows box

add this to global section in smb.conf
    encrypt passwords = true
    interfaces = 192.168.0.     (edit it to your network adresses if you can't   give me your linux box and windows box adresses)
     invalid users = root
     valid users = (here add user names, be sure did you add them to samba?. type to console sudo smbpassword -a username )
     passwd program = /usr/bin/passwd %u
     passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssucc
essfully* .

and change your wins support to no

finally restart your samba    sudo /etc/init.d/samba restart

---

### Post by grim918 on 2006-08-16
Im still getting connections refused messages. What should I put in the interfaces part that you specified.
My windows box has an internal ip: 192.168.1.46
Ubuntu box is: 192.168.1.47

Thank you.

---

### Post by taner on 2006-08-17
interfaces = 192.168.1.
this is interfaces part for you.
try again ...
(restart samba after some configuration)

---

### Post by grim918 on 2006-08-17
I still get nothing. All connections are refused. I dont know what I am doing wrong. Now my Ubuntu box cant even detect the windows box its like nothing is there. I thihnk its because I changed wins support to no. Who knowz though. If you have any ideas please let me know, For now im going to go read the samba.org website and see if I can figure this out. Thank you for the help.

---

### Post by dmizer on 2006-08-17
on this section of your smb.conf:
> force user = grim
force group = grim
is grim the user name that is logged into your UBUNTU box hosting the share?

i also notice that at the very top it reads "global]"

is this a typo, or does your actual smb.conf not have the leading [ in front of [global]?

edit:
also also ... if your ubuntu box is connected via dhcp, you will have to change wins support to no.

---

### Post by lerrup on 2006-08-17
I have tried the steps in your signatures how-to and the windows machine still won't connect.  It will when booting ubuntu.

Anyone any ideas?

Thanks.

---

### Post by djsroknrol on 2006-08-17
> **grim918 said:**
> Here is my /etc/samba/smb.conf file:


Here is my /etc/fstab file:



I followed the instructions on the thread
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


How do I define a share on the Windows box.If there is another way to get samba working please let me know. I'm anxioux to know. Thank you for your help.

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Mshome
   netbios name=server

# server string is the equivalent of the NT Description field
  server string = (Ubuntu)

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
   name resolve order = lmhosts host wins bcast


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
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

#   guest account = no
#   invalid users = root

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
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
#   printing = bsd
#   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
#   printing = cups
#   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
#   printer admin = @ntadmin


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
   browseable = yes
   path=/home/bob

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

available = yes
public = yes
[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
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



[Movies]
path = /media/hdb1/Movies
available = yes
browseable = yes
public = yes
writable = yes


[A-K]
path = /media/hdc1/A - K
available = yes
browseable = yes
public = yes
writable = yes

[L-Z]
path = /media/hdc1/L - Z
available = yes
browseable = yes
public = yes
writable = yes

[NewMP3's]
path = /media/hdc1/New MP3's
available = yes
browseable = yes
public = yes
writable = yes

[Transfers]
path = /media/hda1/Network transfers
available = yes
browseable = yes
public = yes
writable = yes


```

And here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdb1       /media/hdb1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdc1       /media/hdc1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hda3       none            swap    sw	0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto	0       0


```

I'd try a more simpler way, i.e. get rid of the masks, and try opening up everything as I did in my shared folders. See if that helps...

---

### Post by grim918 on 2006-08-18
> **dmizer said:**
> on this section of your smb.conf:

is grim the user name that is logged into your UBUNTU box hosting the share?
yes grim is the user that is logged into the ubuntu box. Is this how it is supposed to be set up or should I have the name of the windows user.
> 
i also notice that at the very top it reads "global]"

is this a typo, or does your actual smb.conf not have the leading [ in front of [global]?
It is a typo. I checked the file and it contains the bracket.

> 
edit:
also also ... if your ubuntu box is connected via dhcp, you will have to change wins support to no.
My ubuntu box is not connected via dhcp.

---

### Post by taner on 2006-08-21
> **grim918 said:**
> yes grim is the user that is logged into the ubuntu box. Is this how it is supposed to be set up or should I have the name of the windows user. 
after u add some users with command "smbpassword -a username" add them to valid users, remove the force users...
choose somethg d&#305;fferent than grim

---

### Post by petri on 2006-08-23
Do you samba grim? I used the same howto and mine is working great between windows and ubuntu but not between ubuntu and ubuntu :D

wins yes and wins no, who cares? :-\"  Reconfigure your smb.conf wiht copy and paste from the howto. You do have static ip to your pcs from your router? Then you don't have to make any chances to your wins part n smb.conf.

You should have the same usernames and passwords on windows and ubuntu, just to get it going (and then you can start play with it).

It is very important to follow the howto so you just got to check it again. Reinstall...

---

