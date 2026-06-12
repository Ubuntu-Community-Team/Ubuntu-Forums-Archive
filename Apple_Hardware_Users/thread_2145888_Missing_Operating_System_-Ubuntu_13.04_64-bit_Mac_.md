---
title: "Missing Operating System -Ubuntu 13.04 64-bit Mac on MacBook Pro 8,1"
date: 2013-05-16
forum: Apple Hardware Users
---

### Post by WaMu on 2013-05-16
Hi, I'm an absolute noob here who needs some help trying to get Ubuntu 13.04 up and running on my 2011 MacBook Pro 8,1.

I downloaded Ubuntu 13.04 64bit Mac Edition to begin with and also used the following guide

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Pop in the disc, loads up Ubuntu LiveCD just fine, follow the guide on  how to partition my HDD with SWAP and EX4. (I'm just Dual-Booting Mac OS  X and would be Ubuntu)

But my problem gets to after the  installation, I sync the MBR like it prompts, shut down, turn it on and  select the partition and I get the error of "Missing Operating System"  and a blink cursor. 

I tried reinstalling it again, syncing the MBR and I get the same message.

Here is what I get when I open Partition Inspector.:


> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    487154119  Mac OS X HFS+
 3      487154120    488423655  Mac OS X Boot
 4      488425472    490522623  Linux Swap
 5      490522624    625141764  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    487154119  af  Mac OS X HFS+
 3      487154120    488423655  ab  Mac OS X Boot
 4      488425472    490522623  82  Linux swap / Solaris

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 487154120:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 488425472:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 490522624:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data





Any help would be appreciated. :)

---

### Post by WaMu on 2013-05-16
UPDATE.

I fixed it actually, what I did was SWAP the positions of EXT4 and Linux-Swap and it worked like a charm :)

---

### Post by johnwhelchel on 2013-06-15
EDIT: Solved.

To fix this, I did a full re-install, but when partioning the drive using gparted I made sure to make the ext4 partition *before* the swap one. In addition, right before installing it'll ask you about some seperate partition for a BIOS boot loader. I did it what it said the first time and ignored it the second time (so I recommend ignoring it). Just make sure to install the grub boot loader on the same partion as your main linux one (ext4).


> Can you explain how you switched the two partitions? I'm having the same issue with almost the exact same setup (MBP 8,2 64-bit). Thanks!



*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    797704495  Mac OS X HFS+
 3      797704496    798974031  Mac OS X Boot
 4      798976000    807364607  Linux Swap
 5      807364608    976759139  Basic Data
 6      976760832    976771071  GRUB2 BIOS Boot

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    797704495  af  Mac OS X HFS+
 3      797704496    798974031  ab  Mac OS X Boot
 4      798976000    807364607  82  Linux swap / Solaris

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
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 797704496:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot

Partition at LBA 798976000:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 807364608:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 976760832:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type GRUB2 BIOS Boo

---

