---
title: "Drive mapping error"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by eolatunde4 on 2008-01-23
I am also branded new to linux.  I am trying to setup a file server for shared access to 1 xp client and to vista clients.  I am trying to start off with the XP first.  I have followed instructions on: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I believe I have done everything as instructed, however when ever I attempt to map the drive I get an error.  I have went through my smb.conf file think that the error has to be there.  I did at one point have access to view my exchange folder when you click on browse inthe map drive window.  However, now currently while trying to get that problem fixed I can't even do view them anymore.  

I can see my shared folders in my Networking Places.  However, when it asks for a user name and password I use the one I created for samba and it says that I don't have permission to use the share resource.

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
   workgroup = WORKGROUP
   netbios name = unpsys

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

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
   security = user

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
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

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
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.


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
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[exchange]
comment = Exchange
path = /home/eio6947/Exchange
force user = eio6947
force group = eio6947
read only = No

[share]
comment = Share
path = home/eio6947/Share
comment = Share
path = home/eio6947/Share

```

When I try to log on I use username eio6947 and passwrd.  I have even changed the windows login to the same name and passwrd, rebooted and same problem.

Any help on what I'm doing wrong would be appreciated.  The only thing I've been able to get right so far is the initial install, samba installed, and PuTTY running.

My ultimate goal is once I have the file sharing setup would like to setup a VPN so that I can access my shared resources away from the office.

Using 7.10 server edition.

---

### Post by dannyboy79 on 2008-01-23
for one thing, your Share should be /home/eio6947/Share, you're missing a "/" in the begining. here's my smb.conf and I have 4 computers networked (2 ubuntu, 2 winxp) and 2 xbox's all sharing files. my ubuntu machine is setup as the domain master and local master because sometimes the windows machine is off. I use /etc/hosts with static ip's for all my machines instead of setting winbindd.

security=user
can be tricky to setup. so you have a user on ubuntu being eio6947 and then you added him as a smbuser and gave him a password? i also don't use the tbdsam security database, the default is smbpasswd database. anyway, here it is and modify to your unique stuff like sharenames and workgroup etc etc.

[http://www.pastebin.org/16696](http://www.pastebin.org/16696)

you can download it and the numbers I believe go away from the begining of each line.

good luck. let me know if I can try to help anymore.

---

### Post by eolatunde4 on 2008-01-23
Ok, so I made the necessary changes and added the new smb.conf file and now I am getting "an extended error".  It doesn't really explain where or what this is.

---

### Post by eolatunde4 on 2008-01-23
> **eolatunde4 said:**
> Ok, so I made the necessary changes and added the new smb.conf file and now I am getting "an extended error".  It doesn't really explain where or what this is.

Sorry, I only get this message when I try to try to map the drive again.  In browse I can see the shares again.  But just can't map them.

---

### Post by dannyboy79 on 2008-01-23
you're trying to map a drive on xp or which machine? could you explain when you say, "map driver"?

---

### Post by eolatunde4 on 2008-01-23
> **dannyboy79 said:**
> you're trying to map a drive on xp or which machine? could you explain when you say, "map driver"?

ok, on the xp pc which is the client, I click on start, then right click on my computer, then selected map network drive.  There it asks for the server ip address or name.  Or I can click on browse to find it on the network.  In its current config, I can find the server and the shared files in the browse window.  When I select it, then click on finish then I get the "Extended Error has occured" message.

---

### Post by dannyboy79 on 2008-01-24
uh? using my smb.conf file, I don't get that error. i just tried to map a drive and it works fine. I am not sure as I wouldn't have a clue where to look for errors in windows xp. have you checked the event viewer within  start>settings>control panel>administrative tools. when you try to click through your network places, does it work that way? if so, then I am guessing the mapping of the drtive isn't working because there's no place to store your username or password. but that's right, you said they are the same or didn't you? also, if they are different, you can set up a username.map file. my ssh server went down so I can't check on it right now but it's just a file that maps a local ubuntu account to the xp account like
joe = mike

goggle it for more help, then you just add an option within your smb.conf file and point to where you stored the username.map file. good luck

---

