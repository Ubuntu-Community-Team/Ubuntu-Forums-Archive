---
title: "Triple Boot with Data Partition"
date: 2010-11-13
forum: Apple Hardware Users
---

### Post by huckduck on 2010-11-13
So hello everyone, I've been tinkering for over a week to try and get a functioning triple boot + shared data working. i've hit a road block. i'm using reFIt with SnowLeopard/W7/10.10. i can't get into ubuntu


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    390772495  Mac OS X HFS+
 3      391034640    781659639  Basic Data
 4      781922304    879577087  Basic Data
 5      879579136    976773119  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    390772495  af  Mac OS X HFS+
 3      391034640    781659639  0c  FAT32 (LBA)
 4 *    781922304    879577087  07  NTFS/HPFS

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

Partition at LBA 391034640:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA)

Partition at LBA 781922304:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active

Partition at LBA 879579136:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 5, type Basic Data


OSX and Windows are fine. but whenever i select linux, it boots directly into windows. i'm hoping i don't need to install GRUB2 to the windows partition as that would defeat the purpose of reFIt (would it not?)

---

### Post by coiske on 2010-11-17
Just started looking into this, as I'm about to implement the same sort of thing.  It sounds like Grub might have to be on one of the first four partitions in order for it to successfully boot Linux.    You could accomplish this by making partitions 2-4 your Linux, Windows, and Data partitions, and partition 5 your MacOS partition.   (And installing Grub to your Linux partition.)

I'm not crazy about this solution.  I was under the impression that earlier partitions are toward the outer rim of the drive, leading to faster seek times.   So I really wanted MacOS to be my second partition, rather than my fifth.  But it looks like I may have to bite the bullet and put the MacOS partition fifth.  Let me know if you come up with a better solution, though.

---

### Post by huckduck on 2010-11-17
hi guys,

i got it working after countless trial and error formats because the online information is so sketch.

i found partitioning this way works

Initial setup for win7/vista:
1. HFS+ (OSX)
2. FAT32 (Data/Storage/Shared)
3. FAT32/NTFS (Windows 7 or Vista)
4. FAT32 (Linux)

this will make your MBR look like:
1. EFI Protective
2. HFS+
3. FAT32
4. FAT32

and your gpt look like
1. EFI Protective
2. HFS+
3. Microsoft Basic Data
4. Microsoft Basic Data
5. Microsoft Basic Data


then install (in this order) OSX to the OSX Drive, Windows to the Windows drive, and Linux to the Linux drive ***with the bootloader on the data drive***

---

### Post by coiske on 2010-11-17
So putting the Ubuntu bootloader on the data partition doesn't keep any of the OS's from reading/writing to the data partition?   Does the data partition have to be a particular format for this to work?   (I need mine to be HFS+ unjournaled.   Not sure if that would mess up Ubuntu's ability to read the bootloader from there.)

---

### Post by huckduck on 2010-11-18
it shouldn't matter. i'm going to format mine to ntfs, but at the boot level, it doesn't matter what the format is. mine's fat32, but the boot sector is readable by efi/mbr anyways, so as long as the boot sectors are there it works.

---

