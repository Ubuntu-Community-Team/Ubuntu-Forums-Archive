---
title: "a question for ext hard disk"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by tim01 on 2006-12-22
i have been trying every post on how to set permission for write on my external hard disk and the only option am about to do is to format it to fat32.is this really a good idea?will it be of less performance and will i be able to write to it when its fat32?
its 320GB. please help out a desperate linux learner.

and many thanks for linux developers.

---

### Post by taurus on 2006-12-22
Are you talking about writing to ntfs filesystem in Ubuntu?  Well, you can do that with ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by tim01 on 2006-12-22
> **taurus said:**
> Are you talking about writing to ntfs filesystem in Ubuntu?  Well, you can do that with ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

thanks for your reply.but i tried  the link before but without luck.actually i meant that i am trying to format the disk from ntfs to fat32.

many thanks

---

### Post by taurus on 2006-12-22
I just checked and the link is good!

If you want to convert ntfs to vfat, you can use gparted in Ubuntu.  Just make sure you don't have it mount first before you do the converting...

---

