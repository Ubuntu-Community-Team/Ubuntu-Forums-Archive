---
title: "external usb bootable linux???"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-10-17
basically what i want to do is have an external bootable disk with linux that i can move to different pcs is that possible?
thanx

---

### Post by anemptygun on 2007-10-17
:S I tried to do this with my computer and fried it. I hope you have better luck than me.:(

---

### Post by LinuxNewGuy on 2007-10-17
> **evkefalas said:**
> basically what i want to do is have an external bootable disk with linux that i can move to different pcs is that possible?
thanx

Does it have to be booted from USB?  Will a Live CD work for you?

---

### Post by skymera on 2007-10-17
i installed to my exteranl USB HD

justr make sure you install grub to a serperate MBR

---

### Post by anemptygun on 2007-10-17
> **skymera said:**
> 

just make sure you install grub to a serperate MBR

This is most likely where I went wrong.

---

### Post by skymera on 2007-10-17
yeah it sort of wrote its own grub and couldnt boot with out it loleasily fixable, but not convenient

---

### Post by evkefalas on 2007-10-17
is mrb another partition?
cause i also made a 10 mb partition for the grub at the brginning of the disk and installed it at \boot seperately the grub that is
and is the same result
thanx

p.s id like a disk not a live cd

---

### Post by Pete B on 2007-10-17
Have a look at Damn Small Linux (DSL) here [http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/") and/or just google/wiki it. I'm about to try it myself from a CD because I couldn't get Xubuntu to recognise the CD drive on the old laptop I want to use.

I guess it should be possible to create a bootable usb pen yourself, but judging by some of the comments here it's an experts only job. DSL seems to have been around a while and you can download it for free or buy a usb pen and help support the Open Source community.

Good luck,

Pete

---

### Post by logos34 on 2007-10-17
> **evkefalas said:**
> is mrb another partition?

no, it's a special section (512 bytes) at the very beginning of the disk reserved for bootloaders.

> cause i also made a 10 mb partition for the grub at the brginning of the disk and installed it at \boot seperately the grub that is 

if you mean on the usb drive, you didn't need to do that...just make sure Grub installs to the MBR on the external USB and not the internal drive.  one way to insure this is to unplug the internal drive before the installation.

---

