---
title: "Created Samba user and lost ability to see XP shares"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by minion.ts on 2008-01-31
Hi everyone, 

I have 3 computers on the network, a Toshiba a70 laptop running Ubuntu 7.10, an Acer 5050 laptop running XP Media Center, and an emachines desktop running XP Home. All are connected through a DLink router. The router is currently set up with MAC filtering and reserved DHCP leases by MAC ID, IPs are .197 (Ubuntu), .198 (XP Lap), .199 (XP desk) the firewall is not enabled, nor is encryption. I have the laptops both connected wirelessly and the desktop wired, all are using DHCP. The XP boxes have been working happily in this configuration for quite some time.

After I installed Ubuntu, the first thing I did was create a folder "Shared" in my /home directory and shared it (right click, share folder). When prompted, I installed both support for windows networks and unix networks. After the installation and sharing of the folder, I go to "Places -> Network" where I can see "Windows Network". Double clicked that and I can see my workgroup, Mshome. Double click on that and I can see and access all my shares on both XP machines. When I go to the XP machines, I can see my Ubuntu share folder also, great!.... NOT. 

I can't access the Ubuntu share, needs user/pass....Here's where the problem started. When I discovered the need for a user/pass, I created one by following instructions on this forum, thread link.... eh i dunno, here's the code from my terminal:

sudo /etc/init.d/samba stop
sudo smbpasswd -a minion (entered password when prompted)
sudo /etc/init.d/samba start 

I used the same username i used when installing Ubuntu, same pass also.

Once I used the above code to create the user, I can no longer see any of my windows shares. I go into Places -> Network and I can see Windows Network, but when I double click it, I can't see the workgroup, and the status bar at the bottom simply says 0 items. My XP boxes can both still see the Ubuntu share folder with no trouble. 

Any help is greatly appreciated, I know there are alot of these threads but they all seem to be about XP not seeing Ubuntu... I'm a little backward I guess.

-minion.ts

---

### Post by minion.ts on 2008-01-31
Here is my smb.conf file if it helps, though I did not modify it.




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
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

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
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

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
# This might need tweaking when using external authentication schemes
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

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


[shared]
path = /home/minion/shared
available = yes
browsable = yes
public = yes
writable = yes

---

### Post by oedha on 2008-01-31
may i ?
you want to shared /home/minion/shared.....
can you check the permission ? 
open terminal then :==> ls -l /home/minion/shared
if it was not like drwxrwxrwx.....means you have to 
sudo chown -Rf root.root /home/minion/shared
sudo chmod -Rf 777 /home/minion/shared

regards;
~E~

---

### Post by minion.ts on 2008-01-31
Wow, thanks for the quick reply.

But.... does the permissions for the shared folder on my ubuntu computer have an effect on my ability to see folders that I have shared from my XP computers? I can hop on either XP computer and transfer files to and from my Ubuntu computer right now, infact I just sent a movie from my xp laptop to the ubuntu laptop as a test. The problem is that i have lost the ability to see my xp computers from my Ubuntu computer.

minion@laptop-02:~$ ls -l /home/minion/shared
total 716076
-rwxr--r-- 1 minion minion 732538880 2007-12-27 00:49 testclip.avi

I'll give your suggestion a go and see what happens

-minion.ts

*edit:

I tried your suggestion but nothing changes, I can still freely read or write to my Ubuntu laptop from both XP machines but they are both invisible to Ubuntu. Please let me know if and how i should reverse those commands if necessary... I'm a newb and have had to re-install on more than one occasion because I don't know how to reverse something I've done.....

Here's what I tried (I don't think stopping and starting samba was necessary, but just incase...):

sudo /etc/init.d/samba stop
sudo chown -Rf root.root /home/minion/shared
sudo chmod -Rf 777 /home/minion/shared
sudo /etc/init.d/samba start

---

### Post by oedha on 2008-01-31
first....make yours rwx...then see what happen ...can the XP work on that ?
next...about seeing XP....i guess it can be done from nautilus...by typing computer name or the IP address

~E~

---

### Post by minion.ts on 2008-01-31
Thanks again for the reply, but sorry, I'm not sure how to "make yours rwx".. I'm not really even sure what that means.

What I really want to do is somehow reverse what I did when I used the smbpasswd line to create the username. Before I ran that command, I was able to read and write *from* Ubuntu *to* windows.... now It is the opposite, I can only read and write *from* windows *to* Ubuntu.

If I can't have both... I'd rather access windows shares from Ubuntu. I just don't want to have to reinstall it to get back to the state it was before. 

-minion.ts

---

### Post by minion.ts on 2008-01-31
Ok, so I ran the following code:

sudo smbpasswd -x minion

I received confirmation that the user 'minion' was deleted. After a reboot I am now back where I started, with a slight change. Now on the Ubuntu box I can see all 3 computers alongside "Windows Network" when I go to "Places -> Network". Originally I had to go into the Windows Network, then into the workgroup (I still can I suppose).

So on the XP machines now I can see Ubuntu but not access it. Any suggestions as to how to access Ubuntu without losing the ability to access windows?

-minion.ts

---

### Post by oedha on 2008-01-31
sudo chmod -Rf 777 will make your folder rwx
if you done this....why dont you check on xp....can it open your folder ?

have you open nautilus then type :==> smb://computerxpname ?

~E~

---

### Post by minion.ts on 2008-01-31
Ok, the command you just gave me was also in your original suggestion, so yes, the folder is rwx. 

I'm not really sure what's going on here but I've fixed my problem, hopefully permenantly. 

I was sure the smbpasswd creation caused the issue so I removed the username with smbpasswd -x minion. This removed the ability for XP to see Ubuntu, but allowed Ubuntu to see XP.... then after reading your second suggestion, about typing smb://computername, I recretaed the samba user with sudo smbpasswd -a minion (and set my pass) and rebooted. After the reboot I got a gnome error about its configuration daemon (great...) so I rebooted again.

After the second reboot, and with no other changes, I can again see all 3 computers and access them from the Ubuntu box... and I can also now access the Ubuntu shared folders from one of the XP machines! I'm sure the other xp box will see it, but its my roomates box and he's asleep now :P

Thanks for the help, 
minion.ts

---

