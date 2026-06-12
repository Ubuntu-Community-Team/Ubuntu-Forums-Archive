---
title: "Screen Is WAY TOO SMALL"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-09-18
Help.  I Have gotten my laptop to boot up ubuntu finally, however the screen size is tiny there is almost a 2in border around my screen.

The laptop specs
   Dell Latitude
   Dual Boot with Windows 2000
   Pentium3
   ATI Rage Card

---

### Post by Arghhh haha on 2007-09-18
System > Preferences > Screen Resolution

---

### Post by z0mbie on 2007-09-18
You will need to define the Horizontal and Vertical Refresh Rates in **/etc/X11/xorg.conf** according to the manufactures spec for your display.

---

### Post by madmatrixz3000 on 2007-09-18
I tried screen res so I think the other idea is how to do it plz give me a step by step, it took me three days to get this far

---

### Post by K.Mandla on 2007-09-18
Double-check the color depth too. Some older video cards can't do 24-bit color depth, which Ubuntu sets as a default, and as a result they switch to a tiny screen. 

Find this line in your xorg.conf file.

```
DefaultDepth 24
```
and change it to 

```
DefaultDepth 16
```
If your screen dimensions need changed at the 16-bit depth, you should change that while you're in there too. Just add them to the "Modes" lines.

Hope that helps.

---

### Post by madmatrixz3000 on 2007-09-18
How do i get to the config...?

---

### Post by madmatrixz3000 on 2007-09-18
i have used my driver specific help here so far rebooting now

[http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x](http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x)

---

### Post by K.Mandla on 2007-09-19
> **madmatrixz3000 said:**
> i have used my driver specific help here so far rebooting now

[http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x](http://wiki.zenwalk.org/index.php?title=ATI_Rage_Mobility_M3_AGP_2x)
Hmm. Seven hours later. ... Well, no news is good news, I guess. :-k

> **madmatrixz3000 said:**
> How do i get to the config...?
Sorry, that was an oversight. I thought you had already edited your xorg.conf once, so I suggested one small change.

Open a terminal (Applications > Accessories > Terminal) and enter this command.

```
sudo nano -w /etc/X11/xorg.conf
```
When you're done editing it, you can save the file with CTRL+O, then exit with CTRL+X. Restart the desktop by pressing CTRL+ALT+BACKSPACE.

---

### Post by alienexplorers on 2007-09-19
Why not use ENVY to load the proper drivers for your card.  Sounds like you have a driver problem and maybe ENVY might help.

---

### Post by madmatrixz3000 on 2007-09-19
I got it completely fixed but what is ENVY, will it help solve the problem I am now having as my hi-res screen is only receiving a 800X600 resolution and yes I have tried the screen resolution utility

---

### Post by CaptainInsaneO on 2007-09-19
Envy is a great program that will auto-install your video drivers for you. I love it.

---

### Post by madmatrixz3000 on 2007-09-19
how will envy help i though that the installer installed the driver and the command that i changed in my earlier fixed all my driver issues

---

