---
title: "[SOLVED] SAMBA shares with XP broken suddenly; can't fix"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-03-03
I share several directories on my 7.04 box with an XP machine.  The XP machine has been able to see and write to these directories freely, but today they are broken.  I don't know why; I haven't installed anything or changed any software.

The XP machine can see the Linux machine in file manager but can't enter the diirectories.  The Linux machine can see and make file actions in shared XP folders OK.  So actually, it's broken one direction only.

I have reinstalled SAMBA, checked the user accounts, and the problem persists.

Here are the contents of smb.conf:
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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = RBZGROUP

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


[mp3 JAZZ, BLUES and UNFILED]
path = /mnt/local2/mp3 JAZZ, BLUES and UNFILED
available = yes
browsable = yes
public = yes
writable = yes

[mp3 ROCK, POP]
path = /mnt/local2/mp3 ROCK, POP
available = yes
browsable = yes
public = yes
writable = yes

[f@h]
path = /home/thunderrd/f@h
comment = f@h1 on q-6600
available = yes
browsable = yes
public = yes
writable = yes

[f@h2]
path = /home/thunderrd/f@h2
available = yes
browsable = yes
public = yes
writable = yes  
```

---

### Post by superprash2003 on 2008-03-03
there is a fileshare in the name /mnt/local2/ .. is this as external device?? try opening this  location locally in your ubuntu pc and check if it opens.. go to places->computer ... and in the location tab type /mnt/local2/ .. let me know if it opens or not!!

---

### Post by dstew on 2008-03-03
If you do not want people to use password authentication, you can use security = share. Also, the security = user is commented out, but I think user is the default, so maybe it doesn't make a difference. Also, the mount point file names might five Samba some trouble. There are multiple spaces, and commas. Maybe make simple mount point names like mp3_jazz and mp3_rock. I don't think Samba cares about the share names, but I have had a lot of Samba problems related to funny file and directory names.

---

### Post by ThunderRd on 2008-03-03
> **superprash2003 said:**
> there is a fileshare in the name /mnt/local2/ .. is this as external device?? try opening this  location locally in your ubuntu pc and check if it opens.. go to places->computer ... and in the location tab type /mnt/local2/ .. let me know if it opens or not!!

It's an internal SATA drive, and yes, it opens fine from the local machine [2 directories shared].  The other two shares are on the IDE drives.

The four shared directories are not visible in the XP machine, BUT they have been visible and accessible for ages...until today.  

[QUOTE=dstew]Also, the mount point file names might five Samba some trouble. There are multiple spaces, and commas. Maybe make simple mount point names like mp3_jazz and mp3_rock.[/QUOTE]

Since they have been working fine until now, I think the folder names are OK.  I could change them but it would be a headache if I had to, since on the XP box they are referenced this way already in many locations.

---

### Post by rkd on 2008-03-04
It's always frustrating when something stops working when you haven't changed anything.  But, obviously, something is different.

Can you think of anything in either the Ubuntu machine, the Windows machines, or the LAN that changed at the time you started having the problem?  Even if you don't think it could be related, mention it just in case there is a connection you aren't aware of.  How are the IP addresses assigned to the systems on the LAN?  DHCP or static?  

If you haven't already looked at log files, that might turn up a clue.  It looks like your Samba config has it logging to:

  /var/log/samba/log.smbd 
  /var/log/samba/log.nmbd 

Those are text files, so you can look at them with your favorite editor.

On the Windows systems, go to the Event Viewer (right click My Computer, choose Manage, then under System Tools, choose Event Viewer).  I don't know which of the three logs would be most likely to show the problems with file sharing, so look in all of them.  Since you don't even see the shared directories from the Windows systems, there might not be anything to see in the Windows log files, but it usually is a good idea to check anyway.

It probably wouldn't hurt to look in the Linux system log too: /var/log/syslog.

I can't tell you exactly what to look for.  In all of these log files, go to the entries around the time you started noticing the problem, or a little before, and try to see whether any of the messages seem to be reporting something relating to a failure to make the shared directories available.

If looking at the log files yourself doesn't lead you to a solution, it would be good to post log files here.  To be sure we see everything significant, I think it would be a good idea to make note of the system time, then boot both the Linux system and one of the Windows systems, then try to connect from the Windows system to the Samba shares, then copy all the entries made after the time you noted from the Samba log files and the syslog into separate text files and attach those files to a post (not paste them into the post) so we can look at them.

I don't know whether it is worth including the log files from the Windows system.  The Event Viewer can export the files one at a time (under the Action menu), but they typically are fairly large.  I've not worked with them much, so I don't know whether there is a way to export just a portion of the events.  I believe the exported Event files may contain some binary data, so if you try to attach exported Event files, be careful when working with them so you don't accidentally mangle them.

---

### Post by ThunderRd on 2008-03-05
> **rkd said:**
> 
How are the IP addresses assigned to the systems on the LAN?  DHCP or static?  

Static IP; the opteron machine is the gateway 192.168.0.1; the others are also static.

[Quote=rkd]If you haven't already looked at log files, that might turn up a clue.  It looks like your Samba config has it logging to:

  /var/log/samba/log.smbd 
  /var/log/samba/log.nmbd 

Those are text files, so you can look at them with your favorite editor.

On the Windows systems, go to the Event Viewer (right click My Computer, choose Manage, then under System Tools, choose Event Viewer).  I don't know which of the three logs would be most likely to show the problems with file sharing, so look in all of them.  Since you don't even see the shared directories from the Windows systems, there might not be anything to see in the Windows log files, but it usually is a good idea to check anyway.

It probably wouldn't hurt to look in the Linux system log too: /var/log/syslog.

[/QUOTE]

I have rebooted the ubuntu machine and the gateway, and have attached the pertinent logfiles here, after attempting to connect to the shares both ways.  I see some things but don't really know what I'm looking at ;)

I'm intimate with the windows events; there's nothing there that is related.

---

### Post by spiderbatdad on 2008-03-05
did the user accounts expire on linux?

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html)

---

### Post by ThunderRd on 2008-03-05
Should they somehow expire by default?

I have read the link you have sent but can't find information about that.  Can you tell me how to check?

---

### Post by rkd on 2008-03-05
The log files don't show many clues to the problem that I noticed, though I could easily be overlooking something.  There is one message in syslog at 13:29:46 that says gdm couldn't authenticate a user, but gdm is the Gnome display manager, so I think that is not connected with Samba. The series of messages at the end are reporting connection attempts from the Linux system to one of the other systems on your LAN using TCP ports connected with Windows file sharing, so that is probably Samba doing something, but I can't tell from those messages what it is doing or whether it succeeded.

Since that didn't show us the source of the problem, we'll have to try a few other things to see what clues we can turn up.

You have already reinstalled Samba, and you mentioned that you checked the user accounts.  Did you remember to enter exactly the same user name and password for both the Linux userid and the smbpasswd command?  Can you login to the Linux system using those accounts?  Even if you think you set everything up properly, it might be worthwhile to remove Samba, make sure the /etc/samba/smbpasswd file is gone, delete the Linux user accounts, then start over.  Try some simpler things first, but keep in mind that you might have done something wrong on the reinstall.

Did you do anything around the time the problem started with iptables or firestarter that might have blocked a TCP/IP port that Samba uses?

Have you tried to go to a shared directory explicitly rather than browsing to it, to see whether it is just the network browser that is the problem?  To try that, on the Windows computer, go to Start/Run and enter \\Q-6600\f@h into the Open: line and see whether it will display the contents of f@h for you.  Another experiment is to try the same thing using the IP address of the Linux machine instead of Q-6600.  (If I got your machine name wrong, use that instead of Q-6600.)

Windows file sharing has a sort of self-organizing way of letting computers on the LAN learn what other computers are there.  I don't completely understand it, but one of the machines gets chosen to be what is known as the Local Master Browser.  As I understand it, which computer gets so chosen is somewhat random.  I suppose there could be something about your collection of computers that allows Samba to work when the Local Master Browser is one of a subset of your computers, but prevents it from working when one of the other computers is the Local Master Browser.  I don't know how to influence or test that.

Are the Windows computers able to share files on other Windows computers on your LAN?  Is it only sharing from Windows to Linux that doesn't work?

There is a long, step-by-step troubleshooting description at:

   [http://www.samba.org/samba/docs/using_samba/ch12.html#samba2-CHP-12-SECT-2](http://www.samba.org/samba/docs/using_samba/ch12.html#samba2-CHP-12-SECT-2)

If none of the above helps, you might be able to work through that list to find what isn't working.  Ask any questions you have about what it says to do or how to interpret the results, and we'll try to answer.

---

### Post by ThunderRd on 2008-03-05
> **rkd said:**
> There is one message in syslog at 13:29:46 that says gdm couldn't authenticate a user, but gdm is the Gnome display manager, so I think that is not connected with Samba. 
That was me; I miskeyed my username on logon.

> 
it might be worthwhile to remove Samba, make sure the /etc/samba/smbpasswd file is gone, delete the Linux user accounts, then start over. 
That's where I am now; I uninstalled samba, deleted the /etc/samba/ directory, and now I can go through the process again.  I'll have to try to remember how I did it the first time, though, as I've only done it once, and it was a challenge.

> Did you do anything around the time the problem started with iptables or firestarter that might have blocked a TCP/IP port that Samba uses?
Interestingly enough, I recently allowed some ports for bittorrent; I don't think that I made any other changes.  If I remember correctly, default policy is to allow all outbound, but it's restrictive on inbound policy; I used firestarter but it doesn't display all the default rules. I know it's a front end for iptables but i don't know what to look for there, in case I made an error.  What do you suggest?

> Have you tried to go to a shared directory explicitly rather than browsing to it, to see whether it is just the network browser that is the problem? 
Can't see the shares this way either.

> Are the Windows computers able to share files on other Windows computers on your LAN?  Is it only sharing from Windows to Linux that doesn't work? 
At this time it's only two machines; the others were taken to my office weeks ago.  The Linux machine see the shared folders on the XP machine fine.  The reverse isn't true.

> There is a long, step-by-step troubleshooting description at:

   [http://www.samba.org/samba/docs/using_samba/ch12.html#samba2-CHP-12-SECT-2](http://www.samba.org/samba/docs/using_samba/ch12.html#samba2-CHP-12-SECT-2)


I'll look at that, but troubleshooting isn't an issue anymore since I uninstalled samba and reinstalled.    Although it will most likely be useful for me to have the link handy(along with the dozen others I have collected.)  ;)

I am going to try to reconfigure samba for the 4 shared directories, now that it is reinstalled.  If I remember correctly, that part of the process is easy.  I got a bit confused when creating the user account and the samba password for the client access.  I've done my homework, but there are many, many procedures that folks recommend for this, involving editing samba.conf and smbusers.  Since I'm the only user here, I'm not really particular about the security.  I just want to be able to have the 4 directories available to the XP machine.  What would you suggest as the easiest way to do that?

---

### Post by rkd on 2008-03-05
Yes, Samba is confusing. I think it is because the Samba project didn't do a very good job of documenting how to configure it and didn't provide a very good automatic setup.  So lots of people have stepped in, each with a partial understanding and his own idea of the way to do it.  Unfortunately, the many ways are each different, and while they may work for the originator of each, I've seen many complaints that those directions don't work for others.

A suggestion: As you set up Samba, or anything complicated, keep notes of each step.  When you get it working, look over the notes to make sure the notes are readable and complete, then put them somewhere you will be able to find them when you have to set up your system again.  

I claim no special knowledge of Samba.  I've experimented with Samba to answer questions from others and have had some success.  But I can't tell in advance what will work.

If you still have trouble after the reinstall, keep in mind that the iptables might be causing it.  I haven't experimented with it, so I can't tell you how to check anything.  There probably is some simple way to temporarily disable it, just to see whether that lets the Samba stuff start working.  You could unplug your modem from the network during the test to be safe.  If Samba works with iptables turned off, but not when you turn it on again, look for a blocked port that Windows needs to use to communicate with Samba.

Edit: Oops, I copied the wrong test smb.conf file to do the below. It probably won't work for what you want (I don't remember what problem I was trying to solve with it).  Sorry -- if you don't get your shares working, I'll spend a little more time to find the right copy of smb.conf to use as a template for your setup.  End Edit. 

Later Edit: Since you solved the problem, I'm editing this post again to remove the example I created from the wrong smb.conf, since I don't remember what it was trying to solve or even whether it worked. End Edit.

---

### Post by ThunderRd on 2008-03-05
OK, rkd, you've done it again.  

Problem is solved; I would have never thought of checking the firewall configuration through firestarter unless you'd mentioned it.

Yes, it doesn't allow traffic on the netbios ports by default, so you have to manually open ports 137-139 for samba.  I had it working before, but I must have done it from the command line with iptables, then I installed firestarter after that; when you install it you have to configure it completely.  Apparently I didn't, and it was some time before I realized that the shares were broken-that's why I didn't make the connection.

Live and learn.  Thanks again for the help;)

EDIT:
Seems we have crossed posts- I have just now seen the post prior to this one!  That's pretty funny because while you were cribbing that config file for me I was studying this:
[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

It is actually an interesting read about firestarter and problems with samba.

---

### Post by rkd on 2008-03-05
I'm glad you got it solved.  And thanks for the pointer to that thread about how to keep firestarter and iptables from preventing Samba from working. That's useful information.

---

