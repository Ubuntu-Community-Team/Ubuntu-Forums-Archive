---
title: "Problem with 8800GTX"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by techmunkey on 2007-08-19
Hello all,

I am attempting to get the Nvidia drivers installed on Ubuntu 7.04 32-bit. The current resolution is 1024x768 60hz :(. I really want to use my hardware to it's full potential in Linux and get over the noob syndrome. I am weak in command lining in linux and really need HELP. 

My computer is a few months old and I am attempting to get away from Windows for day to day operations. 

My system is the following:
Dell XPS 410
Intel C2DUO 6420@2.13GHz
Intel P965 MOBO
Nvidia 8800GTX 768MB
2046MB RAM DDR2 800MHz
320 Gig SATA Drive
NEC DVD+/- Burner
ViewSonic VG2230wm Series

---

### Post by mysticmatrix on 2007-08-19
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Check this post and then ask for help if further required.

TIP: Most of common problem are already documented at ubuntu wiki :)

---

### Post by Hobo Joe on 2007-08-19
You need the proper nVidia drivers.

Use Envy. I have a link in my sig. Just download and install, and then run it and tell it to install the nVidia drivers and let it configure your xorg when it asks if it can.

Once it's done, you can use the command:
```

sudo nvidia-settings

```
To get to the nVidia control panel, it has all the things like configuring multiple monitors and resolution and color settings and all that.

---

### Post by techmunkey on 2007-08-19
One word.. Envy. Fixed all my issues and now I am rockin in 1600x1050. Thanks for all the help. It was really easy and had great tutorials.

---

