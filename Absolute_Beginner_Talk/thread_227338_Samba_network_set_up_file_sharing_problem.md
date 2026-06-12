---
title: "Samba network set up: file sharing problem"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by stig on 2006-08-01
Hi,
I have used Samba to network three PCs but still have a problem copying files from one PC to another. I have only elementary knowledge of Linux and would be grateful if someone could help solve my problem. I’ve read a lot of guides and forum posts but still cannot find what is wrong - although it’s probably something quite simple! Although I have a Windows PC networked at present, my main objective is to get the Ubuntu PCs working together because I hope to drop Windows soon. I have copied the smb.conf file at the end of my message.

I have two Ubuntu 6.06 PCs and one Windows 98 behind a broadband NAT router and connected by cable. The Ubuntu PCs have identical set up and samba and smbfs are installed. Both have a directory called Shared in the Home folder, and Shared has two sub-directories called Docs and Back-ups. Following guidance, I used System/Admin/Shared Folders to share these two folders through SMB. “Read only” is unticked and “Allow browsing” is ticked. General Windows Sharing Settings has MSHOME as my domain (the same as on my Windows PC). The Windows PC does not use any passwords.

The only change I have made to the smb.conf file is to uncomment security = user, again following advice.

I call the two Linux PCs Ubuntu1 and Ubuntu2. I used smbpasswd -a on Ubuntu1 to put in the username and login password for Ubuntu1, and likewise on Ubuntu2 put in the name and password for Ubuntu2.

Disregarding Windows for the moment, when I open Places/Network Servers I get an icon saying Windows Network. On, say, Ubuntu1 clicking this gives me a new icon, mshome, and clicking that gives icons for Ubuntu1 and Ubuntu2. I can click Ubuntu2 to see the Shared folder and its two sub-folders and any files in them. I can open the files. However I cannot copy a file from Ubuntu1 and paste it into the Docs folder on Ubuntu2 - it gives an error notice. This is important to me because my main uses for the network are to copy and move files from one PC to another, both for general use and as a back-up.

I still don’t fully understand how permissions work and I don’t want to risk making my system insecure, so I would rather get some help at this stage.
Thanks!

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
   security = user

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


[Backup]
path = /home/stig/Shared/Backup
available = yes
browseable = yes
public = yes
writable = yes

[Docs]
path = /home/stig/Shared/Docs
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by simonn on 2006-08-01
> 
However I cannot copy a file from Ubuntu1 and paste it into the Docs folder on Ubuntu2 - it gives an error notice


The error message being... ?

---

### Post by stig on 2006-08-02
> **simonn said:**
> The error message being... ?

Sorry for the late response but we have rather a large time difference!

When I wrote the post last night I didn't have access to the network, but here is the message:

Error "Access denied" while copying
"/home/stig/filename"
Would you like to continue?

and it offers Cancel or Retry (and Retry repeats the error message).

So I suppose the "Access denied" is the important bit.
Thanks for replying to my plea for help!

---

### Post by stig on 2006-08-02
To add a little more information.......

I get the same error message when trying to copy the file from Ubuntu1 to the Win 98 PC.

Also, when I open Network Neighbourhood on the Win 98 PC I get the icon for Ubuntu1. But when I click it a box opens saying:
Enter Network Password
You must supply a password to make this connection
Resource: \\UBUNTU1\IPC$
The space for entering a password is empty
The box is ticked for "Save this password in your password list"

If I click the box without entering a password, it tells me the pw is incorrect and try again. And I get the same if I enter my Ubuntu login password (which is also what I set for my username in smbpasswd).

I have had a Windows network but never used passwords on it. In Control Panel/Network on the Windows PC I have file and print sharing ticked. The same workgroup name is in the Identification as on the Ubuntu PCs, and Access Level is set for Share Level control.

---

### Post by mips on 2006-08-02
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by beniwtv on 2006-08-02
Ok, I'll try to help you as best as I can. I can't say I'm a huge smb shares geek, but I've gotten Ubuntu and my brother's WinME to share files and even the printers atached to my Ubuntu.

First of all, I don't make me the hassle of letting windows configure a home network. I don't use the windows assistan cause this has lead to huge problems (not only with sharing with Ubuntu but also with other PC's).

Normally, I setup my network as follows:

Say we have 2 PC's: Win 98 and Ubuntu. Win98 is called Flo and Ubuntu is called relamppc.

Now, the first thing would be configuring our network. We'll start with Flo. Open the network configuration. Check that you have at least the TCP/IP protocol and files/printer sharing installed. Then, configure the TCP/IP protocol. Select manual IP. Call it something like 192.168.XXX.XXX, eg: 192.168.100.1. Let the default submask on 255.255.255.0. If you're accessing the internet from this machine, also don't forget to fill in the router's ip. Finally, save and give the PC a unique workgroup.

Then, we do the same with relamppc. Configure your network adapter's IP with another manual assigned IP, eg. 192.168.100.2.
Submask again (and this is important) 255.255.255.0. Fill in the router's IP if needed. Then go to the sharing folders configuration. If prompted to install something, do so. The give the PC a unique workgroup too. Setup the shared folders. Be sure to select 'Allow browsing' on each of them.

Then in smb.conf, since relamppc has got some printers, I uncomment the following lines:

```
printing = cups
printcap name = cups

```

Normally, after this point, I can see Flo from relamppc and relamppc from Flo. Since I don't share my home directory and since I'm behind my router, I don't set any password for relamppc, so if you have issues wiht that I would need to digg into samba to find out.

Also don't forget to set the appropiate permissions on your shared folders.

So, tell me if you still have issues. Last time that worked for me, but it's quite a long time ago, I might have forgotten something.

Hope it helps.

NOTE: I'm not at home right now. I'll be there in about 3 hours, so if you have further questions then I can look into my own samba config file.

---

### Post by stig on 2006-08-02
> **mips said:**
> [http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Thanks! I don't recall having seen this page before. I'll read it and try yet again.

Where it says "Finally, create a SMB user..."
 sudo smbpasswd -a `whoami`

is the `whoami' the word that I should type in or does it represent my username? i.e. should I type `whoami' (in single quotes) or my username `stig' (in single quotes)?

---

### Post by stig on 2006-08-02
beniwtv, thanks for the detailed reply.

My router was provided as part of my internet connection package by the ISP and was supplied set up with DHCP, therefore my PCs do not have manually set, permanent IP addresses.

I don't know if it is OK simply to set the Ubuntu and Windows PCs to static IP when the router is all set for DHCP. Perhaps the router would not work properly. The ISP technical support people tend to get upset if anything is changed from their settings!

I would be tempted to try it and see, but I need the PCs functioning to do my work! Also, the problems seem to be concerned with file sharing and permissions rather than connections.

---

### Post by beniwtv on 2006-08-02
Just some basic toughts about networking.

The static ip you set on your home network does not affect your router in any way. That only would affect the actual machines. Your internet connection has nothing to do with that.

DHCP is meant to autoconfigure your home network's machines IP's and DNS servers. Both can be done manually as well.

The reason I'm saying this is because, as said before, I ran into huge trouble using DHCP for my home network. Not only in ubuntu, but sharing files between different windows versions as well. That was my experience at home and in my company, where I manage our 15 web pages we have (the servers). Anyway, it *should* work with DHCP too.

If you still want to keep DHCP, it's OK also. I'm still not at home, so I can't check with my own smb.conf files regarding to your permission issues. I hope I'll find something that helps you.

---

### Post by stig on 2006-08-02
Thanks for explaining more about DHCP. I would rather continue to use it if possible because (a) I had these computers successfuly networked on Windows using DHCP before I started with Ubuntu and (b) I feel like I've been almost at the point of success - but not quite.

Some time ago I opened the Properties menu of my shared folders and ticked Write for Group and Other (which meant all 6 boxes were ticked). This allowed me to copy files from Ubuntu to Ubuntu computer - but Windows wanted a password (and none of mine worked).

Following some advice seen in the Forums, I also opened smb.conf and set security = share. With this I could copy files from Windows to Ubuntu without a password. At first I thought I had success, but later found that the copies had little "lock" icons and they had become read-only. Also, I was worried about the safety (security) of having all those permission boxes ticked (even though it was only on specific shared folders which are sub-folders of my home directory).

Sorry for all the detail but this helps explain why I feel my problems are more concerned with permissions and sharing than other aspects.

---

### Post by mips on 2006-08-02
stig,

Off topic but did you get your handle/alias from the "The Stig" on the Top Gear show by any chance ? Best car program out there.

---

### Post by beniwtv on 2006-08-03
Yes, you can use DHCP if you want.

Maybe you try setting these:

```
# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
; create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700
```

Uncomment the two lines and set the first to 0644 and the second to 0775.

This should solve the little 'lock' problem you have.

As for the security=share option, it's true that then you don't need a password. I personally use this setting because then I can share everything. It's not a security issue for me either, since I only have two PC's on my network, both sharing subfolders or special folders. 

So unless somebody has access to your home network from the internet or something it should be OK to set this option.

---

### Post by stig on 2006-08-03
> **mips said:**
> stig,

Off topic but did you get your handle/alias from the "The Stig" on the Top Gear show by any chance ? Best car program out there.

The boring answer is that the day I joined the Forum I was in a hurry and needed to think of an alias that was safe, inoffensive etc. I had just been emailing a customer in Scandinavia whose first name was Stig. That's how it began - and it never crossed my mind about "The Stig".

But (even further OT) I have to admit that I have had some very fast cars - not expensive, just old classics or modified such as Alfas and Jaguars. At 59 years old I drive a bit more slowly now and I would come rather low down on Jeremy Clarkson's list?

You are in South Africa and the last person who asked was in USA - so Top Gear seems very successful.

---

### Post by stig on 2006-08-03
> **beniwtv said:**
> Yes, you can use DHCP if you want.

Maybe you try setting these:

```
# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
; create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700
```

Uncomment the two lines and set the first to 0644 and the second to 0775.

This should solve the little 'lock' problem you have.

As for the security=share option, it's true that then you don't need a password. I personally use this setting because then I can share everything. It's not a security issue for me either, since I only have two PC's on my network, both sharing subfolders or special folders. 

So unless somebody has access to your home network from the internet or something it should be OK to set this option.

Thanks - I'll give this a try.

Just at the moment I'm finding the Forum pages very slow to load.

---

