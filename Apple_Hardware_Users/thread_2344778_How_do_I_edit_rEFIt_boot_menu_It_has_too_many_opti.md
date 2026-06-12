---
title: "How do I edit rEFIt boot menu? It has too many options."
date: 2016-11-28
forum: Apple Hardware Users
---

### Post by dmugambi on 2016-11-28
I have installed Ubuntu 16.04 LTS 64bit, Mac OS X Lion, and Windows 7 on a MacBook 2010 (white). I installed rEFIt through Mac OS and it is showing about 4 options for Linux. How do I get it to just one. Two of these do boot into Linux. Here is the partition information. I would like to just show three options; Ubuntu, Mac, and Windows.



*** Report for internal hard disk ***


Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    244550263  Mac OS X HFS+
 3      244550264    245819799  Mac OS X Boot
 4      245821440    429646040  Basic Data
 5      429647872    484732927  Unknown
 6      484732928    488396799  Linux Swap


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    156301487  ee  EFI Protective


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


Partition at LBA 244550264:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot


Partition at LBA 245821440:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data


Partition at LBA 429647872:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Unknown


Partition at LBA 484732928:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap

---

### Post by howefield on 2016-11-28
A support thread, so moved to the "*Apple Hardware Users*" forum for a better fit.

---

