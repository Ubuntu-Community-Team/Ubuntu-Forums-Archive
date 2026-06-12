---
title: "Windows on one SATA HDD and UBUNTU on another IDE HDD?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by alexuz on 2007-01-31
I have just completed the nice installation of ubuntu on my IDE HDD. After the installation it told me to remove the CD and reboot. Which I did and then my Windows XP booted by default. I did NOT get to choose anything. Windows XP was the first OS on this computer.

This is what my partitions look like:

250gb SATAII HDD =
- 40gb for Windows XP (NTFS)
- 200gb for storage (NTFS)

300gb IDE HDD =
- 215gb for storage (NTFS)
- 60gb for Ubuntu (ext3)
- 1gb for swap (linux-swap)

:confused:

---

### Post by glabouni on 2007-01-31
seems your bios is configured to boot on hard drive where windows is by default.
you'll have to change this in your bios or to install grub on the drive where windows is.

---

### Post by old_geekster on 2007-01-31
You didn't mention seeing GRUB (GRand Universal Bootloader).  This is where you should have the choice of which OS you want to boot.

If GRUB is not installed, you would have to set boot order in your BIOS, as suggested previously.

---

### Post by VraiChevalier on 2007-01-31
I have a very similar question and so am posting it here with this thread. Hope this is the right place.

I am about to install a second hard drive (120Gb IDE) for Ubuntu dual boot install beside Windows XP and am trying to figure out the best setup.

Would it be better to install Ubuntu boot records on first hard drive and balance of Ubuntu on second hard drive?

If I change BIOS settings to boot from second hard drive would I have to change back to first hard drive again to boot Windows?

I have only about 11Gb free space on first hard drive. 

Or should I install all of Ubuntu on first hard drive and just use second hard drive for Ubuntu files storage?

Does GRUB come on the install CD?

---

### Post by skyhopper88 on 2007-01-31
My setup is done in a similar way. I have Windows on a Sata set as master and Ubuntu on an IDE slave. I install grub ONLY on the HD for Ubuntu. In the Bios I set the first boot HD to the IDE slave, and grub will still see Windows on the Sata master.

---

### Post by VraiChevalier on 2007-01-31
> **skyhopper88 said:**
> My setup is done in a similar way. I have Windows on a Sata set as master and Ubuntu on an IDE slave. I install grub ONLY on the HD for Ubuntu. In the Bios I set the first boot HD to the IDE slave, and grub will still see Windows on the Sata master.

GREAT! Thats's what I needed to know! 
Thanks for the info.
Watch out "XP" box, I'm goin' in!

---

