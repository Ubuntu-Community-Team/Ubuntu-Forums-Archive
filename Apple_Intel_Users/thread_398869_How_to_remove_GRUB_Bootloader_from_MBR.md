---
title: "How to remove GRUB Bootloader from MBR???"
date: 2007-04-01
forum: Apple Intel Users
---

### Post by koni2005 on 2007-04-01
As I was trying to install Ubuntu to an external USB drive from the (K)ubuntu Live DVD, I unfortunatley installed the GRUB Bootloader onto my internal HD's MBR. Now, I can't boot XP anymore, as bootcamp and refit always start GRUB.... How do I get rid of it?

The Partitionanalyzer from refit gives my the following output:



*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    128335911  Mac OS X HFS+
 3      128598056    195371527  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    128335911  af  Mac OS X HFS+
 3 *    128598056    195371527  0c  FAT32 (LBA)

MBR contents:
 Boot Code: **GRUB**

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 128598056:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA), active

---

### Post by Harkonnen80 on 2007-04-01
For recover your MBR is quite easy. Put your CD of Windows XP and run the installation from it. In the first screen choose the option Repair from the console command.
You will arrive to the typical MS-DOS console, then use the command FIXMBR and you'll start your windows normally again.

---

### Post by koni2005 on 2007-04-02
Thanks!!!!

---

