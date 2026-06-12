---
title: "Backup?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by houseisland on 2006-07-30
Hi,

Can someone point me towards backup applications for data and/or system?  

To DVDs would be cool.

The Package Manager has a utility for KDE.  Does this work with Gnome?

What disk cloning utilities will work with Linux file systems?

Thanks.

---

### Post by nanotube on 2006-07-31
you could try using rdiff-backup. it's pretty simple to set up and use. (and available in the repos).

---

### Post by houseisland on 2006-07-31
> **nanotube said:**
> you could try using rdiff-backup. it's pretty simple to set up and use. (and available in the repos).

Thanks.  I will give it a try.

I also found this somewhat dated thread:

[http://ubuntuforums.org/showthread.php?t=35087&highlight=disk+cloning](http://ubuntuforums.org/showthread.php?t=35087&highlight=disk+cloning)

---

### Post by aysiu on 2006-07-31
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by houseisland on 2006-07-31
Thanks, all.

I am looking for something that a non-techie kid can handle.   The command line stuff is a bit off the deep end -- ok for me, maybe, but a bit harsh for my kid.

I tried Simple Backup, but it wouldn't work with the DVD burner, at least not easily.  Haven't time to tweak.

I would like to find something that can back up user data to an optical drive -- set up a job and run it every so often.  I may have to rely on the native burner software.

For full system disaster recorvery an imaging program would be cool.  

I own multiple legal copies of various versions of Ghost.   I have heard that Ghost 2003 supports Linux partitions -- mever tried it, though.  True?  

I also have Active Disk but I can't remember whether it supports Linux partitions and optical drives.  

I don't think BootItNG does imaging -- must look the next time I use it.

Must experiment.

Thanks again.

:)

---

### Post by houseisland on 2006-07-31
> **houseisland said:**
> I have heard that Ghost 2003 supports Linux partitions -- mever tried it, though.  True? 

Yes and no.  2003, 7.5 and newer will image Linux partitions but a recovery from the image will require a reinstallation of Grub. 

> **houseisland said:**
> I also have Active Disk but I can't remember whether it supports Linux partitions and optical drives.  

No Linux.  No optical drives.

> **houseisland said:**
> I don't think BootItNG does imaging -- must look the next time I use it.

No cloning.  But Terabyte does have a Linux cloning utility.

---

### Post by Smandola on 2006-07-31
houseisland,
I use K3b, its actually requires KDE, so it will load a number of KDE files.  The reason I like it:  simple to use, drag and drop functionality.  As for scheduling backups.  I schedule those when I remember to do it.;)

---

### Post by shoki on 2006-08-01
> **houseisland said:**
> 
I own multiple legal copies of various versions of Ghost.   I have heard that Ghost 2003 supports Linux partitions -- mever tried it, though.  True?  



I happen to have Ghost 2003... used it all the time with XP Pro :rolleyes:

Since I already bought it I would be ashamed in using it. Other than that if there is a step by step guide for how to use sbackup to completely back up and restore your you system. Either way would be fine with me.

---

