---
title: "Kubuntu Feisty: I hosed myself with the nvidia driver again..."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2007-04-20
I've had nothing but trouble with the proprietary drivers for my Nvidia card (GeForce Fx5200) in the past, but I decided to give it another try in Feisty.  I installed nvidia-glx and selected the "proprietary" option in the Monitors config, rebooted and now I get a black screen.  First things first, how can I get back into my machine?  (I'm typing this from the live CD.)  Second, can anyone give me any advice on getting the driver working?  Thx...

-p.

---

### Post by maniacmusician on 2007-05-05
> **TeeAhr1 said:**
> I've had nothing but trouble with the proprietary drivers for my Nvidia card (GeForce Fx5200) in the past, but I decided to give it another try in Feisty.  I installed nvidia-glx and selected the "proprietary" option in the Monitors config, rebooted and now I get a black screen.  First things first, how can I get back into my machine?  (I'm typing this from the live CD.)  Second, can anyone give me any advice on getting the driver working?  Thx...

-p.
you can get in through the recovery mode. When you start your computer, Grub start's loading. It gives you 3 seconds to press Escape before it loads Ubuntu. During this time, press Escape. Select the second entry from the list, and boot into it. This will be your recovery mode. From there, you can do "sudo nano /etc/X11/xorg.conf" and fix it.

By that I mean, go to the Device section and change the driver from "nvidia" to "nv". You should be able to log back in after that.

---

