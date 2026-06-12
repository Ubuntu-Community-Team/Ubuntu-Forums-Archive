---
title: "Installation Woes!! Help plz"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-19
hey guys,

So I disconnected all internal drives and popped in the LiveCD and ran the installer to an external HD. Everything went good and I rebooted. I got

Loading Grub

then Grub Error 18

I tried booting with the LiveCD again and now all I get are crazy lines all over my screen

ahhhh!! lol

plz help!!

thanks

---

### Post by PPAAUULL on 2007-10-19
Are you booting form the external?

---

### Post by JasonBourneLinux on 2007-10-19
yes- Grub is on the external on a ext3 partition (I did what the instructions said)

thanks for the quick reply!

---

### Post by PPAAUULL on 2007-10-19
Well ya grub can be on there but are you booting from the external (usually choosen from the bios menu)?

---

### Post by JasonBourneLinux on 2007-10-19
yup- checked that

---

### Post by PPAAUULL on 2007-10-19
ok so it seems that you might have corrupted Ubuntu in the proccess of installing it. I think I have this happen to me once and once I deleted the partition and the same thing happened to me. Hold on I will look some stuff up.

---

### Post by JasonBourneLinux on 2007-10-19
thanks so much!!

---

### Post by JasonBourneLinux on 2007-10-19
perhaps its something with the MBR- how do I repair the MBR via Lilo and LiveCD?

---

### Post by PPAAUULL on 2007-10-19
Ok so I found this:

> Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel.

The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem.
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot.

The address is [http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18) if you want to take a look.

PS I was wrong about the corruption and I think it was an error 17 that I got.

---

### Post by JasonBourneLinux on 2007-10-19
cool- what is the biggest boot partition I can do then? (in terms of GB)

---

### Post by JasonBourneLinux on 2007-10-19
and before I let the installation of Grub run to hd0- where do I put it this time?

---

### Post by PPAAUULL on 2007-10-19
Last time did you put it at the very front?

And the largest depends on your bios. It shouldn't be that hard to find on google or in the manual.

---

### Post by JasonBourneLinux on 2007-10-19
yup it was- first partition (primary) my HD is SATA so Ill do the partition round 7 GB

---

### Post by JasonBourneLinux on 2007-10-19
well my internal is SATA (external is USB) for windows so yeah i think 7 gb should be plenty

---

### Post by PPAAUULL on 2007-10-19
Try it and see what happens. Beyond that I have no idea. lol I hope it works.

---

