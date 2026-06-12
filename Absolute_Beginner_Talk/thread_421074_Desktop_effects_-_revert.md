---
title: "Desktop effects - revert"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2007-04-24
Hi. Yesterday I installed Feisty on a friends PC. 
Hi is liking it a lot, but his video card does not support "Desktop Effects" quite well.
After activate it, a message appears saying something about his video card (unfortunately I was too fast in clicking in the OK !!!), and a new driver was downloaded and installed!

But the "Desktop Effects" did not work smoothly as they should and we disable it.

The problem is that even after disabling the Effects, the video refresh stills too slow. And this only occurs after we activate the "Desktop Effects" on the first time. So, this is most probably due to the new installed driver.

How can I revert to the driver installed by default?

Thank you in advance

(Fortunately, in my PC it works great!!!!! continue the very good work)

---

### Post by mikeyphi on 2007-04-24
Can't answer about removing the unknown driver BUT you might be able to change the refresh rate through System - Preferences - Screen Resolution.

---

### Post by freebird54 on 2007-04-24
There is a file in /etc/X11/ called xorg.conf that configures your X window system.  If you post the results of opening a terminal and entering and running this command:

```
ls -l /etc/X11/xorg*
```

we might be able to see if there is a backup copy of this file that we can re-install.  

PS:  you can cut and paste the command from here, rather than retyping if you want..

---

### Post by ubuntukid on 2007-04-24
Go into System -> Administration -> Restricted Drivers Manager and disable the proprietary driver. Restart gnome and see if that solves it.

---

### Post by Carlos Santiago on 2007-04-24
The problem was solved disabling the proprietary driver.
Ty all.

---

### Post by Atmosphere on 2007-04-24
is there a way to disable the proprietary driver when in "safe" mode ?

i did the same thing however the results were that there is no display while in the GUI

---

