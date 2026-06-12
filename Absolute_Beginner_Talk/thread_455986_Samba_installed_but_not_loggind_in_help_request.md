---
title: "Samba installed but not loggind in help request"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by boardtc on 2007-05-27
Having come from Mandrake 9.2 I have installed 7.04 desktop a week ago I still have not achieved my goals - to use it as a lamp server in my house only for some php/mysql apps and as a samba server for backups.

I've pulled this request from my other post ([http://ubuntuforums.org/showthread.php?t=448732](http://ubuntuforums.org/showthread.php?t=448732)) where it got lost I think.

I have installed samba and set the domain as described on [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) My windows machine sees the box but I can't log in with my ubuntu username and password. Is there more up to date documentation than the above link which is for an older version, for example,
it talks about Windows Networking option being on the networks general tab which it is not.

It's my understanding I have to run "smbpasswd"...I tried a smbpasswd tom and nothing happened, looking at the help I tried smbpasswd -a -s tom but was not prompted for a password.

Any help to get samba installed is appreciated

Thanks, Tom.

---

### Post by RudolfMDLT on 2007-05-27
I think the command that you are looking for is

sudo smbpasswd

I'm not sure where you are in the whole setup process, but here is an old school solid way of setting up Samba server. Follow it and if it still doesn't work post back here and I'll see if I can get you out of your fix! :)


[http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing](http://ubuntuforums.org/showthread.php?t=202605&highlight=file+sharing)

Cheers,

Rudolf

---

### Post by boardtc on 2007-05-27
Thanks a lot. I followed all the instructions at that link but now my linux box does not show under mshome on my windows box ! On that page we have:

-> force user = YOUR_USERNAME
-> force group = YOUR_USERNAME

However the actual file has
-> force group = YOUR_USERGROUP

I now have
force user = tom
force group = tom

But should the later be different?

Also I did not change the enable wins in the config.But I am not sure my linux ip is static, How do I make it so, is that in my router setup?

And doing those setting on my wireless card, took me offline on my windows machine :-( I've tried reversing things on the windows box but that's still down, i can only get online on the linux box now. So much time spent on this today. Got to call it a night now i think, disaster, old school far from good school in this case for me.

---

### Post by RudolfMDLT on 2007-05-28
Hang in there! :) I', writing exams... so I'm gonna try my BEST to write you a complete from the start to finish how to for this Samba thing! If you get here before I post - do you want security or not? ie passwordless logins on that server or username and password control?

---

### Post by gary0 on 2007-05-28
Try this:

[global]
    ; General server settings
    netbios name = garyo-linux
    
    workgroup = Workgroup
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
    path = /home/MyShare
    
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gary
    force group = gary
available = no
browsable = yes
public = no
writable = no

Subsituting your name and workgroup. This is my smb.conf and I can see all the other pcs in my network, read and write to/from them etc. Don't forget to stop samba first - sudo /etc/init.d/samba stop 
and start it again after you've made the changes. sudo /etc/init.d/samba start. wins support is for other windows based systems on your network. If you have no windows machines on the network, set it to no. You must configure the windows machines by telling them where the wins server is. Go to network properties> tcpip> advanced> wins and enter the ip address of your ubuntu machine.

Gary.

---

### Post by RudolfMDLT on 2007-05-28
OKAY! :)

We are starting from scratch! 


open up the terminal and enter the following command:

**sudo /etc/init.d/samba stop**

press alt+f2 and type/copy in 

**gksu gedit /etc/samba/smb.conf**

now, I strongly suggest you can create a backup of this current file by saving it as something else, ie smb.conf.backup. if you do create a backup, make sure you open the origanal smb.conf file again before proceeding.

now, selectall in the editor and press delete. copy and paste the following:

[PHP]
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
;   security = user

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
[/PHP]

The above does not make assurances for domains as you didn't mention anything about PDC's and SDC's in your post and I doubt you are running Active Directory at home. It does how ever contain a WORKGROUP name and makes allowance for username and password Logins.

Scroll to the top and make sure that the workgroup is YOUR workgroup.  now save the file and exit.

in the terminal enter the following command:

[B]sudo /etc/init.d/samba start
[/B]

now point to System, Administration, Users and Groups. add a user called network or backup or tom. give this user a password and also if you wish make him a system admin.

now in the terminal enter the following two commands.
[B]
sudo smbpasswd -L -a *network*
sudo smbpasswd -L -e [I]network
[/I][/B]

with network being the exact to the case username that you entered in the user and groups manager.

now pick a folder or a couple to share. rightclick on respective folders, click share, and make sure you UNtick the read only flag. 

Lastly, open up the terminal, type ifconfig and make a note of your IP address.

In windows open up the network browser and see if your machine is there?... if not then the workgroup has been entered wrongly. in the address bar in Windows type in \\IPADDRESS of Ubuntu box. this must work.

> 
Also I did not change the enable wins in the config.But I am not sure my linux ip is static, How do I make it so, is that in my router setup?

static IP's are nice but you don't need them. You can have a static and dynamic IP on ONE network card in Linux you really wish! (A very handy trick windows can't do! :) ). But lets not go there right now - If you wish I can explain this later.

> 
And doing those setting on my wireless card, took me offline on my windows machine I've tried reversing things on the windows box but that's still down, i can only get online on the linux box now. So much time spent on this today. Got to call it a night now i think,

I have no idea what you are refereeing to - a little bit of detail would be helpful.

> old school far from good school in this case for me.

Come on! Nothing worth doing is ever easy! :) Just joking! Lets hope this can get you sharing files - I have struggeled myself with samba. The hole thing is actually rediculasly easy to setup once you know what you are doing. 

 post back and lets see if we can't get the wireless online! :)

Best of luck! I'll be online for about another 5 hours or so, so the sooner you get on it the better! :)

Cheers,

Rudolf

---

### Post by boardtc on 2007-05-28
Rudolf! What can I say, I followed your instructions, I did not add a user and just used tom that was there already and I set the password to my windows password. Then I went to MSHome on my windows box and the samba directory was there! No logging in needed even. Thanks so much for taking the time, especially being so busy. 

Your method seems a better option that the wins route, I know when it was working with mandrake before I did not use wins either.

To get my windows box online I had to run a wired connection as the efforts last night adding the wins stuff seemed to kill it. But then after a reboot the wireless worked again! I don't actually boot by xp pro machine a lot anymore, which says a lot how far windows has come.

Garu O as well, thanks you, i was going to try your instructions before Rudolph posted. 

To be honest I considered getting rid of the linux box after my efforts to upgrade from mandrake 9.2 did not reward but thanks to you 
now I'm very close.

Will try and restore my mysql/php apps now on the server (now I can get them from my windows box) and I am seeing light at the end of the tunnel....will post my progress.

Thanks again for your help, I'm very grateful :p

---

### Post by RudolfMDLT on 2007-05-28
Pleasure! =D>

Best of luck with the rest of you endeavors!

---

### Post by krambo on 2007-06-06
Thank you so much for your invaluable help RudolfMDLT - I was looking for just this information, having spent several hours trying to remember how to get my Linux box sharing with my Windows network.  Your solution worked first time and I am most grateful ;)

---

### Post by napoli3 on 2007-06-06
Too bad this thread wasn't started a few weeks earlier when I was trying to figure out Samba for my first time.:)

Nice work on the explaination RudolfMDLT!!

---

