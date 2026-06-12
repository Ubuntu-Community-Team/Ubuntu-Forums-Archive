---
title: "Excruciatingly slow boot to installation CD"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by New-In-Ohio on 2007-06-07
Problem: I have a dual boot machine (Fedora2 and XP) using GRUB as the OS loader.  I want to completely overwrite the Fedora2 system with Ubuntu.  I downloaded the ISO image, burned to CD, loaded it, rebooted the machine, it went straight to the CD (never made it to GRUB) and became the most painfully slow boot up I have ever encountered.  Literally 10 minutes of CD spinning just to get the screen that has the examples icon and the install icon.  I double clicked on the install icon and (I kid you not) i went and had dinner with the family and came back to what was the beginnings of a window that may some day have installation instructions in the middle of it and then the screen went blank (probably the built in screensaver).  I did a hard reboot, removed the CD and came here to see if there is some fundamental problem with already having GRUB and trying to load Ubuntu.  If anyone knows of why this would be happening this way, please respond.  I dont want to give up on Ubuntu before I can even try it.  Thanks.  System information:  X86-based PC (eMachines - 2.67Ghz celeron w/256M RAM)

---

### Post by dbbolton on 2007-06-07
> **New-In-Ohio said:**
> Problem: I have a dual boot machine (Fedora2 and XP) using GRUB as the OS loader.  I want to completely overwrite the Fedora2 system with Ubuntu.  I downloaded the ISO image, burned to CD, loaded it, rebooted the machine, it went straight to the CD (never made it to GRUB) and became the most painfully slow boot up I have ever encountered.  Literally 10 minutes of CD spinning just to get the screen that has the examples icon and the install icon.  I double clicked on the install icon and (I kid you not) i went and had dinner with the family and came back to what was the beginnings of a window that may some day have installation instructions in the middle of it and then the screen went blank (probably the built in screensaver).  I did a hard reboot, removed the CD and came here to see if there is some fundamental problem with already having GRUB and trying to load Ubuntu.  If anyone knows of why this would be happening this way, please respond.  I dont want to give up on Ubuntu before I can even try it.  Thanks.  System information:  X86-based PC (eMachines - 2.67Ghz celeron w/256M RAM)
if the liveCD doesn't work, you should try the alternate installer cd.

---

### Post by NeoLithium on 2007-06-07
The LiveCD doesn't generally load with only 256MB of ram, because it puts the operating system basically into your RAM and spins the CD.  If you wanted to install it, dbbolton is correct that you should grab the alternate install CD.  For a setup that would remain relatively quick with that amount, check out Xubuntu, or Fluxbuntu, which use XFCE or Fluxbox respectively, and maintain a decent speed with that type of setup.

Hope this helps.

---

