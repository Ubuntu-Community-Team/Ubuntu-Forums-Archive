---
title: "Enabling direct rendering for my SIS card"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-29
Hi everyone! This is my VGA card according with lspci output:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I configured my card with xserver, and ive really felt quite a change. But when i want to install Google Earth or just play TuxRacer, both programs just crash. I googled a bit and found that i need direct rendering enabled in my video card to do both things. I typed "glxinfo | grep direct" but it also crashes and sends me back to the login screen. Then i typed "glxgears", and noticed that the     wheels spin in a very laggy way. That lead me to think that i didnt have direct rendering enabled (lol). Ive googled a lot and seems that SIS does not like linux type systems. Everything in the website is about windows, and the few things i found have the same effect as configuring xserver with the "sis" option, so no DRI for me.

I wanna know if this sis model has DRI support under ubuntu, or if i have to desist and buy a graphic card :(

Cheers

---

