---
title: "xorg.conf messed up - how can I get to command line?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by ahickman on 2007-06-02
New user. Had everything working fine with my new Ubuntu install. Was pleasantly surprised at relative ease of getting wireless netwroking installed etc (I did install SuSE in about 1998! but didn't stick with it). 

The only thing wrong with my install was that my Intel 810 based graphics were not so good. Max resolution was 800x600 (Google Earth caused crash!) and there 3D graphics were unusuable. 

I tried to change over to "Intel" driver rather than "i810" and adjust xorg.conf to 1024*768.  I've managed to screw up my xorg.conf in the process and it now doesn't boot to a screen that I can see. Ubuntu progreess bar gets to end, then rather than see login screen my monitor flashes VGA.

**I guess my first question is can I interupt the graphical login to get to a command line somehow??**

Any further guidelines in how to get graphics working better on Intel810 (Packard Bell Houston3+ motherboard) would be a bonus for now

---

### Post by taurus on 2007-06-02
Press <Ctrl><Alt>F2 and log in with your name and password.  Then run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ahickman on 2007-06-02
Thanks - when I press Ctrl Alt F2 it interupts the graphical progress bar and cuts to the blank monitor screen with VGA flashing...

Anthing else I can do?

---

### Post by blue_shift on 2007-06-02
Boot from Grub into recovery mode?

---

### Post by ahickman on 2007-06-02
OK sorted. Thanks for the help!

I swapped from my LCD TV back to a regular monitor and could then see the command line (?)

I managed to reconfigure the xserver using "Intel" rather than "i810" and now have the choice of 1024*768 :)

---

