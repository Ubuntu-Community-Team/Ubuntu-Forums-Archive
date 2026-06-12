---
title: "Samba problems"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by SpikeyMike on 2007-07-23
Having read and tried a few 'how to' guides on setting up Samba to allow sharing between windows and ubuntu I agree with alot of posts that there is alot of confusing and sometimes conflicting info. I have just reinstalled samba and configured it as shown below, now on my windows machine I see ubuntu in the workgroup, it shows up as 'MyUbuntu(Myubuntu)' I am not sure why the part in brackets is shown. When I try opening it I just get an error message saying I do not have the right permissions to go there. Can anyone help??????/

Spikey



[SIZE="1"]# Sample configuration file for the Samba suite for Debian GNU/Linux.
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
   workgroup = STUDIO54

  

# server string is the equivalent of the NT Description field
    server string = MyUbuntu

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

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
;   security = share

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
   comment = Home Directories
   browseable = yes
   writeable = yes

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
[/SIZE]

---

### Post by philter on 2007-07-23
I'm not an expert but I believe the lines below will set your samba share password to whatever your username and password are for the server. The earlier portion of the config also invalidates logging into your samba share as root.

```
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
```

I think what you want to do in Windows is put \\MyUbuntu\<your username> into the explorer address bar and it will open a password dialog. From there enter the login info you use to login to the server.

---

### Post by kirios on 2007-07-23
[COLOR="DarkRed"]Have a look at this thread:[/COLOR]
[http://ubuntuforums.org/showthread.php?t=505289&highlight=samba&page=2](http://ubuntuforums.org/showthread.php?t=505289&highlight=samba&page=2)

---

### Post by SpikeyMike on 2007-07-24
Thanks for your replies, I have tried everything here including the youtube tutorial but no luck, when I go to menu > places > network  on my ubuntu pc I see 'windows network' but when I click on the icon it just doesn't do anything, I am unable to open it. also on my windows pc I can see ubuntu but I am unable to open it. I was wondering, I have installed samba but do I also need samba-server in order to share ubuntu on my home network?

Spikey

---

### Post by SpikeyMike on 2007-07-24
ok, I managed to connect from windows to linux, I had to configure firestarter to allow samba, the problem is I still cannot connect from ubuntu to windows, when I open places > network I see an icon for the windows network but I cannot do anything with it, if I click on it nothing happens. Any ideas?

Spikey

---

### Post by SpikeyMike on 2007-07-29
anyone? :confused::confused:

---

### Post by Koybe on 2007-07-29
Try to open a nautilus windows, hit CTRL+L and type this in the address bar :
smb://name_of_your_windows_xp_computer/name_of_your_share

---

### Post by SpikeyMike on 2007-07-29
> **Koybe said:**
> Try to open a nautilus windows, hit CTRL+L and type this in the address bar :
smb://name_of_your_windows_xp_computer/name_of_your_share

Thanks for your reply, I typed sudo nautilus in the terminal and then tried what you said but it just kept giving this error message:

[I]Nautilus cannot display "smb://joey/SharedDocs".

Please select another viewer and try again.[/I]


Spikey

---

### Post by llamaGod on 2007-07-29
> **SpikeyMike said:**
> Thanks for your reply, I typed sudo nautilus in the terminal and then tried what you said but it just kept giving this error message:

[I]Nautilus cannot display "smb://joey/SharedDocs".

Please select another viewer and try again.[/I]


Spikey

i've been playing around with ubuntu for a while now... and i'm quickly becoming a HUGE fan - i've got a couple computers networked together and i'm trying to set one up ubuntu - i've got a shared folder that i am trying to access with samba and i'm running into the same problem. 

i'm relatively new at linux (i've installed a bunch of distros, but never really did much with them - now i'm trying to take my knowledge to the next level).

thanks

---

### Post by jimrz on 2007-07-29
> **SpikeyMike said:**
> Thanks for your replies, I have tried everything here including the youtube tutorial but no luck, when I go to menu > places > network  on my ubuntu pc I see 'windows network' but when I click on the icon it just doesn't do anything, I am unable to open it. also on my windows pc I can see ubuntu but I am unable to open it. I was wondering, I have installed samba but do I also need samba-server in order to share ubuntu on my home network?

Spikey   

edit smb.conf to change the "server string" line under "Browsing/Identification" to look like
```
server string = %h server (Samba, Ubuntu)
```

this will now show the computer name of your server and that it is a samba server running ubuntu, instead of the current MyUbuntu. of course, if your puter name = MyUbuntu it won't help much :)

---

### Post by SpikeyMike on 2007-07-30
> **jimrz said:**
> edit smb.conf to change the "server string" line under "Browsing/Identification" to look like
```
server string = %h server (Samba, Ubuntu)
```

this will now show the computer name of your server and that it is a samba server running ubuntu, instead of the current MyUbuntu. of course, if your puter name = MyUbuntu it won't help much :)

Hi, smb.conf already has that for the server string, in 'Network Settings' the host name is set to MyUbuntu so now on my windows machine ubuntu shows up as:

MyUbuntu server (Samba, Ubuntu)(Myubuntu)

I am not sure where the last part in brackets comes from with ubuntu spelt with a small letter (Myubuntu) but anyway I can access the ubuntu pc from windows, despite it taking a while to appear when I start both computers, sometimes it can take about 5 minutes before I can see the ubuntu pc from windows, and I am still unable to access windows from ubuntu, any ideas?

Spikey (confused)

---

### Post by qpieus on 2007-07-30
OK, dumb question time. You did set up a shared folder on your windows pc, right? Another thing - is there a firewall on the windows pc that is blocking access to it?

So my suggestions are:
1. Verify a shared folder exists on the windows pc
2. turn off the firewall on the windows pc while you are troubleshooting this problem.

---

### Post by SpikeyMike on 2007-08-01
> **qpieus said:**
> OK, dumb question time. You did set up a shared folder on your windows pc, right? Another thing - is there a firewall on the windows pc that is blocking access to it?

So my suggestions are:
1. Verify a shared folder exists on the windows pc
2. turn off the firewall on the windows pc while you are troubleshooting this problem.

Hi, thanks for your reply, I have the normal shared documents folder on the windows pc and I have now added another one and shared it to see if that makes a difference but it doesn't. I also tried turning off the firewall but it doesn't help. When I open Network on ubuntu I can see 'Windows Network' but am unable to do anything with it, if I click on it nothing happens, I really want to get this working but I just cannot figure it out. I am sure it is something really simple
Any help appreciated...........

Spikey

---

### Post by calvin81 on 2007-08-01
Hi, I am new to ubuntu and i have been using it for few weeks.

since someone open a topic on samba, i would like to ask some question about it.

Below is my smb.conf

> [global]
   ; General server settings
   netbios name = ubuntu
   server string = cUbuntu
   workgroup = MSHOME
   announce version = 5.0
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

   passdb backend = tdbsam
   security = share
   null passwords = true
   name resolve order = hosts wins bcast

   wins support = yes

   printing = CUPS
   printcap name = CUPS

   syslog = 1
   syslog only = yes

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



[ubuntu]
path = /home/calvin/sharefolder
available = yes
browsable = yes
public = yes
writable = yes

 

My problem is, I am able to share my files with windows xp using share smb but what ever files written by windows xp in ubuntu 7.04 shared folder has nobody as the file ownership. This make me unable to edit or delete the files or folder.

If there is any related information in any part of this forum, please direct me to there else please advice on this matter.

Thank you,

Calvin

---

