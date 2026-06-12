---
title: "Dual Boot Grub Error 18"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by stevegowan on 2008-03-02
I have been using a dual boot system (XP and Ubuntu) using two hard discs for a while on my desktop and wanted to install dual boot on my laptop (Time A520-K7). As it only had a 60GB drive in it, I've bought a larger drive (160GB) and installed this. The laptop's a 2.4gHz Athlon XP 2.4 with 1GB of memory. 
I installed Windows and then Ubuntu 7.10 and it all seemed to go great until I got the Grub error 18 on boot up. 
I've read quite a lot on the net about this including on the threads here but I'm still pretty confused. Whilst I kind of understand the problem (the 137GB HDD limit in the BIOS) and understand the theory behind the solution (have a separate boot directory for the start up stuff within the sector limit) I'm struggling to understand how this is actually done during the install of Ubuntu.
I reformatted and installed XP as before, then used a Parted Magic boot CD to put a space before the XP directory but when I install Ubuntu I can't seem to find out how to put the boot partition in place. I can set up the swap and root partitions OK using the manual setup in the install process in Ubuntu but I can't work out how to get a boot file and partition into the space saved at the start of the HDD.
Can anyone help to explain how this is achieved to someone who understands just enough to be dangerous! Or am I just being a bit thick? (entirely possible!)
Thanks.

---

### Post by wolfen69 on 2008-03-02
Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

---

