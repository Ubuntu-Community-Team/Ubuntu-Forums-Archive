---
title: "How to mount a network hard drive?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by endokrin on 2005-11-16
Hi.. of course, I'm brand new.  I just installed Ubuntu last night and was surprised I got it working and my wireless connection is working too!

When I switched from Windows XP to Ubuntu, I saved all of my files to a network hard drive on the LAN I have at home.

How do I mount this using Ubuntu?

To mount in Windows I had to simply select the name of the drive I wanted it saved as and type the hard drive's location and the folder, ie. \\backup\netfolder
(where "backup" is the name of the actual network hard drive and "netfolder" is the folder where my files are stored) and then enter the username and password.

How do I connect to this using Ubuntu?

Thanks

---

### Post by matthewv on 2005-11-17
Does anything show up in Places --> Network Servers ?
Or you could try Places --> Connect to server...

---

### Post by endokrin on 2005-11-18
Under 'Network Servers' only one item is listed:  Windows Network.  And when I click on that, nothing shows up.

I tried Places--> Connect to Server
but am unsure which choice I need: FTP, Windows Share, Custom, etc.


Thanks

---

### Post by mwinther on 2005-12-01
Check out [http://ubuntuguide.org/#mountunmountnetworkfoldersall](http://ubuntuguide.org/#mountunmountnetworkfoldersall)

---

### Post by ashrack on 2005-12-08
[QUOTE=mwinther]Check out [http://ubuntuguide.org/#mountunmountnetworkfoldersall](http://ubuntuguide.org/#mountunmountnetworkfoldersall)[/QUOTE]
this is the error I get:
```
mount: wrong fs type, bad option, bad superblock on //server/d,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Here-s the SYSLOG
```
[4300331.965000] smbfs: mount_data version 1684370019 is not supported
```

But thru this command I can access without problems:
```
smb://server/D
```

---

### Post by ashrack on 2005-12-08
Had to install SMBFS
This should be noted in the GUIDE above

---

### Post by kaamos on 2005-12-08
It is noted.
> 
Q: How to mount network folders on boot-up, and allow all users to read?

   1. Read General Notes
   2. Read How to install Samba Server for files/folders sharing service?
   3. ...

It's in number 2..

---

