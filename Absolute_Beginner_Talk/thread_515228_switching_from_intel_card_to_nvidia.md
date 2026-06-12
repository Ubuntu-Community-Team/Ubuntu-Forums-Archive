---
title: "switching from intel card to nvidia"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-08-01
im swapping from and intel intergrated graphics card to an nvidia.

is installation of the card simple?

i.e - plug in, attach screen,  boot ubuntu, then restricted driver manager?

or is it far more complicated?

---

### Post by steve.horsley on 2007-08-01
The GUI will probably fail to start aftere changing the card, leaving you in a text-mode terminal. The command you need (write it down) after logging in is
**sudo dpkg-reconfigure xserver-xorg**
Which asks lots ot questions. Just taking the defaults should get you working again. After the questionaire is over, use this command:
**sudo /etc/init.d/gdm start**
to launch the GUI again.

---

### Post by annda on 2007-08-01
i'd suggest running 
```
dpkg-reconfigure -phigh xserver-xorg
```
in recovery mode on the first boot to adjust xorg.conf.

---

### Post by skymera on 2007-08-01
thanks.

what if i plug nvidia in, but not the screen in the nvidia?

keep in intel.

and install nvidia, then plug in to nvidia.

---

