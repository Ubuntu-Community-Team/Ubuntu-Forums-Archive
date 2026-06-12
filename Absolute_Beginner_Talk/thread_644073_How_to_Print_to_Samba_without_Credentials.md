---
title: "How to Print to Samba without Credentials"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by luke802 on 2007-12-18
Hi All, thanks in advance for any help you may have...

I am more accustomed to Fedora but have become a big fan of ubuntu in recent times. I am taking the plunge of setting up Ubuntu to be our home printer/file share server and replace the old fedora box but i am having just one problem:

I would like to allow windows users to be able to print to the shared Samba Printer without having to enter any samba/linux credentials. This is becoming a pain as it with windows Vista the user isn't prompted for credentials when attempting to print, instead they have to point an explorer browser to \\*printer IP/Host* and then enter the appropriate credentials.

Once this is done they can begin printing after. I would like to avoid that step....

Here is my Samba Config:
```
#

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = SILVER2

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
; wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
; syslog only = no

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
security = user

# You may wish to use password encryption. See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

; guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
; unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
; pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
; domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
; logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
; logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
printing = bsd
printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
printing = cups
printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
; printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
; domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
; winbind enum groups = yes
; winbind enum users = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
; comment = Home Directories
; browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
; valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
; writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
; create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

wins support = yes
[printers]
comment = All Printers
browseable = yes
path = /var/spool/samba
printable = yes
public = yes
writable = yes
create mode = 0777

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
browseable = yes
read only = no
guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom


[allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
writable = yes

available = yes
browsable = yes
public = yes
[homes]
comment = Home Directories
browseable = no
valid users = %S
writable = yes
create mask = 0700
directory mask = 0700
```

#================================================= =========


Here is my Cupsd Conf:
```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
# Allow shared printing and remote administration...
Order allow,deny
Allow all
</Location>
<Location /admin>
# Allow remote administration...
Order allow,deny
Allow all
</Location>
<Location /admin/conf>
AuthType Default
Require user @SYSTEM
# Allow remote access to the configuration files...
Order allow,deny
Allow all
</Location>
<Policy default>
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
AuthType Default
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
AuthType Default
Require user @SYSTEM
Order deny,allow
</Limit>
<Limit CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>
<Limit All>
Order deny,allow
</Limit>
</Policy>
```
#================================================= ======

Any help appreciated!! Thanks

---

### Post by Nano Geek on 2007-12-18
Can they not install the samba printer like you can a normal printer in XP or Ubuntu?

---

### Post by BjBlaster on 2007-12-19
I think this is the same problem I'm having with sharing a "share" instead of a user authenticated share. 

Sorry to hijack your thread a bit, but this is what I'm having trouble with.....

I've been a Fedora bloke for quite some time, and finally snapped over to Ubuntu, I've currently running 7.10 and have this issue I would love some info on...

I have a Fedora server running samba, I have had this for several years and been using winXP to connect to my shares without any trouble in shared mode without user auth.

Now I have an Ubuntu desktop machine if I use the built in Places/Connect to a server option I can connect and read and write to the share I have (which is a share without any username or password) without trouble. That is; this path works: **smb://hanna/hanna_d/Mp3**s read/write.

If I then mount the path using this:
**mount -t cifs //hanna/hanna_d /mnt/hanna/j_drive -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77**

It mounts ok, I can read everything from the new mounted point, but if I create a directory, I then can't delete the directory I just made. If i then go in this way -> **smb://hanna/hanna_d/** I can then delete the folder and read and write fine, just not to the actual mounted location** /mnt/hanna/j_drive**.

I know it's some permissions thing, but I would like to know how the **smb://** method avoids this, and how I can get my shares to mount with full read write access without user authentication.

Thanks for any help.

But here is the interesting thing, I can print without a username and password fine but only on XP machines! My Vista box and using Ubuntu as a "desktop" machines do what yours does.

Can anyone help us Fedora-to-be-converted people here?

Cheers

Bj

---

### Post by luke802 on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> Can they not install the samba printer like you can a normal printer in XP or Ubuntu?

Indeed they can do this. The printer is installed on their machine, they can see it and what not. The linux Machine just seems to be denying the print requests until the Vista Machine actually logs into the samba share using some form of linux credentials. 

I am trying to figure out how to get around that part, the credentials part, not the how to add the printer part. 

Thanks for the reply and any other suggestions! :(

---

### Post by Nano Geek on 2007-12-19
That's strange.
Unfortunately, I don't have much experience with Samba or printing from Samba.
It your Linux computer isn't a file-server also, you could try disabling password login and see if that fixes the problem.

---

### Post by luke802 on 2007-12-19
How do i disable password authentication?

---

### Post by luke802 on 2007-12-19
Bump Bump

---

### Post by Nano Geek on 2007-12-19
I was just looking around, and this looks like it might have the answer to your problem under Setting Up Access Control.

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

I hope it works for you.

---

### Post by luke802 on 2007-12-23
> **asjdfwejqrfjcvm msz34rq33 said:**
> I was just looking around, and this looks like it might have the answer to your problem under Setting Up Access Control.

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

I hope it works for you.


thanks. Will try it out.

---

### Post by luke802 on 2007-12-23
there seems to be alot more information there for connecting to shares on windows machiens than using samba as a fileshare in itself.... Theres nothing there in the access controls for disabling passwords.

---

### Post by Nano Geek on 2007-12-23
But it looked like it might be showing you how to permanently keep the password for the printer share in Windows.

Is it not showing that?

---

