---
title: "USB Hard Drive"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Jonathan Leshin on 2007-08-31
Hi all. I recently purchased a USB connected Hard Drive (Western Digital Passport 250GB)  and decided to use it to try out Ubuntu. I installed everything to the hard drive with no problems but now if the hard drive is not connected, Windows won't boot. I get GRUB stage 1.5 and then an error message. My boot order is CD, USB, SATA. How can I get it so that when the hard drive is plugged in, it boots to Ubuntu, when no, boots to Windows? Thank you very much for any assistance.

---

### Post by BobCFC on 2007-08-31
So you installed ubuntu to the external drive but installed grub to the internal drive?

If I understand you correctly I think that you want to restore the windows MBR on the internal drive then install grub to the beginning of the external drive.  That way if you set it to boot usb before sata in the bios and the external is plugged in it will boot the grub menu, but if not plugged in it will just boot windows.

To restore the windows MBR to the internal drive you can boot up the XP install cd and at the blue screen press R to enter the recovery console and type **FIXMBR** to restore the windows boot menu.  (then reboot you don't need to reinstall)

Then you can use the ubuntu live cd to install grub to the USB drive.   When in the live cd type: ** sudo -i**    to become root....  then type   **grub**    to get to the grub>  prompt.

You will have to be careful installing to the correct partitions but basically   (hd0,0)   is the first drive, first partition....   (hd0,1)      is the first drive, second partion  etc... they are zero based.

You can use    ** find /boot/grub/stage1**    inside grub to find the boot partition for grub (if not root this will say filenotfound)  

When you are sure you can point grub to the boot partition with    **root (hdX,Y) **    where x and y are the numbers of the drive and partition..    Then  you can install grub  with    **setup (hdX)**    where   x is the USB drive   not the internal drive in your case.

Type quit to exit the grub> prompt

I'm sure you can find grub tutorials to help.

---

