---
title: "Compiz Fusion not working on ATI RV300 PCI-E"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by mythloaf on 2007-10-23
I downloaded ubuntu 7.10 and installed it. But somehow i cant get the compiz fusion effect.
When i enable the appearance effects and the third radio button it says cannot load effects.

My Graphics card is ATI RV300 PCI-E 128MB 

Please help me to work around this problem.

Thanks in advance.:KS

---

### Post by Afkpuz on 2007-10-25
First, you must install the ati restricted driver for your video card.  

System>Administration>Restricted Driver Manager

Check the box next to "Ati accelerated graphics driver" to install the driver


Then, install the "xserver-xgl" and "compizconfig-settings-manager" packages using synaptic

Reboot and you should be able to turn on those beautiful effects.  The settings manager will allow you to change the settings of compiz.

Those settings can be found by going here:

System>Preferences>Advanced Desktop Effects Settings

---

