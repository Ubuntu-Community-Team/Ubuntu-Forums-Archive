---
title: "Creative Audigy 2 ZS Platnum not detected?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by JAB Creations on 2007-06-06
I'm testing Ubuntu 7.04 (AMD64) via VMware server and I have a Creative Audigy 2 ZS Platinum sound card. Under System -> Preferences -> Sound neither my Creative Audigy 2 ZS Platinum nor the crappy Realtek audio devices have been detected. How can I install drivers for these devices? I choose auto-detect and test and the application just closes. Any specific device and testing will receive weird error messages?

---

### Post by fletchergroves on 2007-06-09
I believe that if you installed it in VMware Server, you will have a virtualized sound card - it won't see your actual sound card.  Specs for the Virtual Sound Adapter from the VMware Server admin guide:

Virtual Sound Adapter
-Sound output and input.
-Creative Labs Sound Blaster AudioPCI emulation. MIDI input, game controllers,
and joysticks are not supported.

If you want to enable the virtual sound card, I think you will need to power off your virtual machine, then go to its properties.  From there you will need to choose add new hardware and add the sound card.  I don't know what kind of functionality this will give you other than basic in and out, but if you just want to hear sound from the VM, this should help out.

---

