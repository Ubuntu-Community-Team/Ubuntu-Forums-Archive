---
title: "Voodoo3, works but only sorta!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-09-01
I got a voodoo3 card in right now, typing glxgears brings up the three turning gears, runs fine and all. I don't remember what I put into the terminal, but it said "direct rendering: yes" or something.

But it's still odd. Trying to look at "Endgame" screensaver, it's REALLY slow, like crap framerate. I couldn't figure it out, so I installed a couple 3D games, one of which was "Torcs", a racing sim game. Because I thought it might help fix everything else, i'm gonna try and see if this is able to be fixed.

Once I get into the race, it does the same thing. Framerate is crap. I set the settings in game to 16 color, the voodoo card is set right on only 16 colors, and 1024x768. Also in the game, the cars are transparent. Which they're not supposed to be.

Hoping this will help my card troubles. Thank you for any help!

---

### Post by TFX360 on 2006-09-01
> **Taigrr said:**
> I got a voodoo3 card in right now, typing glxgears brings up the three turning gears, runs fine and all. I don't remember what I put into the terminal, but it said "direct rendering: yes" or something.

But it's still odd. Trying to look at "Endgame" screensaver, it's REALLY slow, like crap framerate. I couldn't figure it out, so I installed a couple 3D games, one of which was "Torcs", a racing sim game. Because I thought it might help fix everything else, i'm gonna try and see if this is able to be fixed.

Once I get into the race, it does the same thing. Framerate is crap. I set the settings in game to 16 color, the voodoo card is set right on only 16 colors, and 1024x768. Also in the game, the cars are transparent. Which they're not supposed to be.

Hoping this will help my card troubles. Thank you for any help!


No offense but isn't this card ancient?

I had a VooDoo2 card in my QuakeWorld years and that's ten years ago.


For a graphics card thats pre-historic.


How much memory does the card have?

---

### Post by darkteckno on 2006-09-27
I got mine in an old machine running Xubuntu.

---

### Post by meborc on 2006-09-27
if u open your X conf file, what does it say about your display driver?

i found this by doing apt-cache search voodoo:
```

xserver-xorg-driver-tdfx - X.Org X server -- tdfx display driver
xserver-xorg-driver-voodoo - X.Org X server -- Voodoo display driver
glide2-bin - graphics library for 3Dfx Voodoo based cards - support programs
libggi-target-glide - General Graphics Interface Glide2 display target
libglide2 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide2-dev - graphics library for 3Dfx Voodoo based cards - development fileslibglide3 - graphics library for 3Dfx Voodoo based cards - shared libraries
libglide3-dev - graphics library for 3Dfx Voodoo based cards - development 

```
maybe you need to install a package called xserver-xorg-driver-voodoo ?

try it out... although vesa might work better :) cuz it IS an ancient card... (have GF2 MX200 miself :mrgreen: )

---

### Post by rölli on 2006-09-29
The Voodoo3 is not so ancient as you think and really nicely supported under Linux. You need to install the package libglide3. Then the card scores in glxgears easily 25% higher than an ATI Radeon 7000 (RV100), which is by the way still produced today...

P.S.: DRI is running only in 16bit colour mode on the Voodoo3!

Data:
ATI Radeon 7000, PCI (without 'e'!), 64MB, AMD64 3000+: 325 FPS
Voodoo3, PCI, 16MB, PII/266: 410 FPS (while the system is making a long download!)

---

