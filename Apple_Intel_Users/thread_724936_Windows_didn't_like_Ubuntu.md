---
title: "Windows didn't like Ubuntu"
date: 2008-03-15
forum: Apple Intel Users
---

### Post by Alar on 2008-03-15
I have put ubuntu on my macbook pro today using the guide from ubuntu wiki.  Now my windows has exploded and keeps giveing the missing or corrupt hal.dll error.  I tried looking around for fixes to this error but none of them seem to be working.  Including (repeated) reinstalls of windows.

This is the output from partition inspector if it helps at all.

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    180502567  Mac OS X HFS+
 3      180764712    219827211  Basic Data
 4      219827212    232487368  Basic Data
 5      232487369    234440494  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    180502567  af  Mac OS X HFS+
 3      180764712    219827211  07  NTFS/HPFS
 4 *    219827212    232487368  83  Linux

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 180764712:
 Boot Code: Windows NTLDR
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS

Partition at LBA 219827212:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 232487369:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by Infinite Recursion on 2008-03-22
It looks like the positioning of your partitions is the problem.  On a MacBook (Pro), the Windows partition must be the last on the drive.  Also, from what I've heard, only four primary partitions are allowed, which means that there is no room for a swap partition - you will need to make a swapfile instead.

A great tutorial on getting a MacBook (Pro) to triple boot can be found here: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

---

### Post by cyberdork33 on 2008-03-23
yes, your windows partition needs to be #4.

You swap in 5 is fine that won't hurt anything. There is a lot of confusing information out there about the 4 partition thing and people are misunderstanding the issue. There is a 4 partition "limit" for windows but pretty much everything else uses the GPT to find partitions, and has no issue with partitions beyond #4.

---

### Post by Infinite Recursion on 2008-03-23
> **cyberdork33 said:**
> There is a 4 partition "limit" for windows but pretty much everything else uses the GPT to find partitions, and has no issue with partitions beyond #4.

Good to know; I thought that might be the case, but I wasn't sure - and up until now was unable to find any confirmation one way or another.

---

### Post by cyberdork33 on 2008-03-23
> **Infinite Recursion said:**
> Good to know; I thought that might be the case, but I wasn't sure - and up until now was unable to find any confirmation one way or another.
The only limitation that I have seen in relation to Ubuntu is that the bootable partition needs to be one of the first four, though I have seen evidence that this can be worked around, but never have tried it. OSX can go wherever though since it boot directly from EFI.

---

