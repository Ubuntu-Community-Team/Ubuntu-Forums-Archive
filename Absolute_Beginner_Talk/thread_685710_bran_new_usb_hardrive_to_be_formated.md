---
title: "bran new usb hardrive to be formated"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by rudedcam on 2008-02-02
i bought an 320G external harddrive for storing purposes.
ubuntu is installed on my master 80G hardrive 

Q1: what kind of filesystem should i used knowing that i want my usb harddrive to be compatible with window XP and ubuntu? (i heard NTFS was the way to go, is it?)

Q2: how do i format it? partitioning isn't a must since no OS will be installed on the harddrive; only files.

Q3: how can i mount it easily?

```
sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b851b8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9363    75208266   83  Linux
/dev/hda2            9364        9729     2939895    5  Extended
/dev/hda5            9364        9729     2939863+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120060444672 bytes
240 heads, 63 sectors/track, 15508 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x86ebe9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       15508   117232920    f  W95 Ext'd (LBA)
/dev/hdb5               2       15508   117232888+   b  W95 FAT32

[B]Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table[/B]

```

thanks in advance for any help:D

cam

---

### Post by taurus on 2008-02-02
If you don't have it in System -> Administration, install gparted and use it to format that harddrive to ntfs filesystem.  

```
sudo apt-get update
sudo apt-get install gparted
```
Then, you can install and use ntfs-3g to mount that drive so you can write to it.

---

### Post by The Cog on 2008-02-02
You could either format it NTFS, or format it ext3 and install the ext3 drivers into XP. Both support large files.I would expect that you need to use XP to format it with NTFS if that's the one you choose.

---

