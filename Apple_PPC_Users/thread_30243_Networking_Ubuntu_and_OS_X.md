---
title: "Networking Ubuntu and OS X"
date: 2005-04-27
forum: Apple PPC Users
---

### Post by dan1928 on 2005-04-27
I'm not sure if this is the right location for this question, but...
I currently have a WIn2k server that works well with my OS X powerbook through my LAN, but I am trying to add a second server box with Ubuntu (Hoary) installed. My problem is that while OS X can talk to the Win2k box just fine (and visa versa) and the Ubuntu box can also talk to Win2k just fine, the OS X box can't seem to connect to the Ubuntu box and visa versa. I'm using Samba for them all at this point.
Any ideas on what I may be doing wrong? A few notes, I have VNC running on all of them and I can log into any of them through VNC successfully. Also, my OS X is connected to the LAN wirelessly (not sure why that would matter...). OS X has firewall running but with windows sharing and personal file sharing enabled. I'm more familiar with OS X (and Windows) than Ubuntu at this point.

Thanks!

---

### Post by farruinn on 2005-04-28
Could you provide some more details on exactly how you're trying to connect to the Ubuntu box from OS X?  I don't use samba much, but my guess would be command-k from the Finder and enter "smb://<ip address of ubuntu box>".

---

### Post by dan1928 on 2005-04-29
ok, I guess I can connect by using the command-k and smb://computer/shared folder. Why is it that if I click on "network" in the finder window, it will show my ubuntu computer, but upon clicking it I get an error stating it can't be opened because the original item cannot be found? I can see my windows computers as well and upon double-clicking i get a user/password screen which allows me to connect to the windows computers, but i get the error for the ubuntu computer. If samba is the protocol used for all this (obviously samba is installed and working on ubuntu as I can connect), why can't I use the OS X network finder to connect to Ubuntu?

---

### Post by Ptero-4 on 2005-05-01
[QUOTE=dan1928]ok, I guess I can connect by using the command-k and smb://computer/shared folder. Why is it that if I click on "network" in the finder window, it will show my ubuntu computer, but upon clicking it I get an error stating it can't be opened because the original item cannot be found? I can see my windows computers as well and upon double-clicking i get a user/password screen which allows me to connect to the windows computers, but i get the error for the ubuntu computer. If samba is the protocol used for all this (obviously samba is installed and working on ubuntu as I can connect), why can't I use the OS X network finder to connect to Ubuntu?[/QUOTE]
 AFAIK samba allows you to hook a Windoze and a UNIX (Linux or OSX) box together but it can't connect two *NIX boxes to each other. This means that you can connect OSX (a *NIX) to Win2k and Ubuntu (a *NIX) to Win2k but not Ubuntu to OSX. To connect OSX and Ubuntu you need to use nfs sharing instead of samba.

Hope it help.

---

### Post by dan1928 on 2005-05-01
Well that is very helpful to know! No use ](*,) over samba then. I'll look into nfs. Thanks!

---

### Post by Tofu on 2005-05-03
I installed Netatalk on Ubuntu which got it talking to the OS X machine using Appletalk.

---

### Post by Disorder2 on 2005-05-05
[QUOTE=Ptero-4]AFAIK samba allows you to hook a Windoze and a UNIX (Linux or OSX) box together but it can't connect two *NIX boxes to each other. 
Hope it help.[/QUOTE]

Yes it can.
You install at least the Samba Server  on the server side and the samba client on the client side. Works fine.
I have two Ubuntu boxes here connected with Samba. No prob. And I see no reason why it shouldn't work with OS X but I'll try that out on the weekend hopefully.

The reason why I do not use Appltetalk between *NIX and Mac OS is because during the netatalk start at system boot you can can have a coffee,walk the dog *and* write your biography   ;-)

---

### Post by dan1928 on 2005-05-05
Per Tofu's suggestion, I messed a bit with netatalk and got my powerbook able to mount and access my ubuntu share. I've read a little about how using howl with netatalk enables the rendevous type features (e.g. itunes streaming, computer name broadcast...showing up in finders network, etc), but I haven't quite figured how to get it running on ubuntu yet (other than synaptic getting the packages).

If disorder2 can get it working through samba, i'd still be interested to know how, just to know and have more options. Thanks!

---

### Post by dan1928 on 2005-05-06
Hate to answer my own thread here but I got samba working for OS X. I guess I had everything properly configured, I just neglected to add my OS X user to the smbpasswd. I hate when it's something so simple... Thanks again.

---

### Post by Uta on 2005-06-15
could you explain exactly where (within) samba do you get to enter a user and password-- My Mac doesn't sees my Kubuntu laptop but my Kubuntu can see the shared folders on my iBook laptop-- Thanks.

---

### Post by dan1928 on 2005-06-16
I just used the terminal application within Ubuntu. The command is smbpasswd. It's described [here](http://ubuntuguide.org/#addeditdeletenetworkusers) in the Starter Guide. I added the root user for my Mac and everything works fine. I haven't tried adding and using one of the limited apple users, so I'm not sure if you need to use the root account or not.

---

### Post by Uta on 2005-06-16
I did this also and it didn't work. Nothing showed up in the Mac's network browser nor was I able to connect via smb://xxx.xxx.x.xxx Would you mind sharing your SAMBA config file (minus any sensitive IP addresses).Thank you! Do you actually see your LINUX share via the Mac's Network browser window?

---

### Post by sscotti on 2005-06-17
Hate to interrupt.  I'm sort of a newbie to Ubuntu, but quite a bit of Windoze and OS X experience.  I have an iMac that has firewire, USB, ethernet, modem and CD, but no DVD or burner.  I'd like to install Tiger on the iMac.  I have a DVD image of Tiger that I have on my Windoze machine (or Linux) and I'd like to use Ubuntu to act as a Netboot server in order to complete the install, plus I've never done that before.

There is a reference here:

[http://frank.gwc.org.uk/~ali/nb/](http://frank.gwc.org.uk/~ali/nb/)

I am up to step 4 in How to Do It.  Appletalk is installed and apparently working since I am able to connect using appletalk to the Ubuntu machine.

Just wondering if you had any advice, or should I just follow the directions (neat idea!) and see what happens.

/sds

---

### Post by dan1928 on 2005-06-18
Uta,
Yes I do see my Linux share via the mac network browser (by the way, I'm using 10.3.9 if I didn't already mention that). As far as my smb.conf file goes, here it is:

##############################################
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
   workgroup = HOMELAN

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
;   security = user

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

[ServerShare]
path = /servershare
available = yes
browseable = yes
public = yes
writable = yes

##################################################

The last 6 lines I added as the folder (named "servershare") that I use for sharing on my Ubuntu box (its permissions are set to everyone and it is shared via the administration gui tool).

As for sscotti's question to netbooting, other than setting up appletalk between my osx and ubuntu box, I haven't had an experience with what you are trying to do. The how-to you found is more help than I could offer. Good luck!

p.s. I stuck with Samba rather than appletalk as the os x finder/network browser uses samba. Since I use windows, osx and ubuntu all on my network, I wanted something where they could all talk and see each other and as far as I know samba is the only one/easiest one to use.

---

### Post by Uta on 2005-06-18
Thanks for the info, I will retackle the server issue. I would be very curious to know about your Ubuntu share folder, how was it created, the file system, is it a seperate partition? I have recently installed a 2nd HD(on my Linux laptop) and have decided I want to share it with both the Mac and Linux OS. From others comments it seems to be generally suggested to create a FAT32 file system or if I have the formatting tools to make it HFS+
What did you do? Again thanks...

---

### Post by dan1928 on 2005-06-19
Actually I haven't yet gotten to the point of adding a second harddrive and sharing it entirely. My folder "servershare" is simply a created folder at /servershare located at root (you can't create folders there through the gui as far as i can tell, so i had to use the terminal + sudo). I am planning on adding two harddrives in a raid array and sharing them as the main server shares (my current "servershare" folder is just to get things working first). While I haven't done it yet, a friend of mine has done just that only using windows and he formatted his raid drives using ReiserFS. He has a linux server and windows2000 clients, so while I personally haven't done it, I know he has them all working together. I'm not sure how OS X plays with reiserfs, so I don't know if it will work for me... I guess Fat32 would work otherwise (windows and mac can both read the current ext3 in ubuntu, so maybe thats an option too). If you are planning on dualbooting that machine and running windows on it then fat32 would be your choice... hope some of this helps.

---

### Post by Uta on 2005-06-19
mmm...so you are able to share a folder @ root level, obviously a Linux file system, what exactly are the permisions on this folder? Thanks!
--Ok I got as far as getting the Linux shares to show up in the Mac's network browser but ran into the same problem you did previously...clicking on the alias and the original folder can't be found. How do I trouble shoot that? Thanks--

---

