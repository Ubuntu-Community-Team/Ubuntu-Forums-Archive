---
title: "Problem installin Ubuntu 7.04"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by gvillaran on 2007-05-31
Hi, i have dowloaded Ubuntu 7.04 and when i try to boot with the cd i had burned and choosed install to the hard drive im getting the message:

Invalid compressed format (err=2)

--System Halted

and thats all

my machine is a P4 3.0GHZ and 512MB of memory 80GB HD.

anyone have an idea on how to resolve this?

Thanks

---

### Post by Mazza558 on 2007-05-31
Try burning another CD, but at a slower speed (2x or 4x)

---

### Post by kernel tom on 2007-05-31
did you burn the iso image onto the cd directly?  this is a very strange messege to get... i had problems when i "finalized" the cd, but an unfinished cd burned with the iso image should work fine

---

### Post by GabrielDunn on 2007-05-31
Good point, burn it at a slow speed.  Also is the drive you're installing it on clean?  Might be a waste of time but consider booting with g-parted and formatting the drive ext3.

---

### Post by gvillaran on 2007-05-31
Maxumin speed was 4x, im gonna try to burn it again.

thanks

---

### Post by gvillaran on 2007-05-31
i have burned another CD but still failing :(

gonna try to download the ISO again i think, just in case

---

### Post by Sparkster185 on 2007-05-31
Also you might want to check the CD for errors.  After your machine boots to the CD, you'll see a menu.  One of the options is to "Check CD for errors".  Do this and see what it says.  Then you'll know if the CD itself is corrupted.

---

### Post by gvillaran on 2007-05-31
i did that (Check CD for errors) and says the same.

Invalid compressed format (err=2) etc etc

---

### Post by Sunflower1970 on 2007-05-31
Have you tried, maybe using the alternate CD? Sometimes that will get past whatever problem the graphical installer had...

I did a google search for that phrase, and I found this bit of info from a Gentoo forum It's from 2002, but may still apply:

> I have a newly-obtained IBM PC 300PL (PII 400) . When I tried booting off the Gentoo 1.2 CD, I got exactly this error. I knew booting from the CD drive worked, as I was able to boot off a Debian CD. Also, I knew the CD-R was good because I could boot my Dell desktop from the CD. From another thread, I found out that bootable CD-ROMs have two modes: emulation and no-emulation. If in emulation mode, the boot image on the CD is limited in size to that of a floppy. In no-emulation, it is not so limited. Apparently, the IBMs from the 1998-1999 era had BIOSes that did not support the no-emulation mode. Also, apparently, the Gentoo CD requires no-emulation. Fortunately, IBM is very good about supporting its machines, and
I was able to download a BIOS flashing program. After I flashed the BIOS, everything worked fine, and I was able to bboot the Gentoo CD.

So: if you have this trouble, it's not the CD, nor the CD-ROM, it's likely your BIOS (particularly if you have an IBM from this era). Get a BIOS upgrade - if it's an IBM, go to their support page and look up your model.

[http://forums.gentoo.org/viewtopic.php?t=8521](http://forums.gentoo.org/viewtopic.php?t=8521)

---

### Post by lilro on 2007-05-31
how are you burning it? do exactly as [this]("https://help.ubuntu.com/community/HowToMD5SUM") says, then [this]("https://help.ubuntu.com/community/BurningIsoHowto"). hope it helps

---

