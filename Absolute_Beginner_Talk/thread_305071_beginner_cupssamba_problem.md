---
title: "beginner cups/samba problem"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dross on 2006-11-22
Hi everyone,
I have cups and samba installed on my Ubuntu server (6.06 - auto-LAMP)...but am having problems sharing files/printers.  All I want to do is be able to save some files from my XP and OS X laptops onto my Ubuntu server, and (more importantly) give those laptops access to a printer on the server.  Right now, both cups and samba are running but I can't see them from XP laptop...any suggestions?

---

### Post by BoneKracker on 2006-11-22
```
man 5 smb.conf
```

---

### Post by dross on 2006-11-23
Thanks...I took a look at the samba man pages and some sample smb.conf files and made 'some' progress...I can now see my Linux server from my windows laptop, but when I try to access 'homes', I get one of two messages:

\\server\homes is not accessible. You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.  The network path was not found.

or it offers a login screen where I enter my host\user and password (which I set up using 'smbpasswd -A user' ), which always rejects my credentials.

First, of all, I have no idea why it offers two different messages when I try to log in...I am not making any changes to samba!!

Second, not sure why it is rejected my username and pass...

Any help would be much appreciated!

here's my smb.conf:

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
workgroup = mshome

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

#security = user or security = share (for no passwd)
security = user

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
printing = cups
printcap name = cups

map to guest = Bad User
show add printer wizard = No

[homes]
comment = Home Directories
path = /home/brian
browseable = yes
writable = yes
create mask = 0700
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/cups
printable = Yes
guest ok = Yes
use client driver = Yes
browseable = No

[brian]
path = /home/brian
available = yes
browseable = no
public = yes
writable = yes

---

