---
title: "Installing XP On Seperate Sata"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by spyd3r on 2008-04-09
I have 710 on one SATA and i want to install XP on a second SATA drive that i have.  What is the best way to go about this?

---

### Post by hurtstotalktoyou on 2008-04-09
Hmm.  This has the potential for problems.  Generally speaking, you want to install XP on the primary drive C:.  However, I'm guessing Ubuntu is already installed there.  This means you'll have to change Ubuntu to a secondary channel, which could disrupt its functionality.  You therefore might want to consider a fresh install of both OSes.

However, if you want to avoid this, and try to preserve your current Ubuntu install, here's what I suggest:  Open up your case and physically disconnect all drives but the one intended for XP.  Then just install XP on that drive, and once you're finished, physically reconnect the other drive(s).

You'll also have to re-install grub, instructions for which are found [here](http://ubuntuforums.org/showthread.php?t=224351).

Good luck!

---

