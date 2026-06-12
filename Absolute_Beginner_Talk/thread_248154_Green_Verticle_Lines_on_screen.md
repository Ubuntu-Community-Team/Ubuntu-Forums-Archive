---
title: "Green Verticle Lines on screen"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by lynxus on 2006-08-31
Hey guys,
Im trying to install to a PC and when it finally gets to teh desktop i can hear the welcome sounds, BUT cannot see a thing.

All i can see is green verticle lines on screen.

Ive tried the TFT auto tune, No luck.


My GFX card is a Nvidia 6600 GT.

Any ideas?!

Ive got ubuntu installed fine on my laptop.. But would love it actually installed on my main PC. :(

---

### Post by Toxicity999 on 2006-08-31
when you get to the GDM login prompt press ctrl+shift F1 enter your login info now type nano /etc/X11/xorg.conf (this is view only mode just so you don't mess anything up by mistake!) Use the arrow keys to skim down to the Video card bit and tell me what the driver used is.

After you look through this Report any questions or isses here if none press ctrl+x to kill nano. and use sudo nano /etc/X11/xorg.conf to open it an edit mode. I know it's redundant but just to play it safe View only mode helps out. Now run through the following.

If it's nvidia (proprietary driver) change it to nv. if it's nv try vesa. Now... I don't keep up with the progress of the open source drivers but it's possible that it's a known bug. So switching to Vesa which is a waaaaay generic Driver will alow do hopefully log in with no graphical distortion long enough to attempt installing the proprietary drivers. which you will need to read a guide on as I claim no stake to being an Expert on nvidias.

---

### Post by lynxus on 2006-08-31
Thanks :)

Got it to load now..

Just to be faced with another problem :(
Will post a new thread for that..

---

