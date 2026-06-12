---
title: "Jesus Christ....metacity stops working!"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-11-22
It just god damn stops working.

I just installed Ubuntu Server without any other crap installed.
I install the bare software using:
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal

EVerytime I boot into the desktop, metacity stops working and i don't get any borders, minimize and maximize buttons. I enable metacity by opening a terminal and typing metacity and it works for 5 seconds then goes back!

Does anyone even do any QA before releasing to the public???????????????????

---

### Post by Kingsley on 2007-11-22
Hi. Try Xfce.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by spiderbatdad on 2007-11-22
```
metacity --replace
```
then restart

---

