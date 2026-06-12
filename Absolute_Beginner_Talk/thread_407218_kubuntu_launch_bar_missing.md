---
title: "kubuntu launch bar missing"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by califman831 on 2007-04-11
The bar at the bottom of my screen is gone, i tried restoring the kubuntu desktop under gnome but still nothing.  Any help would be appreciated thanks.

---

### Post by mexlinux on 2007-04-11
> **califman831 said:**
> The bar at the bottom of my screen is gone, i tried restoring the kubuntu desktop under gnome but still nothing.  Any help would be appreciated thanks.

Try renameing this file, in order to let KDE restore defaults
~/.kde/share/config/kickerrc

---

### Post by califman831 on 2007-04-11
Thats the ticket, thanks

---

### Post by tehdon on 2007-05-10
Instead of renaming the kickerrc file, you can open it with vi, find the [GENERAL] section, and modify the AutoHidePanel=true to AutoHidePanel=false. Save the file, then, 'sudo killall kicker && kicker &'

The quickest way to get a terminal with kubuntu, assuming you don't have a shortcut on your desktop, is pressing alt-f2, 'xterm'

After you get your kicker back, you can re-edit your preferences.

---

### Post by ebenezum on 2007-07-29
I am experiencing the same problem. First i checked the contents of ~/.kde/share/config/kickerrc and in [General] section i already have <AutoHidePanel=false>. I also tried renaming ~/.kde/share/config/kickerrc ,to no avail. Still missing kicker panel. 
Any other suggestions?

Update.

Checked if KDE recreates the kickerrc file after reanming it and rebooting. Result is that i only have the kickerrc.backup file that i created, no new kickerrc file.

---

