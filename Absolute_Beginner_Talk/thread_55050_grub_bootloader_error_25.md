---
title: "grub bootloader error 25"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by Trops on 2005-08-07
after trying the live cd of ubuntu I liked it and decided to go ahead and install it on my second hard drive (10 gig) install went well with no problems, I chose to install grub to the MBR and then rebooted to finish the installation, all I get is: loading grub 1.5.
starting grub (about 30 seconds)
error 25

I have seen a few postings about people having problems with grub but can't find any that actually remedy it.

1 more thing is it possible to remove previous postings that are unanswered now I have sorted that particular problem?

thx


seems no answers to this problem I can fully understand so I guess it's back to MS for me :-(

---

### Post by tonysathre on 2005-08-10
it sounds like an error with your menu.lst file

---

### Post by Trops on 2005-08-10
I couldn't get it sorted on the 2nd hdd but after partitioning my 1st hdd and installing on that it's fine so I formatted my 2nd hdd as fat32 and mount it on startup so I can read and write to the space from both xp and ubuntu, not what I set out to do but it works.

---

### Post by DaveQB on 2006-01-26
So from my reseaching, the only way to fix "Error 25" from grub is to install /boot on hda.  Can people confirm or deny this ???

Seems such a "Microsoft" fix; really cumbersome.

Anyway to get LILO installed during the install ??  I was thinking maybe using the Advanced install method you could select packages (including LILO) ??

---

