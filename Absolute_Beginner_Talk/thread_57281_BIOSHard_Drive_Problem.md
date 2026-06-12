---
title: "BIOS/Hard Drive Problem?"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by Captain Booty on 2005-08-15
The thing is, my brand new computer won't boot from the hard drive (yes, it's a SATA drive). I receive  the following message:

> PXE-E61: Media test failure, check cable
PXE-M0F: Exiting NVIDIA Boot Agent.

Afterwhich the underscore starts to torment me with its blinking. 

The thing I found weird is that I was able to install Ubuntu to the hard drive, just not boot from it. Booting from the CD drive is fine.

---

### Post by Nequeo on 2005-08-15
This won't really help solve you problem... But PXE is a remote network boot. So your machine either isn't even trying to boot off the HDD, or is failing silently and moving on to the next item in the boot order.

Generally, if there is a problem with the HDD installation, your machine would freeze up, displaying a GRUB error, if you even hit the boot sector on your drive.

Did you ask the installer to partition your drive automatically? Or did you set up the partition table yourself... If so, how?

Cheers,

---

### Post by Captain Booty on 2005-08-15
[QUOTE=Nequeo]This won't really help solve you problem... But PXE is a remote network boot. So your machine either isn't even trying to boot off the HDD, or is failing silently and moving on to the next item in the boot order.

Generally, if there is a problem with the HDD installation, your machine would freeze up, displaying a GRUB error, if you even hit the boot sector on your drive.

Did you ask the installer to partition your drive automatically? Or did you set up the partition table yourself... If so, how?

Cheers,[/QUOTE]
It did ask me whether I wanted to do it manually, but I just choose automatic - the six week wait plus my lack of practical experience with Linux (and "technical stuff" in general) meant that I just wanted to get the thing running. (By the way: Floppy -> CD -> Hard Drive goes the boot order, and changing it doesn't do anything, not sure if it would make a difference but I've heard some pretty weird things work before).

As for information, I welcome it. If it doesn't fix my problem, I'll still learn something new anyway.

---

