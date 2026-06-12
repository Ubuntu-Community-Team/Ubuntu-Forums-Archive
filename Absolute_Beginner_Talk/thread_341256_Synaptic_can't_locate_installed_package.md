---
title: "Synaptic: can't locate installed package"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by beaulanger on 2007-01-18
[COLOR="Red"]**_SOLVED _**[/COLOR] Disregard and thanks. 

From Synaptic I selected, and presumably installed, the calendar program "gdeskcal". It doesn't show up anywhere and I  can't locate it. I've run "Search For Files" with the search "gdeskcal" and nothing shows. In the File Browser and going through all the folders I did find in usr\bin a file by that name but opening it up was some kind of text file. 

Okay, I just went into Synaptic, searched and found the installed gdescal and looked at its properties. I did see a path to it usr\share\gdeskcal but there is no executable.

The file systems on several other distros I have tried have also mystified me. When I try and install something from Synaptic I can't locate it and eventually get so frustrated I dump the distro and go back to WinXP. I have done a lot of searching on this problem but have not found any answers. Every time I install something from Synaptic and can't locate it I go back in and and uninstall it. 

I can install from Add/Remove.

Any help would be appreciated.

---

### Post by taurus on 2007-01-18
Gdeskcal is a python, not an actual binary program like others.  What happens when you run this from a terminal?

```
/usr/share/gdeskcal/gdeskcal
```

(It's forward slash in Unix...)

---

### Post by beaulanger on 2007-01-18
All I get is:
gDeskCal version 0.57.1
copyright (C) 2002 - 2004 by Martin Grimme
This software is licensed under the terms of the GNU GPL.

---

### Post by beaulanger on 2007-01-18
The GDeskCal IS showing up on my desktop. Sorry about that and many thanks for your very quick help on this.
Beau

Followup: Welp, the next day when I booted it was gone from the desktop so I removed it. I can't see running it from terminal anyway just to see a calendar.

---

