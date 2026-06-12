---
title: "Problem configuring double monitor"
date: 2010-01-11
forum: Apple Hardware Users
---

### Post by jako83 on 2010-01-11
Hi all,
this is my first post here...
I hope that someone could help me.
My macbook v 1.1 doesn't reconize my home tv as second screen, how can I do? i plug the mini-dvi cable to a scart converter but when i go to sys->preferences->monitor nothing appear :(
thank you in advance,
Bye

---

### Post by sanderd17 on 2010-01-11
Can you try to reboot with the screen plugged in?

---

### Post by jako83 on 2010-01-11
> **sanderd17 said:**
> Can you try to reboot with the screen plugged in?

Yes I did it, but nothing changed...

---

### Post by sanderd17 on 2010-01-12
It seems to be a bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/420577]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/420577")

Marko Mikulicic Has the solution of executing
```
xrandr --newmode 1680x1050 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -HSync +VSync
xrandr --addmode DVI1 1680x1050
xrandr --output VGA --off --output DVI1 --mode 1680x1050
```

in the terminal.

If this works you can make a script of it and execute it at startup if you use the second screen a lot.

---

