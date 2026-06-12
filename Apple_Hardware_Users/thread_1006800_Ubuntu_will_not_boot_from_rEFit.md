---
title: "Ubuntu will not boot from rEFit"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by smartaggie2010 on 2008-12-09
I own a macbook pro (Fourth generation) and I triple boot Microsoft XP, Leopard, and Ubuntu 8.10.  I have installed rEFit to boot these and when I hold down "alt" at start up I have no trouble finding the option to select "boot Ubuntu from hard drive" but whenever I do it shows the penguin on a white screen then turns to a black screen with just a blinking "_" in the top left corner.  

Here is the report Partition Inspector gave me if it's any help.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    413024295  Mac OS X HFS+
 3      413286440    444743719  Basic Data
 4      445005864    488397127  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    488397167  ee  EFI Protective

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 413286440:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 445005864:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 4, type Basic Data

---

### Post by pxwpxw on 2008-12-09
**smartaggie2010**

Partition Inspector report for the MBR shows that you need to run the rEFIt Partitioning Tool (from the rEFIt menu) to restore your MBR partition info.
This should get ubuntu booting.

---

### Post by cyberdork33 on 2008-12-11
also, if you are holding 'alt' on startup, you are bypassing rEFIt. rEFIt should appear automatically without holding any keys if it is properly installed.

---

### Post by smartaggie2010 on 2008-12-11
I just tested it today and works great.

Thanks alot

---

