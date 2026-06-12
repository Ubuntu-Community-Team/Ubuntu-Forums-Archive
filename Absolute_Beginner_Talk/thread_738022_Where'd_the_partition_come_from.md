---
title: "Where'd the partition come from?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by gray_damascus on 2008-03-28
Been a long time since i formatted to 7.04

(yes still using 7.04 'cause of some issues with 7.10, but will try suggestions after some weeks)


Just asking... when you format your main hard disk does it have an ntfs partition?
Is it not supposed to be a 100% pure ext3?

'cause in my main HD, i have 2(mainly)

the ext3 and the 'extended'(ntfs under the extended)

why is there an ntfs partition here? (size 3.08Gb, used 18.32Mb, unused 3.06Gb)

is it something critical?
can i remove it and hopefully resize my ext3 ubuntu to full?

***
tried searching for this... maybe i can't seem to search the right keywords...

one more thing.... how do you move an application window where, it only moves when you have placed it on a 'place'...
i mean... the app window does not follow your mouse until you release it.. what is that setting again?

again thanks to all and sorry

---

### Post by stalkingwolf on 2008-03-28
As I recall ( and I could be wrong) if you used the guided complete drive method when you installed
it will format 3 partitions.
/ for the system
swap to save RAM as I recall
and an emergency partition ( about the size of the ext partition you have) for use by root
if the drive gets close to max capacity.  This is as I recall so that you can clean out the /
partition.

---

### Post by bumanie on 2008-03-28
If you are not running windows there is no need to have any ntfs partitions. What may have happened is that your drive had been 100% ntfs prior to installing ubuntu. If you allowed ubuntu to resize the partitions automatically, it typically chooses about half the drive's available space. That may be why there is still an ntfs partiton. If you are only going to use linux, you can safely change the entire drive to ext3. You can do this when you install ubutnu by choosing manual at the partitioning stage or you can achieve this by using the gparted live cd. Sorry, can't remember the fix for your second question. Will post back if I remember.

---

### Post by gray_damascus on 2008-03-28
i will take that reply as a "the extra partitions (extended and ntfs[media-disk-2])

are safe to remove and AS FAR AS I KNOW, do no harm but you can TAKE THE RISK."

thanks... at least i have an idea

---

### Post by mister_pink on 2008-03-28
Sounds like a recovery partion put there by the manufacturers of the computer. If so you can probably get rid of it, as long as you're sure you never want to recover your computer back to factory. The amount of free space doesn't really fit with that interpretation though. Could you give the exact output of the "sudo fdisk -l" command?

No idea what you mean on the second bit I'm afraid.

---

### Post by gray_damascus on 2008-03-28
@ bumanie

then it is safe to remove that 3Gb ntfs-partition? 

BTW it resides on /media/disk-2
I'll take that as a yes.. hmmm seems i will remove it... just wait for some more opinions

thanks

---

### Post by gray_damascus on 2008-03-28
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+   7  HPFS/NTFS

Disk /dev/sdb: 8178 MB, 8178892800 bytes
255 heads, 63 sectors/track, 994 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         994     7984273+   b  W95 FAT32

Disk /dev/mmcblk0: 1019 MB, 1019215872 bytes
14 heads, 45 sectors/track, 3159 cylinders
Units = cylinders of 630 * 512 = 322560 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        3160      995203+   b  W95 FAT32

```

---

### Post by bumanie on 2008-03-28
> then it is safe to remove that 3Gb ntfs-partition?
As stated as long as you are not running windows there is no need for ntfs file system on your hard drive. Linux/ubuntu don't natively use ntfs (as you are aware). I run a dual boot. Have windows mainly for my son, as he has no interest in linux. My linux drive is 100% ext3.

---

