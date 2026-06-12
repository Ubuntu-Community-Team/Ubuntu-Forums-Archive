---
title: "Anyone used a joystick with the GIMP?"
date: 2009-09-12
forum: Art &amp; Design
---

### Post by dsavi on 2009-09-12
I have this Logitech extreme 3d joystick just sitting around and I noticed that the GIMP detects it as a Linux input. It doesn't really work though, I tried to bind some actions on the joystick to actions in the GIMP but it didn't really work. Anyone tried/done this before? I'm interested to know how.

---

### Post by motonnerd on 2009-10-29
[FONT=Comic Sans MS]I'm trying to do the same thing.  I have something from an old Win.  95 computer, the only id on there is 'F-16 Flight Stick" and I'm using the game port on my sound card .  Xubuntu, 2.5GHz processor, 512 RAM, so I don't think lag is a problem with me.  (By the way I'm using the GIMP from Ubuntu's package installer, v2.6)

The joystick config program works great, and I got GIMP to dump input (something I would recommend to you to make sure it's getting there).  When you go to edit the device on the 'Input Devices' preferences of the GIMP menu the helpfiles told me that you can check the 'enable debugging' box to have GIMP dump controller imput to the commandline.  I started it in terminal and saw a beautiful stream of data -- however, nothing is working.  I just tried to map the scroll-(left, right, etc.) functions to the x- and y-axes and save/zoom fit/new layer/new layer mask to the four buttons.  Nothing's working.  (I"m trying to use it to scroll around while zoomed in).

I had the config open and watched both it and GIMP report on the joystick's functionality, but the image window didn't respond.  Let me know if you find anything!
[/FONT]

---

### Post by motonnerd on 2009-11-01
[FONT=Comic Sans MS]You should note that at the time of my writing this the jscalibrator package was dropped from Ubuntu 9.10, the bug site says that it's too antiquated and needs to be ported for GNOME, so I'll keep my eyes open for a replacement/port.  If you are considering upgrading your install, you might be able to keep those old packages and still have it work -- I'm not sure if it's automatically obliterated or not.  I'm gonna search for linux drivers for mine...
[/FONT]

---

