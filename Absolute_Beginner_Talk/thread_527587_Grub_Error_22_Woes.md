---
title: "Grub Error 22 Woes"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-16
I loaded Ubuntu 7.04, and on reboot, I never saw the GRUB menu, only
 
```
GRUB Loading stages1.5
 
GRUB loading, please wait . . . 
Error 22
```
 
Now, I *think* I know how to fix it (boot from WinXP CD and run **fixmbr; **and I *think* I know how I caused this.  But I don't know how to fix it (until the patient folks on the forum sigh and take pity on a denser-than-average newbie).

I decided to load Ubuntu NOT on my laptop hard drive, but on an external USB 2.0-attached HDD.  It had two partitions, 1 NTFS (about 150 Gb) and 1 unused (about another 150 Gb).  I walked through the LiveCD install, but chose to partition manually, choosing to create the following partiions:

1) Left partition 1 alone as an NTFS; 

2) 20 Gb /etc partition, mounted as /root.

3) 20 Gb /etc partition, unmounted and unused (for another future Ubuntu or other Linux distro

4) [last logical partition for extended partitions]

5) 5 Gb Swap partition

6) 45 gb /etc mounted as /home

7) remainder (approx 40 Gb) for a FAT32 partition (making exchange with XP easier) mounted as /windows.

After that, everything seemed unremarkable about the partitioning and loading of Ubuntu (until the GRUB error, of course).

My *guess* (and it's only that) is that the problem lies in the fact that all of Ubuntu is on another drive (which the gparted saw as "SCSI2" ["SCSI1" being a smaller, separate USB backup drive attached to the same laptop.

I'll sit right here and wait for rescue!

---

### Post by Arthur Archnix on 2007-08-16
I think you're guess is pretty accurate. Plug in your external drive and restart, do you still get the error? 

Grub is installed in two parts. One part in the MBR on your hard-drive. The second on your linux file system.

I think you're right. You should you fixmbr to repair your windows MBR. Then change your Bios to boot from a usb hard-disk first. Then toss in a feisty live cd and follow the tips on the forums about how to repair grub. But, install it to the usb hard-disk. Plugging it in while running a feisty live cd and typing sudo fdisk -l should give you the info you need to do a nice grub reinstall.

If all goes well, when the hard drive is plugged in Grub will come up and you can boot feisty or windows. When it's not plugged in windows will just fire up.

---

### Post by MQMike on 2007-08-16
You’ll have to patiently sort this out, but it’s fixable (I think).

I just did it and wrote it up at:
How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)
How to install K/Ubuntu 7.04 to an external USB hard disk drive (HDD). 
(Scroll to the second post, August 14, 2007.)

The 22 business has to do with BIOS drive-shifting for USB drives.  Long story.  But it’s in the link I gave you.  Everything Arthur Archnix said is correct, btw.  You do want GRUB installed to the MBR of the external USB drive, and you must configure BIOS to detect it and place it first in boot order and Enable Booting From USB in BIOS.  Etc.  Dig in, and you’ll see it all, just a bunch of details is all.

---

### Post by Curbuntu on 2007-08-16
> **Arthur Archnix said:**
> If all goes well, when the hard drive is plugged in Grub will come up and you can boot feisty or windows. When it's not plugged in windows will just fire up.

Ah, I encountered something I hadn't expected -- my BIOS (on a less-than-three-year-old Compaq laptop) doesn't have the option of booting from *any* USB device.  Floppy, yes; CD-ROM, yes; NIC, yes; and, of course, the HDD.  But there are no options for booting from anything else.  I guess I've never tried this, so I had no idea.

Stranger still is that the boot menu is separate from the standard BIOS/CMOS menus (where the options are pretty minimalistic anyway).  On any boot, F10 brings up the standard BIOS options, but ESC brings up the boot-order options, separate from BIOS setup.  Setup can be reached from the boot-order menu, but not vice versa.

So no *wonder* GRUB went catatonic with an Error 22 -- there was no way to pick up any boot information from the USB drive.

---

### Post by MQMike on 2007-08-17
Yep – it’s the first requirement in my How-To.
Here’s an esoteric solution to that, but involves some details (listed at the end of the How-To):

If your BIOS does not support booting from USB, see this:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Case:  [http://ubuntuforums.org/showthread.php?t=506179](http://ubuntuforums.org/showthread.php?t=506179)
(Basically, you must build a bootable CD that will boot the external USB.)

---

