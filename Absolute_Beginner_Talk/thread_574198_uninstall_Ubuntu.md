---
title: "uninstall Ubuntu"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by lavew2000 on 2007-10-12
Hi , I was tweaking my laptop so that i could get the s video out working and I ended up disabling xserver.So i am not able to get my interface to work . I tried to boot of a cd and for some reason , that doesnt seem to work too.I was wondering if there is a way to uninstall ubuntu from the command prompt so that i cam start all over again .

---

### Post by Joeb454 on 2007-10-12
easiest way would be to just reinstall from scratch. Failing that try ```
sudo dpkg xorg.conf
``` I think that's right lol.

---

### Post by alan34 on 2007-10-12
The command is this then choose the vesa driver reboot then you should get your desktop back,


sudo dpkg-reconfigure -phigh xserver-xorg

Good Luck

---

### Post by bodhi.zazen on 2007-10-12
To re-configure X :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Keep in mind, always back up system files before you edit them, and use comments to document what (and why?) you have changed. You can then just restore from back up.

If the first command I gave you fails, edit xorg.conf and use the vesa driver.

```
sudo nano /etc/X11/xorg.conf
```

You are looking for the "Device" section :> Section "Device"

    Identifier  "6600gt_twinview"
    Driver      "nvidia"
    BusID       "PCI:01:00:0"

Change the driver to vesa> Section "Device"

    Identifier  "6600gt_twinview"
#     Driver      "nvidia"
    Driver      "vesa"
    BusID       "PCI:01:00:0"

and re-start X. The graphics will not be good, but you can work in X to resolve the problem if you wish.

Other then that, what video card ? What monitor ?

What and how did you do to change xorg.conf ?

---

