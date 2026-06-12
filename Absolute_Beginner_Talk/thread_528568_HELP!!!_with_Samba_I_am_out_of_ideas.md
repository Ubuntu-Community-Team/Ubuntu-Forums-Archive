---
title: "HELP!!! with Samba I am out of ideas"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by D_2 on 2007-08-18
I have been looking around on these forums and talking with others about my Samba shares. I have 2 windows computers one running XP and the other running Vista. On both systems I can read only the one directory that I have shared and that is the /var/www directory. I am trying to setup a webserver. I have 7.04 server installed and LAMP. Ok like I said on both boxes I have read only permisions but I need write so I can copy some files from my Windows boxes to my webserver. Also on my Vista box it does ask me for a username and password but not on my XP box, under networking it just shows the VAR directory as being shared.
I hope someone here can help me get this fixed. Below is my smb.conf file if it looks messed up its because I have tryed different things to get the write permision going.


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
	log file = /var/log/samba/log.%m
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	encrypt passwords = yes
	passdb backend = tdbsam
	dns proxy = no
	browseable = yes
	server string = %h server (Samba, Ubuntu)
	writable = yes
	invalid users = root
	default = var
	workgroup = WORKGROUP
	os level = 20
	comment = Home Directories
	security = user
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

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

# Put a capping on the size of the log files (in Kb).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

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

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.

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


[var]
	locking = no
	write list = damon,@admin,@damon
	path = /var/www
	comment = Web Directory
	valid users = damon,@admin,@damon
	create mode = 777
	browsable = yes
	directory mode = 777

---

### Post by HermanAB on 2007-08-18
Uhhh, it seems like you are confusing Apache and Samba?

Here is a general purpose Samba debugging guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by hyper_ch on 2007-08-18
Here's my samba config. It's pretty straight forward:

```

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/hyper/Appz

```

first of all, I use 10.x as private network and I don't want that from the outside it can be accessed, so 10.0.0.1 belongs to my router and is denied ;)

the workgroup name of windows is "WORKGROUP"

Then I have two folder shared. One with write permissions and one with read-only.

In the Exchange folder I force a username and groupname so that files will be stored as my user.

It's straight forward and it's working.

Regaring the issue that you can connect with WinXP without telling a username/pwd --> maybe you have already stored that information in your WinXP Settings.

---

### Post by D_2 on 2007-08-18
> **HermanAB said:**
> Uhhh, it seems like you are confusing Apache and Samba?

Here is a general purpose Samba debugging guide:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

I do know the difference between Apache and Samba. Apache is what controls my webserver and Samba is what lets my windows talk with my Linix system.

[QUOTE=Hyper_ch] Here's my samba config. It's pretty straight forward:


Code:
[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[appz]
comment = Appz
path = /home/hyper/Appzfirst of all, I use 10.x as private network and I don't want that from the outside it can be accessed, so 10.0.0.1 belongs to my router and is denied 

the workgroup name of windows is "WORKGROUP"

Then I have two folder shared. One with write permissions and one with read-only.

In the Exchange folder I force a username and groupname so that files will be stored as my user.

It's straight forward and it's working.

Regaring the issue that you can connect with WinXP without telling a username/pwd --> maybe you have already stored that information in your WinXP Settings. 
[/QUOTE]

I tried what you said and it is still no go. I for some reason only have read access. I did restart both windows computers and they both do ask for a user name and password and then I can browse the files.
This is how my directory share reads now after I did some changes

[var]
                 locking = no
                 write list = damon,@admin,@damon
                 path = /var/www
                 comment = Web Directory
                 force user = damon
                 force group = damon
                 browsable = yes
                 read only = no


any other ides to for me to get write access?

---

### Post by hyper_ch on 2007-08-19
please paste this output:

```

ls -al /var/www

```

---

### Post by D_2 on 2007-08-19
ok I did the ```
ls -al /var/www
``` command and this is what I get back

```
total 16
drwxr-xr-x  4 root root 4096 2007-08-14 01:08 .
drwxr-xr-x 17 root root 4096 2007-08-14 01:00 ..
drwxr-xr-x  2 root root 4096 2007-08-02 15:35 apache2-default
lrwxrwxrwx  1 root root   22 2007-08-13 22:00 phpbb -> /usr/share/phpbb2/site
lrwxrwxrwx  1 root root   21 2007-08-14 00:15 phpmyadmin -> /usr/share/phpmyadmin
drwxr-xr-x  2 root root 4096 2007-08-14 01:09 webalizer
```

I know what the ls command is for but not sure what the -al does, execpt it shows different information than the normal ls command would do.

---

### Post by hyper_ch on 2007-08-19
only root can write to the "www" folder... so you will need to change those permissions...

---

### Post by D_2 on 2007-08-19
> **hyper_ch said:**
> only root can write to the "www" folder... so you will need to change those permissions...

ok I would be happy to do so, but can you tell me how that is done?

---

### Post by hyper_ch on 2007-08-19
there are varioues ways... either by chaning the owner of the /var/www folder or group or the acual permissions...

simplest thing - but not best would be:

```

sudo chmod 0777 /var/www

```

---

### Post by D_2 on 2007-08-19
ok I might have shot myself in the foot, but I did go and start looking around on the forums on how to change the file permisions and what I found to do is 
```
sudo chmod -R damon:damon /var/www
```
 
and this is what happened
 
```
total 16
drwxr-xr-x  4 damon damon 4096 2007-08-14 01:08 .
drwxr-xr-x 17 root  root  4096 2007-08-14 01:00 ..
drwxr-xr-x  2 damon damon 4096 2007-08-02 15:35 apache2-default
lrwxrwxrwx  1 damon damon   22 2007-08-13 22:00 phpbb -> /usr/share/phpbb2/site
lrwxrwxrwx  1 damon damon   21 2007-08-14 00:15 phpmyadmin -> /usr/share/phpmyadmin
drwxr-xr-x  2 damon damon 4096 2007-08-14 01:09 webalizer

```
 
then I saw your reply and I did run it but its still the same as above, but I did go back and see if now I can reght to a directory in the www area and it still says I can't.

---

### Post by D_2 on 2007-08-20
ok after much looking around and going to each directory and doing chown I am now starting to be able to wright to the directories that i am wanting to. I am not sure why the chown -R isn't working so it does all of the subdirectories of the /var/www but I now know what I am needing to do for the others that I run accross that I can't either access or write to.
 
Thanks for all of your help Hyper_ch

---

