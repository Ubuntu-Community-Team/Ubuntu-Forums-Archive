---
title: "Accessing my second Ubuntu hard drive"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by grte on 2005-12-04
Okay, so I installed Ubuntu to my 10 GB hard drive about a week ago.  I loved it so much that I deleted windows from my 80 GB and installed it there.

But now, I want to grab some files from the 10 GB drive and move them over to the 80 GB.  Can anyone tell me how to access it?  Both are running Breezy.

---

### Post by aysiu on 2005-12-04
Where does your 10 GB drive live? /dev/hda1? If you're not sure, post the output of ```
df -h
sudo fdisk -l
cat /etc/fstab
``` and I'll help you try to figure it out.

If it is, try ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
gksudo nautilus
``` and then copy everything you want.

---

### Post by grte on 2005-12-04
Here are the results of those commands:

> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc1              73G  5.5G   64G   8% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1             4.7G  4.3G  378M  93% /media/M500

> sudo fdisk -l

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9587    77007546   83  Linux
/dev/hdc2            9588        9964     3028252+   5  Extended
/dev/hdc5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/hdd: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1          31      248976   83  Linux
/dev/hdd2              32        1401    11004525    5  Extended
/dev/hdd5              32        1401    11004493+  8e  Linux LVM

Disk /dev/sda: 4997 MB, 4997823488 bytes
1 heads, 62 sectors/track, 157441 cylinders
Units = cylinders of 62 * 512 = 31744 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      157442     4880686+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


You'll have to excuse me, I'm new at this so I haven't a clue what any of that means.

---

### Post by aysiu on 2005-12-04
Okay. This here is your 10 GB drive: ```
 Device Boot Start End Blocks Id System
/dev/hdd1 * 1 31 248976 83 Linux
/dev/hdd2 32 1401 11004525 5 Extended
/dev/hdd5 32 1401 11004493+ 8e Linux LVM
``` Only problem... I don't know  what's the difference between hdd1, hdd2, and hdd5. Try this: ```
sudo mkdir /recovery
``` This makes a directory called *recovery* where your 10 GB drive will be mounted to. Then try ```
sudo mount -t ext3 /dev/hdd5 /recovery
``` Any error messages?

If not, then try ```
gksudo nautilus
``` and browse to the recovery folder. See anything?

If so, what's the error message? And also try ```
sudo mount -t ext3 /dev/hdd2 /recovery
```

---

