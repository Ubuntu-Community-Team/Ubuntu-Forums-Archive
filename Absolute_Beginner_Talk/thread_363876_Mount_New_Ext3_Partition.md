---
title: "Mount New Ext3 Partition"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Zadok001 on 2007-02-17
I had a secondary HD with three NTFS partitions.  Using gparted, I deleted two of those three partitions (hdb2 and hdb3), and created a new partition in ext3 to replace them.  That worked perfectly.  I cannot seem to decipher how to mount my new partition such that I can actually USE it, however.  :-)  Help?

gparted registers the new partition as /dev/hdb2, but it's got no mount point.  Intuitively, I tried 'mount /dev/hdb2,' which informed me that /etc/fstab had no record of such a thing.  I'm unclear on what /etc/fstab has to do with /dev/hdb2 or /media/hdb2 (the point I'm trying to mount the new partition to).

Save me, Gods of Ubuntu!

---

### Post by Zadok001 on 2007-02-17
AH-HA!

So after digging through a few extra reams of documentation, I discovered the correct process, I think.  You have to first edit fstab, which appears to be a list of partitions, and add something like this:

/dev/hdb2 /media/hdb2 ext3 defaults 0 0

(And I have no idea what defaults 0 0 does, so if anyone sees this, please enlighten me.)

Then you run a sudo mount -a, which appears to use fstab to determine what disks exist and where to mount them.  The extra partition then exists in the /media/hdb2 folder.

This brings up a philosophical point.  Since these mount points allow me to essentially mount a disk invisibly inside of my file system (unlike Windows, where I end up with two partitions that I have to navigate to separately), is there any real reason to partition disk space under ext3?  Or should I just make my disk one big partition and organize it in the file system?

---

