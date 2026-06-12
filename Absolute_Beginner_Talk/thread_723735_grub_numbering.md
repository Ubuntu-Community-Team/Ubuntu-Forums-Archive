---
title: "grub numbering ?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-13
I finally got Gusty installed on a new HD but grub will not boot (error 17)
I was going to try some of the fixes I've read but the problem is I'm not sure the numbering will work. I'm trying to dual boot with Windows already installed on two drives & Gusty on the third.
The problem is I have 2 ATA drives & 1 SATA. 
windows was booting  from the first ATA drive & was also using the SATA drive.
I installed a slave ATA & put Gusty on it. 
Fdisk -l shows in order

sda 1   Fat32 .... my SATA drive
hda1  NTFS
hdb1 Ext3
ext & swap partitions.

All the drives are a single partition.

I'm affraid that Grubs hd (0,0) is the SATA  when windows is using the first ATA for the OS.
How can I remedy this?

---

### Post by Duck2006 on 2008-03-13
This may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by garyed on 2008-03-13
Thanks for the help but so far nothing has helped.
I did the----  find  /boot/grub stage1  ----, root (hd1,0)--------  setup (hd0) thing & it said it was successful but when I rebooted it stills locks up at Grub error 17. 
I've been through this before on another computer a while backl & it took a couple of reinstalls  to get working. I think I'll try super grub & see if that helps.

---

### Post by garyed on 2008-03-13
I finally got it:

I used supergrub to get my mbr bootable but I still couldn't get into Linux but I could get back to windows.
I then changed the menu.lst to (hd2,0) for the Linux kernel
Whats funny is my device map reads:
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda
but my fdisk reads:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92c092c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92819281

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005598e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       18700   150207718+  83  Linux
/dev/hdb2           18701       19457     6080602+   5  Extended
/dev/hdb5           18701       19457     6080571   82  Linux swap / Solaris
gary@gary-desktop:/boot/grub$ 

So Windows works on (0,0)  - hda1  which is right in Device map (wrong in fdisk)
Linux works on   (2,0)  - hdb1  which is wrong in Device map. (right in fdisk)

Anyone have an idea why?

---

