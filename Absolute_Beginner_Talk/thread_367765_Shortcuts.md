---
title: "Shortcuts"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by kryos on 2007-02-22
Thanks to all.

---

### Post by netkid91 on 2007-02-22
Check the mouse, is the cable frayed, mouse broken, or not plugged in correctly?  If not, try it in a different PC to check and see if it's good.  If it doesn't work on the other machine it's either a BIOS or X configuration issue.

---

### Post by kryos on 2007-02-22
Mouse worked fine under W and PCLOS.  Not a damage or BIOS problem.  It is a serial mouse so trying it on another machine is not currently possible.  How would one configure X at this point?  I can get to the CLI but am relatively clueless from there!

---

### Post by netkid91 on 2007-02-22
In PCLOS, look at /etc/X11/xorg.conf and find the inputdevices section that defines your mouse, do the same in Ubuntu, set the Ubuntu section the same as the PLOS one (particularly the Driver line) and it should work fine.

---

### Post by kryos on 2007-02-22
PCLOS is no longer installed.  What is the text editor in Xubuntu?  I can sudo gedit ok in U but need it for X to view xorg.conf, no?

---

### Post by netkid91 on 2007-02-22
The text editor in Xubuntu is mousepad, however if you are having mouse issues I'd suggest using nano from the CLI (vi is kinda broken in 6.10 for some reason.....and emacs sucks).

---

