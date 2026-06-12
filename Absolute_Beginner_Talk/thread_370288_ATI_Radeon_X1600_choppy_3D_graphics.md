---
title: "ATI Radeon X1600 choppy 3D graphics"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-25
I have installed the driver from the ATI site. Everything works fine except when I try to play 3D games. I tried to play Balazar, and it took about 30 seconds for a move to happen. I know my card has 3D capabilities. All 3D games are extremely choppy and jerky. What is happening?

---

### Post by cocoia on 2007-02-25
Hey there, I have the same card as you have. Perhaps you could open a terminal for me;
 
Programs > Accessories > Terminal

and post the output of fglrxinfo, or glxinfo

I should be able to help you from there. Otherwise , check the ubuntu guide (ubuntuguide.org) for the ATI driver install howto.

---

### Post by 67GTA on 2007-02-25
Here is both:


[ATTACH]26135[/ATTACH]

---

### Post by igknighted on 2007-02-25
The ATI driver did not install properly.  I would highly recommend uninstalling the drivers you go from the ati page and installing the package "fglrx-driver" from synaptic (or apt).  This gives you a prebuilt kernel module for the Ubuntu kernel so it doesn't need to custom build one, which is likely where your problem is (and will install the linux-restricted-modules-common package which is needed).

---

### Post by 67GTA on 2007-02-25
I uninstalled the ati proprietary driver. What do I need or don't need according to Synaptic?

Synaptic search for fglrx:
[ATTACH]26142[/ATTACH]

---

### Post by 67GTA on 2007-02-26
After a month of trying to get the ATI drivers installed, and direct rendering working, I came across Envy. Everything is working fine after using envy. Anyone having ATI driver problems should give it a try!

---

