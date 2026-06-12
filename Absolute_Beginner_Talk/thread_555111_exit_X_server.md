---
title: "exit X server"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by ags40 on 2007-09-19
How do you exit exit X server?  Thx, very much.

---

### Post by Pumalite on 2007-09-19
Ctrl+Alt+F1
sudo /etc/init.d/gdm stop

---

### Post by -SpaZ on 2007-09-19
Assuming you're using Gnome:```
/etc/init.d/gdm stop
```
If you're using KDM:```
/etc/init.d/kdm stop
```

---

