---
title: "installing lucid on an iMac with only external monitor"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by 2cute4u on 2010-05-04
I have an early 2006 intel core duo iMac 20".  The internal monitor is dead, and the external monitor only comes on, after the kernel is loaded.   

Previously I had a working copy of karmic, which I installed before the internal monitor died.  I could get into ubuntu blind, using rEFIT, by hitting right arrow then return 10 seconds after the boot tone.

I deleted my linux partition to do a clean install of lucid, but after I installed lucid, I couldn't boot into it. I couldn't see what was going on with rEFIt,  or grub, because the monitor was still blank.

Booting into OS X,I got the following from refits partition inspector.

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    126385103  Mac OS X HFS+
 3      126647248    378155743  Mac OS X HFS+
 4      378157056    378159103  GRUB2 BIOS Boot
 5      378159104    483801087  Basic Data
 6      483801088    488396799  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    126385103  af  Mac OS X HFS+
 3      126647248    378155743  af  Mac OS X HFS+
 4              1    378159103  ee  EFI Protective

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 126647248:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 378157056:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type GRUB2 BIOS Boot

Partition at LBA 378159104:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 483801088:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap

```
 

what do I need to do to fix things, and how can I do it without being able to see the boot process?

---

### Post by DoubleClicker on 2010-05-05
Many people are having trouble with Grub2 on Macs,  what is probably happening is that you are getting a grub error, (which you can't see because of the dead monitor).  also logical partitions are necessary on  EFI Macs.   

try deleting your current partitions sda4-sda6, then manually create sda4 as your ubuntu partition and sda5 as swap using gparted.  I would also recommend using ext3 instead of ext4 , because there are no ext4 drivers for Mac OSX.

When you install ubuntu select sda4 dor grub under advanced options.   

good luck

---

### Post by 2cute4u on 2010-05-06
ok tried that, but it didn't help.

---

### Post by linuxopjemac on 2010-05-06
It's extremely difficult what you try to do. Maybe you can upgrade your box from Karmic to Lucid, using ssh from another box. Sory, wrong idea. You wiped Karmic already...

---

### Post by 2cute4u on 2010-05-09
> **linuxopjemac said:**
> It's extremely difficult what you try to do. Maybe you can upgrade your box from Karmic to Lucid, using ssh from another box. Sory, wrong idea. You wiped Karmic already...

it's frustrating enough that I can't get this working, making fun of me doesn't help.

---

