---
title: "Mouse problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by andypandy99 on 2007-08-02
I accidently unplugged my mouse and when I plugged it back into the USB ubuntu doesn't seems to recognize it. What shall I do to solve the problem? My mouse is raptor-gaming.

---

### Post by zeekay on 2007-08-02
Tried restarting the PC already?

With the keyboard you can press "Alt+F1" and search through the menus to restart it.
If it still does not work, you could try testing some modifications at xorg.conf, in my opinion.

---

### Post by asmoore82 on 2007-08-02
open a terminal; unplug the mouse and plug it back in, then run ...
```
~ $ dmesg | tail
```
and post the output if its still not working...

---

### Post by kraventhearcher on 2007-08-05
HI, Im having a similar problem.
I ran the diagnostic you suggested and here&#347; what I got.
Well, I cant$ really cut and paste without a mouse, (or can I?) so I´ll just say that what I see is describing bluetooth activity and it&#347; a standard ps2 socket on an old HP box.

i.e.: HCI device and connection manager initialized 

any way to cut and past from the terminal to firefox would be keen.

---

### Post by kraventhearcher on 2007-08-05
Here&#347; a screenshot of what Im seeing.

---

