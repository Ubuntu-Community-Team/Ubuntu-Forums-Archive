---
title: "boot.ini infinite loop"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by njparton on 2006-09-26
Hi,

I've just (almost) successfully followed the directions on this page:

[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

to use bootpart to create a bootsect.lnx file and add the appropriate entry to the boot.ini file windows uses to boot, hopefully allowing me to dual boot ubuntu and XP without using grub (which I couldn't get to work). Grub is installed on root partition of my ubuntu installation, not the MBR of my windows HDD.

However, although windows continues to boot correctly, when I select the ubuntu entry in the boot menu, the screen goes black and then returns straight back to the NTLDR boot menu. I could sit there for all eternity in an infitite loop.

I have windows installed on a SATA HDD and Ubuntu installed on a seperate IDE HDD all of it's own.

Where do I start to diagnose the cause of this problem?

Edit: I've just made sure the main ubuntu partition is active using Partition Manager in windows and this didn't help. Help!

---

### Post by njparton on 2006-09-26
Can NTLDR boot a primary partition on another hard disk? Or can it only boot another partition on the same hard disk?

Picking at straws here :-k

---

### Post by njparton on 2006-09-27
Someone must have encountered this and solved it?

---

