---
title: "[SOLVED] Error copying files on installation"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by kulotzy on 2008-03-12
Hi there...

My XP was eaten up due to some virus and i was forced to delete a lot of vital files... in a nutshell: it crashed i can no longer boot it. Luckily, i was able to purchase an external hard drive and backup my files before it happened...

Now, ive been working on getting Ubuntu installed as my OS for 3 days now... still no luck. First it wouldnt boot at all, turns out i burnt it incorrectly, and **now im having issues in installing it... it stopped at 59% the first time, then froze at 5% the second time, and at 34% the third time**

i keep getting this message:
[I]

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/I]


I ran the CD check from the Ubuntu boot menu thing and it says its fine... Im not sure if i burnt it incorrectly or if im missing files or.........

PC is a Compaq, Athlon, 160GB HDD, DVD/CD and CD drives... i think its more than capable right?

Im currently downloading the "alternate" Ubuntu CD...

Any ideas? Help would be very appreciated... thanks..

---

### Post by PmDematagoda on 2008-03-12
At what speed did you burn the Live CD?

---

### Post by kulotzy on 2008-03-12
> **PmDematagoda said:**
> At what speed did you burn the Live CD?

I used Roxio Media Creator at default/normal speed of burning discs, i unfortunately dont remember...

Also... what is Gutsy or Grub?

---

### Post by PmDematagoda on 2008-03-12
GRUB(GRand Unified Bootloader) is the bootloader for Linux.

Also, try burning the CD at a speed of 4x or less and then see if the problems are solved.

---

### Post by kulotzy on 2008-03-12
> **PmDematagoda said:**
> GRUB(GRand Unified Bootloader) is the bootloader for Linux.

Also, try burning the CD at a speed of 4x or less and then see if the problems are solved.

Thank you, i will try that. I will post update if anything happens.

---

### Post by kulotzy on 2008-03-12
After reburning the .iso file at x3.8 speed.. i was able to boot Live CD and run the installer from the desktop... it was able to progress as far as to 74% until i got another error:

[Errno 2] No such file or directory: '/rofs/usr/src/linux-headers-2.6.22-14/include/asm-m68knommu/spinlock.h'

What am i doing wrong?? Gah

---

### Post by kulotzy on 2008-03-12
Perhaps i should try again, if it still doesnt work, i might have to burn the Alternative CD and use that instead... its at 80% now.

Edit. I also noticed that in the desktop, there is now a file called /target... im not sure what the significance of that is but it wasnt there prior to the failed installation attempt

---

### Post by kulotzy on 2008-03-12
> **PmDematagoda said:**
> GRUB(GRand Unified Bootloader) is the bootloader for Linux.

Also, try burning the CD at a speed of 4x or less and then see if the problems are solved.

It worked!!! It failed the first time but it worked after that. I cant believe the solution was that EASY! Thank you.

---

