---
title: "Graphics card problem.."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-01-13
I'm having problems with choppy scrolling, Google earth loading etc., and I guess I need a graphics card driver.
The card info. is:  North Bridge Chipset: 741  
                    South Bridge Chipset: 964L 
                    Graphics Processing Unit: SiS Mirage Graphics

I've tried the SiS website and couldn't find a linux driver there.
I have XP and ubuntu 6.10 dual booted and the graphics are fine with XP.
Could anyone offer a suggestion for a fix?
Thanks---Milt

---

### Post by bigken on 2007-01-13
in a terminal type  sudo dpkg-reconfigure -phigh xserver-xorg
and try the various sis drivers

---

### Post by Milt888 on 2007-01-13
OK, I'm kinda confused.
When I select SiS and hit enter, It goes to a window with what looks like various screen resolutions.
I'm not sure what to do from there.

---

### Post by bigken on 2007-01-13
use the space bar to select your screen resolutions ;)

---

### Post by Milt888 on 2007-01-13
I tried all those but didn't see any improvement.
Thanks

---

### Post by bigken on 2007-01-13
sorry I cant help you anymore give google a shot

---

### Post by Milt888 on 2007-01-13
OK, thanks anyway.

---

### Post by TuxCrafter on 2007-02-26
The driver should be supported under linux! I have just orderd a this chipset I think I have it in 1 week I can take a look at it.

---

