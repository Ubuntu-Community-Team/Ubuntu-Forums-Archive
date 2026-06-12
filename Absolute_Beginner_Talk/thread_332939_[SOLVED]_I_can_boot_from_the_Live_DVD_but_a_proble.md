---
title: "[SOLVED] I can boot from the Live DVD but a problem after that."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-01-06
After playing around with the BIOS for a while, I could boot from the Live DVD (I had it disabled under secondary slave so it did not matter if I changed the boot sequence)

After that when I try to either run the CD or check the CD for defects I get this error:

Uncompressing Linux... Ok booting the kernel.
[4294670.40000]. . MP-BIOS bug : 8254 timer not connected to IO-APIC


I got this DVD from the book "Moving to Ubuntu Linux" by Marcel Gagné.

If nothing else works, I could just burn the latest version of Ubuntu to a regular CD and then try that,(but would I use version 6.06 or the new 6.1?) but I'm guessing there is some useful software on the DVD which makes it a little over 3 gigs.

---

### Post by jvc26 on 2007-01-06
May I ask what you did with the bios? Did you just go and set the first boot drive to boot from cdrom? Or did you do something a little more crazy?
Il

---

### Post by SilverDragon on 2007-01-06
On the first part of the BIOS. I disabled(set it to none) the Primary Slave, because I don't have one and the secondary master, because I can only change that to the cd-rom drive and I'm using the DVD-rom drive which is under the Secondary Slave. Also, I enabled S.M.A.R.T. on my hard drive. In addition, under the boot sequence, I disabled the removable device because it was on top, set the ATAPI-MO(I think thats what its called) to boot from the DVD-ROM drive and put the hard drive under that. I also disabled the Full Screen Logo? which is under Boot options.

---

### Post by SilverDragon on 2007-01-07
Okay I loaded up the BIOS default settings and only changed it to boot from the DVD before the Hard drive. Then I tried checking the cd for defects and it came up with the same error as before.

Also, I had another problem which would load up for a second, saying:

No Drive Attached to the FastTrack Controller. Bios is not installed.

I resolved this problem, thinking maybe it was related to the error message from earlier, by disabling ATA Boot ROM(or something along those lines, because I had to play around with it because the fixes I found only lead me to that general area, but I didn't have the option they wanted me to use)

Either way I still have the original error and am not sure how to fix it.](*,)

---

### Post by SilverDragon on 2007-01-08
Well the original error:

Uncompressing Linux... Ok booting the kernel.
[4294670.40000]. . MP-BIOS bug : 8254 timer not connected to IO-APIC

has been fixed (maybe not permanently) by booting up with the noapic boot parameter.

Ubuntu starts to load up a little more than it did before, but then I get this error:

Uncompressing Linux... Ok booting the kernel.
[4294805.102000] Buffer I/O error on device hdd, logical block 23723

I did a search on this problem and this person's thread is similar:
[http://www.ubuntuforums.org/showthread.php?t=320374](http://www.ubuntuforums.org/showthread.php?t=320374)

But a main difference is it seems as if that person already has Ubuntu installed.

Any help would be appreciated :-)

---

### Post by Duck2006 on 2007-01-08
What type of system are you trying to run the setup on?

---

### Post by SilverDragon on 2007-01-08
Windows XP Professional Service Pack 2 (build 2600)
1.30 gigahertz AMD Athlon XP
WDC WD1200JB-00DUA3 [Hard drive] (120.03 GB) -- drive 0, s/n WD-WMACM1350590, rev 75.13B75, SMART Status: Healthy
1536 Megabytes Installed Memory
Motherboard: ASUSTeK Computer INC. A7V8X REV 1.xx
Videocard: NVIDIA GeForce4 Ti 4200v

I think that's all the important stuff.

---

### Post by Duck2006 on 2007-01-08
It may be the video card where your problem lay. Can you run the alternate CD on the system, if so it will be the way to go and then you can set your video card after.

---

### Post by SilverDragon on 2007-01-08
I'll do that. I'm downloading the alternate CD now to burn to a CD :-)

I have a question though. I think I saw something about checking the CD after burning it? I'm not sure but I think it was like checkdum5? or something like that? eh thats probably not very  specific. Well if anyone can figure out what that is, how would I check it?

---

### Post by c-ron on 2007-01-08
Try booting with some special kernel boot parameters.
Hit the Esc key at the startup options on the live dvd, and select OK to the warning that pops up about leaving the graphical mode. At the "boot:" prompt, try typing "live noapic nolapic" (without the quotation marks) and press enter, and then post your results. Thanks!

---

### Post by SilverDragon on 2007-01-08
My original error went from:

Uncompressing Linux... Ok booting the kernel.
[4294670.40000]. . MP-BIOS bug : 8254 timer not connected to IO-APIC

to

Uncompressing Linux... Ok booting the kernel.
[4294805.102000] Buffer I/O error on device hdd, logical block 23723

when I use the "noapic" boot parameter, and it changes to 

Uncompressing Linux... Ok booting the kernel.
[4294805.240000] Buffer I/O error on device hdd, logical block 23723

When I use the "live noapic nolapic"

What is the difference between "noapic" and "live noapic lapic" anyways?

---

### Post by SilverDragon on 2007-01-09
Well I used the alternate CD and used the noapic boot parameter and it worked =)

Anything I should do first? Well actually I should probably follow the book I got for Ubuntu huh? :-)

Actually im gonna work on dual booting Windows and Ubuntu off two hard drives now.

---

