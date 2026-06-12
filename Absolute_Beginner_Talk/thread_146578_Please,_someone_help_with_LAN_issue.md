---
title: "Please, someone help with LAN issue"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-03-18
First off, I need to apoligize in advance, as I think I posted in the wrong area to start of with due to the major overhaul in menus. I must apologize for the length of the post also, but I feel the need to provide everything needed for someone to answer me..in any event, here goes:

I have 4 computers, 3 windows boxs sharing with 1 Ubuntu box. The oldest machine is550Mhz the newest(Ubuntu) is 1.6Mhz all working fine, except the speed at which the windows shares see each other and the ubuntu shares is far faster than the Ubuntu computer seeing the windows shares as well as it's own shares across the workgroup, a difference of about 10 - 15 seconds.  I thought that my internet connection was somehow connected with the LAN issue untill I played with "about:config" in Firefox and it helped to speed up. At that point I figured it was strictly a LAN problem on the Linux side. I am running a DSL router(firewall open in the LAN) which goes to a workgroup hub for distribution to the boxes. DHCP is enabled and everything works...but slow.....It's almost like there might be some sort of redundance somewhere that might be the search delay(?)...or am I asking for too much from a cross platform filing system?..I don't know, and I don't  want to give up on this, as it seems to possibly be something simple. I'll post a few things here, with the hope that someone could lead me to a solution:

First, a little terminal snooping:

bob@server:~$ sudo su
root@server:/home/bob# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

iface dsl-provider inet ppp
provider dsl-provider
root@server:/home/bob# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:6D:F6:5C
          inet addr:192.168.8.XX  Bcast:192.168.8.XXX  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe6d:f65c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:13 txqueuelen:1000
          RX bytes:2622154 (2.5 MiB)  TX bytes:250024 (244.1 KiB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1271597 (1.2 MiB)  TX bytes:1271597 (1.2 MiB)

root@server:/home/bob# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.8.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.8.1     0.0.0.0         UG    0      0        0 eth0
root@server:/home/bob# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@server:/home/bob#

And here's my smb.conf file:

 Sample configuration file for the Samba suite for Debian GNU/Linux.
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
   workgroup =mshome
   netbios name=server

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

Now bear in mind that the Ubuntu box is a dual-boot, so the connection is the same one on both OS's and again, no problem on the M$ side of the box....
Hopefully someone understands what I'm trying to do and what I see as the problem and lend a thought or a direction to this...thanks for your time and attention.

Bob

---

### Post by dcstar on 2006-03-18
Do a forum search for "disable IPv6", that may help with overall network speed.

---

### Post by djsroknrol on 2006-03-18
Yeah!!...that was it...disabling ipv6 helped alot...I guess the router is too old for it...thanks..

---

