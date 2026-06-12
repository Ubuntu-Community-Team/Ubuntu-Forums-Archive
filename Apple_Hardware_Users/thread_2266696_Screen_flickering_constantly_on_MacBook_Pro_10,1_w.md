---
title: "Screen flickering constantly on MacBook Pro 10,1 with retina display"
date: 2015-02-24
forum: Apple Hardware Users
---

### Post by rajnikhil on 2015-02-24
I've installed Ubuntu 14.04.2 on my MacBook Pro 10,1 (mid 2012). Initially it was working fine, but then it started to act up. Now, the screen flickers whenever there is a new window that comes up on the screen and does so constantly. I've tried to select the nvidia proprietary drivers in whatever small window of time but I could never complete the process as the screens starts to flicker while I'm still in the middle of the process. Is there a way to prevent this flickering?

Please let me know if you require anymore details.

Thank you in advance.

---

### Post by este.el.paz on 2015-02-28
Does the same thing happen if you boot a LiveDVD?  Or does it happen if you boot OSX?

e.e.p.

---

### Post by rajnikhil on 2015-02-28
It happens when I install b43 drivers for the wifi. Until I install those drivers the systems (except wifi) works fine. The system works fine again when I remove the this driver.

---

### Post by este.el.paz on 2015-02-28
Interesting . . . haven't heard that one before . . . .  How are you installing the drivers?  Using Software Services "additional drivers"??  Synaptic?  Or Terminal?  This one is probably beyond me, but, why not try to install whatever Nvidia drivers are "suggested" first, and then try for the B43 . . . .  Possibly you might need an xorg.conf file??  Are you using 32 bit or 64bit??

Also did you check the md5sum number of the iso before install??

e.e.p.

---

### Post by rajnikhil on 2015-03-01
I'm installing through terminal as I can't see the driver in 'additional drivers'. When I select Nvidia drivers from 'additional drivers' and reboot, the screen turns blank on start-up.

---

### Post by este.el.paz on 2015-03-01
> **rajnikhil said:**
> I'm installing through terminal as I can't see the driver in 'additional drivers'. When I select Nvidia drivers from 'additional drivers' and reboot, the screen turns blank on start-up.

OK, so you mean you are installing the B43 driver with Terminal?  And, selecting the Nvidia drivers that are listed in "additional drivers"?  And when you do that the screen goes blank?

What about my other questions?  md5sum number checked?  OSX runs the screen perfectly?  It's all a bit odd, as wifi card has little to do with the screen.  I have LM17 (aka 14.04.1) running on my MBPro from '10, so two years older, and was able to use aditional drivers to set up the Nvidia card . . . and probably the wifi driver.  Everything should therefore be better for your computer, unless the iso you downloaded was somehow "corrupted" for instance . . . .

Possibly the problem may be with "b43" . . . and the Terminal, there are some hoops to jump through to get wifi set up in my PPC computers, which don't show "b43" . . . and it has to be done "manually" . . . and depending on what you type in the Terminal it might be loading the "wrong" driver.  I use Synaptic to search for stuff that is applicable for my system . . . and either use it to install or figure out the exact terms to use on the Terminal to get the right items/modules.apps.

e.e.p.

---

### Post by MikeBraxner on 2015-03-04
Sounds familiar. If I remember correctly, this stems from a power control issue with the b43 under some kernels. Two suggestions. First, try to suspend and then wake your system - that should get rid of the flickering. Second, try a newer version of bcmwl. Good luck.

---

