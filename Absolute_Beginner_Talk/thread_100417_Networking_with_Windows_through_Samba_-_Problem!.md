---
title: "Networking with Windows through Samba - Problem!"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by kilps on 2005-12-07
Hi all - I have finally gotten my Winmodem to work and am now trying to connect to my Windows XP computer via Wireless ... I am following the instructions at [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29) and have gotten to the stage were I need to fill in my settings for the Windows workgroup etc. - Problem is (as someone has mentioned) I do not see a windows networking section :confused: - any ideas would be appreatiated - thanks

---

### Post by BatsotO on 2005-12-07
sudo /etc/init.d/samba restart
i dunno for sure but that's work for me

---

### Post by kilps on 2005-12-07
[QUOTE=BatsotO]sudo /etc/init.d/samba restart
i dunno for sure but that's work for me[/QUOTE]
Still not there ... I'll restart later and see what happens then ... I just don' whant to loose my dialup connection right now ... - thanks though

---

### Post by adduds on 2005-12-07
Hey guys, I've done all the tinkering in samba (sudo gedit /etc/samba/smb.conf)

Now when i go to my desktop (XP) i get this: go to My Network Places-->View Work Group Computers (left hand margin, when folders is not cliked) click on Adtop (my lappy)...

[[IMG]http://img116.imageshack.us/img116/6818/networkproblem6iu.png[/IMG]](http://imageshack.us)

---

### Post by Ozitraveller on 2005-12-07
Could you please post smb.conf, it might help in the discussion if we can see what changes have been made.

---

### Post by adduds on 2005-12-07
This is sudo gedit /etc/samba/smb.conf

EDIT: how do you get the post to scroll? i figured it would automatically

> #
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
   workgroup = MADADUDS

# server string is the equivalent of the NT Description field
   server string = %h adtop

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

wins support = no
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

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


[Homeadduds]
path = /root
available = yes
browseable = no
public = yes
writable = yes


---

### Post by Ozitraveller on 2005-12-07
[Homeadduds]
path = /root
available = yes
browseable = no
public = yes
writable = yes

 
Does you win user have permission to logon to /root?
 
Did you add this line manually, it's commented out further up the file.
wins support = no
 
Just edit the files manually and don't go into the Networking screen after you have done the changes.
 
I need to test out an idea I have, but I think the networking screen might have a bug in it.
 
 
Unofficial Ubuntu 5.04 Starter Guide 
[http://ubuntuguide.org/]("http://ubuntuguide.org/")
 
 
I used these instructions, and all seems to work ok. Apart from configuring the firewall.
 
[Samba Server]("http://ubuntuforums.org/")
[http://ubuntuguide.org/#sambaserver]("http://ubuntuguide.org/#sambaserver")
 
How to share public folders with read/write permissions (Authentication=No)?
[http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare]("http://ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare")

---

### Post by adduds on 2005-12-07
> Does you win user have permission to logon to /root?

I'm not sure.....sorry very new, how do i know if my win user has permission to logon to /root?

> 
Did you add this line manually, it's commented out further up the file.
wins support = no

No I did not manually add this line

1. Does a comment start w/ ;thenwhaterafter?
2. Should this line be set to yes and uncommented?

---

### Post by Ozitraveller on 2005-12-07
[quote=adduds]I'm not sure.....sorry very new, how do i know if my win user has permission to logon to /root?
 
 
 
No I did not manually add this line
 
1. Does a comment start w/ ;thenwhaterafter?
2. Should this line be set to yes and uncommented?[/quote]
 
I don't think any external user would have access to /root by default.
 
I'd probably delete that wins line, there is commented line further up the file.
 
My suggestion would be to follow the instructions in 
"How to share public folders with read/write permissions (Authentication=No)?", there is a link on my last post. 
 
Basically it will get you to create a public folder with R/W without any authentication. 
 
Once you get this working, you should be able to then be able to configure it the way you want. But for now just get the basics working first.
 
There is a very good section on samba in the guide I linked in the last post, well worth a read to get you started.

---

### Post by adduds on 2005-12-07
**** i'm an idiot, i forgot to drop the firewalls, i got the public sharing running, which has all the stuff i need in it. :) Thanks very much for your help.

cheers,
ad

---

### Post by Ozitraveller on 2005-12-07
Totally ok! I've done the same thing myself. I'll be nice when networking just works....
 
;-)

---

### Post by adduds on 2005-12-07
[QUOTE=Ozitraveller]
Totally ok! I've done the same thing myself. I'll be nice when networking just works....
[/QUOTE]

it truly will be...although, how do i get to see my WinXP on Ubuntu now?

---

### Post by Ozitraveller on 2005-12-07
Sorry for the delay I've been out for the long lunch!! ;-)
 
Which firewall do you have installed? Firestarter?

---

### Post by adduds on 2005-12-08
[Quote=Ozitraveller]
Which firewall do you have installed? Firestarter?[/QUOTE]

Yes I have firestarter on my laptop(ubuntu)and Sygate on my desktop(XP home)....i'm just not sure how to find/read files from my windows computer on ubuntu......i have a wireless router (D-link DI-624) though that shouldn't be a problem...

anyhelp would be nice thanks,

cheers,
ad

ps. thanks for the other help :)

---

### Post by BLTicklemonster on 2005-12-08
Shoot, I'm afraid to touch the network. Every time I've used it, something happens. It will ask for a username and password which are obviously different from what I have. Out of no where. Bam. And the documentation I have been able to find on samba is written way above my pay grade, so I have no freaking idea what any of it means. It seems like some kind of warning and or consistancy would be nice in samba.

I just quit using the network, and burn cdrws if I need something from one of the other machines. One day I'll get it right, but at present, it's too much of a hassle to mess with.

---

### Post by Ozitraveller on 2005-12-08
[quote=adduds]Yes I have firestarter on my laptop(ubuntu)and Sygate on my desktop(XP home)....i'm just not sure how to find/read files from my windows computer on ubuntu......i have a wireless router (D-link DI-624) though that shouldn't be a problem...
 
anyhelp would be nice thanks,
 
cheers,
ad
 
ps. thanks for the other help :)[/quote]
 
I only have the std winxp firewall and firestarter. I just shutdown firestarter so I didn't have to change the config for it, until I knew the network works. But w/o the firewall, and if you created the public folder on Ubuntu,  you should be able to browse to the Network Neighourhood where you should see a Ubuntu node (if that's the name you gave to the Ubuntu box?). If you want to browse ubuntu further than the public folder? Setup the /home directories as browseable (see Ubuntu Guide). If you want to browse further into the system directories, theis is probably not a good idea 'cuz some/all of those folder have root as owner and really souldn't be made visible across a network.

---

### Post by adduds on 2005-12-08
no i mean read XP on my ubuntu box sorry if i was unclear

---

### Post by Ozitraveller on 2005-12-08
Actions menu > Networks
 
Nautilus should open and display the network nodes in the right pane. Double click to open.
 
It's be nice if it had a network node on the treeview!

---

### Post by adduds on 2005-12-08
acions menu?

---

### Post by Ozitraveller on 2005-12-08
[quote=adduds]acions menu?[/quote]
 
Sorry for the delay! The day ended, and sleep over took me! ;-)
 
What desktop are you using, Gnome, KDE, xfce, .....?

---

### Post by adduds on 2005-12-08
GUH NOME

lol

i've been able to access my windows using

ALT-F2 them

SMB://ADDESK

1. Is their an easier way??

2. i would like to mount this folder when i tried i got this

[ATTACH]4298[/ATTACH]

If i'm unclear at all just ask....thanks again buddy

---

### Post by deNoobius on 2005-12-08
If you're in Gnome, you should be able to see your Windows machine from the GUI.  First, turn on file sharing on the Windows machine for the folders you want to see (right click on a folder, select "sharing and security").

On the Ubuntu machine:  assuming you haven't moved things around, there should be a menu bar at the very top of your screen that has three items:  Applications  Places  System.  Select "Places."  First, try "Network Servers" and see if the other computer is automatically detected.  If that doesn't work, select "connect to server" and you'll enter the IP of the Windows machine by hand.

Another nice little thing I discovered is nmap, a program found on the repositories.  You can ping your network and get information about the other computer(s), including the IP address, the operating system, and other things (the man page is really complete, just read that after you install the program).  This is a good way to make sure your Ubuntu machine can see the other machine(s), and you can get the remote IP without leaving the Ubuntu machine.

---

### Post by Ozitraveller on 2005-12-08
yep Places > Network Servers!

---

### Post by adduds on 2005-12-08
[QUOTE=Ozitraveller]yep Places > Network Servers![/QUOTE]

Ya i tried that last night...and it didn't work. now all of a sudden it works lol....queeerrr.

It seems to be very finicy too, like i'll sometimes be prompted for a password (i only use 1 password for all my computers) so i enter it and it just re-prompts so i just esc out of it and it works.....and sometimes i won't be prompted at all...... it's weird...

But thanks tho :)

---

### Post by Ozitraveller on 2005-12-08
Have you setup users on ubuntu to match the winxp users? With matching UID/password (case matters)? But if it's a public folder with no authentication, then you are right, it shouldn't ask. 
 
I hoping Dapper Drake 6.05 will resolve more/all of these networking issues! So any detected networks just integrate into everything that needs to know about networky things!!!!!

---

