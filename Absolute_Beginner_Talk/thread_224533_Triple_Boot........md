---
title: "Triple Boot......."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by bootbat on 2006-07-28
Hello All...

My name is Rupam. Just joined you all to find more about Ubuntu. Heard a lot, never tried:) I am ready to try it now..

I thought seeking some expert advice would help me avoid issues that might crop up. Here are my system stats - Pentium IV 2.93 GHz processor, 915 GV Motherboard with 256 DDR RAM and 2x40 GB HDD. I have XP on one and FC 5 on the other. I want to create a seperate partition on the FC 5 drive and install Ubuntu on it. I also want to have Grub to display all three on startup. 

I use windows just for games and wipe it clean the moment I find alternatives. FC5 is the one I use mostly but I want to give Ubuntu a shot. 

Any pointers would really help me avoid system crashes.:confused:

---

### Post by rowanparker on 2006-07-28
I don't understand what you are exactly asking?

---

### Post by MrHorus on 2006-07-28
If you have a seperate drive or a spare partition then yes, you can sub partition this into a new root filesystem for Ubuntu and the bootloader will pick up Windows and FC5 and all three operating systems will quite happily live together.

---

### Post by Indras on 2006-07-28
I have a triple boot system right now, with Win98 in a 2Gb FAT32 partition, Mac OS X (patched 10.4.6) in a 10Gb HFS+ partition, and Ubuntu in the extended partition with about 55Gb of ext3 space and 1Gb swap partition.

I've got all three operating systems showing up perfectly in Grub, and just yesterday I installed grub-gfxboot which allows for a more graphical bootloader.

I can't say that I see any problems you're going to run into.  The most common one I see is with trying to install to a system with not enough RAM.  Other than that, be aware that proprietary video drivers can be a pain to install (Nvidia and ATI).  I'd recommend before you try anything, search the forums for a HOWTO first.

---

### Post by confused57 on 2006-07-28
> **bootbat said:**
> Hello All...

My name is Rupam. Just joined you all to find more about Ubuntu. Heard a lot, never tried:) I am ready to try it now..

I thought seeking some expert advice would help me avoid issues that might crop up. Here are my system stats - Pentium IV 2.93 GHz processor, 915 GV Motherboard with 256 DDR RAM and 2x40 GB HDD. I have XP on one and FC 5 on the other. I want to create a seperate partition on the FC 5 drive and install Ubuntu on it. I also want to have Grub to display all three on startup. 

I use windows just for games and wipe it clean the moment I find alternatives. FC5 is the one I use mostly but I want to give Ubuntu a shot. 

Any pointers would really help me avoid system crashes.:confused:
The Dapper installer **should** detect both your other OS and add to grub; however, you might want to want to open up your FC5 grub entry(menu.lst) and write down(or print) the exact entry used to boot your FC5...that way, you can always manually add the FC5 entry to the Ubuntu menu.lst if the installer doesn't.  I had to do that after installing Mepis along with Dapper, the Mepis installer didn't add Dapper to it's grub menu.lst.  I'm not familiar with FC5, so I don't know for sure.
You still may want to backup any important data you don't want to lose.

---

