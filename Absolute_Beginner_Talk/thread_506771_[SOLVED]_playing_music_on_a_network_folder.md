---
title: "[SOLVED] playing music on a network folder"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by NeillHog on 2007-07-22
I have Kubuntu installed since three days and the learning curve is very steep.
I have Amarok playing mp3s. It will play any mp3s in my home folder and also any on storage media (including those on my windows partition.

Most of my music is on an external server which I can see under network folders
smb://admin@nslu_1/music/
If I try to play on any of these mp3s I get an error message "Error loading media".

What am I doing wrong?

Thank you!

---

### Post by Hossie on 2007-07-22
You can mount a samba share. Then every application is able to use it.

```
sudo mount -t smbfs //1.2.3.4/Sharename /some/dir/to/mount -o "workgroup=XXX,username=XXX"
```

You can omit workgroup and username if not needed.

---

### Post by NeillHog on 2007-07-22
> **Hossie said:**
> You can mount a samba share. Then every application is able to use it.


Thanks. I will try that. Do I just do it once or must it be somewhere that runs every time I start?

Thanks again.
Neill

---

### Post by Hossie on 2007-07-22
You can add it in your /etc/fstab.

```
//1.2.3.4/Sharename /dir/to/mount smbfs uid=yourusername,gid=yourgroup 0 0
```

---

### Post by NeillHog on 2007-07-22
Just spent an hour trying but it is not working

I created a local dirctory /media/nmusic

and then tried:
sudo mount -t smbfs //192.168.178.29/music /media/nmusic -o "workgroup=XXX, username=XXX"

to which I received the answer "mount: wrong fs tyoe, bad option, bad superblock on //192.168.178.29/music
miising codepage or other error ...

What am I doing wrong.
Thanks!

Something I forgot - The music is on a Linux server (ext3)

---

### Post by Hossie on 2007-07-22
Works for me.

```
tuxy hossie # mount -t smbfs //192.168.1.131/C\$ /mnt -o "username=Administrator"
Password:
tuxy hossie # echo $?
0
```

I'm using Gentoo, so I cant really tell what packages smbfs depends on. Try a

```
sudo apt-cache search samba
```

```
sudo apt-cache search smb
```

Maybe packages are missing.

---

### Post by NeillHog on 2007-07-23
> Try - sudo apt-cache search samba
The result was as follows:

ccache - Compiler results cacher, for fast recompiles
kdenetwork-filesharing - network filesharing configuration module for KDE
libpam-smbpass - pluggable authentication module for SMB/CIFS password database
libsmbclient - shared library that allows applications to talk to SMB/CIFS servers
libsmbclient-dev - libsmbclient static libraries and headers
python-samba - Python bindings that allow access to various aspects of Samba
samba - a LanManager-like file and printer server for Unix
samba-common - Samba common files used by both the server and the client
samba-dbg - Samba debugging symbols
samba-doc - Samba documentation
samba-doc-pdf - Samba documentation (PDF format)
smbclient - a LanManager-like simple client for Unix
smbfs - mount and umount commands for the smbfs (for kernels >= than 2.2.x)
swat - Samba Web Administration Tool
xubuntu-system-tools - graphical system administration tools for Xubuntu
cadaver - command-line WebDAV client
dbench - The dbench (disk) and tbench (TCP) benchmarks
distcc - Simple distributed compiler client and server
distccmon-gnome - GTK monitor for distcc a distributed client and server
dpsyco-samba - Automate administration of access to samba
egroupware-sambaadmin - eGroupWare Samba administration application
fusesmb - filesystem client based on the SMB file transfer protocol
gadmintools - GTK+ server administration tools
gosa - Web Based LDAP Administration Program
gsambad - GTK+ configuration tool for samba
jags - Just Another GTK+ Samba Client
komba2 - KDE Samba browser
ldap-account-manager - webfrontend for managing accounts in an LDAP directory
ldapscripts - Add and remove user and groups (stored in a ldap directory)
ldaptor-common - Pure-Python library for LDAP (common files)
libcrypt-smbhash-perl - generate LM/NT hash of a password for samba
libfilesys-smbclient-perl - perl interface to access Samba filesystem
libnet-nbname-perl - NetBIOS Name Service Requests
libpam-mount - PAM module that can mount volumes for a user session
libroxen-ntuserauth - WinNT/SMB user authentication module for the Roxen Challenger web server
libtalloc1 - hierarchical pool based memory allocator
linneighborhood - An SMB network browser for Linux and X11.
linpopup - X Window System port of Winpopup, running over Samba
nautilus-share - Nautilus extension to share folder using samba
php-auth - PHP PEAR modules for creating an authentication system
pyneighborhood - An SMB network browser for Linux and X11 written in Python
python-ldaptor - Pure-Python library for LDAP
python-smbpasswd - This module can generate both LANMAN and NT password hashes
python-wmi - DCOM/WMI client implementation, Python bindings
smb2www - A Windows Network client that is accessible through a web browser
smb4k - A Samba (SMB) share advanced browser for KDE
smbc - samba-commander - curses based samba network browser
smbldap-tools - Scripts to manage Unix and Samba accounts stored on LDAP
snort - Flexible Network Intrusion Detection System
snort-common - Flexible Network Intrusion Detection System [common files]
snort-doc - Documentation for the Snort IDS [documentation]
snort-mysql - Flexible Network Intrusion Detection System [MySQL]
snort-pgsql - Flexible Network Intrusion Detection System [PostgreSQL]
tksmb - SMB (Samba and Windows) network browser
wmi-client - DCOM/WMI client implementation
xffm4-samba - Samba browser for Xffm
xmms2-plugin-smb - XMMS2 - Samba transport
xsmbrowser - X11 tool for navigating SMB Networks
zope-exuserfolder - extensible user authentication product for zope

which unfortunately tells me absolutely nothing. That is why I am in the beginners forum :-)

At least the command
sudo mount -t smbfs //192.168.178.29/music /media/nmusic -o "workgroup=XXX, username=XXX" now produces the error
5649: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
so maybe we are getting somewhere.
The username and password I am using are correct. They are the ones that I use when I go to this drive via "Network folders" - "samba shares" - "Hogarth" (workgroup) - "Nslu_1" (server) - "music" (share).

I am sorry but I no longer no what to try.
Maybe I am just too stupid for Linux :-)

Thanks!

---

### Post by Hossie on 2007-07-24
So the two needed packages are samba and smbfs.

```
sudo apt-get install samba smbfs
```

You could also try to omit the workgroup or to share your folder as full-guest access and leave out the options completly.

---

### Post by NeillHog on 2007-07-24
>So the two needed packages are samba and smbfs.
Did that and got this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
samba is already the newest version.
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 346 not upgraded.

> You could also try to omit the workgroup or to share your folder as full-guest access and leave out the options completly.

Brilliant! Fantastic!
I gave the group everyone read rights and it works!
Thank you Hossie for your time and patience.

Kubuntu is about as clear as mud but the forum is great!

---

### Post by NeillHog on 2007-07-28
More problems :-(

I logged out and back on and my music was no longer there. It is still on the server but no longer in /media/nmusic which is where Amarok is looking for it.

Once I did
sudo mount -t smbfs //192.168.178.29/music /media/nmusic
it was back again but my question is how do I do this permanently?

Hossie wrote 
> You can add it in your /etc/fstab.
but I have tried repeatedly with the syntax
//192.168.178.29/music /media/nmusic smbfs defaults 0 0
but it does not work :-(

What am I doing wrong?

As always thanks for the help.

Neill

---

### Post by NeillHog on 2007-07-30
Sorry. It works now. Must have been a spelling mistake.

---

### Post by NeillHog on 2007-08-12
Solved at
[http://ubuntuforums.org/showthread.php?t=519054](http://ubuntuforums.org/showthread.php?t=519054)

thanks!

---

