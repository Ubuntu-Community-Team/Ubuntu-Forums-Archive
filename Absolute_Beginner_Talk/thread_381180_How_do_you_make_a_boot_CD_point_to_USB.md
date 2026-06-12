---
title: "How do you make a boot CD point to USB?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by bluecaterpillar on 2007-03-10
I have a Gateway 200X whose motherboard has a delightful tendency to eat hard drives. After replacing the HDD three times in the past year, I finally gave up and ordered a new Thinkpad.

Meanwhile, I still have the Gateway, which is not entirely useless - I can still run WIndows XP off the HDD, as I don't terribly mind the fact that it crashes at least three times a day, and in fact I am typing this post in Ubuntu off the LiveCD.

What I'd like to do is run Ubuntu from a USB flash drive on this computer. I used the guide on pendrivelinux.com to some success. Unfortunately, the BIOS on this machine has no option to boot from USB. It has an option to boot from "Removable Devices," and surely any reasonable person would qualify a USB flash drive as "removable," but no dice.:confused: 

Anyway. I'm arriving at my point here. How do I make a bootable CD point to my USB drive? Extensive Googling led me to  this page: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) but I fear that the instructions are a bit over my head.... I also found a guide to installing Smart Boot Manager on a floppy, but my computer has no floppy drive. Can I just install SBM on a CD? How?

Also, am I right in assuming that such a setup will bypass the hard drive entirely, thus eliminating my problems with the aforementioned thrice-daily crashing?

Thanks in advance for your help.

---

### Post by computx on 2007-03-10
I don't think you can. although a bootcd and a usb drive are both removable thay are very different devices and your bios can't substitute one for the other. However look on the manufacturers web page, there may be a bios update that will allow booting from usb devices.
Also it is quite possible that the laptop "eating harddrives" was a windows related problem and won't happen using linux. 
Good Luck!

---

### Post by ajgreeny on 2007-03-10
I don't know the Gateway 200X, but if by chance it has a floppy drive, get a copy of smartboot manager which will allow booting from CD or, I think, a usb drive (not sure about that) if your bios does not accept that possibility.  If no floppy, then I do not have a clue where you can go; unfortunately I don't think you can get SMB on to the mbr of your hard disk, though other people may know differently.

---

### Post by bluecaterpillar on 2007-03-11
I guess I was just being Lazy and Impatient (but not in the good way.) I know that it is possible to make a boot CD point to USB, as outlined here: [http://www.ubuntuforums.org/showthread.php?t=266068](http://www.ubuntuforums.org/showthread.php?t=266068) as well as the link I posted above, but I am having trouble following the instructions.

First off, where is etc/mkinitramfs/modules? Should it be on the LiveCD? All the instructions seem to imply that this file already exists somewhere, and I just add a couple lines of code to the end.

Help!

---

### Post by bluecaterpillar on 2007-03-15
For anyone who's curious, there were two solutions to my problem...

1) I downloaded the grub boot cd here: [http://www.gap.ien.05.ac-aix-marseil...untu/grub2.iso](http://www.gap.ien.05.ac-aix-marseil...untu/grub2.iso)
and followed the directions here: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB) for booting from grub.

2) My hard drive was so toasted that I finally up and disconnected it... the next time I turned on the computer with the USB key plugged in, it automatically booted from there.

Yay!

---

### Post by dstew on 2007-03-15
I think the instructions you are referrring to depend on an already-installed Ubuntu linux. You can create fles and directories, and even install and run new programs using the live CD, but the file names are different because the Live CD uses a different file system than an installed linux system.

---

