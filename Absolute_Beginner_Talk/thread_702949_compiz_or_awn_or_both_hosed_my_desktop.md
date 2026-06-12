---
title: "compiz or awn or both hosed my desktop"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by sir4taye on 2008-02-20
I can't access my desktop except through recovery kernel. I can access the failsafe terminal though. I could use some help with comands to exterminate the awn curves and the compiz deskto settings I've setup which I'm sure are halting my machine just as gnome becomes active. just as the icons start appearing, it freezes.

Anyone got any ideas about so terminal work I can do?

---

### Post by tyggna1 on 2008-02-20
```
metacity --replace
```

for compiz.

```
sudo dpkg-reconfigure xserver-xorg
```

for most GUI problems.

---

### Post by macogw on 2008-02-20
You can hit Ctrl+Alt+F1 and log in there first, then hit Ctrl+Alt+F7 (or F9...sometimes it's on F9 for some reason) and log in to the GUI way, then go back to the first one with Ctrl+Alt+F1 and type "killall compiz" so that Compiz is forced to quit in the GUI area.  It might not automatically load Metacity, so there might be no window management going on, but you should still be able to hit Alt+F2 from inside the GUI to run the "metacity --replace" command tyggna1 gave to start up the normal window manager.

---

