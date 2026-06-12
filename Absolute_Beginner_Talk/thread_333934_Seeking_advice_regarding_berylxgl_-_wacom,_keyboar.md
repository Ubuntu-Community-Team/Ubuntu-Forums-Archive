---
title: "Seeking advice regarding beryl/xgl - wacom, keyboard"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-08
I recently installed Beryl following various different guides and I'm not sure I got it all right.

Should I try to correct xgl (or what ever the problem is) or should I reinstall everything using aixgl?

Situation:
Ubuntu 6.10, asus w1j ati x1600 1680x1050 (have been through the usual driver installation)
Everything appears to work fine - in general, Login is ok (can chose between gnome and xgl). I can double click the Beryl icon and beryl runs fine.

But:
1. Wacom problem:
During startup - login my wacom (intous2 a6) is recognized with correct screen resolution. I guess that it is assigned to the correct /dev/input/event number. After login it usually no longer work with correct resolution - regardless of which session I log in to.
I correct this by first finding the event number for wacom pad (move pen after command):
```
sudo cat /dev/input/event1
... event2
etc 
```
Then change the entries in xorg.conf, then restart desktop (Ctrl-Alt+Backsp)

2. Keyboard problem: (forgot to test before login - sorry)
After login my keyboard is no longer correct I change that with the command
```
sudo xmodmap /usr/share/xmodmap/xmodmap.dk
```

How to fix these issues permanently?

---

