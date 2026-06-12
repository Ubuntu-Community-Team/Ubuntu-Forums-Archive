---
title: "Booting into Ubuntu on Intel iMac"
date: 2008-05-26
forum: Apple Hardware Users
---

### Post by awills on 2008-05-26
I've followed the instructions on the FAQ page and when I reboot I get the option for OSX of Linux if I choose Linux the 'penguin' icon appears but nothing happens - OS X boots OK.

Any help would be greatly appreciated.

This is the report from Partition Inspector


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    421675047  Mac OS X HFS+
 3      421675048    437675048  Linux Swap
 4      437675049    488395752  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    421675047  af  Mac OS X HFS+
 3      421675048    437675048  82  Linux swap / Solaris
 4 *    437675049    488395752  83  Linux

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 421675048:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 437675049:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

---

### Post by cyberdork33 on 2008-05-26
See this thread:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

You have the second issue mentioned.

---

### Post by awills on 2008-05-28
Thanks for that I can now boot into Linux. I do now one OSX and two linux options (one says boot from HD the other boot from linux) is this normal?

---

### Post by cyberdork33 on 2008-05-28
> **awills said:**
> Thanks for that I can now boot into Linux. I do now one OSX and two linux options (one says boot from HD the other boot from linux) is this normal?
Yes/No. There is should not be two, but considering the steps taken, yes. It now sees to ways to boot grub, one at the MBR and the other at your Ubuntu partition.

Try this:
[http://ubuntuforums.org/showthread.php?t=800698](http://ubuntuforums.org/showthread.php?t=800698)

---

