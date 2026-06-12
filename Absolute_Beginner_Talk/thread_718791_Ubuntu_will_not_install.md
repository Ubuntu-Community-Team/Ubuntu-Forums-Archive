---
title: "Ubuntu will not install"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Crash90 on 2008-03-08
[http://ubuntuforums.org/showthread.php?t=717226](http://ubuntuforums.org/showthread.php?t=717226)

In that thread, I described why I need to reinstall.


When I try to install Ubuntu now, I get an error no matter if I use the guided (all of hard drive) guided (use free space) or even the manual.

The error I get  is:

he attempt to mount a file system with type reiserfs in SCSI1 (0,0,0), partition #3 (sda) at /home failed.

You may resume partitioning from the partitioning menu.

It makes no difference if I use the ext3 format.


Help! I need my computer back:D

---

### Post by ugm6hr on 2008-03-08
Try starting with a fresh blank HD.

Use any of the Hard Disk Wiping Tools here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Then try again.

I am assuming you are using the same install CD as you successfully used previously.

PS: ReiserFS does not work with Ubuntu (I believe).  Use ext3.

---

### Post by Arthur Archnix on 2008-03-08
Do you mind losing the data on the hard-drive? If you're willing to do a clean install, download the gparted live cd, boot it up, delete all the partitions and reboot.

You can use gparted live to create a new partition layout if you like. I do, then I tell Ubuntu where to mount things. 

In any event, once you delete everything you should have any more problems.

---

### Post by timbounceback on 2008-03-08
> **ugm6hr said:**
> PS: ReiserFS does not work with Ubuntu (I believe).  Use ext3.
Actually, it does (I'm using it for my home directory now), but you're more likely to get support with Ext3; it's more widely used and for Ubuntu is generally the "default".

---

### Post by ugm6hr on 2008-03-08
> **timbounceback said:**
> Actually, it does (I'm using it for my home directory now), but you're more likely to get support with Ext3; it's more widely used and for Ubuntu is generally the "default".

Good to know. Cheers.

---

