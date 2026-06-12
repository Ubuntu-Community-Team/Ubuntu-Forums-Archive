---
title: "screen resolution - neither 915resolution nor xserver-xorg-video-intel working"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2007-05-19
It's my second Ubuntu installation. A few months ago I installed Ubuntu 6.06 and I think I got the resolution well with 915resolution.

Now I'm installing Ubuntu Studio 7.04.

I've installed 915resolution and the output when trying to use it is:

> 
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unknown chipset type and unrecognized bios.
915resolution only works with Intel 800/900 series graphic chipsets.
Chipset Id: 6611039




I have also used this command

> sudo apt-get install xserver-xorg-video-intel

but I don't know how it's supposed to work. The right resolution (1280-800) is still not available in Screen resolution.

THANK YOU VERY MUCH FOR YOUR HELP :)

---

### Post by Kobalt on 2007-05-19
Usually installing the intel drivers is enough (and make sure to have the drivers set as "intel" in your xorg.conf).```
sudo apt-get install xserver-xorg-video-intel
```

---

