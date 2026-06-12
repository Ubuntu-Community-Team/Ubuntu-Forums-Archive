---
title: "Not allowing me to install Steam in my second hard drive"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by sumsimpleracer on 2008-03-25
Well i have some pretty small space left in my hard drive and i don't have enough space to install steam on my drive_c if i plan on installing Counterstrike Source as well. So i hooked up a second hard drive (z drive) and when i go into the steam_install.exe and try to save the file in the z drive it wont' let me...

any answers?

thanks ahead

---

### Post by Logistics64 on 2008-03-26
Well, are you sure that the Second HDD even mounted?

---

### Post by sumsimpleracer on 2008-03-27
thanks for the reply, i was starting to think this was going to end up being a dead topic...

anywayz yes i think it's mounted because
1. I can read all the files inside the drive
2. In the file explorer when i go inside the drive there is an option that says unmount, but no option to mount.

weird thing is, it won't let me save any files into the drive

---

### Post by Laser Dude on 2008-03-27
It sounds like you don't have write access to the drive.  Perhaps chmod would do the trick.

---

### Post by sumsimpleracer on 2008-03-27
whats that? sorry i'm still getting into this whole linux thing, slowly building up my gaming rig

well i found this site [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

and i'll use their procedure tomorrow after tennis practice and i'll update you guys

---

### Post by sumsimpleracer on 2008-03-27
alright so this is what i get after i try to mount it

NTFS signature is missing. Failed to mount '/dev/hdb1': Invalid argument The divice '/dev/hdb1' doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g./dev/hda, not /dev/hda1)? Or the other way around?


any ideas?

---

### Post by sumsimpleracer on 2008-03-27
```
bryan@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         961     7719201    7  HPFS/NTFS
/dev/hda2   *         962        1782     6594682+  83  Linux
/dev/hda3            1783        1826      353430    5  Extended
/dev/hda5            1783        1826      353398+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

Disk /dev/hdb doesn't contain a valid partition table
bryan@ubuntu:~$ 


```

alright so it doesn't contain a valid partition table...how do i edit that

---

### Post by ByteJuggler on 2008-03-27
> **sumsimpleracer said:**
> ```
bryan@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         961     7719201    7  HPFS/NTFS
/dev/hda2   *         962        1782     6594682+  83  Linux
/dev/hda3            1783        1826      353430    5  Extended
/dev/hda5            1783        1826      353398+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

Disk /dev/hdb doesn't contain a valid partition table
bryan@ubuntu:~$ 


```

alright so it doesn't contain a valid partition table...how do i edit that

Use the partition editor (System->Administration->Partition Editor), if you don't have that entry, then install "gparted" using Synaptic, after which you'll have it.  

Aside:  Did you have nothing on your external disk then?  If you did (and you want to keep what was on the disk) then you shouldn't use gparted to create a new partition, but instead should use "testdisk" to recover your lost partition.

---

### Post by sumsimpleracer on 2008-03-27
I did have some stuff in the drive but i just deleted all of it...anywayz, i was playing with the partition editor today and had little no clue as to what i was doing...but since this computer is only using ubuntu i went to the top right corner and tried to change it so it ran off of ext3...but it failed to change...i'll try again tomorrow...but i think i'm buying a 320gb hard drive and i'll reinstall ubuntu on that HDD and not have to worry about this whole thing

---

