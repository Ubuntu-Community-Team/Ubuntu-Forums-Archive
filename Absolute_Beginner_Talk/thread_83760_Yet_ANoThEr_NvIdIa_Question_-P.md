---
title: "Yet ANoThEr NvIdIa Question :-P"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-29
I installed ubuntu on a computer that has an nVidia Geforce FX5200 (128 DRR, PCI) and was wondering what the apt-get command is to install the driver for the card since it only shows me the black Xscreen(?) and no GUI\desktop or GDM.

Thanks

---

### Post by shandar on 2005-10-29
```
sudo apt-get install nvidia-glx
```
then edit your /etc/X11/xorg.conf by executing:
```
sudo pico /etc/X11/xorg.conf
```

Another option is to use the vesa driver instead and download the drivers for the card using synaptic in Gnome. To do that run ```
sudo pico /etc/X11/xorg.conf
``` and change the driver from "nvidia" or "nv" to "vesa".

---

