---
title: "repairing a hard drive"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by daputerguy on 2006-04-03
I was finalizing an installation of Ubuntu when I had a power failure. Now my hard drive is not recognized by my system. I can replace the hard drive with a Win98 drive and boot with no problems. There seems to be nothing wrong with the mobo/cpu/ram etc.. only the hd w/Ubuntu partially installed.

Any suggestions will be appreciated.

---

### Post by izmaelis on 2006-04-03
I think that you should do a fresh install on the same hard disk that failed during power outage. Ubuntu install is clean, easy and _fast_!

---

### Post by az on 2006-04-03
[QUOTE=daputerguy]Any suggestions will be appreciated.[/QUOTE]

If the drive is not detected by the bios, try going into the bios settings and playing around.  Can it auto detect it from within the bios setup program?  Can you enter user values for cylinders, sectors and so forth?  Does the drive power up (audible sounds)?

---

### Post by daputerguy on 2006-04-03
The pc I'm working on is an ASUS P4T-CM mobo with a 1.3ghz CPU and 128mb RAM. The hard drive is an IBM 20 Gb Deskstar and had Win ME installed and working fine. I decided to convert the drive to Ubuntu to learn Linux. I booted with the Ubuntu cd and the install went as normal. During the re-boot to finish the install I had a power failure. When I was able to recover from the power failure, the PC would not recognise the drive, or boot up. I replaced the drive with a working drive w/ME and booted fine. There appears to be no problem with anything other than the hard drive. I entered the BIOS to try to "tweak" it but am unable to get the BIOS to even see the drive. It appears to be locked. I wonder if an incomplete installation could do this? There was a time span of about 4 1/2 hours with no power.

---

### Post by az on 2006-04-03
[QUOTE=daputerguy] It appears to be locked. [/QUOTE]

Your bios would still see the drive if the partition table was "customised".  I would guess it is fried.

That's just a guess, though...

---

