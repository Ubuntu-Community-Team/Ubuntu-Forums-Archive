---
title: "USB drive dismounts by itself in 7.10"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by kingleer on 2008-02-08
I unfortunately set my usb connection to USB 1.0 because I read it would make my install more stable. It seemed to be dismounting randomly, but it wasn't I fixed that.

> 

To disable USB 2.0, type this in the terminal:

sudo modprobe -r ehci_hcd

Test if the copy/write process is stable, and if you want to disable USB 2.0 upon boot, type:

sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo update-initramfs -u -k `uname -r`
 

I would now like to reverse this.

---

### Post by kingleer on 2008-02-08
Seriously, USB 1.0 speeds are annoying. HEELP.

---

### Post by kingleer on 2008-02-08
I'll keep on bumping until I can at least get some tips.

---

### Post by Hmarroqu on 2008-02-08
i get the same issue with a WD external hdd.. this drive i notice is the only one and it draws its power from the hdd, probably alot of power...maybe to much?

---

### Post by kingleer on 2008-02-08
OOOOOOOh how I hate USB 1.0. I will never bitch about USB 2.0 being slow ever again...Except when USB 3.0 comes out maybe.

---

### Post by Hmarroqu on 2008-02-09
god i dont even want to know what thats like.

---

