---
title: "Moving Grub/MBR?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by whein on 2008-02-05
Hi all.  This computer is a Frankenstein reaching back years.  It started as a Win2k machine with two PATA drives and has since gotten three SATA drives and four iterations of Ubuntu, ending in the current 7.10 that I'm typing from.  Oh yeah, Ubuntu is installed on the first SATA drive.

All is well except one of the old PATA drives keeps giving a LOT of I/O errors during the boot-up process and once everything is booted it is very hit or miss (usually miss) whether I can access that drive or not.  So I'm guessing that it's reached the end of its life and needs to be retired.  Except when I took it out and tried to boot, my machine would hang right after the "Verifying MI Pool Data....." line but before saying anything about GRUB.  When I put the hard drive back in and tell the computer to boot from that drive, everything works again.   So my hunch is that GRUB and/or the MBR is on that drive.  I know computers to a point, but I've never learned much about stuff that low down and dangerous.  So my question is, how do I make everything happy again and still get rid of the two PATA drives?  Details are good, this will be very unfamiliar territory for me.  Thanks in advance!
-Will

---

### Post by hinchy34 on 2008-02-05
I did that a few weeks ago, I just installed GRUB again. I'm still not to familiar with linux but I found dealing with GRUB not too terribly difficult.

---

### Post by louieb on 2008-02-05
If it were me 
1st I'd get a copy of the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")
2nd take out  the two pata drives. 
3rd. Use the super grub disk to fix the MBR of the sata drive to boot Ubuntu. [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Should work. Then you can put the two pata drives back in - if you need to get some data off.

---

### Post by logos34 on 2008-02-05
You'll need to reinstall grub to the mbr of the ubuntu sata drive, and edit menu.lst.  

What's 

sudo fdisk -l 

show?

---

### Post by whein on 2008-02-16
> **logos34 said:**
> What's 
sudo fdisk -l 
show?
Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f123f11

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hda2            1276        2491     9767520    c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1db60f50

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/hdb2            2433        7296    39070080    f  W95 Ext'd (LBA)
/dev/hdb3            7297        9729    19543072+  83  Linux
/dev/hdb5            2433        4864    19535008+   c  W95 FAT32 (LBA)
/dev/hdb6            4865        7296    19535008+   c  W95 FAT32 (LBA)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ecb06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda3           12749       38539   207166207+  83  Linux
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eeba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed0e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

---

