---
title: "[SOLVED] Cursor disapears since going to 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-10-21
I remember back on my old laptop that when I had put in the OpenChrome driver I had to specify something in the xorg.conf file (something to the effect of software cursor) to correct having my cursor disappear sometimes.  Well, now on this clunky old desktop (Diamond V770??) - uses the nVidia tnt2 driver - the mouse disappears sometimes again.  It's like it goes "behind" the thing I want to click.

Any ideas?

Thanks!:)

---

### Post by anewguy on 2007-10-21
Though it wasn't needed in 7.04, for some reason I had to put the following on the adaptor section of xorg.conf to get my cursor/mouse pointer back:

Option   "SHcursor"  "true"

---

