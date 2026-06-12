---
title: "Ubuntu 6.10 halts on startup"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Tearlow on 2007-02-06
Since I haven't had much experience so far I don't know much about problem solving yet... However Ubunto stops at the startup screen, I've located the problem to the USB Drives- If theres nothing plugged everything launches just fine and I can plug kb/mouse at the loginscreen.

anyone that might be able to assist me with this, Just try to keep it kinda simple ;-)

---

### Post by ComplexNumber on 2007-02-06
> **Tearlow said:**
> Since I haven't had much experience so far I don't know much about problem solving yet... However Ubunto stops at the startup screen, I've located the problem to the USB Drives- If theres nothing plugged everything launches just fine and I can plug kb/mouse at the loginscreen.

anyone that might be able to assist me with this, Just try to keep it kinda simple ;-)
are you sure its not just taking a while to initialise everything. i remember when i had an unused network card inserted in my PC, bootup would take a lot longer because ubuntu was trying to access and determine the IP address etc for that network card. but because there is no lead attached to it, it failed. when i removed it, bootup was normal.

---

### Post by neji on 2007-02-06
Yes I have this problem too with my USB memory card reader. What I do is just unplug the device before boot and plug it in after boot. It mounts fine after everything else is loaded but somehow it interferes with boot. Hope they fix this in the future.

---

### Post by Tearlow on 2007-02-06
After a few more boots I've come to this conclusion.

If anything is plugged into any USB sockets it will halt and never go past that step forcing me to reset. However If I keep pressing for ex. num-lock key while having everything plugged into the computer it will launch just fine thus proving everything works but for some reason halts if inactive...

Where do I find the startup logs? I've looked over the System logs but don't see anything wrong there...

And I'm much sure it's only the USB since my network starts just fine. I'm actually posting this message from the very same computer ;-)

> **neji said:**
> Yes I have this problem too with my USB memory card reader. What I do is just unplug the device before boot and plug it in after boot. It mounts fine after everything else is loaded but somehow it interferes with boot. Hope they fix this in the future.
Could you test this as well? When GRUB reaches 0 (Make sure that your USB reader is plugged in) keep pressing num-lock till you see the progressbar move- It will take about 3-4sec so...

---

### Post by aerie on 2007-02-28
Hi, I'm new to ubuntu/linux and to this thread and I had a similar problem with my internal memory card reader. I couldn't even start the live cd, well this is not exactly true, it started twice from 30 attempts. I noticed that the card reader's power led turned off when it failed to start. Then I started the live cd pressed F6 remove quiet splash ant typed break=bottom and I saw where did the process stop, it was a problem with the OHCI Host controller the only USB device I had connected was the card reader so unplugged it from the motherboard and since then no problem. But the two successes I had with the reader connected keep me guessing...

Anyway I have tested starting pressing num-lock till grub countdown reaches 0 and surprisingly it works!

---

