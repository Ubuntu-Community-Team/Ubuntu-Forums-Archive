---
title: "Help removing Ubuntu from MacBook Pro 8,2"
date: 2012-09-30
forum: Apple Hardware Users
---

### Post by jyarbr2 on 2012-09-30
Hi all,

I need some advice on removing Ubuntu from my macbook.  I have OS X Mountain Lion, Ubuntu and Windows 7 installed and would like to keep just OS X Mountain Lion and Windows 7.  I use rEFIt to boot and would like to remove that as well. I ran partition inspector to show the following:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    787442535  Mac OS X HFS+
 3      787442536    788712071  Mac OS X Boot
 4      788713472    837402541  Basic Data
 5      888399872    976773119  Basic Data
 6      837402542    837404495  GRUB2 BIOS Boot
 7      837404496    880193558  Basic Data
 8      880193559    888399871  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    787442535  af  Mac OS X HFS+
 3      787442536    788712071  af  Mac OS X HFS+
 4      788713472    837402541  0b  FAT32 (CHS)

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

Partition at LBA 787442536:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 788713472:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 0b  FAT32 (CHS)

Partition at LBA 888399872:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 837402542:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type GRUB2 BIOS Boot

Partition at LBA 837404496:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 7, type Basic Data

Partition at LBA 880193559:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 8, type Linux Swap

---

### Post by 2F4U on 2012-10-01
You should be able to do this from OSX:

[http://www.ehow.com/how_12188806_delete-ubuntu-mac.html](http://www.ehow.com/how_12188806_delete-ubuntu-mac.html)
[https://discussions.apple.com/thread/2344909?start=0&tstart=0](https://discussions.apple.com/thread/2344909?start=0&tstart=0)

---

### Post by jyarbr2 on 2012-10-01
Thanks 2F4U!

I still am having trouble deleting the linux swap partition. My bootcamp and linux swap partitions can't be selected (screenshot 1), and it says that the partition cannot be modified. See screenshot 2. How can I allocate all of the space for Mac OSX? I am thinking about just reinstalling my windows later so I would like the entire partition to be Mac OS X.

---

### Post by jyarbr2 on 2012-10-01
Sorry here are the screeshots.

---

