---
title: "Triple boot Windows partition no longer works after Yosemite upgrade"
date: 2015-01-08
forum: Apple Hardware Users
---

### Post by Jordan_Mecom on 2015-01-08
**The problem:**
After upgrading to OS X Yosemite, my triple boot through rEFInd no longer works as it did before. Specifically, I can boot into OS X and Ubuntu, but not Windows. Furthermore, the way I boot into Ubuntu is different than before.

[B]Details:
[/B]I upgraded to OS X Yosemite and reinstalled rEFInd to upgrade to version 0.8.4, which supports Yosemite. Before, on boot I was presented with three options: OS X, Linux, and Windows. When I chose Linux or Windows I was sent to GNU Grub, and from there I could select Linux or Windows to boot to the desired OS. Now, things are different. Instead, I'm presented with OS X, a lot of Linux choices, and then the old Linux and Windows choices (the ones, by name, that I used before). The old ones don't work -- I'm presented with a black screen with 'invalid license' and then 'no bootable device'. The new Linux choices boot directly through rEFInd, and do work. I think that the Yosemite upgrade messed up Grub, and since I accessed Windows through Grub before I can no longer access it.

Here's what efibootmgr displays, on Ubuntu:
BootCurrent: 0080
Timeout: 5 seconds
BootOrder: 0080,0000
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Mac OS X
Boot0082* 
BootFFFF*

Here's a screenshot of Gparted, if it helps:
 [IMG]http://i.imgur.com/QRa0yA5.png[/IMG]


I've been searching around some more, and edited in some additional information if it is helpful.
Here are my GPT and MBR partition tables. 

> *** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    389765343  Mac OS X HFS+
 3      389765344    392304639  Mac OS X Boot
 4      392304640   1124724735  Basic Data
 5     1124724736   1456943103  Basic Data
 6     1456943104   1465147391  Linux Swap


Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    389765343  af  Mac OS X HFS+
 3      389765344    392304639  ab  Mac OS X Boot
 4 *    392304640   1124724735  07  NTFS/HPFS


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


Partition at LBA 389765344:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X Boot
 Listed in MBR as partition 3, type ab  Mac OS X Boot


Partition at LBA 392304640:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 07  NTFS/HPFS, active


Partition at LBA 1124724736:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 5, type Basic Data


Partition at LBA 1456943104:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap




**Attempted solutions:**
I tried to use boot-repair to fix Grub. I now have Grub again, and my new default option on boot is to boot Ubuntu through Grub, but really this hasn't solved anything as Grub doesn't present a choice to load Windows. 
I also tried everything on this page: [http://www.rodsbooks.com/refind/yosemite.html](http://www.rodsbooks.com/refind/yosemite.html) 
I'm not really sure where to go from here. 

My desired boot would be to bypass Grub at all, and just use rEFInd, but if I can get things back to how they were that would work as well. 
I can provide more details as you need them, just let me know. I'm going to sleep as of posting this thread, and I'll get back with more details as needed ASAP. Thanks in advance.

---

### Post by este.el.paz on 2015-01-09
@jordan:

Yes, I think OSX messed up GRUB . . . that's what happened to me recently when I upgraded to 10.9.3?? or whatever the latest upgrade was, and that messed up rEFInd and GRUB . . . for my triple boot set up, but, with 2 OSX partitions and one for linux.  rEFInd would load linux either through the "windows" icon or "linux" . . . I tried all the "boot recovery" items, including SuperGRUB2 . . . trying to get GRUB repaired, but . . . "failed."  I don't have a lot of computer science background to know where GRUB is installed and using CLI to re-install GRUB, so for me I had to wipe the linux install and do a fresh install . . . including setting aside a partition for "bios_grub" using the "something else" option in the installer.  W/O doing that the install says "successful" on my '10 MBPro, but, it won't boot.

I've also found that with Bootcamp I couldn't modify the HD at one point, that was when going from dual-boot and trying to get triple boot set up, so, you'll have to see if you just try a fresh install of linux, then shut down the computer and see if on re-boot rEFInd finds everything and you can get to you selected OS . . . .

e.e.p.

---

