---
title: "Can't install updates after edgy to feisty upgrade (nvidia, glx)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Yellowbelly on 2007-05-18
I just got home from college and I decided to upgrade here so if I lost my computer somehow it wouldn't affect school. Basically I have Beryl 0.2.0 running with the aiglx thing I think, a 6600gt with the drivers on there by envy. Ran into a couple things during the upgrade like it couldn't replace some stuff or things like that but I ran into some of them right off the bat when the system restarted and now i'm on feisty. I immediately got a system update icon so I did it and ran into 2 packages (nvidia glx, and glx dev; it also says 4 packages for some reason but only see 2) that couldn't be installed so here's the error message:

E: /var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2
E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-15.20_i386.deb: conflicting packages - not installing nvidia-glx
E: /var/cache/apt/archives/libgl1-mesa-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing libgl1-mesa-dev
E: /var/cache/apt/archives/mesa-common-dev_6.5.2-3ubuntu7_all.deb: conflicting packages - not installing mesa-common-dev


Another thing, I started up beryl and it appears that I can use compiz with it. Problem is, I don't have window borders with it. Same with desktop effects. Also with the regular metacity themse, it seems that I can't change the colors becuase it isnt' the right theme but i've tried basically all the ones that come stock.

---

### Post by AlexenderReez on 2007-05-19
remove completely nvidia driver.....
open synaptic...search for nvidia-glx-new.....install everything new there...


P/S:feisty use nvidia-glx-new instead of nvidia-glx

---

### Post by Bachstelze on 2007-05-19
Feisty uses nvidia-glx too. They just install different versions of the driver...

---

### Post by Yellowbelly on 2007-05-19
How should I remove the driver? Synaptic package or what code?

also something weird has come up. I never started beryl today so I tried desktop effects but it switched to only one desktop instead of multiple so the cube didn't work. I tried to add some but it wouldn't switch it with the cube.

---

### Post by Yellowbelly on 2007-05-22
Sorry to bump this but do I need to remove my nvidia video card drivers or just the xgl ones and how should I do it?

---

