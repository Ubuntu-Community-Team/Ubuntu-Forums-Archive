---
title: "Unistall Samsung Universal Print Driver"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by jrich1 on 2008-01-27
Ubuntu Pals:

I am a bit of a newbie at this, so please bear with me.  I managed to install the Samsung ML-2510 universal print driver on Feisty.  I just upgraded to Gutsy.  I want to uninstall this driver, and just try a postscript driver because I think the Samsung driver is preventing me from using a scanner.  Now, there is a menu item in the applications pull down menu to uninstall the Samsung package, but when I click on it, it tells me I must be root.  I searched the forums and found a thread that talks about how to uninstall by command line, but I just couldn't find the right folder.  The Samsung driver is apparently in the cdroot folder, but I cannot find such a folder.  How do I go about uninstalling this driver?

---

### Post by dndrich on 2008-01-27
We solved this by finding the uninstall shell in the Samsung folder which was in the home folder.  Problem solved by running Nautilus in root, and running the uninstall.

---

