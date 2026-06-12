---
title: "Hosed my x-server"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by BomanAJeff on 2007-02-18
I tried suggestions online to change my screen resolution to 2024x68. Now I get an error only that my x-server can't start.

I bacjed up vorg.comf before I messed with it. How do I restore it?

---

### Post by Crakie on 2007-02-18
2024x68? What were you thinking ;)

There are several ways to go about this; all require the terminal. If you don't see one after the failing boot sequence, press cntrl-alt-f1 and login.

1) restore your previous xorg.conf: sudo cp /location/of/backup.file /etc/X11/xorg.conf (case sensitive), then reboot (sudo reboot now)

2) edit xorg.conf yourself: sudo nano /etc/X11/xorg.conf and change the resolution options, save and reboot.

3) If all fails: sudo dpkg-reconfigure -phigh xserver-xorg and answer a few questions. The vesa driver will get you back in a graphical environment after reboot. You can then go about reinstalling your drivers, which is probably the easiest to get everything back to normal.

---

### Post by r4ik on 2007-02-18
Try,
sudo dpkg-reconfigure xserver-xorg

follow the defaults and finish with a

sudo etc/init.d/gdm restart

If you have a visual get you're drivers here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by BomanAJeff on 2007-02-18
I tried to do that. One problem: I don't get a command line. The screen ends up just devoid of anything.

---

### Post by PartisanEntity on 2007-02-18
Are you using dapper? And is the screen turned off completely?

---

### Post by arochester on 2007-02-18
Try Alt+Ctrl+F1 and see what happens...

---

### Post by BomanAJeff on 2007-02-18
> **PartisanEntity said:**
> Are you using dapper? And is the screen turned off completely?
Actually I'm using Edgy Eft.

My Xserver is working now, in any event.

---

