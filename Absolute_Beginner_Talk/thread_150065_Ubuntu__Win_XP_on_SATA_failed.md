---
title: "Ubuntu / Win XP on SATA failed"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by jkeyes0 on 2006-03-25
I tried following the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=149877") to install Ubuntu from Windows. Somewhere in the install process however, I managed to screw my system up, and now I'm getting an "Error loading operating system" on startup (after detecting hardware, before grub or the windows boot loader would load).

I believe the error may lie in the partitioning process. It sets the windows partition as non-bootable. Possible?

I'm reinstalling from CD now, having set the windows partition to bootable, and we'll see what happens there.

Any suggestions otherwise?
I've been an ubuntu user for over a week now (typing this on my ubuntu laptop) and I'm loving it. I've learned a LOT, and I've even gotten myself out of some sticky situations with X not starting and what not, but this is one I'm kinda stumped on. I'd hate to have to format the drive and start over...

If nothing else, I can install Ubuntu on my secondary drive (primary is SATA, secondary is IDE) and force the system to boot from it. That should get me up and ready to go...I think (again).

---

### Post by jkeyes0 on 2006-03-25
Update: I ran the install from the CD, set the XP partition flag to bootable, and after the install finished, and the system booted, it gave me the option to boot into XP (from the NT boot loader, not the Grub one) so I'm in XP for now.
Time to delete the partitions for Ubuntu, clean up the NT Boot Loader, and attempt an install again. (I'm a glutton for punishment)

---

