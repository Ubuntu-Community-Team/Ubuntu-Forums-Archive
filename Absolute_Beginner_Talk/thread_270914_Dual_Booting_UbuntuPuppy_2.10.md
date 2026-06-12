---
title: "Dual Booting Ubuntu/Puppy 2.10"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by bosston on 2006-10-03
Is it possible to dual boot Ubuntu with Puppy Linux 2.10?

---

### Post by kidders on 2006-10-03
You can install as many operating systems you like, as long as you can find a bootloader that knows how to handle them. You should have no problems :-)

---

### Post by Sef on 2006-10-03
Here's a link to [dual boot.]("http://users.bigpond.net.au/hermanzone/")

It's windows and ubuntu, but the basics are the same.  Just don't worry about making a fat32 file.

---

### Post by confused57 on 2006-10-03
Yes, but I think you need to create an ext2 partition before hand to install Puppy on...probably best to use the gparted live cd:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

What I did was install the Puppy grub to the root partition, then added an entry in Dapper grub to boot Puppy:

title   Puppy
rootnoverify   (hdX,X)
chainloader +1

Be sure to write down the partition number when you're creating it, so you can set up grub to boot Puppy.

I'd advise not to allow Puppy to install grub to the mbr, I did this & was unable to boot Dapper; although, you can reinstall Dapper grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

What you could do is install Puppy's grub to the mbr, write down the exact entry to boot Puppy.  Then reinstall Dapper's grub using the live cd, then add the entry to boot Puppy.

It's some options for you to consider.

---

### Post by kidders on 2006-10-04
You only need one bootloader on any system (unless you want to make more than one hard drive boot you into multiple OSs). There's no reason to reinstall grub over and over if you can avoid doing it.

---

### Post by confused57 on 2006-10-04
> **kidders said:**
> You only need one bootloader on any system (unless you want to make more than one hard drive boot you into multiple OSs). There's no reason to reinstall grub over and over if you can avoid doing it.

I agree...the OP just asked if it was possible, not how to actually dualboot Ubuntu & Puppy...hopefully, the info I provided(from experience with Puppy) can help if he tries it and runs into problems.

---

