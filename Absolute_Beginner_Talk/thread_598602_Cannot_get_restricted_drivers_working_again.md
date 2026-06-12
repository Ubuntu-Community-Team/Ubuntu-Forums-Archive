---
title: "Cannot get restricted drivers working again"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by ubunick on 2007-10-31
Everything WAS working before in Feisty -- but I had turned off the effects because I didn't like how a lot of things were displaying (mainly text, dunno.. it was weird) and I figured I would try to get things working again so I tried to enable my restricted drivers again and here it was it says:

```

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: trying to overwrite `/usr/bin/nvidia-xconfig', which is also in package nvidia-xconfig

```

I do believe uninstalling nvidia-xconfig fixed this, but after rebooting it would only display in 800x600 or 640x480 and the restricted drivers were in fact enabled.  Probably an easy fix for more experienced users, but I didn't think I'd need nvidia-glx-new.. considering I have geforce 6200 (ironically it's the card I got to run linux).

Any replies are welcome, thanks. :???:

---

### Post by skyjacker on 2007-10-31
Try this Procedure:

1) Back up the present xorg.conf
Code :sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

2) Stop gdm or kdm
Code: sudo /etc/init.d/gdm stop (or kdm for kde)	

3) Edit xorg.conf
Code: sudo dpkg-reconfigure xserver-xorg

4) Select the resolutions you want available by arrowing down to each desired line and pressing the “space bar”

5) Validate your choices with “enter”

6) restart X with Control+Alt+Backspace

7) Choose the desired resolution under the “Systems/Preferences/Screen Resolutions drop down list

NOTE:  if you don't need to add any additional resolution sizes, skip # 4 & 5
Good Luck - let us know if you need any more help.:)

---

### Post by ubunick on 2007-10-31
Well, the desired resolution works when I'm not using restricted drivers.. ubuntu itself recognizes it's a Geforce 6200.  Whenever I enable restricted drivers is when it doesn't allow me to change resolution from those two.

Basically, is there a better fix other than editing xorg?

---

### Post by skyjacker on 2007-10-31
I n
have a nVidia driver, and this is the only way I could get the resolutions  that I wanted added.

---

### Post by ubunick on 2007-10-31
I have the drivers and this issue was nonexistent when using Feisty.

---

### Post by skyjacker on 2007-10-31
When I upgraded from Feisty to Gutsy I had to do the procedure to get my resolution correct again (It was fine in Feisty). Don't have another solution, maybe someone else can help you. P.S. as long as you make a back-up to your .conf file you should be safe.

---

### Post by fly3836 on 2007-10-31
I have GeForce 6200 and I use the following procedure on Gusty
1) back-up xorg.conf
2) install nvidia-glx-new from Synaptic
3) nvidia-glx-config enable 
4) dpkg-reconfigure -phigh xserver-xorg
choose resolutions
5) enable proprietary driver NVIDIA

---

