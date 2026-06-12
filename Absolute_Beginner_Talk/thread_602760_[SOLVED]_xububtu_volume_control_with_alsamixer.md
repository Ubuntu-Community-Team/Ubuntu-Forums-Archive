---
title: "[SOLVED] xububtu volume control with alsamixer"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tettayes on 2007-11-04
I am using xubuntu feisty; can anyone tell me how to get gnome-volume-controller on system tray so it can launch on startup?

thanks in advance!

---

### Post by mali2297 on 2007-11-04
Wouldn't [Xfce4-mixer]("http://www.xfce.org/projects/xfce4-mixer") do the job as well? (Can be found in the repositories.)

---

### Post by sisco311 on 2007-11-04
xfce4-mixer is installed by default. you can add it to the panel.(right click on the panel, select Add New Item, select Volume Control)

---

### Post by tettayes on 2007-11-04
actually yes, but for xfce4-mixer, i don't know how to make keyboard shortcuts for controlling volume...
I wanna have Ctrl+down & Ctrl+up for controlling up and down; Alt+M for mute.
do anyone know how to do this???

---

### Post by sisco311 on 2007-11-04
you can use aumix:
```
sudo aptitude install aumix
```> aumix -w 0  --> mute
aumix -w -10 --> volume down
aumix -w +10 --> volume up```
man aumix
```to get a list of channels(-w is for PCM, -v is for master ...).

to set the shortcuts, go to the
Applications -->> Settings --> Keyboard Settings --> Shortcuts tab

---

### Post by mali2297 on 2007-11-04
> **sisco311 said:**
> you can use aumix:
```
sudo aptitude install aumix
``````
man aumix
```to get a list of channels(-w is for PCM, -v is for master ...).

to set the shortcuts, go to the
Applications -->> Settings --> Keyboard Settings --> Shortcuts tab

**amixer** (installed by default) can do the same thing:
```

amixer set PCM 5%-
amixer set PCM 5%+
amixer set PCM toggle

```
(Respectively: decrease volume, increase volume and mute/unmute.)

---

### Post by tettayes on 2007-11-04
omg! it did amazing job!!  thank you guys!!!!!

---

