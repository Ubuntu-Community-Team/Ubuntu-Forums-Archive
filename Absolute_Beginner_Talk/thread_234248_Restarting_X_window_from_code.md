---
title: "Restarting X window from code"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by stevoid17 on 2006-08-11
Hi, i've managed to put unbuntu onto a portable HDD and managed to make a USB grub CD. now when i boot it on new computers, the X window system fails to boot and gives me an error message. i think that it doesn't pick up it is a different system and tries to use the x800 gfx card drivers.

can someone throw me a bone and help me fix this?


thanks
Stevoid

---

### Post by robinl on 2006-08-11
If it's a driver issue just type in
```
 sudo nano /etc/X11/xorg.conf 
```
and change the thing after Driver in Section "Device" to "vesa". 
Save (ctrl+x) and type startx to see if it solved the problem.

---

