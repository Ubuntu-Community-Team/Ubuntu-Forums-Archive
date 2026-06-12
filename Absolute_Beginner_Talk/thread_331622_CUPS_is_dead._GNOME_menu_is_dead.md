---
title: "CUPS is dead. GNOME menu is dead"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by polc1410 on 2007-01-04
**Problem1:** I've killed CUPS. I have no idea what i've done but CUPS will not talk at all.

localhost:631 just fails to do anything (browser never shows a fail but never shows anything)

```
sudo /etc/init.d/cups restart
```
gives:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

and
```
sudo /etc/init.d/cups status
``` gives:
Status of Common Unix Printing System: cupsd is running.

All programs hang when trying to print.

Launching GNOME or KDE print manager nearly kills the system

Not sure when the problem arose, or what I did (haven't printed for a few days.)

Recent upgrade of kernel so I've tried using older version - no different.

Anyone got any suggestions - cause I'm completely stuck.

**Second problem:**
GNOME has lost its applications launcher (M$ start Menu thingy) again suggestions to replace it would be appreciated.

---

### Post by jpeddicord on 2007-01-04
While I don't have any clue on how to fix the CUPS problem, here is how to fix the menu problem:

To add the Applications menu back to the panel, right-click on a blank space on it and select Add to Panel. Scroll down to find Menu Bar, then drag it to the space you want on the panel. That should bring it back. :)

---

