---
title: "Many different problems!!!"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by digital006 on 2007-07-12
Today was the first time in 3 years I've tried to install a distro (Ubuntu 7.0.4) of Linux (First time bricked a hard drive). It's nice to see that it's still as bloody hard as it is back then.

Computer Specs:

AMD Athlon XP 2000+
1gb Ram
2 x 200g HDD (IDE)
NO Floppy Drive!
WG331v1 (Atheros Chipset).

My first problem occurred after installing it onto my second clean hard drive (200gb formatted, Win XP Pro on first HDD). I restart my computer and get confronted with Grub Error 18. This is what I've found from searching around these forums:

> Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel it self does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.
[edit] Tips

Because I couldn't get into Ubuntu I went into Windows XP pro instead, read up a bit more and decided to try and reformat with the 1023 cylinders thing. Unfortunately I couldn't even get an error message it refused to boot into grub so I had to fixmbr with an xp pro disc. Edit: It gave no error message just restarted.

I'm going to try and install again but I need to know how to set a boot partition on my second drive so that I avoid error 18, when I looked in the manual partitions part of the install I couldn't see anything resembling a boot partition (I'm pretty n00b). 

[http://www.linuxquestions.org/questions/showthread.php?t=423307](http://www.linuxquestions.org/questions/showthread.php?t=423307) <<< This thread here links to a wiki page and someone commenting that they fixed it by placing a file in MBR, can anyone expand?

Any help is greatly appreciated.

Mike

---

### Post by snobby500 on 2007-07-12
first of all, sorry i dont know much about this, i got a similar problem, when itried to install ubuntu fresh on an extra hard drive, and it gave me a grub error, so what i did was make my secopnmdary hard drive (ubuntu) the primary boot device in bios, and the xp hard drive the second boot device, and that solved my problem, im sorry i dont know i it will help u, but for a couple of minuted work (if that) i thuoght it might be worth a try, seeing as it wont damage your partitions :) just remember if it doesnt work, switch the boot sequence back :)

i dont know if this will help yuo because i couldntboot into anything, and it seems you can boot into xp? i dont know if this will help but muight aswell give it a try :) 

hope this helps

---

### Post by regomodo on 2007-07-12
this may help. It's not the one i used to reconfigure my grub (can't find it) but it's similar

[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by digital006 on 2007-07-12
Thanks, the problem is I don't want to have to install it all again just to have to fixmbr, as I can't garuntee that it will work again (previous bricked hdd was due to problems with MBR).

---

### Post by regomodo on 2007-07-12
in that case you need an xp install disk and you need to run fixmbr in a command line once booted into it

just search fixmbr

btw. you haven't bricked your hdd. Far far from it.

---

### Post by digital006 on 2007-07-12
Ah I think your confused, Both new hard drives are fine I'm was just worried about having to continually fixmbr to be able to get back into windows again.

---

### Post by digital006 on 2007-07-12
Just reinstalled it and changed over the order of booting but that didn't help, I'm still stuck and the next time I restart I'll have to use fixmbr to get into windows.

If I set it so that the partitions of the install were about 50gb would that work?

---

