---
title: "Can NTLDR boot a different hard disk?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by njparton on 2006-09-27
Hi,

I've just (almost) successfully followed the directions on this page:

[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

to use bootpart to create a bootsect.lnx file and add the appropriate entry to the boot.ini file windows uses to boot, hopefully allowing me to dual boot ubuntu and XP without using grub (which I couldn't get to work either). Grub is installed on the root partition of my ubuntu installation, not the MBR of my windows HDD.

However, although windows continues to boot correctly, when I select the ubuntu entry in the boot menu, the screen goes black and then returns straight back to the NTLDR boot menu. I could sit there for all eternity in an infitite loop.

I have windows installed on a SATA HDD and Ubuntu installed on a seperate IDE HDD all of it's own.

Where do I start to diagnose the cause of this problem?

I've made sure the main ubuntu partition is active using Partition Manager in windows and this didn't help. Please help!

---

