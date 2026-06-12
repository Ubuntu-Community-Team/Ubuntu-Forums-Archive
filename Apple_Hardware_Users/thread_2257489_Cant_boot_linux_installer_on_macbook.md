---
title: "Cant boot linux installer on macbook?"
date: 2014-12-20
forum: Apple Hardware Users
---

### Post by Jakesploder on 2014-12-20
I downloaded ubuntu 14.0.1 LTS for amd64 + mac, and put it on  a usb sitck, but when i hold the option key down to get to the boot screen, it only shows mac os, windows and the recovery disk.  How do i boot this?







Mid 2007 Macbook, Core 2 duo 2GHz, Mac OSX 10.7, 4GB of RAM, 250GB 7500 RPM HDD

---

### Post by este.el.paz on 2014-12-20
Is this for the MacBook or the G5?  Did you format the USB drive and make a boot-able drive?  If it's for the G5 you might have to read the "PowerPCFAQ" and find the instructions on using "open firmware" to boot the USB drive.  Rsavage just posted the link on the forum a few days ago, either to me or rican-linux . . . .

I also made a boot-able USB version of 14.04 Ubuntu MATE and it didn't show up on my iBook G4 using the option key--I burned a DVD and used the c key to test it out . . . .

e.e.p.

Edit: {PS: If it's for the G5 you would want the "PPC" iso . . . otherwise you should be OK with amd64.}

---

### Post by Jakesploder on 2014-12-20
its for the macbook, and it doesn't have a DVD writer, so i can't burn a DVD.(and i ran out of blank discs).I formatted the usb as mac os extended and the partition map as GUID. i also tried FAT and it did not work either.  I'm actually waiting for a hard drive thermal sensor for the g5 to be shipped from ebay, so i won't be installing linux on the G5 until that comes.

---

### Post by Jakesploder on 2014-12-20
would it be possible to use another machine to install linux to the macbook's hard drive?

---

### Post by este.el.paz on 2014-12-20
> **este.el.paz said:**
> Is this for the MacBook or the G5?  Did you format the USB drive and make a boot-able drive?  If it's for the G5 you might have to read the "PowerPCFAQ" and find the instructions on using "open firmware" to boot the USB drive.  Rsavage just posted the link on the forum a few days ago, either to me or rican-linux . . . .


Same question, did you just copy the iso to the USB or did you use an app that creates a boot-able drive?  Find the wiki on booting from USB . . . .

> **Jakesploder said:**
> i i also tried FAT and it did not work either. 

Generally in OSX Disk Utility, when I'm formatting a disk for linux I set it as FAT, but not everyone seems to agree; it's just a matter of keeping on until you find your answer.

> **Jakesploder said:**
> would it be possible to use another machine to install linux to the macbook's hard drive?

Anything is possible, you could try connecting by FW and using Target mode . . . you would just need to figure out which disk is which . . . in linux it's labeled "sda6" or "sdax" (some number) . . . you just have to be very clear which is which.  Use the installer version og GParted and look at the table with the macbook unplugged and then compare to when it is plugged in . . . see what changes.  For my own experience, installing into the computer the installer is booted in is the most simple . . . .  Perhaps buy a plug in DVD burner or borrow one . . . um, buy a DVD . . . RW type????

e.e.p.

---

