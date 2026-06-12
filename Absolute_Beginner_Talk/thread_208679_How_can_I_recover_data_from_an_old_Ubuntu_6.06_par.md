---
title: "How can I recover data from an old Ubuntu 6.06 partition?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by ChiendeRue on 2006-07-03
The Question:

[B]How can I recover the files on my old partitions (in the unbootable Ubuntu 6.06)?
[/B]
The history: I deleted a partition on my second physical hard drive. I had dual Win XP / Dapper
GRUB & MBR were destroyed because I deleted the first partition on the second physical hard disk.
Win XP installation disk fixed (created a new) MBR - I can boot XP
After several attempts to recreate a grub and enter into my old ubuntu, I gave up.
I installed a new Ubuntu 6.06 with alternate Ubuntu CD

Now I see the old partitions but I can not mount them:

oem@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           15299       16573    10241437+  83  Linux
/dev/sdb2           16574       19457    23165730    5  Extended
/dev/sdb3   *           1       14920   119844868+  83  Linux
/dev/sdb4           14921       15298     3036285   82  Linux swap / Solaris
/dev/sdb5           16574       19330    22145571   83  Linux
/dev/sdb6           19331       19457     1020096   82  Linux swap / Solaris

---

### Post by encompass on 2006-07-04
what command are you using for the mount and which partition is it?

---

### Post by ChiendeRue on 2006-07-04
Hey encompass!

I'm trying to install device /dev/sdb5
Like a real XP-user, I just right-click the volume (Places > Computer ) and then "mount" as in screenshot

Note that it keeps telling me that /dev/sdb5 is not a removable device; could not execute pmount . Sure it's not removable! It's actually a partition on my second physical internal HDD.

**Is there a better way to mount?**

Note also that I deleted partition 1 on the HDD from win XP - that's how trouble started

---

### Post by confused57 on 2006-07-04
If you haven't found a solution, maybe this could help:

[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

---

### Post by encompass on 2006-07-04
I would look at the link above, he is right, it looks like it was never assigned and setup.  I can help you with that if you can't figure out that howto.  But I am hoping you can teach yourself this one.  Once you figure out how to mount it.  I can give you some guidence on how to have it mounted at boot too.  (hint... /etc/fstab)
¶:  good luck my dear fellow!

---

### Post by ChiendeRue on 2006-07-05
Thanks guys, very much appreciated!

I followed the instructions on [http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)
My problem is SOLVED:D

---

