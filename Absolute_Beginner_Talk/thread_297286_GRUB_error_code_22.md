---
title: "GRUB error code 22"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by holyowned on 2006-11-10
I partitioned my hdd with GParte (WinXP-NTFS, data-FAT32, Swap, and ext3), and installed Ubuntu 6.06.  When I restarted, GRUB gives me 3 options for Ubuntu (norm, safe, and memcheck); all 3 get an error 22.  WinXP loads fine.  Data and XP partitions are accessible in XP.  If I boot from LiveCD, it shows my entire hdd as unallocated.  Is there a way to salvage this?  TIA

---

### Post by confused57 on 2006-11-10
Try booting the desktop live cd, open a terminal(Applications---Accessories---Terminal), and post the output of:

```
sudo fdisk -l
```
The -l is a small "L"

---

### Post by holyowned on 2006-11-11
Here's the fdisk info:

Disk/dev/sda: 99.8GB 99830223360 bytes
255 heads, 63 sectors/track, 12137 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device    Boot Start    End   Blocks      Id  System
/dev/sda1   *     1    3850   30925093+   7   HPFS/NTFS
/dev/sda2      3851    8575   37953531    f   W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary
/dev/sda3      8576    12137  28611733    83  Linux
/dev/sda5      3851     8313  35849016    b   W95 FAT32
/dev/sda6      8314     8575  2104483+    82  Linux swap/Solaris
TIA

---

### Post by holyowned on 2006-11-11
Ok, got this calf licked right.  Ran testdrive, and deleted the Linux /root and swap partitions.  Rebooted from the LiveCD, and created an extended partition, with a 2GB swap, a 1GB /home, and a 27GB /root.  Restarted, and GRUB worked great.  Does this make me an official Ububtu user now?  lol

---

### Post by ThrobbingBrain66 on 2006-11-11
Surely it does, but in all honesty, i would drastically reduce your root partition size and increase your home partition.  something like:

8-10GB root
18-20GB home

home is where all your user settings get stored along with pretty much anything else (music, documents, etc)  1 GB will fill up pretty quick

---

### Post by holyowned on 2006-11-11
Thanks for the tip, but my data will be stored in a 35GB FAT32 partition that will be used by Ubuntu and XP.  My /home will be just for my Ubuntu settings.  I have a 160GB external hdd I can use in a pinch for data storage, as well. ;)   Now, anyone know where I can find drivers for a Sierra A860 wireless card?  I found a tutorial on HOW to install it at [http://mycusthelp.com/sierrawireless/supportkbitem.asp](http://mycusthelp.com/sierrawireless/supportkbitem.asp) , but the driver file is not there.

---

