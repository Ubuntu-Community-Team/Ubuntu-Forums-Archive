---
title: "Swap Partition"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by dkmp on 2008-02-17
Hey,

Specs 1.73Ghz CPU centrino, 512Ram, 80gb HDD, Nvidia 6400 128mb graphic card.

I've managed to remove Wubi and install Ubuntu fesity fawn. Compiz works really well and have managed to get the cube!

Only problem I have is the CPU is constantly using a lot of power ( 85-95%). This seems to be taken up by the idle process from the very beginning. Does not happen in XP?

I thought it may be the size of the swap partition and I tried changing it to 1GB but Gpart doesn't allow me to when I use the live CD. My HDD is paratitioned as : sda1 NTFS 37GB, sda2 NTFS 33GB which includes the SWAP of 628Mb, and sda3 EXT3 10GB.

I cant manage to move any freespace in sda2 to ncrease the size of the swap partition. it just says an error occurred when descreasing size of the NTFS to free up space

Any ideas?

Cheers

D

---

### Post by aashay on 2008-02-17
The higher cpu usage on the idle process the better. idle = 100 - sum of all others. It is analogous to the "System idle process" under windows, which too is at 99% most of the time. Use the command "top" to view the cpu% of the top processes in descending order

---

### Post by dkmp on 2008-02-17
oh, ok.

But should the fans on my laptop be at full blast, this doesn't happen with XP.

And when I open an app the CPU usage jumps to very high levels.

does the size of my swap partition need to be changed?

Thanks

D

---

### Post by aashay on 2008-02-17
In most cases, swap should be equal to the amount of physical memory. So 628 mb is (more than ) enough. I have a swap of 1gb and phy of 1gb. The swap has NEVER been used, not even 1%. So check if your swap ever fills up to the brim (which i doubt). In which case, you might want to resize it. 
Cant comment about the fans. Can hardly feel / hear mine. As a sidenote, you might try to enable the CPU frequency scaling monitor using ```
sudo dpkg-reconfigure gnome-applets
``` if you havent done so. It will scale down the cpu freq (and possibly the fan speed) when the system is under light load. Just add "CPU freq monitor" applet to the panel to monitor it

---

### Post by housam on 2008-02-17
Usually the swap partition is 2 x RAM , but it has no effect of your cpu usage.
Also I wonder how it comes the swap is included in a ntfs partition ? it should be a separate partition linux/solaris.

please type in a terminal ```
sudo fdisk -l
``` where -l is a small L and post the output.

---

### Post by dkmp on 2008-02-17
hey,

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        8057    25647772+   f  W95 Ext'd (LBA)
/dev/sda3            8058        9729    13430340   83  Linux
/dev/sda5            4865        7977    25005141    7  HPFS/NTFS
/dev/sda6            7978        8057      642568+  82  Linux swap / Solaris

---

### Post by aashay on 2008-02-17
use the "free" command to monitor the swap usage

---

### Post by dkmp on 2008-02-17
hey,

i used free cmd:

             total       used       free     shared    buffers     cached
Mem:        514572     498076      16496          0      13988     256884
-/+ buffers/cache:     227204     287368
Swap:       642560      33872     608688


Any ideas?

---

### Post by housam on 2008-02-17
> **dkmp said:**
> hey,

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865        8057    25647772+   f  W95 Ext'd (LBA)
/dev/sda3            8058        9729    13430340   83  Linux
/dev/sda5            4865        7977    25005141    7  HPFS/NTFS
/dev/sda6            7978        8057      642568+  82  Linux swap / Solaris

Ok this is right. you have 2 primary partitions sda1 & sda3 and one extended partition sda2 which has two logical partitions sda5 & sda6 ( the swap partition ). you have a good partition table , no problem with it.

use aashay adviceto monitor your cpu

---

### Post by housam on 2008-02-17
go for the upper panel and right click >> add to panel >> system & hardware >> system monitor>> add . then you can monitor the usage of the cpu and also the usage of your RAM & swap.

---

