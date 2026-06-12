---
title: "Ubuntu 10.04 livecd won't boot on mac pro"
date: 2011-04-13
forum: Apple Hardware Users
---

### Post by randallecook on 2011-04-13
I am trying to set up a quadruple boot on a brand new Mac Pro: Mac OS, Windows, Ubuntu 10.04 32-bit, and Ubuntu 10.04 64-bit. The goal is to explore programming with certain PCI cards and various software we need to work with.

While this may seem daunting, I am having trouble getting off the ground. Creating partitions is straightforward, but the main problem I am encountering is that my Ubuntu 10.04 32-bit liveCD will not boot the machine. When I boot from CD, I get the console screen with the initial messages, then I get the graphical screen with the Ubuntu logo and the five red and white dots. Then it goes black.

If I hit enter, I can hear the CD-ROM drive springing to life, but with nothing on the monitor, I can't proceed. Yes, I suppose I should stretch out with my feelings, use the force, and make it go, but I am no jedi. :)

The machine is a 2x 2.4 GHz quad-core Xeon with a 2560x1440 LED Cinema display. Any suggestions for getting the liveCD to drive the display? Thanks.

---

### Post by isaacahloe on 2011-04-17
i have the same problem with 11.04, i've tried holding C on startup and "option" both method start but then go black

---

### Post by randallecook on 2011-04-29
Regarding my problems: Yesterday I downloaded 11.04 64-bit and its live desktop CD booted the machine just fine. It installed during the night and seems to be running fine. The only problem is that the Mac/Windows dual boot I had before installing Ubuntu is now gone. Only the Mac boot is left. The Windows partition is still there, but it's not in rEFIt's boot menu anymore. I'll post again as I resolve this.

Regarding isaacahloe's problems: Are you running rEFIt? I am and had no trouble booting the live CD all the way to Firefox. I did not try it without rEFIt.

---

