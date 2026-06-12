---
title: "Cannot boot to Edgy"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by johatte on 2006-10-29
I have a HP Pavillion dv6000 laptop. It has a AMD Turion 64 x 2 and Nvidia Geforce 7200 graphicscard. I have been trying to install 32-bit version of Ubuntu Edgy. Live CD version works fine,sounds, screen and all. But after installation to hard disk Ubuntu will not boot. After booting in grub the Ubuntu splash screen starts and after finishing this the screen becomes blank and the system hangs.
Please help! I really would like to have Ubuntu up and runnig.

---

### Post by Perfect Storm on 2006-10-29
Boot up in failsafe mode, then:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by johatte on 2006-10-29
After doing the command you suggested I got following:
xserver-xorg postinst warning: not updating /etc/X11/X.file has been customized
xserver-xorg postinst warning: overwriting possibly-customized configuration file: backup in /etc/X11/xorg.conf2006102991942
Trying startx hung the system.

---

