---
title: "Dual boot system 7.04 and 7.10"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Thies on 2007-11-26
Hi folks!

I'm running a fine Feisty (7.04) solo, non-dual-boot system and would like to try Gutsy (7.10) on a 2nd harddisk. Is there any risk to install Gutsy the other disk? How will this impact the GRUB? Just looking for some advice before messing up my system. Thanks!

/Thies

---

### Post by rsambuca on 2007-11-26
You will be fine.  If you want to keep Feisty's grub in control of the bootup, I recommend installing the Gutsy Grubloader (at the last stage of installation) to the Gutsy partition, not the mbr.  Then add the chainloading entry to the Feisty menu.lst.

---

### Post by Thies on 2007-11-26
> **rsambuca said:**
> [...]Then add the chainloading entry to the Feisty menu.lst.
Thanks for the help. But your last sentence is out of my Linux knowledge. Could you please explain this a bit more?
/T.

---

### Post by rsambuca on 2007-11-26
No problem.  When installing Gutsy to the second hard drive (I recommend the Alternate CD, by the way), you will direct the installer to use the second hard drive.  At the very last step of the installation, it will say something to the effect :  grub will be installed to hd0.  This will overwrite your Feisty grub, which I assume you do not want for now.  You can change the location from hd0 to (hd1,0), if that is where you installed Gutsy to.  Then, you just add an entry to your Feisty grub:

title Gutsy
root (hd1,0)
chainloader +1

Then you can go from Feisty to Gutsy.

---

### Post by Thies on 2007-11-26
> **rsambuca said:**
>  [...] You can change the location from hd0 to (hd1,0), if that is where you installed Gutsy to.  Then, you just add an entry to your Feisty grub:

title Gutsy
root (hd1,0)
chainloader +1

Then you can go from Feisty to Gutsy.

Bingo ... now I got it! :) Great!
/T.

---

