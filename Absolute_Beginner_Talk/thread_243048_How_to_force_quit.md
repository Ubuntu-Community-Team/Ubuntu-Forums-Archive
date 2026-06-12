---
title: "How to force quit?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by nzk on 2006-08-24
How do I force quit programs that wont close?

---

### Post by christhemonkey on 2006-08-24
if you get a terminal and type xkill into it,
you will then get a nice little cursor that will kill any programs you feel neccesary to end.

---

### Post by aysiu on 2006-08-24
If you're using KDE, press Control-Alt-Escape.

Or press Alt-F2 and type ```
xkill
```

---

### Post by noynac on 2006-08-24
Add a "force quit" icon to a panel.

---

### Post by MHlavsa on 2006-08-24
The two easy ways are:

1.  Add Force Quit icon on a menu.  Right click panel, _A_dd to Panel..., under Desktop & Windows "Force Quit".  What I did was create a Drawer (add the same way) and put misc. items in there, like Root Nautalis, Force Quit, Search, Lock Desktop, and Themes.

2.  Ctrl + Alt + Del may work, I added it through Automatix.

---

### Post by MaximB on 2006-08-24
okokok...force quit and xkill I know and love
but if I can't get to the panel
if I'm inside a game (full screen) and the game stuck
what can I do ?

---

### Post by aysiu on 2006-08-24
> **MAXDDARK said:**
> okokok...force quit and xkill I know and love
but if I can't get to the panel
if I'm inside a game (full screen) and the game stuck
what can I do ?
Does Alt-F2 not work when you're in full-screen?

---

### Post by MaximB on 2006-08-24
well....I've said "IF"....so it didn't happened to me for a long time (my problem was that I didn't install my video card - so nothing worked).

but let say that alt+F2 doesn't work.....what then ?
how can I quit without restarting the xserver with ctrl+alt+backspace ?

---

### Post by aysiu on 2006-08-24
Control-Alt-F1.
Log in.
```
killall *nameofprogram*
```

---

