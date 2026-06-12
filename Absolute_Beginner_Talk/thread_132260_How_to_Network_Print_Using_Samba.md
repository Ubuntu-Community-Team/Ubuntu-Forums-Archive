---
title: "How to Network Print Using Samba"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by whatnot on 2006-02-17
I have mucked around with my smb.conf file, and now I am really confused. I can connect, it seems, but then I get the message that the printing is paused.

I am trying to print from my Ubuntu machine to the XP machine. The printer is attached to the XP machine. 

Below is my entire smb.conf file.

[PHP]#
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
   server string = MSHOME

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = no

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
security = share

null passwords = yes
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
 load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
  preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

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
   browseable = yes

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

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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
[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

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





available = no
browseable = no
[Mud]
path = /home/jon
available = yes
browseable = yes
public = yes
writable = yes
[/PHP]

---

### Post by whatnot on 2006-02-18
I've tried several things now. 

This is the error message I get now: Paused: ERRDOS - ERRbadaccess (Invalid open mode.) opening remote spool Test Page

Here is the dump of the current smb.conf:
# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[MSHOME]
        path = /home/jon
        read only = No
        guest ok = Yes


The file sharing is okay. I can place files on the XP machine from the Ubuntu machine.

---

### Post by Zerocool10482 on 2006-02-25
I'mm trying to do the same thing. And I'm stilling looking for the answer.

---

### Post by whatnot on 2006-02-28
I found the answer. Follow the directions found in SettingUpSamba, [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

I followed the directions closely, and it worked for me. 

I had found this once before, but it is for Hoary Hedgehog, or Ubuntu 5.04. Looking it up using Google and Wiki, I was unable to find it again. I stumbled across a mention of it posted on this site. I just tried it tonight, and it worked. 

Okay, so I'm new to Ubuntu, and to Linux. I get that. But why does it have to be so hard to do this? I can't be the only person using Ubuntu that wants to network a printer running on XP Professional. I mean there is no "HowTo" listing anywhere, that I can find, except this one. And this HowTo isn't for Breezy Badger.

Having said that, I think Ubuntu is great, and I really do love it. There are still a few quirks I'm trying to iron out. This was a big one for me, and I'm glad I got it fixed. The fact that it's free (sort of, at least), and that it does everything I want it to do, factors big for me. 

Two highlights of "what I learned from this experience:"

1 -- Log in as root user by typing into Applications->Accessories->Terminal by typing in the magic code: ***sudo -s***
(From a quick look over of posts it seems a lot of people who know a lot more than I know don't know this). 

2 -- Although several of the Breezy How-Tos tell me to change my samba password by typing in ***sudo smbpasswed -a usernam***e
The problem is that either I missed it, or they didn't explain that you must log:-D  in as root user for this to work. Tried it the other way. All I can say is this is the only way that worked on my machine. 

I hope this will be helpful to other people because I have really had a very difficult time getting to the posting mentioned above, even though I had used it once before. I just couldn't find it. 

Once again, the answer you seek, if you want to print from Ubuntu Breezy to a printer attached to an XP machine is probably found at [https://wiki.ubuntu.com/SettingUpSamba:-D](https://wiki.ubuntu.com/SettingUpSamba:-D)

---

