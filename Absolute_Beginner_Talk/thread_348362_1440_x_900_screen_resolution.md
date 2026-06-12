---
title: "1440 x 900 screen resolution"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by mgdell on 2007-01-28
I have a ViewSonic VA1912wb wide screen LCD and I can't for the life of me figure out how to get the resolution to work on Ubuntu.  I do the xserver config just as someone else posted before. When I reboot, it either says the sync range is out of range and or it just comes up 1024 x768. 

I know my video card works at that res ( an Intel onboard card ) because it works in Windows.

What next?

Thanks!

-Mike:confused:

---

### Post by Happy_Man on 2007-01-28
Do you have the latest drivers? Sometimes, that can be pretty important.

---

### Post by mgdell on 2007-01-28
I think I have the latest drivers.. Not sure.. how do I tell? 

I'm really new at this :)

-Mike

---

### Post by Blutack on 2007-01-28
intel onboard! Try installing 915resolution
Intel graphics cards have a bug which means xorg thinks they cannot be pushed about 1024/768.  915 resolution fixes it!
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
to install it use sudo aptitude install 915resolution

---

