---
title: "Networking between my macs"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by Atomic Ant on 2005-11-18
Hi People,

I am brand new user of ubuntu ( linux in general) and I would like to get my pc running ubuntu 5.10 to talk with my macintoshes.
I heard that Samba talks between then. Ok how on earth I can do that???!!!
I tried going to /system/adminstrators/shared folders but still my macs cannot login in.
They see my linux machine but cannot login.
On the macs I have the sharing preferences on and we are using tiger 10.4 ( all of then). what can I do?
Please help.

JR

---

### Post by ChrisTheGeek on 2005-11-18
Not really my area of expertise but I've heard something about adding linux user accounts on Ubuntu for each remote user you want to be able to connect.  I think this depends on whether the guest account is enabled.  Try adding user accounts in Ubuntu and then use the smbpasswd command to tell samba about the accounts.

More information about samba here: [http://us4.samba.org/samba](http://us4.samba.org/samba)

Click the links under 'Learn Samba' in the left hand menu.

---

### Post by thomas.mcmahon on 2005-11-20
Hi Atomic Ant,

First things first, do you actually have a connection between you Ubuntu box and your macs. To make sure that you do, open up a terminal and "ping" the macs from your linux box, or vice - versa. To do this type

ping -c 5 ipaddressofcomputerhere 

replace ipaddressofcomputerhere with the actual ip address of the computer you want to ping.

If this works the next thing to do is install and configure samba. Samba is the software that you will use to have graphical shares between Linux and the Macs.

To install Samba open up the terminal and type

sudo apt-get install samba

This will install all you need to get samba running. Once you've got this done, try and create a share by right - clicking on the folder you want to share, and going to properties then make this folder shared.

Now if everything has worked, you should be able to see the shared folder from the Mac off the linux box. If not, just post here and we'll see if we can fix it. 

Good luck :)

---

### Post by Installer36 on 2005-11-20
Thank you this is all I needed to do and was making it so much harder ....I think my fear of linux lets me for get  KISS ...keep it simple stupid.....I have been trying for 3 days to see my XP box and this solved it..Once again Thankyou

---

### Post by Atomic Ant on 2005-11-20
Hi Chris te Geek, Thomas.mcmahon;

I did wat you said. I have connections between the linux and the mac using the terminal. I installed the samba software and shared the folder as you said. My mac sees the linux but when I click to open the connection he freezes !!!!!!I don't get the login box with username and password, my mac goed on a loop ( keeps thinking) I need to force quit my finder to get it working again.
As for the linux box it doesn't see any mac on the network, but on the my macs I have the folder already shared.
Really thank you guys for your patiente and help as I'm starting to think that this is getting more and more complicated.
It can't be that hard???!!! I share files between macs and pcs all the time?

cheers

AA

---

### Post by thomas.mcmahon on 2005-11-20
Hey,

OK well we're making progress! I'll admit that getting Samba set up on Ubuntu is more difficult than it should be, I think that the dev's should take notice of this, because it is a fairly common task.

What I want you to do is open up the terminal for me and type

cat /etc/samba/smb.conf

And paste the output of that into here.

To try and connect your linux box to the macs, go to "Connect to server" in the "Places" menu in gnome, and type the mac's IP addresses and connect via "Samba", see how that goes :)

Don't worry, we'll get through this and it'll work fine after you've set it up.

---

### Post by nrwilk on 2005-11-20
heya, I'm having the exact same problem here.  I can see and connect to my Powermac from my ubuntu box, but when I try to connect to the ubuntu box, I get a system hang, just like this other guy.  I have to restart the Finder.  in order to connect to the Mac from the Linux box, I use this command in the URL field in a konqueror window:
```
smb://<MacUsername>@<Mac.Internal.IP>/<MacSharedFolder>
```
so, for me it's like this:
```
smb://fealos@192.168.0.3/fealos
```

The output from my smb.conf file follows:

```
fealos@LinuxCompy:/usr/src$ cat /etc/samba/smb.conf
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


## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
  workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
  server string = %h

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
  browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
  writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
  create mask = 0644

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
  directory mask = 0755

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
  path = /var/spool/samba
  browseable = yes
  public = yes
  guest ok = yes
  writable = yes
  printable = yes
  printer admin = root, @ntadmins


# Windows clients look for this share name as a source of downloadable
# printer drivers
; [print$]
;    comment = Printer Drivers
;    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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


[www]
       comment = www-root
       writable = yes
       path = /var/www/html
       public = yes
       create mask = 0664
       directory mask = 0775

[Linuxcompy]
       comment = Sharedname on computername
       writable = yes
       path = /home/noah
       public = yes
       create mask = 0664
       directory mask = 0775
```

Maybe we can get this resolved!

---

### Post by Atomic Ant on 2005-11-21
Hi Thomas,

I did as you said, please look below to see the text from my terminal.
I tried to login from the Linux Box but in the "Places" menu in gnome, and typed the mac's IP addresses and connect via "Samba", I didn't see anywere to connect trough Samba, maybe there lies the problem.

Thanks

AA

> **thomas.mcmahon]Hey,

OK well we're making progress! I'll admit that getting Samba set up on Ubuntu is more difficult than it should be, I think that the dev's should take notice of this, because it is a fairly common task.

What I want you to do is open up the terminal for me and type

cat /etc/samba/smb.conf

And paste the output of that into here.

jr@ubuntu-server:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a  said:**
> 

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = workgroupDAC

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

wins support = no
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


[Sharingfolder]
path = /home/jr/Desktop
available = yes
browseable = yes
public = yes
writable = no
jr@ubuntu-server:~$



To try and connect your linux box to the macs, go to "Connect to server" in the "Places" menu in gnome, and type the mac's IP addresses and connect via "Samba", see how that goes :)

Don't worry, we'll get through this and it'll work fine after you've set it up.

---

### Post by thomas.mcmahon on 2005-11-23
Hi Atomic Ant,

OK sorry I wasn't at my Ubuntu box (on my GF's iBook actually :)), the actual way to connect to a windows share in gnome is 

Places > Connect to server... > Service Type > Windows Share

Then you enter the rest of the details there. I'm gonna have a look at your smb.conf and see if I can figure out why it's not working :)

---

### Post by thomas.mcmahon on 2005-11-23
OK here's something that you can try, just to get this set up we'll reduce the security of this setup. We can fix that later, first thing is to get it running.

open up that smb.conf as root, with your fav text editor (I use nano)

sudo nano -w /etc/samba/smb.conf

Go to the line "security" under the authentication section, uncomment it by removing the ";" in front of the word security, then change it from "security = user" to "security = share".

Another thing (I'm pretty sure this doesn't matter, but we'll do it anyway) is make the name of your share all lowercase, so change it from "Sharingfolder" to "sharingfolder". 

Now restart samba so that the new config file is in effect with

sudo /etc/init.d/samba restart

Now I want you to type this command to see whether everything is ok on your smb.conf and that your share is working. 

smbclient -L localhost -U%

You should see your sharename there and what type it is, if not then we'll have to think again, try and connect from the mac and see if it works :)

---

### Post by rob_gendreau@yahoo.com on 2005-12-03
[QUOTE=thomas.mcmahon]
Another thing (I'm pretty sure this doesn't matter, but we'll do it anyway) is make the name of your share all lowercase, so change it from "Sharingfolder" to "sharingfolder". :)[/QUOTE]

The case DID matter on my Mac at least. Thanks for the tips.

---

### Post by malcanta on 2005-12-06
[QUOTE=Fealos]heya, I'm having the exact same problem here.  I can see and connect to my Powermac from my ubuntu box, but when I try to connect to the ubuntu box, I get a system hang, just like this other guy.  I have to restart the Finder.  in order to connect to the Mac from the Linux box...[/QUOTE]

ok, count me in with this group.  although i did get my mac to print to usb printer connected to my Ubuntu machine.  Did this by uncommenting a few lines in smb.conf  Printing is not perfect though, if i change printing preferences it will not print.

I'm really puzzled by the Finder crashing when it attempts to connect to samba shares...my best guess is that it is an authentication problem, and i did uncomment security and switched to security = share , it was mentioned that this may make the system vulnerable.

anyways....we could really use some help here!

---

### Post by malcanta on 2005-12-06
well, i just got it to work.  found the answer in this thread:
[http://ubuntuforums.org/showthread.php?t=91871&highlight=samba+mac](http://ubuntuforums.org/showthread.php?t=91871&highlight=samba+mac)

i was successful in accessing my shares...however when i use apple+k to connect to servers i type in cifs://home-net;malcanta@ubuntu/malcanta

anyone know what cifs is?

Edit - - 

so i googled cifs.
also logged in by using smb://networkname;username@server/sharename
no problems.
until my printer went down again!!! I don't know why they just stopped working, I thought when I got something working in Linux it was solid! Oh well, back to looking at smb.conf to see what is wrong.  Would be nice if there was a team working on an ubuntu samba gui manager thingy.

if anyone can give me any pointers, here is my smb.conf (the error i get is an NT_PASSWORD error, btw)

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = home-net

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


[malcanta]
path = /home/malcanta
available = yes
browseable = no
public = yes
writable = yes

[NFS]
path = /media/hdb1
available = yes
browseable = no
public = yes
writable = yes

```

---

