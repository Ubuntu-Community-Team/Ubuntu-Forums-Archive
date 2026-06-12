---
title: "system locked"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by La.Cutter1 on 2008-03-10
clicked on screen savers :Molecules:. Locked up  system.  Hard boot recovered but everytime I click on screen savers, I cannot move from Molecules and the computer locks up again...any ideas??

---

### Post by ukripper on 2008-03-10
disable screensaver

---

### Post by red_Marvin on 2008-03-10
Press alt+f2, type *gconf-editor* and press ok.
When the program starts navigate to apps->gnome-screensaver.

**Alternative 1: To set a black screen as the screensaver**
Find the key *mode*, double-click and change its value from *single* or *random* to *blank-only*.
Also double-click on *theme* and remove all values in the list.

**Alternative 2: To use set a single screensaver that doesn't crasch the computer.**
Find the key *mode*, double click and change its value to *single*.
Also double-click on *theme* and remove all values, and then add the value *screensavers-* followed by the screensaver name (no spaces).

**Alternative 3: To choose between a list of random screensavers that doesn't crasch the computer.**
Find the key *mode*, double click and change its value to *random*.
Also double-click on *theme* and remove all values, and then add all the screensavers you want as separate values, just as in alt 2.

To find out which screensavers crash your computer might require some trial and error though.

---

