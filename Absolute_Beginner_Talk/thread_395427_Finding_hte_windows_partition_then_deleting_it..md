---
title: "Finding hte windows partition then deleting it."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Little Pete on 2007-03-28
Hi folks,

 Been lurking for a while but I thought it was time to get my Ubuntu running fully now as I've been just going along with it so far (good though it is). My problem is fairly simple (I think) but I can't seem to make it all work.

 I installed Ubuntu 6.06 alongside Win XP. I intended to install over but bottled out at the last second lol. Now I've realised there are about 10 files I want to get back from that partition that I forgot to transfer to my USB stick before I did the install. I've tried the basic mounting of the partition and onstensibly have access to the windows partition. The problem is that I can only access 1Mb of data that all appears to be Dell info files or the like. I know there must be closer to 15Gb on the drive but I just can't seem to access it. Can anyone suggest a way in that might find these files or alternatively the way to boot into Win XP so I can retrieve them.

 After I have these files I wanted to delete the windows partition to make room for the various linux progs and so on that I want to use. Help on that front would be much appreciated.

 Thanks everyone,

 Pete

---

### Post by mahy on 2007-03-28
Please post the output of

sudo fdisk -l

---

### Post by george29 on 2007-03-28
type

```
 sudo fdisk -l 
```

into a terminal and post up the results.

also type ```
 df 
```

and post 

from that we can see what partitions you have, their size and how much data they have on them..

---

### Post by Little Pete on 2007-03-29
Sorry for the delayon this one. Been busy at work :)

> Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2237    17968671   83  Linux
/dev/hda2            4678        4863     1494045    5  Extended
/dev/hda3   *        2238        4677    19599300   83  Linux
/dev/hda5            4771        4863      746991   82  Linux swap / Solaris
/dev/hda6            4678        4770      746959+  82  Linux swap / Solaris

Partition table entries are not in disk order
peter@ubuntu:~

---

### Post by Little Pete on 2007-03-29
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/hda3             19291368   2209252  16102152  13% /
varrun                  127884       128    127756   1% /var/run
varlock                 127884         4    127880   1% /var/lock
udev                    127884       136    127748   1% /dev
devshm                  127884         0    127884   0% /dev/shm
lrm                     127884     18856    109028  15% /lib/modules/2.6.15-28-3 86/volatile
/dev/hda1                32018      1390     30628   5% /media/windows

---

### Post by Little Pete on 2007-03-30
bump.

thanks

---

### Post by freebird54 on 2007-03-30
I think all your helpers are staring at that list from fdisk and going OH OH.  I don't see any sign that your partition with XP still exists.  Should look something like this if it did...

```
Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**/dev/hde1   *           1        3824    30716248+   b  W95 FAT32**
/dev/hde2            4869        5129     2096482+  82  Linux swap / Solaris
/dev/hde3            5130       19457   115089660   83  Linux
/dev/hde4            3825        4868     8385930   83  Linux

Partition table entries are not in disk order

```

The bold entry is a Win system.  Could also say NTFS if it was formatted that way - but it would definitely stand out from the Linux partitions.  Any chance you deleted any partitions already??

---

### Post by Gina on 2007-03-30
I'm a bit of a newbie myself but two things strike me about your partition list
1. It's not listing the Windows partition - usually shows as  **HPFS/NTFS** or **FAT32**
2. There's nothing showing for **hda4**

When I installed Ubuntu (6.06) and keeping Windows (by resizing the Win partition and using the recovered space) it automatically installed the dual-boot system - leaving Windows available at bootup.  The Win partition showed in the partition lists either from command line or GUI.

I suspect something went wrong with your Ubuntu installation and your Win system is corrupted.  You may be able to recover some files using a **Recovery CD** though.

---

### Post by george29 on 2007-03-30
Looking at your /etc/fstab it would appear you have installed ubuntu to hda3, unfortunately it would seem that what was your windows partition hda1 has been reformated to an ext3 partition which means the data is pretty much unrecoverable - you could try sending the drive to a professional data recovery service, but i'm guessing the 10 files you want aren't going to be worth the money it'll cost.

---

### Post by Little Pete on 2007-03-30
Thanks very much for the help folks.

 The files are no major issue, just some pictures of people I know. Fortunately I can get all the pictures again (or at least we can all pose in a similar way :lolflag: ).

 I'll get onto the partition program tonight and see if I can't merge the two larger partitions into one that gives space for Ubuntu updates.

 Pete

---

### Post by acalafra on 2007-05-05
Lets keep this thread alive shall we..... I have a windows partition how can I give myself permision to delete certain annoying windows components from system32 and dllcache.  I tried gksudo nautilus but couldn't see the partition as root. 

sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11473    92156841    7  HPFS/NTFS
/dev/sda2           11474       23571    97177185   83  Linux
/dev/sda3           23572       24321     6024375    5  Extended
/dev/sda5           23947       24321     3012156   82  Linux swap / Solaris
/dev/sda6           23572       23946     3012124+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

