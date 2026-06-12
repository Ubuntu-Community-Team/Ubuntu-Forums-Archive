---
title: "Screen Resolution OK - then degrades"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by John Boy on 2007-07-01
From help given in this forum, I have got Nvidia drivers installed etc. When the Kubuntu login screen comes up, it is 1400x1050 

	information	NVIDIA(0): Setting mode "1400x1050"
	information	Loading extension NV-GLX
	information	NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
	information	NVIDIA(0): Using the NVIDIA 2D acceleration architecture
	default setting	NVIDIA(0): Backing store disabled

(which is recommended for my Viewsonic VG2021m ) and the probed queries seem to be fine. However, some lines later in the X.org Log after loading built in extensions and then failing to load some cyrillic fonts, it gives the message:

	information	NVIDIA(0): Setting mode "1024x768_70"

Why would it revert at this late stage in the game? I can confirm that the LCD monitor is driver at 1400x1050 at the login and then is 1024x768 :(

            Thanks,

                      John

---

### Post by Raineer on 2007-07-01
I played with Kubuntu quite a bit last week and ran into a Xorg problem that required some debugging.  I continually went through the scenario of 1024x768 in KDM (the login manager) and then *sometimes* I could see higher once the desktop came up...and sometimes not.

The root of my problem was me "playing around" and I had let Automatix2 install a newer NVidia driver. The ones my kernel was built with is version 97.55.  I would recommend trying these, as soon as I went back to that driver level it cured 100% of my problems.

---

### Post by John Boy on 2007-07-01
Thanks. After 'playing around' for a while I was encouraged to use Envy which worked like a dream. Will look into what you have recommended.

           John

---

