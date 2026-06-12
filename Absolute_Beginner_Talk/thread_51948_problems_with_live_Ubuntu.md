---
title: "problems with live Ubuntu"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by dross on 2005-07-25
Hi,
I am trying to use the live version of Ubuntu Hoary...my machine (Dell Dimensions xps  
450 previously running Windows 98) boots the cd fine, but when I get to the gui nothing much really happens: the mouse cursor moves but periodically freezes up, and using the keyboard or clicking the mouse does nothing.  Anybody else have this problem?

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=dross]Hi,
I am trying to use the live version of Ubuntu Hoary...my machine (Dell Dimensions xps  
450 previously running Windows 98) boots the cd fine, but when I get to the gui nothing much really happens: the mouse cursor moves but periodically freezes up, and using the keyboard or clicking the mouse does nothing.  Anybody else have this problem?[/QUOTE]

Do you just go to a brown screen?

---

### Post by dross on 2005-07-26
I'm not sure if "brown screen" is a specific term...the screen was brown, but not as in "brown screen of death" (pardon the windows reference).  It looked like a desktop gui.

Could ACPI be the problem here?  I'm away from my machine at the moment, so I can't try disabling it right now, but was wondering if anyone had any thoughts.   :smile:

---

### Post by dross on 2005-07-26
OK, so I tried the live cd on my laptop (Dell Inspiron 1150 running winXP) and it is working great!  I'm not too worried about running the live CD on my old Dell desktop (the box that I originally posted about), but I would like to do a full install of Ubuntu on it.  Considering that the live cd crapped the bed on that machine, do you think there is anything that I should look out for when doing the full install??  Thanks!   :smile:

---

### Post by poofyhairguy on 2005-07-26
[QUOTE=dross]OK, so I tried the live cd on my laptop (Dell Inspiron 1150 running winXP) and it is working great!  I'm not too worried about running the live CD on my old Dell desktop (the box that I originally posted about), but I would like to do a full install of Ubuntu on it.  Considering that the live cd crapped the bed on that machine, do you think there is anything that I should look out for when doing the full install??  Thanks!   :smile:[/QUOTE]

At the first screen type this:

> linux acpi=off noacpi

then hit enter and start installing.

---

