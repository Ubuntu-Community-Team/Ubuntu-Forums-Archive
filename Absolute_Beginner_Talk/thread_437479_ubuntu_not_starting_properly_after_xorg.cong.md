---
title: "ubuntu not starting properly after xorg.cong"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-08
I have tuned up some resolution modes and screens in the xorg, and now when I start, after loading, ubuntu giives me an error saying that my X server (graphical interface)failed to start likely because it is not set up correctly. Was wondering what I can do to restore it.

---

### Post by aidanr on 2007-05-08
login on the command line and type
```
sudo nano /etc/X11/xorg.conf
```
and undo any changes, or if you used gedit it would've made a backup so you can do
```
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
and then type sudo reboot

---

### Post by simplekin on 2007-05-08
> **aidanr said:**
> login on the command line and type
```
sudo nano /etc/X11/xorg.conf
```
and undo any changes, or if you used gedit it would've made a backup so you can do
```
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
and then type sudo reboot


thank you, works fine now

---

