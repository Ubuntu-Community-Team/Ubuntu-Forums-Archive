---
title: "How can I exit X?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-12-15
Hi,

  I'm trying to install the nVidia drivers for my 2.6.19-custom kernel and the installer says it needs to run not in X and I can't seem to find a way to exit X, I tried killing the process and it just came back. Anyone know how?

  Also anyone know if it's possible to have X running on Alt+F1 and have terminals on Alt+F2 through 5 or something?

  Any help is much appreciated.

---

### Post by total wormage on 2006-12-15
try ctrl + alt + backspace
this should kill your X and lead you to a terminal

about the other thing, i probably would make a few workspaces and fill the first one just with windows and run terminals full-screen (f11 in gnome) on the other workspaces
and make a keyboard-shortcut for alt + f1 / f5 to switch between the workspaces

---

### Post by po0f on 2006-12-15
uriahs,

Ctrl + Alt + F1-6 will get you to a virtual console where you can log on.  The above solution will restart X.

[EDIT]

To stop X, execute:
```
$ sudo /etc/init.d/gdm stop
```

---

### Post by bodhi.zazen on 2006-12-15
```
sudo /etc/init.d/gdm start
``` to restart X :

(Or ```
sudo gdm
``` also works

So should ```
startx
``` )

---

