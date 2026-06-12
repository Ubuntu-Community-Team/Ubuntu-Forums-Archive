---
title: "Compiz on ATi Raedon x1600"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-12-13
Just got Ubuntu installed on the family computer, and now I need to know how to enable Composting, to use Compiz. Any link or help would appreciated :) And I am using the proprietary drivers because they give better FPS, I still use this computer for gaming abit...

---

### Post by elliotjreed on 2007-12-13
Install the XGL (or XGL-Server) package from synaptic

Then go to appearance and enable the effects (it's on the last tab)

---

### Post by TidusBlade on 2007-12-13
Only found xserver-xgl, didnt work, ill check the Ubuntu Package search.
EDIT: Checked the package search, didnt find it there :(

---

### Post by elliotjreed on 2007-12-13
It may be that the drivers are not in use...

try:-

sudo dpkg-reconfigure xserver-xorg

... and select the fglrx driver

Keep the xserver-xgl installed, as this is essential to compiz.

With me, and a simmilar driver and card, the desktop effects would not enable, so I just kept clicking! Eventually it got the message, and now works perfectly!

but try the reconfigure command above! Worked for me in the most annoying situation!

If you mess it up, run the command again - selecting your previous driver

---

