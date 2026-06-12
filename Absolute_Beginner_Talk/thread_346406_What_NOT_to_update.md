---
title: "What *NOT* to update"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by ffpcs on 2007-01-25
Obviously, I am a rank beginner. The first two times I installed Ubuntu, I allowed the update manager to install all 96 updates it found (coming from the Windows environment, I am used to just letting updates happen). After updating, the system would fail at boot with a kernel panic - syncing error.  OK, I *CAN* learn, so after the THIRD install, I allowed it to update everything except those updates that referred to linux.  Apparently I am currently running Ubuntu 6.06 LTS.  I am running it on a pentium III with 256 RAM and 80GIG HD.  Which of the following updates should I / should I *NOT* install? And if I am not supossed to install these, why does it offer them? How can I educate myself for the future regarding updates that might be offered? Thank you.

linux-386 - complete linux kernel on 386 - new version 2.6.15.25
linux-image-2.6.15.26-386 - linux kernel image for version 2.6.15 on 386
linux-image-2.6.15.27-386 - linux kernel image for version 2.6.15 on 386
linux--restricted-modules-2.6.15.26-386 - non-free linux 2.6.15 modules on 386
linux--restricted-modules-2.6.15.27-386 - non-free linux 2.6.15 modules on 386
linux--restricted-modules-386 - restricted modules on 386
linux--restricted-modules-common - non-free linux 2.6.15 modules helper script

---

### Post by SinxarKnights on 2007-01-25
Are you using a PCI graphics card with a motherboard with onboard graphics by chance?

---

### Post by birdseye on 2007-01-25
If its any consolation I found almost exactly the same thing except that in my case updating caused the modem to fail. So like you I have missed out the linux updates. Doesnt seem to cause a problem.

Maybe now that you're not using Bill Gates system, there is no need to update every few days. If it works, dont fix it!:D

---

### Post by sumguy231 on 2007-01-25
All of those should be fine to update (and you should update them, they include security updates), but if you use proprietary graphics drivers you might want to wait and make sure they don't clash with the *-restricted-modules* packages. If you update those and get the kernel panic again, press Esc when you see the computer mention GRUB - when you get to the menu, select any other boot entries listed that don't end in (recovery mode) or aren't Memtest.

---

### Post by ffpcs on 2007-01-25
Thanks for the replys. I am using a PCI graphics card. It is identified by the system as an nVidia NVS [RIVA TNT2/TNT2 Pro]. There is no integrated graphics chip on the motherboard that I am aware of. I assume if there were, there would be a connecter exposed for it, and there isn't. Why does the graphics card determine if you may install "restricted" updates. Can someone explain what a "retricted" update is? Thanks again. - Frank

---

### Post by ffpcs on 2007-01-28
After reading through the various forums and wiki pages, I was able to get everything installed.

-Frank

---

### Post by SinxarKnights on 2007-01-28
> **ffpcs said:**
> Thanks for the replys. I am using a PCI graphics card. It is identified by the system as an nVidia NVS [RIVA TNT2/TNT2 Pro]. There is no integrated graphics chip on the motherboard that I am aware of. I assume if there were, there would be a connecter exposed for it, and there isn't. Why does the graphics card determine if you may install "restricted" updates. Can someone explain what a "retricted" update is? Thanks again. - Frank

I had to ask because I had a very similar problem with onboard graphics with a PCI graphics card. I'm glad you got it all sorted out. Good luck!

---

