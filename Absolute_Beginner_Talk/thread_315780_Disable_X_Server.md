---
title: "Disable X Server"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-12-09
Does anyone know how to disable X Server? I'm trying to install the nvidia driver, but I need to disable this first, and any other OpenGL sessions.

Thanks in advance guys!!!

---

### Post by r4ik on 2006-12-09
Ctrl Alt F1

Login and

sudo /etc/init.d/gdm stop

when finished

sudo /etc/init.d/gdm start

Good luck !

---

