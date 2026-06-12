---
title: "Display adapter difficulties"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by tc21931 on 2007-12-12
I'm trying to install Gutsy Gibbon on my child's computer, and I cannot get video to work.  Mobo has onboard video, but I have in the past used an add-on nvidia card for my display.  At boot menu display is fine; however, during startup of live CD, I lose the display.  I tried starting with monitor connected to onboard video, and X-server appears to start, but image is complete garbage.  Is there a way to specify at boot that X should use the nvidia card instead of onboard?

---

### Post by teejcee on 2007-12-12
A very good question......and one that I would like an answer to as well.

I have experienced the same problem when I tried the live cd on a second box configured in a similar manner...ie  on board graphics with a nvidia card installed.

The screen turns the familiar brownish colour for a few seconds and then goes black and stays that way.

---

### Post by lswest on 2007-12-12
does this happen in both safe graphics mode, and the normal boot?  happens to me occasionally on my HP laptop, safe graphics mode fixes that problem though... (needs a bit more of configuring regarding the drivers afterwards, but it's not bad)

---

### Post by teejcee on 2007-12-12
Ahhhhh - yes....safe graphics mode.

I've just returned to this box to post a reply saying just that.!!!!!!!!!!

I simply booted the other system in safe graphics mode & away we went.

There were a couple of brief "flashes" on the display which worried me but all looks well now.

I'll try an install on a spare disc later to judge how gutsy runs on this higher spec'd box.

Good luck tc21931.....hope this solves your problem.

---

### Post by tc21931 on 2007-12-12
Thanks for your help, it worked enough.  X-server was unable to start, but at least I was in text mode.  Edited /etc/X11/xorg.conf changing driver and PCI address so that it pointed at my nvidia card.  Then entered *sudo startx* and went straight into graphical desktop.  As I post this, I am installing, and I'm hoping that my modified xorg.conf will be copied over; if not, I at least will be able to fix it.  Thanks for your help!

---

