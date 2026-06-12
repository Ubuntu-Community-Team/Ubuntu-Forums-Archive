---
title: "usb mounts but doesnt show on desktop"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by frenchcr on 2007-09-04
My usb seems to mount at /media/sdb1  (with sdb1 being the usb stick), but its stopped showing up on the desktop, any ideas

---

### Post by Majorix on 2007-09-04
Maybe /home/username/Desktop became read-only? I don't know if its possible though. But this was the first thing that popped up into my mind.

---

### Post by schorsch on 2007-09-04
Press "ALT+F2" and type:
```
gconf-editor /apps/nautilus/desktop
```
Is the options "volumes_visible" checked?

---

### Post by frenchcr on 2007-09-05
yes, its ticked, ah well, thanks anyway .

](*,)...its the only thing in gutsy i haven't been able to fix...worked fine in feisty and all others before.

---

### Post by frenchcr on 2007-09-07
**Solution**

cd /usr/share/share/hal/fdi/policy/

rm gparted-disable-automount.fdi

apparently its to do with recent usage of Gparted

---

