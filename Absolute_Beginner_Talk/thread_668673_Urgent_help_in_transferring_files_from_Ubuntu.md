---
title: "Urgent help in transferring files from Ubuntu"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ahjiefreak on 2008-01-15
Hi,

I need help in Ubuntu 6.06. I wanted to trasnfer a large files from my home directory to my portable hard disk. However, I can only read them and copy them. I could not able to paste to my portable hard disk in Ubuntu platform. 

I tried reading some related post to these but none related to transferring to a portable hard disk.

Please help!

This is the error when I fire up gksu nautilus with Live CD on my CDROM

gksu nautilus
(nautilus:6257): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Thanks.

-ahjiefreak

---

### Post by bwhite82 on 2008-01-15
Have you tried 'sudo nautilus'? You could always move them via the CLI: sudo mv * /home/username (or vice-versa).

---

### Post by ahjiefreak on 2008-01-15
Hi,

I tried on it and still coudl not move them. 

I tried to use CLI and create a new folder in the portable hard disk. 

But the error message of :- mkdir: cannot create directory `new': Read-only file system



Please advise. Thanks..

Jason

---

### Post by zekopeko on 2008-01-15
i'm guessing it's a windows NTFS formated disk. and nautilus should be run with gksudo
and not sudo.

---

### Post by crjackson on 2008-01-15
> **ahjiefreak said:**
> Hi,

I need help in Ubuntu 6.06. I wanted to trasnfer a large files from my home directory to my portable hard disk. However, I can only read them and copy them. I could not able to paste to my portable hard disk in Ubuntu platform. 

I tried reading some related post to these but none related to transferring to a portable hard disk.

Please help!

This is the error when I fire up gksu nautilus with Live CD on my CDROM

gksu nautilus
(nautilus:6257): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Thanks.

-ahjiefreak

Go to the package manager and see if you can install NTFS 3G support.  This needs to be installed before you can write to an NTFS drive.  Once installed you can mount the drive with write privliges.  From there you can copy and past as normal GUI or CLI.

---

### Post by bodhi.zazen on 2008-01-15
What file system is it ? FAT / NTFS ?

---

### Post by ahjiefreak on 2008-01-15
It is NTFS.

---

### Post by bodhi.zazen on 2008-01-15
With ntfs permissions are set at the time of mount and you need the ntfs-3g driver.

Easiest way is :

```
sudo apt-get install ntfs-config
gksu ntfs-config
```

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by ahjiefreak on 2008-01-15
hi,

I tried to do:-sudo apt-get install ntfs-config

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config

---

### Post by bodhi.zazen on 2008-01-15
ntfs-config is in Universe

You need to enable your repos and re-try

---

### Post by ahjiefreak on 2008-01-15
Hi

What do you mean by enable the repos? Sorry as I am quite new to Ubuntu. I just know that normally we do apt-get install and apt-get update, apt-get upgrade for components.


Thanks.

*Edited*

Hi,
I managed to get your meaning for repo in this case. I tried to enable the Universe. And retry yet get the same error message. 

Please advise. Thanks.

---

### Post by bodhi.zazen on 2008-01-15
OK, sorry

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by The Cog on 2008-01-15
I don't think ntfs-3g was available for version 6.06. So it is fundamentally not able to write to NTFS. 

I would suggest getting a Gutsy (7.10) desktop CD and using that to do the file transfer. 7.10 is able to write NTFS.

---

### Post by ahjiefreak on 2008-01-15
Hi,

In the edited message, I did point out after getting the step by step guide on 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
i still could not get the ntfs.

In the steps, in Ubuntu 6.06 LTS,I have done the Reload button yet when I go again to the System->Admin->Software Properties-> Ubuntu 6.60 LTS, i still see te options is still unchecked.

I can see the downloading bar has complted and closed the Software Properties.Yet, it still occur the same error message. Please help.

---

### Post by bodhi.zazen on 2008-01-15
oic, as The Cog said, ntfs-3g does not appear available in 6.04

You will need a more up to date distro, you can do this with almost any live CD, a newer Ubutnu or Knoppix or ....

---

### Post by ahjiefreak on 2008-01-15
hi.

I am using Ubuntu 6.06. I tried to add something close to ntfs in Synaptics yet the error message still appear.

What do you mean by having distro? What would be the shortest and easiest way to work around?


Thanks.

---

### Post by bodhi.zazen on 2008-01-15
You need something like Ubuntu 7.10

You can likely do what you need from the live CD.

---

### Post by The Cog on 2008-01-16
> **ahjiefreak said:**
> hi.
What do you mean by having distro? What would be the shortest and easiest way to work around?

Thanks.

For distro, read version. Ubunti releases a new version about every 6 months. Your version is almost 2 years old, and doeesn't have NTFS support. If you only want to access the files once, then using a recent live CD instead of your installed version of Ubuntu is the quickest and easiest approach. If you want to do this regularly then you had better uppgrade to a larer version of Ubuntu. This is probalby best done by copying all your data off to a backup and then installing a fresh Ubuntu, then copying the data back again, frm the earlier backup.

---

