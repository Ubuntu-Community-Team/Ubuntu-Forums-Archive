---
title: "LiveCD not working..."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by sphere9 on 2007-12-08
I've tried downloading the LiveCD three times, once through the torrent and twice off the website, burnt them correctly verified .etc (I also requested 2CDs from ShipIt and both are giving me the same result)

they all seem to work fine until i try to run the Live environment in which i get the usual Ubuntu boot screen with the orange bar, once loaded the screen goes black and a screwed up looking block of green (think MissingNo from pokemon or Nine Inch Nail's Year Zero websites) and it just... hangs there. 

By holding in the power button on my PC it brings me to the Ubuntu desktop.. in some bizarre resolution that the resolution settings will not let me change.

I have also tried running Ubuntu as a live USB and recieve the same problem, however after awhile i get a screen with an error something along the lines of  "The Display Server has been shutdown 6 times in 90 seconds". 

Please help me :(

Update:

Forgot to post my system specs;

Intel Pentium 4 CPU 3.00GHZ
895MB RAM
NVIDIA GeForce FX 5200

(I hope this is all i need to post, i'm a n00b with these things)

---

### Post by PmDematagoda on 2007-12-08
What are the specifications of your PC?

---

### Post by philinux on 2007-12-08
Especially make and model of graphics card.

---

### Post by derby007 on 2007-12-08
If you're thinking of doing an install, use the Alternate CD. Then when that boots up, you might have to edit your '/etc/X11/xorg.conf' file if you have a graphics issue.

---

### Post by graphisong on 2007-12-08
Try installing in safe graphics mode.

---

### Post by Sammyf on 2007-12-08
I might have the same problem.
Trying to install Ubuntu on a machine with those specs :

MSI K8T8 Neo V (via K8T800+8237/R Chipset)
AMD Sempron 3100+
Nvidia 7600GS AGP
2GB RAM

everything works fine until, normally, the gnome desktop should appear, at which point the screen gets completely garbled up. it is repeated 4 times horizontally, on a 4th of the screen. The rest is just white blocks.

I switched to the shell(alt+F1), stopped gnome, tried restarting it. It works nicely until the first icons appear, at which point it fills with white blocks and no screen refresh is done.

I tried every option in the boot menu of the LiveCD.

I'm now tyring to install the alternative CD to see if I can boot normally afterward (or at least after editing xorg.conf a bit)

any idea?

bbye,
Sammy

---

### Post by Sammyf on 2007-12-08
here is an update :

after installing via the alternative CD, I can boot Ubuntu, but it's still unusable. The login screen is completely white with a small bar (the text inpuit field I presume) of light grey. interestingly, the mouse pointer is fine. I get the ~wheel~ pointer when ubuntu is thinking, I can move the pointer around, it isn't corrupted or anything. 
If I type blindly my login and password, the screen empties itself, becomes ubuntu brown (NO picture though), the taskbars appears (white and empty) and then the screen fills with white and black blocks again.

I tried changing the driver from vesa to nv, but no difference to be seen. 

I *really* need help on this one

---

### Post by Sammyf on 2007-12-08
in case someone has the same problem : the issue was with an option in the Bios called "VLINK 8X Supported". It defaults to "enabled" but it messes things up with the above configuration. Disabling it in the BIOS solved my problems.

---

### Post by sphere9 on 2007-12-08
Hi, thanks for all the quick responses,

however i'm not trying to install on this computer but merely run the ubuntu live environment...

---

### Post by sphere9 on 2007-12-09
I've also tried running the .iso from a flash drive and am receiving the same problem, any ideas?

---

### Post by derby007 on 2007-12-12
Try an older version of Ubuntu, 6.06 Dapper maybe.

---

