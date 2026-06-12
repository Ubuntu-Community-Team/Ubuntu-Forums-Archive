---
title: "Installed Samba"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by davio on 2005-09-21
i've been using ubuntu for 4 days already. love it. problem is, i can see my windows computer icon on ubuntu in network servers, 

however when i try to access it, authentication is required, asking for username, domain and password. 

is there a way to get rid of this authentication thing or set the username, domain and password? if there is, how ?

many thanks

davio.

---

### Post by davmac on 2005-09-21
There are various instructions in the Starter Guide depending on whether you want to do this manually each time or automatically at boot up, and whether you want it to be read only or read/write.

Have a look at [http://ubuntuguide.org/#mountunmountnetworkfolders](http://ubuntuguide.org/#mountunmountnetworkfolders) and the next three sections.

HTH,

Dave Mac

---

### Post by davio on 2005-09-21
eh, the link is not working. thanks.

---

### Post by davmac on 2005-09-21
On another thread someone has just mentioned that the site is down. Luckily I keep an offline copy because I'm referring to it all the time  :) 

From the section on mounting automatically as read/write...

How to mount network folders on boot-up, and allow all users to read/write?

e.g. Assumed that network connections have been configured properly
     Network computer's IP: 192.168.0.1
     Network computer's Username: myusername
     Network computer's Password: mypassword
     Shared folder's name: linux
     Local mount folder: /media/sharenamesudo mkdir /media/sharename

sudo gedit /root/.smbcredentials

Insert the following lines into the new file 

username=myusername
password=mypassword

Save the edited file

sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

Append the following line at the end of file 

//192.168.0.1/linux        /media/sharename  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0

Save and then
 
sudo mount -a

---

### Post by davio on 2005-09-21
when i type sudo mount -a, this message occurs.

params.c:Section() - Badly formed line in configuration file: ]
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Can't load /etc/samba/smb.conf - run testparm to debug it
Could not resolve mount point /media/sharename

anyone can help? thanks.

---

### Post by davio on 2005-09-21
i really need to transfer some files from my personal computer running windows xp pro onto my laptop running ubuntu, if someone could point me in the right direction with specific instructions, i'll be really grateful.

thanks in advance.

davio.

---

### Post by davmac on 2005-09-21
Can you post the contents of your samba configuration file?

You can get this by typing "cat /etc/samba/smb.conf"

When I was setting up samba I found it really useful searching for examples of other people's smb.conf files, and trying to understand how they'd got theirs set up. A quick google for "sample smb.conf" will turn up plenty of examples.

One particularly well commented one is available at [http://distro.ibiblio.org/pub/linux/distributions/slack390/slack390-9.1/patches/source/samba/smb.conf-sample](http://distro.ibiblio.org/pub/linux/distributions/slack390/slack390-9.1/patches/source/samba/smb.conf-sample)

Dave Mac

---

### Post by davio on 2005-09-21
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
   netbios name = dadavio

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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword :* %n\n .

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
   writable = yes

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


[]
path = /home/davio/Desktop
available = yes
browseable = no
public = yes
writable = yes

sorry for adding the whole chunk here, i don't know how to edit it.

by the way, i'm totally clueless on what to do. thanks anyway.

---

### Post by davmac on 2005-09-21
I think the problem is the "[]". You need to have some text in here, like "[myshare]".

HTH,

Dave Mac

---

### Post by davio on 2005-09-21
how do i edit that? 

thanks.

---

### Post by davmac on 2005-09-23
If you open a terminal and type in "sudo gedit /etc/samba/smb.conf" you'll be able to edit it. Once you've saved it, go back to the terminal and type "sudo /etc/init.d/samba restart"

I'm at work on a Win2k machine so this is from (failing) memory. Shout up if it doesn't work.

Dave Mac

---

### Post by davio on 2005-10-01
i've done what you told me to do however, when i double click on the icon for my personal computer, a box appears requesting for authentication and asking for the username, password and domain. 

thanks anyway!

---

