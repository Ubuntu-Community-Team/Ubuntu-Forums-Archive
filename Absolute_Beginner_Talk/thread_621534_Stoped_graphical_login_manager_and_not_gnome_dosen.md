---
title: "Stoped graphical login manager and not gnome dosen't load"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Kuroda_Shun on 2007-11-23
I was trying to stop any services I don't need and I mistakenly lost gnome. how do I start it from the command line?

---

### Post by taurus on 2007-11-23
Either

```
sudo /etc/init.d/gdm start
```
to load GUI login screen

or 

```
startx
```
to start a window manager.

---

