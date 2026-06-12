---
title: "Sharing Printer with XP"
date: 2005-05-22
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-05-22
I never got it to work.
I always saw it though, but it would not print. I followed the instrucitons in Samba How To, but it still wouldn't print
In one of my last configuring adventures, since I had reinstalled it in Ubuntu and XP was telling me that the printer was not found in the server, I deleted the printer but it just wouldn't delete, so I --probably a big mistake-- also deleted the port.
Now when I try to add printer from the network, the dialog shows the Ubuntu machine but, even though there is a plus sign next to it, it doesn't show any printers there.
If anybody could tell me where to go from here I would appreciate it very much.

E_M

---

### Post by clb137 on 2005-05-22
[QUOTE=Error_Msg]I never got it to work.
I always saw it though, but it would not print. I followed the instrucitons in Samba How To, but it still wouldn't print
In one of my last configuring adventures, since I had reinstalled it in Ubuntu and XP was telling me that the printer was not found in the server, I deleted the printer but it just wouldn't delete, so I --probably a big mistake-- also deleted the port.
Now when I try to add printer from the network, the dialog shows the Ubuntu machine but, even though there is a plus sign next to it, it doesn't show any printers there.
If anybody could tell me where to go from here I would appreciate it very much.

E_M[/QUOTE]
Hello can you post your /etc/cups/printerconf

thanks
clinton

---

### Post by Error_Msg on 2005-05-22
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sat May 21 07:13:04 2005
<DefaultPrinter BJC-4400>
Info BJC-4400
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Thanks for looking into it, Clinton.

E_M

---

### Post by Error_Msg on 2005-05-22
I fixed it!
Please don't ask me how, but I fixed it.

E_M

---

### Post by Error_Msg on 2005-05-22
This same printer is also a scanner. You take out the ink cartridge, insert this ink-cartridge-looking thingie, and the printer becomes a scanner.
I googled for a driver with no luck. Is there a workaround or something?
What are my odds to be able to operate the scanner?
Thanks in advance.

E_M

---

### Post by clb137 on 2005-05-22
[QUOTE=Error_Msg]This same printer is also a scanner. You take out the ink cartridge, insert this ink-cartridge-looking thingie, and the printer becomes a scanner.
I googled for a driver with no luck. Is there a workaround or something?
What are my odds to be able to operate the scanner?
Thanks in advance.

E_M[/QUOTE]

Hi,

can you give all the info you can on your scanner/printer

thanks 

clinton

---

### Post by Error_Msg on 2005-05-22
Canon BJC-4400 becomes a scanner when you insert a Cannon IS-22 cartridge.
I don't think I mentioned this before, but my printer-scanner is connected to the Linux box. The Linux box and a laptop running XP are both connected to a router, and the laptop doesn't have a parallel port. 
Worse comes to worse, a USB to parallel cable that would enable a direct connect from the laptop to the printer-scanner would do the trick.
I tested the scanner just to see what would happen, and the scanner driver tells me that there is no scanner driver in the Linux machine. No explosions, smoke or anything.
What do you think, Clinton?

E_M

---

### Post by clb137 on 2005-05-22
[QUOTE=Error_Msg]Canon BJC-4400 becomes a scanner when you insert a Cannon IS-22 cartridge.
I don't think I mentioned this before, but my printer-scanner is connected to the Linux box. The Linux box and a laptop running XP are both connected to a router, and the laptop doesn't have a parallel port. 
Worse comes to worse, a USB to parallel cable that would enable a direct connect from the laptop to the printer-scanner would do the trick.
I tested the scanner just to see what would happen, and the scanner driver tells me that there is no scanner driver in the Linux machine. No explosions, smoke or anything.
What do you think, Clinton?

E_M[/QUOTE]

Hi,

One step at a time 1st how is the printer scanner connected? and what operating system (Linux ?)  

Have you tried the printer just on a win XP machine?

Are ou trying to connect via a network or is it connected to the linux box?

cheers clinton

---

### Post by Error_Msg on 2005-05-22
Hi,

>One step at a time 1st how is the printer scanner connected? and what >operating system (Linux ?)  

The printer-scanner is connected to a desktop running Ubuntu.
The desktop is connected to a router.
The laptop (no parallel port) running XP is connected to the same router.
I can print from the desktop or the laptop.
I cannot scan from the desktop or the laptop (no scanner driver installed in the desktop).

>Have you tried the printer just on a win XP machine?

No because I doesn't have a parallel port. I would have to get a USB to parallel to connect directly.

>Are ou trying to connect via a network or is it connected to the linux box?

The printer-scanner is connected to the Linux box.

---

### Post by clb137 on 2005-05-22
hello,

you are confusing me a little the problem was sharing printer with xp????

is XP on the other side of the router if so this may be your problem,  

linux should se and use your printer no problem, however through a router is a problem, do you have a any fire wall installed either on XP or ur linux box?


clinton

---

### Post by Error_Msg on 2005-05-22
[QUOTE=clb137]hello,

you are confusing me a little the problem was sharing printer with xp????

is XP on the other side of the router if so this may be your problem,  

linux should se and use your printer no problem, however through a router is a problem, do you have a any fire wall installed either on XP or ur linux box?


clinton[/QUOTE]

Clinton,
The printer-scanner uses two drivers, one for printer, and one for scanner.
The laptop and the desktop are both connected to the router, and the printer-scanner is connected to the Linux box.
Up until this morning I couldn't print from XP but I was able to fix that after fiddling with smb.conf.
Now for the scanner to work, I have to install the scanner driver in both, the Linux box and the laptop. I have it installed in the laptop, but I can't find one for Linux to install in the Linux box.
What a riddle! :grin:

---

### Post by clb137 on 2005-05-23
hi,

I will have a look around for some drivers for you, what have you fiddle with in the SMB conf?   As a rule you do NOT need to alter this file, even the workgoup, because the network will treat it as a different workgroup.

Can you post you SMB.CONF?

thanks

clinton

---

### Post by Error_Msg on 2005-05-25
Thanks, Clint, you're da man!
I have the scanner driver but only for windows. I think I'll give up scanning through the network, and get a USB to parallel cable to connect directly if I need to scan something (I rarely do).
As far as not messing with smb.conf, I have blatantly violated that rule and, while it may not look pretty, it's working like a charm, so here it goes:

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
   workgroup = WG1
   netbios = JOKA2
   security = share
   printcap name = cups
   disable spoolss = Yes
   show add printer wizard = No
   printing = cups

[data]
   comment = Data
   path = /SharedDocs
   force user = jorge
   force group = users
   read only = No
   guest ok = Yes
   browseable = Yes

[printers]
   comment = All Printers
   path = /var/spool/samba
   guest ok = Yes
   printable = Yes
   use client driver = Yes
   browseable = No

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
comment = All printers
path = /var/spool/samba
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = Yes

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
   browseable = No

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = Yes

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
   browseable = Yes
   path = /tmp
   printable = yes
   public = Yes
   writable = Yes
   create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = Yes
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

[SharedDocs]
path = /SharedDocs
available = yes
browseable = yes
public = yes
writable = yes

E_M
Ps: I would like to read the Linux box floppy, and Zip Iomega drives from the laptop through the network but, as it is, I got a working system, and I'm falling behind with my homework, so that will have to wait.

---

