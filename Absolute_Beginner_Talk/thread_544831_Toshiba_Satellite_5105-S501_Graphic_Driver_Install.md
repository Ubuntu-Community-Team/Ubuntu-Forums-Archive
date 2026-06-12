---
title: "Toshiba Satellite 5105-S501 Graphic Driver Install Help"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by LipidSama on 2007-09-06
I have a Toshiba Satellite 5105-S501, which has a Geforce 440 Go graphics card in it. My problem is, when I do a fresh install of 7.04 (not sure I think thats the most current) Everything works really well. I update everything get all the latest patches and tinker around with the desktop a little. Anyway I go to pref > desktop features or something like that and it says I have 2d accelerator on and I need a 3d to make this feature work and than it asks me to install the latest graphic drivers from Nvidia. Well I say sure and enter my password and let it download, it than asks me to reboot which I do. Than when it gets to the log in screen my screen is a solid white/salmon color with no text or anything, and I hear the sound in the background. Please MTV help me pimp my ride (sorry lol)

---

### Post by arsonxOnFire on 2007-09-07
Simply add in /etc/X11/xorg.conf

```
Option "UseDisplayDevice" "DFP"
```

to your  Device section

```
Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 440 Go]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option "UseDisplayDevice" "DFP"
EndSection
```

Pimp ON!!!

---

### Post by stchman on 2007-09-07
> **LipidSama said:**
> I have a Toshiba Satellite 5105-S501, which has a Geforce 440 Go graphics card in it. My problem is, when I do a fresh install of 7.04 (not sure I think thats the most current) Everything works really well. I update everything get all the latest patches and tinker around with the desktop a little. Anyway I go to pref > desktop features or something like that and it says I have 2d accelerator on and I need a 3d to make this feature work and than it asks me to install the latest graphic drivers from Nvidia. Well I say sure and enter my password and let it download, it than asks me to reboot which I do. Than when it gets to the log in screen my screen is a solid white/salmon color with no text or anything, and I hear the sound in the background. Please MTV help me pimp my ride (sorry lol)

Enable the nvidia restricted driver.

---

