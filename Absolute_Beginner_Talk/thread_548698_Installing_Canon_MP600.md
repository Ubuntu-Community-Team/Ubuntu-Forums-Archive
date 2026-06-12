---
title: "Installing Canon MP600"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by codeking on 2007-09-11
I tried to get my Canon MP600 working on Kubuntu Fiesty using tzahov's instructions at [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751).  Everything worked, but I didn't get any response when I entered in sudo ln - s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3 through sudo ldconfig.  Then I entered sudo /etc/init.d/cupsys restart.  I checked to see what the next instruction is and it said something to do with the GNOME panel, but I don't have GNOME because I'm using Kubuntu.

---

### Post by mostwanted on 2007-09-12
> **codeking said:**
> I tried to get my Canon MP600 working on Kubuntu Fiesty using tzahov's instructions at [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751).  Everything worked, but I didn't get any response when I entered in sudo ln - s /usr/lib/libpng12.so.0.15.0 /usr/lib/libpng.so.3 through sudo ldconfig.  Then I entered sudo /etc/init.d/cupsys restart.  I checked to see what the next instruction is and it said something to do with the GNOME panel, but I don't have GNOME because I'm using Kubuntu.

Most Linux command-line programs only output text if an error has occured so your *sudo ln* was fine.

As for the Gnome-specific instructions, just find the equivalent in the KDE menu (possibly inside something called Kubuntu control panel, KDE contol panel, or similar) and add your printer trying to accomodate for the difference in graphical interface. I'm on Windows right now, so I can't be more specific, sorry.

---

