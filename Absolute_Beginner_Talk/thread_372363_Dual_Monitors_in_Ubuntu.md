---
title: "Dual Monitors in Ubuntu"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by AustinJM on 2007-02-28
How can I have dual monitors on my Ubuntu machine?

---

### Post by xyz on 2007-02-28
Try this:
[HowTo: Dual Monitors by Ziox]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by kerry_s on 2007-02-28
What kind of card? 
If it's nvidia just install the driver and run> sudo nvidia-xconfig --twinview
and it will auto set it up. See> man nvidia-xconfig

---

### Post by AustinJM on 2007-02-28
Thanks very much to both of you!

The current Ubuntu machine is 2.1 GHz, 1Gb Ram, dual boot w/WinXP SP2.  It's got 3 Sapphire 256Mb video cards, each with a DVI & a vga.

The machine I want to put Ubuntu on is a newer 2.4GHz Intel Core2 Duo, 4Gb ram, Vista, a bunch of hard disks, and two Asus 7600GT 256MB video cards (nVidia chipset) each with two DVI outputs.

---

### Post by charles.g.moore on 2007-02-28
> **AustinJM said:**
> How can I have dual monitors on my Ubuntu machine?

I used an nvidia card and did not have any problems here are the links I used, take a look and hopefully you get some info from them

[http://ubuntuforums.org/showthread.php?t=85769](http://ubuntuforums.org/showthread.php?t=85769)
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)
[http://www.ubuntuforums.org/showthread.php?t=257317](http://www.ubuntuforums.org/showthread.php?t=257317)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I think the second link is what did it for me...Good Luck
Once you get two up you'll never go back to one

---

### Post by bodhi.zazen on 2007-02-28
> **AustinJM said:**
> Thanks very much to both of you!

The current Ubuntu machine is 2.1 GHz, 1Gb Ram, dual boot w/WinXP SP2.  It's got 3 Sapphire 256Mb video cards, each with a DVI & a vga.

The machine I want to put Ubuntu on is a newer 2.4GHz Intel Core2 Duo, 4Gb ram, Vista, a bunch of hard disks, and two Asus 7600GT 256MB video cards (nVidia chipset) each with two DVI outputs.

I have a 7600 video card and the ope source drivers do not work (at least they do not work on my card (to this day) and they were listed an incompatible the last time I looked 6 months ago).

First step is to install the nvidia driver. The easiest way is with the envy script :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

**Go for the beta version** ;)

The beta version runs just fine for me and has a number of improvements over the stable version.

Then, in a terminal, type

nvidia-settings

Now if you can not configure all your monitors you may need to edit xorg.conf ...

I know you will get at least dual monitors ...

---

### Post by kerry_s on 2007-02-28
Just read the man page or doc text. It sounds like your running SLI so you want to try->

sudo nvidia-xconfig --twinview --sli=Auto

Attached is the Readme for nvidia.

---

### Post by jrock2004 on 2007-02-28
I will look into this cause I just install ubuntu

---

