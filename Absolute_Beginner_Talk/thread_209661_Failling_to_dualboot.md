---
title: "Failling to dualboot"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by GaijinOnline on 2006-07-05
Hi there, I recently got a ubuntu 6.06 cd and wanted to install it to a 20Gb partiton that was yet formated. I've done what people were telling me to do to install ubuntu (while being in the live cd) on my second hard drive, but when I reboot my computer I get a message from grub "error 17" or something like that... I have tried and re-tried to install ubuntu a lot of time, I think I reformated my windows partition like 3 time since yesterday(!) and each time I get the same error from grub at the startup.

I have a lot of partition so I'm guessing that it could be the problem. My windows partition is the first one on my first hard drive and the linux partition that I have created during the installations is at the end of my second HDD. 
First HDD : 5 partitions, windows installed in the first one
Second HDD: 5 partitions, linux-swap in fourth and ubuntu intallation in partition number five (as primary drive)

Can somebody help my with this. I have tried mandrake successfuly but the dual boot program was LILO on a floppy, and now I want to try ubuntu and maybe adopt it as an alternative to windows.

---

### Post by scxtt on 2006-07-05
just for curiousity, what's the output of:

```
$:> sudo fdisk -l
```

---

### Post by GaijinOnline on 2006-07-05
Well I am in windows right now, so how could I tell you this ? 
I have a knoppix live cd somewhere around my desk could that be of any help?
I have tried the unofficial super grub disk to repair my MBR but with absolutely no sucess...

---

### Post by scxtt on 2006-07-05
yes, the knoppix disk would work - as would the ubuntu live cd ...

---

### Post by GaijinOnline on 2006-07-05
well I can't figure how to get my dsl working using the ubuntu live cd, only on the knoppix one I can get it working... so I guess I'll use knoppix

and btw I cannot even boot windows, the only way I found to boot it up was with the super grub disk (boot windows option) :(

---

### Post by confused57 on 2006-07-05
Does the grub menu come up at all, i.e. do you see the boot options for Windows and Ubuntu?   If you do, let us know...you might be able to press "e" with the Windows entry highlighted and make sure root is (hd0,0) if Windows is on the 1st partition of hda1...if you can & it's not, try changing it & booting.

Also, you can recover the Windows mbr with the Windows Install CD(not the recovery cd), by booting up with it, press "r" to enter recovery, then enter 
fixmbr...this should enable you to boot Windows, but it'll overwrite grub, which can be reinstalled using the live cd.

Maybe when you're booted up with Knoppix, there may be a way to see what ethernet driver it's using & maybe you can change it in Ubuntu.   I had the experience of not being able to access the internet with the Live Desktop CD, but was able to after installing with the Dapper Alternate CD...may not work for everyone.

I've rambled enough, possibly some of this may help you.

---

### Post by akcom on 2006-07-05
Just figured I'd throw in my $.02 and say that I am having this same problem.  I had windows install on a 90GB primary partition ( hda1 ) and attempted to install Ubuntu onto another 90GB primary partition (hda2).  Now when I restart my computer, I get a GRUB failed at step 1.5 (Error 17) msg.

---

### Post by GaijinOnline on 2006-07-05
looks like we are in the same boat then #-o

Edit: I just did the ```
$:> sudo fdisk -l
```and I get this 

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1834    14731573+   7  HPFS/NTFS
/dev/hda2            1835       19457   141556747+   f  W95 Ext'd (LBA)
/dev/hda5            1835        6403    36700461    7  HPFS/NTFS
/dev/hda6            6404       10319    31455238+   7  HPFS/NTFS
/dev/hda7           10320       16846    52428096    7  HPFS/NTFS
/dev/hda8           16847       19457    20972826    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       21783   174963915    f  W95 Ext'd (LBA)
/dev/hdb2           21784       24321    20386485   83  Linux
/dev/hdb5               2        2612    20972826    7  HPFS/NTFS
/dev/hdb6            2613        7834    41945683+   7  HPFS/NTFS
/dev/hdb7            7835       21671   111145671    7  HPFS/NTFS
/dev/hdb8           21672       21783      899608+  82  Linux swap
```

the linux partition seems to be on "/dev/hdb2" but isn>t marked as bootable from what I understand. how could I repair my grub installation so I could dual boot?

---

### Post by GaijinOnline on 2006-07-05
To answer confused57, grub dont even boot up, I get stuck with the message taht GRUB failed at stage 1.5 (error 17). 

can it be that my linux instalation is wrongly partitioned?
my linux partition was mount as "/" and I set up a swap partition. I saw in other people post that they have a "/","/boot" and swap partitions. Do I need to make some new one?

---

### Post by confused57 on 2006-07-06
I did a google search and found someone who solved this problem by going into bios and changing the HD setting from "auto" to "LBA"?

---

### Post by GaijinOnline on 2006-07-06
nope just tried it right now and it didn't work... 
I just don't understand, the actual ubuntu instalation is not corrupt I pretty sure it is a problem with grub... I really apreciate everyone helping. This problem is really bugging me! I really want to try out ubuntu! well I'll try to find something...

---

