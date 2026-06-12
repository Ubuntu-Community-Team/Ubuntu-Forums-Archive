---
title: "Samba was working, now it's not!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-05-13
I was able to share certain folders with my windows machines last night. as of this morning I cannot. It's just giving me access permission denied or something. 

Here is my smb.conf file. Any help would be greatly appreciated!

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
   workgroup = Ubuntu

# server string is the equivalent of the NT Description field
   server string = Mecca

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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
security = share
#username map = /etc/samba/smbusers

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


[download]
comment = Download
path = /media/hdb1/home/FTP-shared/download
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[upload]
comment = Upload
path = /media/hdb1/home/FTP-shared/upload
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[public]
comment = Public
path = /media/hdb1/home/public
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

```

---

### Post by nickpaton on 2007-05-13
Lots of ideas come to mind, but the first one is to disable the built in firewall iptable using the GUI Firestarter.

If you haven't got Firestarter installed then it can be found in Synaptic.

Get back to me if still no suceess and we can have a look at some of the Samba settings.

---

### Post by Dr Small on 2007-05-13
I had the same problem [here](http://ubuntuforums.org/showthread.php?t=352044)

Dr Small

---

### Post by nickpaton on 2007-05-13
Firestarter can be a little daunting to set up, but is actually straight forward.

Identify the IP addresses of all your PC's - I suggest accessing your router and looking under attached devices section.

For each Ubunutu PC, start up Firestarter and click on Policy tab.

"Editing", select "Inbound Traffic Policy".

Click in box, "Allow connections from host"

Click on "Add Rule" (+ sign).

"IP, host or network", put in the IP address of one of the other PC's.  Add.

Repeat for each of the other PC's.

When you've done this section, click on the "Apply Policy" button at the top.

When finished click within bottom box, "Allow Service..port..For.."

"Name", Samba (smb).

and select bullet, "when the source is anyone".  Add.

Click on Status box again now try accessing your other PC's.

I would appreciate anyone checking / adding / correcting this.

---

### Post by Dr Small on 2007-05-13
[quote=nickpaton]I would appreciate anyone checking / adding / correcting this.[/quote]
You got it right. ;)
That's what I had to do to get my samba to share folders with other network systems. :D

Dr Small

---

### Post by nickpaton on 2007-05-13
> **Dr Small said:**
> You got it right. ;)
That's what I had to do to get my samba to share folders with other network systems. :D

Dr Small

Actually not quite - I'm about to amend to click on the "Apply policy" button which I missed out, but many thanks for checking!

---

### Post by Dr Small on 2007-05-13
> **nickpaton said:**
> Actually not quite - I'm about to amend to click on the "Apply policy" button which I missed out, but many thanks for checking!
But that's just common sense.......

---

### Post by nickpaton on 2007-05-13
> **Dr Small said:**
> But that's just common sense.......

Wanna bet:lolflag:

---

### Post by nickpaton on 2007-05-13
@Homerj742 - I've been having a look at your permissions in your smb.conf and with those 0777 settings I too am not able to access my XP boxes, even with the firewall down and everything rebooted.

Also your smb.conf seems V complicated, possibly causing some confusion somewhere (apologies if you are a network guru BTW) but in case it helps I've set my PC's (2 off XP's and 2 off Ubuntu's), so that every PC can access every other PC using [this]("http://ubuntuforums.org/showthread.php?t=202605") post as a basis.

Notice that Stormbringer who has kindly put the HOWTO together suggests static IP's for all the PC's, and makes setting up Samba and the windows PC's much easier.  
I'll come onto how you can do this at the end.

To help you a little, this is a copy of my smb.conf based on the HOWTO:

```
[global]
    ; General server settings
    netbios name = YOUR_PC_NAME
    
    workgroup = YOUR_WORKGROUP_NAME
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
    path = /home/nick/samba
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = 
    force group = 
available = yes
browsable = yes
public = yes
writable = no
```

The most obvious differences are at the end where there is nothing filled in for force user and group, and 4 extra lines added at the end of the section.

As it stands, when you try to access a Linux PC from a Windows PC, the windows PC will ask you for your Linux username and password.
If you do not want the Windows PC to do this, in the above script change 

> security = user

to

> security = share

and remember to save and close down your smb.conf.

Restart Samba with

```
sudo /etc/init.d/samba restart
```

Regarding simply obtaining static IP's for each PC, again using your router, go to the section which reserves addresses for each PC as it's switched on.  This effectively is the same as each PC having a static IP address.

Again anyone want to add etc feel free.

---

### Post by homerj742 on 2007-05-13
Thank you for all the responses. FYI, I have already used my router to assign static IPs (reservations). 

The last Samba server I setup, I never remember having to install a firewall. but I will give it a shot and let you know of my findings!.

---

### Post by nickpaton on 2007-05-13
> **homerj742 said:**
> Thank you for all the responses. FYI, I have already used my router to assign static IPs (reservations). 

The last Samba server I setup, I never remember having to install a firewall. but I will give it a shot and let you know of my findings!.

Ubuntu by default installs a firewall called iptables which is by default enabled.

You need to install a GUI front end called Firestarter to easily manipulate the firewall settings.

Let me know how you get on.

---

### Post by homerj742 on 2007-05-13
Installed, and I enabled internet connection sharing....

Now it's not even showing up in "my network places" when I look in my windows xp box.

---

### Post by nickpaton on 2007-05-13
Fire up Firestarter.

File > Run Wizard > Forward > Detected Devices (select whatever LAN port you are using) > Forward > deselect "Enable Internet Connection Sharing" > Forward > Start Firewall Now > Save >  Quit.

Then when Firestarter starts, disable it. by clicking on the "Stop Firewall" button.

Minimise but DO NOT close Firestarter.

Now have a look on your Windows PC.

If you have been doing a lot of playing around with both PC's it may be worth doing a reboot of both PC's and then stopping Firestarter as above.

Have you been doing anything to Samba or just to the firewall?  If you have been changing Samba as per my previous post have you also configure the netbios settings in Windows as described in Stormbringers post?

---

### Post by homerj742 on 2007-05-13
Ok, I can see the folder I'm trying to share now. but it won't let me access it. 

smb.conf:

```
# Samba config file created using SWAT
# from 192.168.1.5 (192.168.1.5)
# Date: 2007/05/13 11:55:40

[global]
    ; General server settings
    netbios name = Mecca
    
    workgroup = UBUNTU
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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

;[print$]
    ;path = /var/lib/samba/printers
    ;browseable = yes
    ;guest ok = yes
    ;read only = yes
    ;write list = root
    ;create mask = 0664
    ;directory mask = 0775

;[printers]
    ;path = /tmp
    ;printable = yes
    ;guest ok = yes
    ;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[FTP-Shared]
    path = /media/hdb1/home/FTP-Shared
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = 
    force group = 
available = yes
browsable = yes
public = yes
writable = no

```

---

### Post by homerj742 on 2007-05-13
It's crazy, last night I did a fresh install of Dapper. 

1) Setup Samba = worked
2) Setup Gnump3d = worked
3) Setup Proftpd = worked

this morning, NOTHING was working.

---

### Post by nickpaton on 2007-05-13
Re: workgroup = UBUNTU

You need to specify the workgroup for the Windows PC not the Ubuntu one.

To check the workgroup name, on your Windows box, My Computer > My Network Places > Entire Network > Microsoft Windows Network > Mshome (on my Windows PC).

Insert whatever name you have and save and close the smb.conf file.

Restart smb 

```
sudo /etc/init.d/samba restart
```

and try again in Windows.

Also I'm assuming you are using XP, is that correct?

---

### Post by nickpaton on 2007-05-13
> **homerj742 said:**
> It's crazy, last night I did a fresh install of Dapper. 

1) Setup Samba = worked
2) Setup Gnump3d = worked
3) Setup Proftpd = worked

this morning, NOTHING was working.

You're 110% sure Firestarter is stopped?  Yeah I know silly question, but it's worth the ask LOL!

You can see that big fat red circle with a black box in the middle in your top right panel?

---

### Post by homerj742 on 2007-05-13
Indeed, I'm using XP, I have the workgroup for windows already set to ubuntu. I can browse to the actual folder using "My Network Places", but get a denied message when trying to open the folder...

---

### Post by nickpaton on 2007-05-13
Just to confirm - the immediate next folder down after Microsoft Windows Network is Ubuntu on the XP box

EDIT: To clarify  - Mine is called Mshome then next directories down are nick_laptop (this ubuntu box / lappy), home (my XP box) etc.

It's just an unusual name to call the Windows Workgroup

---

### Post by homerj742 on 2007-05-13
> **nickpaton said:**
> Just to confirm - the immediate next folder down after Microsoft Windows Network is Ubuntu on the XP box

EDIT: To clarify  - I have Mshome then next directories down is nick_laptop (this ubuntu box / lappy), home (my XP box)

It's just an unusual name to call the Windows Workgroup

Yes it is.

Do you think there might be a deeper problem. I mean I had this thing setup with all those functions last night, and now it's not working. Is something corrupt? a fresh install needed?

---

### Post by nickpaton on 2007-05-13
2 secs got an internet problem!

---

### Post by nickpaton on 2007-05-13
No I think it's the joy of networking LOL!

First off, do you have something like Norton or another firewall on XP which you could try disabling?  And the Windows one for good measure.

Can we run through your Windows IP Settings (sorry Grandmothers and sucking eggs but the problem has got to be somewhere around here).

So....

Start > Control panel > Network Settings > hover over the LAN network card you are using and right click.

left click Properties > single left click Internet protocol (TCP/IP) > properties > Advanced > WINS

Add.... WINS Server and add the IP address of your Ubuntu box > Add.  It should now appear in the previous box.
Enable NetBIOS over TCP/IP

OK > OK > Close.

And I would now suggest a reboot of both PC's.

Fingers crossed...


Sorry for the delay - I do need to go to bed in a minute - if this doesn't work can we pick up tomorrow after 9.30 pm UK time?

---

### Post by homerj742 on 2007-05-13
I really appreciate all of your help! Please don't stay up on the count of me! I will post the info here asap, and you answer whenever is most convenient for you. :)

---

### Post by nickpaton on 2007-05-13
Sorry M8 must go but will catch up tomorrow.

G'nite

Nick

---

### Post by homerj742 on 2007-05-13
I just copied my original smb.conf file and redid the settings from scratch. It works now!

Next step is to get proftp working right. I can connect via filezilla, but not via IE.

---

### Post by nickpaton on 2007-05-14
Excellent news!

---

