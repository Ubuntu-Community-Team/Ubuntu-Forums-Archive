---
title: "whats the best driver for a RIVA TNT2 16MB video card (and how do you get it)?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by peterkeyani on 2008-04-17
Hi
Tried the restricted driver offered during installation but it stoped the computer from working!
thanks
pete

---

### Post by anewguy on 2008-04-17
I used to use a Diamond Viper V770, which was basically a TNT2 with 32mb.  I used Envy to install the driver - it uses the legacy driver if I remember correctly.  :)

---

### Post by peterkeyani on 2008-04-17
> **anewguy said:**
> I used to use a Diamond Viper V770, which was basically a TNT2 with 32mb.  I used Envy to install the driver - it uses the legacy driver if I remember correctly.  :)

Tried that but it gave me a very low resolution screen - something like 600x400 !

---

### Post by anewguy on 2008-04-17
Double check your xorg.conf - you may need to edit it to add the higher resolutions.  Also, if you haven't already, once that driver is installed run sudo dpkg-reconfigure xserver-xorg, select your driver, then when you get to resolutions be sure to check those you know your monitor supports, and specify the horz and vert ranges when asked.  It's been a while since I used that card, but I think that's all I did to get it working.  I'll do some more thinking on it and get back to you.  You can also run that card with the vesa driver and get at 1024x768.  Loading in the driver (it will be the legacy nvidia driver) doesn't help much with that card - I could never get desktop effects working with it because the card just doesn't support everything that is needed.  :)

---

