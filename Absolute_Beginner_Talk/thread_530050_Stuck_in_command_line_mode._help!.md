---
title: "Stuck in command line mode. help!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-08-20
In ubuntu, everything works fine. But I want to learn to use console mode.
I can press Ctrl+Alt+F1 to get to the Virtual console.

But when I press Ctrl+Alt+F7, it brings me to a black screen with a cursor,  that's all.

---

### Post by aysiu on 2007-08-20
Control-Alt-Backspace (*after* Control-Alt-F7) resets the X (graphical) server. That may help.

If not, (*after* Control-Alt-F1), you may want to reconfigure your graphics settings: ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

