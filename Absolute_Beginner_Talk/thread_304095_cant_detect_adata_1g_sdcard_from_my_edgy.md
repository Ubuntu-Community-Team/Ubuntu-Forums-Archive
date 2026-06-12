---
title: "cant detect adata 1g sdcard from my edgy"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by efrenefren on 2006-11-21
efren@efren-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

efren@efren-laptop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1084     8707198+   7  HPFS/NTFS
/dev/hda2            1085        7105    48363682+   f  W95 Ext'd (LBA)
/dev/hda5            1085        1750     5349613+   7  HPFS/NTFS
/dev/hda6            2198        6021    30716248+   7  HPFS/NTFS
/dev/hda7            6022        7105     8707198+  83  Linux
/dev/hda8            1751        1873      987966   82  Linux swap / Solaris
/dev/hda9            1874        2197     2602498+  83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 2047 MB, 2047868416 bytes
255 heads, 63 sectors/track, 248 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+   0  Empty
/dev/sda2              11         248     1911735    b  W95 FAT32

Nov 21 23:44:13 efren-laptop kernel: [17181263.108000] tifm_7xx1: sd card detected in socket 3

have done this
mkdir /media/sdcard
havent edited fstab yet.
what should i do so that i can mount it?
when i looked at the card's filesystem in windows its says fat
but when i tried
sudo mount -t vfat /dev/sda1 /media/sdcard
its says bad fs system something.
help pls.
tell me if you need more info :D

---

### Post by ReaderRat on 2006-11-21
Sorry, but I don't know what a sdcard is....Is it a camera flash memory card?

---

### Post by efrenefren on 2006-11-21
> **ReaderRat said:**
> Sorry, but I don't know what a sdcard is....Is it a camera flash memory card?

this is it. i think its called sd mmc card
[IMG]http://static.flickr.com/116/303284922_1fecdfaa33_m.jpg[/IMG]

---

### Post by efrenefren on 2006-11-28
as what i read from a sticky in this forum, a newbie should use dapper instead of edgy because more people are experienced with it. something like that.
nwe, when the live cd started i found the sd card. :D so i guess ill be using dapper

---

