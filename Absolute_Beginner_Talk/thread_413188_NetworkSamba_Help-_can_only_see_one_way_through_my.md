---
title: "Network/Samba Help- can only see one way through my network"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by joshjani on 2007-04-18
OK- got my network printer working, did a big update for Ubuntu, and got my Ubuntu box to see everyone else on my windows network. But I cannot see the Ubuntu box from any other PC. I got very close- I tried adding a network place in windows, where I browsed for the place I wanted- the shared folder I left on the Ubuntu box. When I clicked workgroups, I had Iggynet(my network) and MSHOME to choose from. MSHOME only contains the ubuntu-pc, but I can't go any further. If I try to log in with my Ubuntu login name and password, nothing happens. 

Trying to navigate to ubuntu-pc from a Mac also gives similar results- I can see SOMETHING there, but not what I want, and not in the workgroup I want it in, IGGYNET, not MSHOME.

So how do I make the Ubuntu-pc live in IGGYNET?

I have samba installed, and was able to make shares, but I don't know how to configure or use it. When I look at the samba.conf file, I see a reference to MSHOME in there, and somewhere I read that I need to edit that to be my workgroup. Is this right?

Please help- I'm almost there!

JC

---

### Post by Sirhanz on 2007-04-19
I have a similar problem. I have set up samba in ubuntu 6.06lts and i am trying to connect with an old imac 9.2. I can see the shared folder on the mac from my linux box, but can not see the lin box from the mac. I know very little about macintosh and to be honest i do not have the patience to try to explore it. Any info to help is much appreciated. I want to be able to stream my amarok through the mac and also share ordinary files as well. TYVVM in advance

---

### Post by dfox8895 on 2007-04-19
yes, windows will not recognize share outside of its work group.  I rewrote my samba config by hand ( easier way is to use webmin)  You have to change the work group and give your share directories read/write permissions.

Here is my Config file that you can use as a template:

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
	log file = /var/log/samba/log.%m
	guest account = michael
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	obey pam restrictions = yes
	preserve case = yes
	socket options = TCP_NODELAY
	encrypt passwords = true
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	wins support = yes
	netbios name = SHAKA2006
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	only user = yes
	unix password sync = no
	workgroup = TEHUTI
	os level = 20
	valid users = michael,root,@michael,@root
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	short preserve case = yes
	max log size = 1000

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
# I added the following lines to the config.
; encrypt passwords = yes
; socket options = TCP_NODELAY IPTOS_LOWDELAY
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
;  dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).

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

;wins support = no
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


[Movies]
path = /home/michael/Ubuntu_Main/Movies
comment = Movies and Stuff
available = yes
browseable = yes
public = yes
writable = no

[Torrents]
path = /home/michael/Ubuntu_Main/Torrents
comment = Put all downloaded torrents here
available = yes
browseable = yes
public = yes
writable = yes

[Pictures]
path = /home/michael/Ubuntu_Main/Pictures
comment = Put all downloaded pictures here
available = yes
browseable = yes
public = yes
writable = yes

[Library]
path = /home/michael/Ubuntu_Main/Documents
comment = Put all downloaded documents here
available = yes
browseable = yes
public = yes
writable = yes
############################################3
 Granted this is not the most secure config. , but it works.  After you set this up you should be able to add it as a network drive in windows

---

### Post by scxtt on 2007-04-19
on ubuntu do:

sudo smbpasswd -a <existing username you want to use>
i.e. sudo smbpasswd -a dfox8895

then use that to "map a network drive", etc. ...

---

### Post by joshjani on 2007-04-19
> **dfox8895 said:**
> yes, windows will not recognize share outside of its work group.  I rewrote my samba config by hand ( easier way is to use webmin)  You have to change the work group and give your share directories read/write permissions.

Here is my Config file that you can use as a template:

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
	log file = /var/log/samba/log.%m
	guest account = michael
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	obey pam restrictions = yes
	preserve case = yes
	socket options = TCP_NODELAY
	encrypt passwords = true
	passdb backend = tdbsam guest
	passwd program = /usr/bin/passwd %u
	wins support = yes
	netbios name = SHAKA2006
	writeable = yes
	server string = %h server (Samba, Ubuntu)
	only user = yes
	unix password sync = no
	workgroup = TEHUTI
	os level = 20
	valid users = michael,root,@michael,@root
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	short preserve case = yes
	max log size = 1000

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
# I added the following lines to the config.
; encrypt passwords = yes
; socket options = TCP_NODELAY IPTOS_LOWDELAY
# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
;  dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).

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

;wins support = no
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


[Movies]
path = /home/michael/Ubuntu_Main/Movies
comment = Movies and Stuff
available = yes
browseable = yes
public = yes
writable = no

[Torrents]
path = /home/michael/Ubuntu_Main/Torrents
comment = Put all downloaded torrents here
available = yes
browseable = yes
public = yes
writable = yes

[Pictures]
path = /home/michael/Ubuntu_Main/Pictures
comment = Put all downloaded pictures here
available = yes
browseable = yes
public = yes
writable = yes

[Library]
path = /home/michael/Ubuntu_Main/Documents
comment = Put all downloaded documents here
available = yes
browseable = yes
public = yes
writable = yes
############################################3
 Granted this is not the most secure config. , but it works.  After you set this up you should be able to add it as a network drive in windows

Whwew! Thanks for all of this, I appreciate the trouble you went to, but as an absolute noob to ubuntu- and completely clueless with Samba, I can't make sense of this. I realize I have to change some stuff like:

[I]guest account = michael
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %
netbios name = SHAKA2006
workgroup = TEHUTI
valid users = michael,root,@michael,@root[/I]

But I'm just not sure what all else I have to do or modify. All I really want is for my ubuntu-pc to be forced into the only network I have here, IGGYNET. Can you (or anyone else) explain or highlight what I need to change?

---

### Post by dfox8895 on 2007-04-19
> **joshjani said:**
> Whwew! Thanks for all of this, I appreciate the trouble you went to, but as an absolute noob to ubuntu- and completely clueless with Samba, I can't make sense of this. I realize I have to change some stuff like:

[I]guest account = michael
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %
netbios name = SHAKA2006
workgroup = TEHUTI
valid users = michael,root,@michael,@root[/I]

But I'm just not sure what all else I have to do or modify. All I really want is for my ubuntu-pc to be forced into the only network I have here, IGGYNET. Can you (or anyone else) explain or highlight what I need to change?

-----------------------------------------------------------------------------------------------------------------------------

Backup the existing config and then edit it using your favorite text editor. You should be able to right-click on the file and edit it using root permissions

Then:

Under Global Settings change the netbios name (line 12) to the name of your PC.

**netbios name = YourComputer**

Under Global Settings change the server string (line 14) to:

**server string = %h server (YourServer)**

Under Global Setting change the workgroup (line 17) to:

**workgroup = IGGYNET**

Under Global Setting change valid users (line 19) to:
[B]
valid users= yourusername,root,@yourusername,@root [/B]

Under share definitions, starting at [Movies], you reference actual system folders that you want shared on the SAMBA network.

[Movies]  <-- header

path =/home/michael/Ubuntu_Main/Movies  <--- the actual location of the directory.

comment = Movies and Stuff <--- descriptive statement.

available=yes <--can you use it.

browseable=yes <--can you browse for the directory

public=yes <--can it been seen by everyone 

Writable=no <---can you write to it. ( I wanted the directory to be seen by others on the network but I didn't want them to add stuff to this folder or erase the contents of the folder)

create all of these shares within the home directory first and then append them to this part of the file.  

There are hundreds of ways to configure Samba, this is just one.



Then as scxtt stated 
[B]
sudo smbpasswd -a <existing username you want to use>[/B]
i.e. **sudo smbpasswd -a dfox8895**

then use that to "map a network drive", etc. ...

---

### Post by joshjani on 2007-04-19
Awesome- I'll try this, but just one more question- you said change this:

server string = %h server (YourServer)

I'm sorry, but I don't know what my server is. I have all my PCs on a broadband router. Is it the IP of the router???

*(You're probably, in your Napoleon Dynamite voice, going "Dang! Idiot! Gosh!") *

---

### Post by dfox8895 on 2007-04-20
It's just a banner that you will see when browsing the samba shares, you can name it anything you want.

Thanks

---

### Post by joshjani on 2007-04-20
OK- thanks for the help, I'll give it a try and post back the results!

---

### Post by 3rdgear on 2007-04-20
This has helped me everytime I install ubuntu (which seems to be quite often these days)

HOWTO: Setup Samba peer-to-peer with Windows
[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by joshjani on 2007-04-21
This is what I got when I did:

sudo smbpasswd -a <existing username you want to use>
i.e. sudo smbpasswd -a dfox8895

Except with my password:


No builtin nor plugin backend for tdbsam guest found
PANIC (pid 6654): pdb_get_methods_reload: failed to get pdb methods for backend tdbsam guest

BACKTRACE: 7 stack frames:
 #0 smbpasswd(log_stack_trace+0x22) [0x8105f42]
 #1 smbpasswd(smb_panic+0x43) [0x8106023]
 #2 smbpasswd [0x80c86da]
 #3 smbpasswd(initialize_password_db+0xe) [0x80c872e]
 #4 smbpasswd(main+0x532) [0x807a342]
 #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c40ebc]
 #6 smbpasswd [0x80799a1]
smb_panic(): calling panic action [/usr/share/samba/panic-action 6654]
smb_panic(): action returned status 0
Aborted (core dumped)

I haven't tried the link yet- but it's beautiful outside today, and I don't want to stay in on the PC! I'll try some more later- Thanks for everything so far.
JC

---

