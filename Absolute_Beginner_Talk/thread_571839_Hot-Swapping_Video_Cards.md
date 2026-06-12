---
title: "Hot-Swapping Video Cards"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Crafty Kisses on 2007-10-09
So I found out my current video card doesn't really work, so I was going to stick a older version into my computer, both cards were Nvidia, but I need to know what am I to expect if I hotswap a video card? Thanks for the help.

---

### Post by Joeb454 on 2007-10-09
Depends how much older it is etc. And whether it needs a different driver or not.

I've done it before on a Windows system, it didn't really like it, worked, but didn't like it, could change the graphics options until i reinstalled the driver.

Chances are it'll work, but then again, chances are it won't without some tweaking, what with this being Linux we're talking about :p

Just _*don't*_ try my method - Do it anyway, and hope for the best

---

### Post by taurus on 2007-10-09
What is the current model of your nVidia and the one that you plan to put it in?  Chances are you might not have to do anything.  And if you ever get an error message about video card, just press <Ctrl><Alt>F2 to get to a console and edit /etc/X11/xorg.conf and replace the Driver from "nvidia" back to "nv".  Then, install nvidia again for the old card.

```
sudo nano -Bw /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by rsambuca on 2007-10-09
What are they?

---

### Post by Crafty Kisses on 2007-10-09
> **rsambuca said:**
> What are they?

My current one is a NVIDIA GeForce 6800, and I think I'm gonna put in my GeForce Ti4200, or Geforce FX 5200.

---

### Post by rsambuca on 2007-10-09
You should be fine with the 5200.  The other may require installing legacy drivers.

---

