---
title: "Need to make refit launch linux, not windows"
date: 2012-02-12
forum: Apple Hardware Users
---

### Post by Samushighwind on 2012-02-12
I have been grappling with this problem for several months.  I have Windows 7, Snow Leopard, and Ubuntu 11 on my MacBook Pro 8,1.  When I fixed refit to make Windows work (before it was saying no disk or something), choosing Linux in refit started booting Windows instead.

I've checked refit documentation-- I ran Partition Inspector in Mac and I returned this:

> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    328390615  Mac OS X HFS+
 3      328652800    330747903  Linux Swap
 4      330749952    526061567  Basic Data
 5      526063616    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    526063615  ee  EFI Protective
 2 *    526063616    625141759  0c  FAT32 (LBA)

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 328652800:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap

Partition at LBA 330749952:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 4, type Basic Data

Partition at LBA 526063616:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data
 Listed in MBR as partition 2, type 0c  FAT32 (LBA), active


any ideas?

---

### Post by edgargdl on 2012-05-12
did you solve it?

---

