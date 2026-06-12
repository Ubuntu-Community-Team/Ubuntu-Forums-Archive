---
title: "screen resolution issues"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by try2lickurelbo on 2007-06-23
I just installed ubuntu onto an old PII laptop and installation went beautiful and everything.  When I start the system though, the screen resolution is set to 640x480, and I can't seem to change it!  I went into /etc/X11/xorg.conf and put in "1024x768" and everything, but it still can't change on the screen resolution app.

---

### Post by try2lickurelbo on 2007-06-23
i forgot to mention that when it boots the splash screen is an adequate resolution, its just when it gets to the login screen that it goes to the horrible resolution.

---

### Post by bigken on 2007-06-23
try this in a terminal sudo dpkg-reconfigure -phigh xserver-xorg use the space bar to select your resolution

---

