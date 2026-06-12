---
title: "[SOLVED] Mounting partitioned drive"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Sirchristopher on 2007-08-18
I was running a duel boot system on my laptop.  XP and Ubuntu.  I have a 20GB partition for Ubuntu  and 60GB partition for XP.  I deleated XP and formated the 60GB HD asEXT3.  It worked great.  But I wanted to expand my 20GB HD.  I tried to do this through GParted and I couldn't because the partition I wanted to resize I was on and I  can't unmount it while in use.  So I downloaded the live CD for GParted.  Ran that but it did not allow me to do anything.  I rebooted my system and now I get a message that says Ubuntu can not mount my drive.   Please help. 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7961    63946701   83  Linux
/dev/sda2            9472        9729     2072385    5  Extended
/dev/sda3            7962        9471    12129075   83  Linux
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris
/dev/sda6            9472        9544      586309+  82  Linux swap / Solaris

---

### Post by benerivo on 2007-08-19
It's odd that GParted didn't allow you to change the partitioning, although obviously it did something to your 60GB partition as it now won't mount. I always just use the GParted that comes with the Ubuntu CD rather than the version on its own. Sometimes it won't allow me to make changes to a partition because it is mounted at the time, so i have to unmount it (both from the GParted window and then from the desktop), then try to make the changes.

If it's already formatted you have nothing to lose, so i would delete it, then resize the 20GB, then make a new second partition.

Also, from your image, one error message says that the mount point for the partition has an invalid character, or a new line. Check what the mount point is in your /etc/fstab file. It should be formatted like this example...

/media/storage

---

