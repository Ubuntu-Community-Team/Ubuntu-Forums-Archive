---
title: "File system check failed w/update"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Zero Prime on 2007-04-10
Ok, got this mornings update and the system got hosed again.  While booting I get this error: File System Check Failed.  I checked the checkfs log after I finally got the system up.

Log of fsck -C -R -A -a 
Tue Apr 10 09:37:25 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/hdb1

/dev/hdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 4926 files, 536611/1246606 clusters
fsck died with exit status 8

Tue Apr 10 09:37:27 2007
----------------

Also, all my drives have been unmounted, worse of all even under places there are no HDA1 or HDA2.  HDB1 shows up, but I have to mount it to use it.  Can someone please help!!??

---

### Post by rai4shu2 on 2007-04-10
I think Feisty is using /dev/sdX rather than /dev/hdX lately. For example, hard drives may be sda or sdb and CD/DVDs may be /dev/scd0 or something like that.

---

