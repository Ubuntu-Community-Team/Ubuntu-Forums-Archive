---
title: "Adding Ubuntu and Windows to my FC6 GRUB?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by DevgruSeal on 2007-01-29
I don't how the best way to do it would be, but here's what I'm trying to do, but can't figure out.

I have two linux distros installed, Ubuntu (hd2,0) and Fedora Core 6 (hd2,1). Windows is installed on an entirely different drive (hd1,0) (I think).

I'm trying to get my GRUB menu so that I can boot all three, but after installing FC6 recently, the hard-drive boots FC6's GRUB 0.97 menu, so I can't get into ubuntu at all.

And in order to reach the grub menu, I have to press F8 after the BIOS POSTs, and select my ATA drive, a WD1600, which is weird -- because it has no operating system on it - Perhaps where my MBR is located, since it is the first in the boot line-up?

Any help is much appreciated.

---

### Post by Kapre on 2007-01-29
> **DevgruSeal said:**
> I don't how the best way to do it would be, but here's what I'm trying to do, but can't figure out.

I have two linux distros installed, Ubuntu (hd2,0) and Fedora Core 6 (hd2,1). Windows is installed on an entirely different drive (hd1,0) (I think).

I'm trying to get my GRUB menu so that I can boot all three, but after installing FC6 recently, the hard-drive boots FC6's GRUB 0.97 menu, so I can't get into ubuntu at all.

And in order to reach the grub menu, I have to press F8 after the BIOS POSTs, and select my ATA drive, a WD1600, which is weird -- because it has no operating system on it - Perhaps where my MBR is located, since it is the first in the boot line-up?

Any help is much appreciated.

Devgru - Try this link [LINK ]("http://www.ubuntuforums.org/showthread.php?t=224351") as this will show you how to modify/re-install GRUB.

K

---

