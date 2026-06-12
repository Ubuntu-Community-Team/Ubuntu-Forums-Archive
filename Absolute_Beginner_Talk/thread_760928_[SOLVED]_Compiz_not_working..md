---
title: "[SOLVED] Compiz not working."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2008-04-20
I have an ATI Radeon X1950Pro PCIe video card. I installed the driver with Envy. I typed ```
 sudo apt-get install xserver-xgl
```

I have Hardy Heron installed. That is what I had to do to get it working in Gutsy. But for some reason in Advanced Desktop Effects Settings in General it is not letting me change the number of desktops to 4. What can I do to get the cube to work? I also changed Appearance -> Visual Effects to Extra.

---

### Post by LowSky on 2008-04-20
you need to install ccsm
 its in synaptic

---

### Post by joshrobinson on 2008-04-20
> **LowSky said:**
> you need to install ccsm
 its in synaptic

ccsm isnt the name of it, and might make it hard for the user to find
```
sudo apt-get install compizconfig-settings-manager
```
and launch it with
```
ccsm
```

enable cube, cube rotate, and in the cube options change to 4 viewpoints

---

