---
title: "Installing and sharing HP F300 printer"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by dbansal on 2007-05-06
Hello,

I setup and installed the HP F300 printer on my ubuntu box just fine. It prints a test page just fine. 

However, i am having trouble sharing the printer. I was able to share the printer with the GUI interface and i can see it fine from my windows box. However, my windows box says that the server does not have the proper drivers for it, and it asks me to insert a cd.

I beleive that ubuntu is using the hpilj generic driver. 

So, what do i do?!

thanks!

---

### Post by dbansal on 2007-05-06
Bump!

---

### Post by dbansal on 2007-05-08
bump again?!

---

### Post by jiminycricket on 2007-05-08
How did you share it via GUI?  Via an HP utility?

What does your /etc/samba/smb.conf look like?

---

### Post by houstonbofh on 2007-05-08
Download a Windows driver for the Windows machine.

---

### Post by dbansal on 2007-05-10
THis is my smb.conf file


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
;   browseable = yes
;   writable = yes

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



[Lodge]
path = /files/hda3
available = yes
browsable = yes
public = yes
writable = yes

[external]
path = /media/external
available = yes
browsable = no
public = yes
writable = yes

[external1]
path = /media/external1
available = yes
browsable = no
public = yes
writable = yes

[lester]
path = /media/lester
available = yes
browsable = no
public = yes
writable = yes

[Stevens Servers]
path = /media/servers
available = yes
browsable = yes
public = yes
writable = no


Is there an HP utility for ubuntu that i do now know about?!!

---

### Post by dbansal on 2007-05-11
Update:: I downloaded the windows driver and it works, sort of. The printer takes an extremely long time to respond and there about a 50% chance that the data goes through.

Any ideas?

---

### Post by tagra123 on 2007-05-13
As you might have noticed, printing seems to be very broken in feisty and etch. It wasnt great in dapper either. The last time it seemd to work as documented was in breezy.

Here is a very ugly way to share your printer. It's ugly, but its been working for me. 

I don't think making sure that the printing is working correctly is as near important to any of the dists as the eyecandy and make sure the music and videos are playing. Granted I'm glad to see easier to use video files for the new users, but printing is such a basic function - GET IT WORKING PLEASE.

Here's my workaround. [http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

---

### Post by kramerica on 2007-05-14
funny.  i just did this last weekend with a HP F300 and got the same result.  very slow to print.  but all my other samba stuff was fast.  only the printing was slow.  until i found this fix/hack:

go into regedit on the windows 
under HKEY_CURRENT_USER\Printers\DevModePerUser, delete any keys referencing your shared printer
do the same thing for HKEY_CURRENT_USER\Printers\Devs2 (the name is something like that - im at work and cant get in my regedit to look)

restart windows

found this in another forum and worked perfect.

---

### Post by dbansal on 2007-05-21
Ill have to try it when i get back to school..

What about this HP utility ive been hearing about?

---

