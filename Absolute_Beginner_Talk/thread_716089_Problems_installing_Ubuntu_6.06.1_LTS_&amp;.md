---
title: "Problems installing Ubuntu 6.06.1 LTS &amp; ???"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by dgdeckard on 2008-03-05
I have downloaded ubuntu-6.06.1-desptop-i386.iso, have confirmed it with md5sum and burned it to a CD. I am trying to install to an old Compaq P200 MMX, 256M RAM...was running Win 98 just fine...

Is this distribution too much for this machine?

I am starting with a newly reformatted hard dive, for a clean install with no partitions.

The Live CD comes up and tries to install, with mouse control and progress indicated,  but CD drive access stops and the system freezes after so long, with just the unresponsive mouse pointer on screen and can't eject CD.

One attempt, it got as far as to display a Ubuntu graphic that said "Window Manager"...with a frozen mouse pointer and the CD drive constantly accesssing...

It never got to the Demo.

I tried the Memory test and it ran fine with no errors.

I also tried testing the CD for errors and found the following:
Mismatches for some USB driver and a RAID controller?

[619.9873887] SQUASHFS error: Failed to allocate fragment cache block
[619.987820] SQUASHFS error: Unable to read page block 2c207c5, size65f2

I don't know if I just got a bad copy or if something is wrong with my machine, but it seems to run fine on my other PC.

Thanks in advance.

---

### Post by dstew on 2008-03-05
Probably you have a bad burn. It sounds like your .iso file was OK, but to burn an image you need to be extra careful. The main thing is to burn slow, 4x maximum. Also, good quality CD-R's are recommended.

Sometimes, a CD with a marginal burn will be readable by some CD-ROM drives, but not others. If you get errors on the CD integrity test, it is likely that it will not run properly.

An interesting experiment would be to do the CD integrity test in the computer in which it runs fine. I bet it will come back clean. That means there is a difference in the drives ability to see the bits on the disk.

You might also try to clean the drive lens on the drive that is not working well.

---

