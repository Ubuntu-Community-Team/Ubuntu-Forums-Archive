---
title: "Kubuntu/XGL missing shutdown buttons"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-01-15
this is what my startxgl.sh script looks like
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec /etc/X11/Xsession startkde
```
and yet, when I click logout, I can't restart or shutdown unless i log out of the session first. 

Thanks for any help in advance!

---

### Post by Loonux on 2007-02-11
Did you find a solution for this?
I have the same problem(s)

---

### Post by shanepardue on 2007-02-11
I did not. XGL and Kubuntu seem harder to manage than with Gnome.

---

