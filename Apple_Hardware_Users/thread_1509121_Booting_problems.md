---
title: "Booting problems"
date: 2010-06-13
forum: Apple Hardware Users
---

### Post by FireLizzard on 2010-06-13
My computer is a new MacBook Pro (17", Core i7). The model identifier is MacBookPro6,1.

I am trying to triple boot my computer in Mac OS 10.6, Windows 7, and Linux Mint 9. I am using rEFIt as my boot loader.

My partition table is as follows:
[list][*]**GPT**:
[list][*] EFI Partition (EFI/FAT)
[*] Mac OS 10.6 (JHFS+)
[*] Windows 7 (NTFS)
[*] Linux Mint 9 (Ext4)
[*] rEFIt (HFS+)
[*] Swap (swap)[/list]
[*]**MBR**:
[list][*] ??? (EFI)
[*] Mac (JHFS+)
[*] Windows (NTFS)
[*] Linux (Ext4)[/list][/list]

For those of you who don't know, the second MBR table is some sort of dummy table set up with Boot Camp so that Windows is happy. I installed Windows via Boot Camp. Then I booted off of the Linux Mint 9 64-bit live DVD, modified my partitions, and installed. I told the installer to install the boot loader in the fifth partition (where Linux is) so as to not interfere with the EFI boot system. At this point, the boot partition was between the Mac and the Windows partition. Whenever I tried to boot into Linux, it would just boot Windows. Using the live DVD and chroot, I removed the Mac and Windows entries from grub.cfg (the first line of code in 30_os-prober is now **exit 0;**), and rebooted. This didn't work. I browsed for a while, and then had more partition fun, and moved the rEFIt partition to where it is now. It seems that fix it, I suppose because the Linux partition is now listed in the MBR table. Now when I boot, Grub gives me an **unknown filesystem** error. How can I fix this problem so I can boot into Linux Mint?

Also, while browsing I found [this](http://grub.enbug.org/TestingOnEFI) and [this](http://grub.enbug.org/TestingOnMacbook). I don't know if this will help anything, though it would be nice to have Mac OS/EFI recognize Linux as bootable (right now rEFIt is the only thing that sees it as such). I also don't know how I would go about replacing my kernel with an EFI-compatible one, and I have heard things to the tune that directly booting Linux through EFI rather than as a 'Legacy OS' (with BIOS compatibility mode) breaks graphics acceleration among other things. Anyone know anything about this?

---

