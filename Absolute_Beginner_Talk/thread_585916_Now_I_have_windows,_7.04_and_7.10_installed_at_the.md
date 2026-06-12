---
title: "Now I have windows, 7.04 and 7.10 installed at the same time!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by spylvas on 2007-10-21
I finally did it and managed to install Ubuntu 7.10. Something went wrong though and it gives me error that operator system cannot be found or similar when I am booted after installation. Well I put Ubuntu CD back and booted from first harddrive and there was my old options. Windows, two different Ubuntu 7.04 (two different kernels) and new 7.10.

I think I did something wrong and 7.10 is installed in different partition than 7.04?

Here is what fdisk gives me:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95be95be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       28896   129708810    f  W95 Ext'd (LBA)
/dev/sda3   *       28897       38913    80461552+  83  Linux
/dev/sda5           12749       28533   126792981    7  HPFS/NTFS
/dev/sda6           28534       28896     2915766   82  Linux swap / Solaris

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x493c493b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9791    78646176   83  Linux
/dev/hdc2            9792        9964     1389622+   5  Extended
/dev/hdc5            9792        9964     1389591   82  Linux swap / Solaris

I guess sda1 is my windows and sda5 is my other drive in windows and I want is to keep that way. Then there is all those  linux partitions... I think sda3 is this new installation and hdc1 is old one? 

Now question here is how do I fix booting problem? And how do I get rid of the old Ubuntu?

---

