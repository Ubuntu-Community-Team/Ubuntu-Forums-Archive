---
title: "installed ubuntu, but i want to dual boot, think i messed up"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by turini on 2007-07-08
well i installed ubuntu and i believe i partioned a certain area for it but i have no option to log onto my XP when i start my computer. I had tons of things on my hard drive that would suck to have lost so if any one knows how i can get all that stuff i would appreciate it

---

### Post by mikewhatever on 2007-07-08
Let's see what partitions are on the HDD. In Ubuntu, go to Applications>Accessories>Terminal, type > sudo fdisk -l and post the output here.

---

### Post by turini on 2007-07-08
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris
andrew@andrew-desktop:~$

---

### Post by niteshifter on 2007-07-08
Ok, what kind of computer (make, model, number of hard disks)? What version of Ubuntu? All may or may not be lost (probably not) but it's kinda hard to tell at this point, with what's given :)

---

### Post by cwood06 on 2007-07-08
> **turini said:**
> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris
andrew@andrew-desktop:~$

if that is the only hard drive. You must have partitioned it wrong because it would have had a ntfs files system or fat32 in there.

---

### Post by niteshifter on 2007-07-08
As cwood06 said if that's the only hard drive in the box ....

Just to make sure let Ubuntu boot up, then enter this in a terminal
```
cat /proc/partitions
```
and post the output here.

---

### Post by BL00dFox on 2007-07-08
> **turini said:**
> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris
andrew@andrew-desktop:~$

If that is the only Hard Drive in your machine, you may have deleted your XP partition, since I cant see any NTFS/FAT32 partitions...

If this is the case, you have lost all your data :(. Please make sure to backup next time before altering your partition tables.

---

### Post by neoguy2012 on 2007-07-08
I'm really sorry this happened to you.  If your files are very very important, you may be able to obtain them again, but it's not easy and I wouldn't recommend it if you don't know what you are doing.  There are various data recovery tools on the market that attempt to reconstruct data on the disk since much of it is still physically around, but not accessible.  I have only tried FAT32 data recovery programs in the past, but I'm sure there are NTFS versions around.  However, you must stop working from that hard drive now to prevent any further loss of data.  You may have to install it into another computer as a secondary drive and then run the recovery program from there.

---

### Post by pyros on 2007-07-08
It is possible, but not likely, that you can still recover some of your information. take a look at trinity rescue kit, at  trinityhome.org. I used a tool on their cd called testdisk to recover a formated fat32 partition just yesterday, and it is supposed to work even better with ntfs.

If you choose to go this route, and if the information is really that important to you, stop using the system right now. Use another computer to download and burn the trinity rescue disk. If the information is still on that drive, you would be overwriting more and more of it as your linux system runs.

BUT, like I said at the beginning, it's not likely that you can still recover your information. So, unless we are talking about the only pictures of your child's birth or the only copy of your doctoral thesis, (or, if you just want to OD on teh geekery) I'd consider it lost, mourn, and let the healing process begin.

---

### Post by BL00dFox on 2007-07-08
The user above summed it up perfectly. However, I am interested to know what utility you used to partition your disk. Did you partition while installing Ubuntu or did you use a third party application?

---

### Post by turini on 2007-07-08
i did it during the installation

---

