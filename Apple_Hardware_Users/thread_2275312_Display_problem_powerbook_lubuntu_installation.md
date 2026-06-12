---
title: "Display problem powerbook lubuntu installation"
date: 2015-04-25
forum: Apple Hardware Users
---

### Post by adamo2 on 2015-04-25
Hi all. Iv recently inherited a box of old tech amongst it all was an old g4 power book (500mhz) it's not the fastest notebook but I have been having a play around and have tried to install lubuntu 14.04.2 onto it. 

The problem that I'm getting is when I boot into the command line for the live cd and try to load the live os the whole screen turns red progressively which I presume is a driver error. 

Is there anyone who can please help me get lubuntu up and running for installation. 

Many thanks in advance 

Adam

---

### Post by rican-linux on 2015-04-25
on boot enter these settings if your video card is a ati/radeon one.

```
live radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

---

