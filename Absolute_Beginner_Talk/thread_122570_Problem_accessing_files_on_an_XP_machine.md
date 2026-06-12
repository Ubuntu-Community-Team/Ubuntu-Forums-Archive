---
title: "Problem accessing files on an XP machine"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by derspiess on 2006-01-27
Now that I've introduced myself, here's my first question.  One of the things I wanted to do with Ubuntu on my secondary computer is to be able to access media files.  I had gone into my main computer (which runs XP) long ago to set up the network & share my music, video, and picture folders, and they do show up when I look for them in Samba.

I'm able to mount shortcuts (?) to those folders on my Ubuntu desktop.  I was able to get into those folders & access music & video files on the first couple tries.  The problem I ran into on about the 3rd or 4th attempt to access those folders was that I was prompted for a password for my "MS Home" network.  I never set a password when I set up the network in XP, so I have no idea what I'm supposed to use.  I try just leaving the password blank & clicking "OK" but it keeps prompting me for a password.  I go ahead & use my users password for Ubuntu & no luck.  Same thing had happened with Mepis & a couple other Linux distros, so I'm guessing it's not an anomaly

Any idea what I'm doing wrong?  If I need to provide more detailed info, please let me know.

Thanks in advance!

derspiess

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=derspiess]Now that I've introduced myself, here's my first question.  One of the things I wanted to do with Ubuntu on my secondary computer is to be able to access media files.  I had gone into my main computer (which runs XP) long ago to set up the network & share my music, video, and picture folders, and they do show up when I look for them in Samba.

I'm able to mount shortcuts (?) to those folders on my Ubuntu desktop.  I was able to get into those folders & access music & video files on the first couple tries.  The problem I ran into on about the 3rd or 4th attempt to access those folders was that I was prompted for a password for my "MS Home" network.  I never set a password when I set up the network in XP, so I have no idea what I'm supposed to use.  I try just leaving the password blank & clicking "OK" but it keeps prompting me for a password.  I go ahead & use my users password for Ubuntu & no luck.  Same thing had happened with Mepis & a couple other Linux distros, so I'm guessing it's not an anomaly

Any idea what I'm doing wrong?  If I need to provide more detailed info, please let me know.

Thanks in advance!

derspiess[/QUOTE]

Try posting you /etc/samba/smb.conf.  Folks will look at the settings, and someone will probably be able to tell you what needs to be changed.

---

### Post by UbuntuDupe on 2006-01-28
[QUOTE=cwaldbieser]Try posting you /etc/samba/smb.conf.  Folks will look at the settings, and someone will probably be able to tell you what needs to be changed.[/QUOTE]

Careful with this guy.  If you refuse to tell him what color shirt you were wearing at the time, he'll blame you for being uncooperative and refuse to help.

---

### Post by derspiess on 2006-01-28
[QUOTE=cwaldbieser]Try posting you /etc/samba/smb.conf.  Folks will look at the settings, and someone will probably be able to tell you what needs to be changed.[/QUOTE]

Can anyone help point me in the right direction as far as finding this?  I can handle the copying & pasting :p  but I don't know how to get to this to post it here.

---

### Post by breezyfox on 2006-01-28
go to terminal
type
sudo nano  /etc/samba/smb.conf

or
sudo gedit /etc/samba/smb.conf

then you can edit it or what ever you want to do.

bz

---

### Post by derspiess on 2006-01-28
Thanks breezyfox.

Here is what I have (edited out most of the '#' stuff):

[global]

   workgroup = MSHOME

   server string = %h server (Samba, Ubuntu)

;   wins support = no

;   wins support = no

;   wins server = w.x.y.z


   dns proxy = no


;   name resolve order = lmhosts host wins bcast


   log file = /var/log/samba/log.%m


   max log size = 1000

;   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


;   security = user

   encrypt passwords = true

   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

;   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

;   pam password change = no

;   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

;   printing = cups
;   printcap name = cups

;   printer admin = @ntadmin


######## File sharing ########
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = no


   writable = no


   create mask = 0700


   directory mask = 0700


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


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @ntadmin


;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes


;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by cwaldbieser on 2006-01-28
> **derspiess]Thanks breezyfox.

Here is what I have (edited out most of the '#' stuff):

[global]

   workgroup = MSHOME

   server string = %h server (Samba, Ubuntu)

 said:**
> 
   comment = Home Directories
   browseable = no


   writable = no


   create mask = 0700


   directory mask = 0700


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


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @ntadmin


;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes


;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

I think you probably need to change the "guest ok = No" to "guest ok = Yes".  I am not sure, but you might also want to change the "browsable" setting to Yes.  Also, under the global section where "; security = user" is commented out, I would set this to "secutiry = share".  This is not a particularly secure setup, but it is likely to work.  You could throw in a "hosts allow = 192.168.1." (or whatever your local network numbers are) so that only PCs from your LAN can share.

After you make the changes, run "testparm".  This will check and make sure you didn't make any errors or typos.  Then you can restart samba with "sudo /etc/init.d/samba restart".

---

### Post by derspiess on 2006-01-28
[QUOTE=cwaldbieser]I think you probably need to change the "guest ok = No" to "guest ok = Yes".  I am not sure, but you might also want to change the "browsable" setting to Yes.  Also, under the global section where "; security = user" is commented out, I would set this to "secutiry = share".  This is not a particularly secure setup, but it is likely to work.  You could throw in a "hosts allow = 192.168.1." (or whatever your local network numbers are) so that only PCs from your LAN can share.

After you make the changes, run "testparm".  This will check and make sure you didn't make any errors or typos.  Then you can restart samba with "sudo /etc/init.d/samba restart".[/QUOTE]

Thanks.  I made the changes & ran testparm, which gave me some errors:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        guest ok = Yes

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=derspiess]Thanks.  I made the changes & ran testparm, which gave me some errors:

Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = MSHOME
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        guest ok = Yes[/QUOTE]

I think samba will create those files when it runs, so that should be OK.  I think the "guest ok = Yes" line should be moved under [global].  I didn't notice the section it was in before.  Also, I didn't see the "security = share" in the dump, but I believe that also goes under [global] (you need to remove the semi-colon (;) in front of the definition-- that means it is a comment).
If you get the same errors you could give restarting samba a shot, or you could manually create the folder as root.  Here is what my folder looks like permission-wise:
```

drwxr-xr-x  2 root root 4096 Jan 25 04:54 /var/run/samba

```

---

### Post by hatstand on 2006-02-05
sod all that. Just shange the password:

sudo smbpasswd -a (your username)

It will ask for the new password twice. Then that's your password!
Hey Presto!

---

### Post by derspiess on 2006-02-22
I have to say that despite some frustration I'm liking Ubuntu more & more.  I'm able to do a lot of the stuff I had set out to be able to do, and will definitely keep it here on my 2nd machine while I learn it, despite the fact that I now have an extra XP license I can use.  

I fumbled my way through it and am able to at least access my video and picture files on my XP machine from my Ubuntu box (still something odd with being able to get to my mp3 files but that's not really a concern).  Life is good as far as that is concerned.

Now I'd like to be able to access the hard drive on my Ubuntu box from my XP machine, to use to back up some things I have on my XP machine.  I searched around & tried to follow some instructions posted here & elsewhere, as well as the Ubuntu Starter Guide, but I can't connect to my Ubuntu machine from my XP machine at all.  I can locate it in "Network Connections" in XP but I get denied when I try to enter my user name & password.  Just to keep things simple, I kept my network password the same as my Ubuntu system password.  But I just flat-out cannot get to my Ubuntu box at all from my XP box.  Here is my samba config file:
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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = BRAMMERNET
   	

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
   netbios name = LinuxServer 

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
    guest ok = yes
    security = user	


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
   security = user
   username map = /etc/samba/smbusers

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
   browseable = yes
   writable = yes

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
   browseable = yes
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
   guest ok = yes
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



```

---

### Post by JanvL on 2006-03-21
I have just read this, there is one good book on Samba,
Using Samba from O'Reilly it has helped me a lot.

I now have the same problem and that is XP Home, I can do
anything from XP Pro but with Home there is some kind of problem.

I guess it is in the "new" version 3.x from Samba because there is no
problem with my other Linux-box with Suse 9.0 and some 2.x Samba.

I will do some more research and let you know when I have some results.

Jan

---

### Post by JanvL on 2006-03-21
So I found it,

with me it was Firestarter blocking an IP-adress
after allowing this adress no more problems.

I use fix IP-adresses

used GNome to share some directories
used "useradd" for samba to add the windows users and passwords

did not need to edit the smb.cnf file, most can be done
sooo comfortable with a GUI like in . . . .you know!

Jan

---

