---
title: "Trying to mount my drive"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Zubatron on 2008-03-19
Ok so I just installed 7.10 and when I did it did not mount my backup drive and it changed the file system from a NTFS to an Extended. This is what I get when I see the drives.

matt@matt-laptop:~$ sudo fdisk -l

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9169    73649961   83  Linux
/dev/sda2            9170        9546     3028252+   5  Extended
/dev/sda5            9170        9546     3028221   82  Linux swap / Solaris
matt@matt-laptop:~$ 


sda2 shoulda been my backup drive. So am I screwed now? Or what

---

### Post by bodhi.zazen on 2008-03-19
fdisk -l is listing a single drive, and that drive appears to be all ubuntu.

If that is your backup drive looks like you installed Ubuntu on the entire disk.

You may be able to recover some data with testdisk or photorec :

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)

	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by unutbu on 2008-03-19
You're in luck... sorta.
Your backup drive would be named something like /dev/sdb.
Ubuntu did not overwrite your backup drive or change its filesystem type. 
It simply hasn't detected and mounted the drive.

Why the drive was not detected, I do not know.

---

### Post by Victormd on 2008-03-19
> **unutbu said:**
> You're in luck... sorta.
Your backup drive would be named something like /dev/sdb.
Ubuntu did not overwrite your backup drive or change its filesystem type. 
It simply hasn't detected and mounted the drive.

That depends if the backup was a separate HD or a partition, furthermore, if the partition was created as a logical or extended partition.

If you installed using the automatic settings under the partitioner during install, you might just have formated the entire drive and lost your backup...

---

