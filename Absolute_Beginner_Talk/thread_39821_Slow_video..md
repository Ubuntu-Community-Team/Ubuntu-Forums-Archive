---
title: "Slow video."
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by Ridley on 2005-06-06
Things seem to be running much slower after the initial install video-wise. I haven't configured ubuntu much yet (newbie) But just looking at screensavers and whatnot, I noticed that all the GL and higher ones run very slow and choppy. Some of them run fine in Windows (ie. Flux, Cyclone, Euphoria, Helios, any of the tunnel ones, etc.)

Is this due to video drivers, which I haven't updated yet, or are there some other settings I need to change? 

I'm running:
Nvidia GeForce FX 5700 ultra
Althlon XP 2400+
512MB DDR 400

---

### Post by flanker on 2005-06-06
you need to install the nvidia 3d driver to get decent gl performance.

Search the forum for nvidia 3d but its basicly;

sudo apt-get nvidia-glx
sudo echo nvidia >> /etc/modules

then edit /etc/X11/xorg.conf changing the driver from nv to nvidia and adding the following settings to the device section;

        Option          "NoLogo"        "true"
        Option          "RenderAccel"   "true"

---

### Post by Ridley on 2005-06-06
Cool, I'll give that a try once I get home. Thanks.

---

