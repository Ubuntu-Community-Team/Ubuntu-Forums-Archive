---
title: "Screen Resolution"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by chirawuf on 2007-11-16
am using ubuntu now and I am fairly new to it. The screen resolution is too large and I would like to reduce it, ubuntu only give me one resolution option which is 640 * 480 at a refresh rate of 60hz, I have a trident video accelerator blade 3D/promedia graphics card, Ubuntu picks up the driver to trident microsystem cyber blade/il . 

Please can anyone help me with the screen resolution, I like my font and graphics a little smaller

---

### Post by skymera on 2007-11-16
what is your video card?

also try

sudo dpkg-reconfigure --phigh xserver-xorg

then choose the res. you would like to use

---

### Post by Inxsible on 2007-11-16
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select all the resolutions that you want with the space bar and use tab to tab between the options

---

### Post by Sims2789 on 2007-11-16
^Enter those instructions into the terminal (Applications -> Accessories -> Terminal).

---

