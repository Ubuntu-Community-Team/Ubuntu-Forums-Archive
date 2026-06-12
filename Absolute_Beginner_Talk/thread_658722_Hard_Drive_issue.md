---
title: "Hard Drive issue"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by LeviathanFafner on 2008-01-04
I got 2 hard drives in my PC, one has Ubuntu on it, and the other is a storage drive that has held data through 5 or 6 windows reinstalls. 

Anyway, my question is how do I get this storage drive to mount automatically when I start Ubuntu and would it be a good idea for me to to reformat this drive to to another, more Linux friendly, format?

---

### Post by ryanVickers on 2008-01-05
I would recommend switching to ext3, yes, if it's not too much trouble.

and if you go "gksudo gedit /etc/mtab" and enter where you want it to mount and the name (/dev/sdb1 maybe...), then it should work

an example of an entry would be "/dev/hda1 /backup/WD ext3 rw 0 0"
tells it that "hda1" hsould be mounted at /backup/WD and its ext3 and its read and write and I don't know what the zeros mean... ;)

---

### Post by eternicode on 2008-01-05
That'd be /etc/fstab, not /etc/mtab.  /etc/mtab, I believe, is the filesystems which are currently mounted.

As for reformatting, if this partition must be accessible from windows, stick with FAT32 (unless you have files larger than 4GB, in which case stick with NTFS).  Otherwise, by all means, switch to linux friendly formats ;)

The zeroes are for "dump" and "pass".  No clue about dump, but pass is the order in which fsck (linux version of checkdisk) will check the volumes at boot time.  A 0 means "don't check".

---

### Post by ryanVickers on 2008-01-05
oh, yeah lol 

I was under the impression that it was an external drive for some reason... ;)

---

