---
title: "Install of ubuntu from cd iso"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by madsurfer on 2007-04-09
Hi
I am trying to install Ubuntu 6.10 from the download iso, when I do the cd boots up but with the screen very dodgey, low res and the screen split into 2. The install icon can be seen but when I try to select it the map for the time is too messy to use. I have Ati Rage Mobilty m4  graphics card. Do I need some new drivers? If so how do I get them and install them? Is there a way to do a non-graphics install?

I hope someone can help

Adrian

---

### Post by jvc26 on 2007-04-09
How much RAM do you have out of interest? It may well be that you need different drivers for your gfx card - have you tried installing from the alternate cd? That is available from the same download page as the livecd, but as it isnt graphical it may make installation easier.
Il

---

### Post by Erlander on 2007-04-09
In the menu just after the bios screen at startup select "Safe Graphics Mode"

That should do it.

Rob

---

### Post by siciliancasanova on 2007-04-09
If the safe graphics mode works for you, install ubuntu, restart, and enter safe graphics mode again.  Then find the driver for your card and follow a guide on how to install it.  Restart and see if it works.

---

### Post by dstew on 2007-04-09
I just installed Ubuntu 6.10 on a Dell C800 laptop with an ATI M4 card. I had the same problem, split screen and all that. I tried many boot options (F6 at splash screen) but no dice. So, I installed using the Alternate cd. It installed fine, but then when Ubuntu booted same thing, split screen.

I solved it by editing my /etc/X11/xorg.conf file. I found the ATI card Device entry, and in the driver line I changed "ati" to "vesa". No problems after that.

By the way, I tried the Envy script first, but it said the driver was not appropriate for the M4 card. I installed it anyway, but it did not work. Only changing "ati" to "vesa" worked for me.

---

### Post by siciliancasanova on 2007-04-09
To edit that file ```
sudo gedit /etc/X11/xorg.conf
```

---

