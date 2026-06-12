---
title: "HDMI issues with macbook pro 8,1"
date: 2014-07-11
forum: Apple Hardware Users
---

### Post by carlito3 on 2014-07-11
HI 

i have been trying to connect my MBP to my TV with my HDMI cable buy it seems like ubuntu (14.04) 
does not detect it (however it does say when i reboot that a usb device has been connected) 
i'm new to ubuntu, is there something that i can do to solve this issue?
i know that has something to do with softwares/drivers but i'm a bit lost

would appreciate if someone could help me out please
thanks

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep VGA -A2

---

### Post by carlito3 on 2014-07-12
What is this supposed to do?

the output of "lspci -knn | grep VGA -A2" gave me :

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Apple Inc. Device [106b:00db]
    Kernel driver in use: i915

---

### Post by shadesofoctober on 2014-07-13
I have the same Macbook but unfortunately do not have an thunderbolt->HDMI cable to test :(
Online indications seem to point to mixed results. I'm thinking the issue lies with the Intel integrated graphics.

References I've seen to HDMI working on Macbook Pro 8,* and similar all seem to reference proprietary drivers, which means they're talking one of the bigger models that have dedicated graphics as well.

Also, I've read a few times that it doesn't really seem to support hotswapping cables.. you have to have it plugged in before boot. I'm sure you've tried that, which makes me think it's the graphics controller.

I'll keep my eyes out for anything, but I'm sorry I can't help more!

Oh yeah, I saw this from Intel themselves, but never actually tried it out, because the installed drivers worked fine for me.. maybe you get better luck with it?
[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.5-linux)

---

### Post by carlito3 on 2014-07-13
Thank you for your input shadesofoctober

Unfortunately i have tried what you suggested and nothing actually changed...
It is indeed frustrated as i believe that there is always a way.

---

