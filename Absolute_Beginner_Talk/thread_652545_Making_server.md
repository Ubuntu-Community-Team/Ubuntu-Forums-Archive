---
title: "Making server"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by thebloggu on 2007-12-28
i want to make a server with a computer i have (one of the ideas i have for it see [this post]("http://ubuntuforums.org/showthread.php?t=652471"))

>     *   Intel Pentium MMX 266MHz
    * 12.1in TFT LCD screen
    * ESS ES1879Technologies Sound Blaster pro compatible,
          o 16-bit stereo codec
          o Full duplex support
          o 3D sound
          o Hardware volume control
    * Trident Cyber 9388
          o 2MB VRAM
          o 32-bit PCI bus VGA controller with Graphic Accelerator
          o LCD/CRT simultaneous display capability
          o 1024x768 resolution for CRT
    * 32MB SDRAM DIMM Max 160MB (1 Dimm Expansion Slot)
    * Texas Instrument PCI 1225 PC Card Controller
          o Two Type II PCMCIA or One Type III slot (Zoom Video Support)
    * 2400mAh Li-Ion Battery
          o 2-2.5Hrs, Max APM enabled
          o 3Hrs Charge Time when Off
          o 8Hrs Charge Time when On
    * Li-Ion Bridge Battery
    * 2.8A/16V Mains Adapter


tried ubuntu server i and was able to install it and solve the loop problem. but besides that i don't know command line. and i need to install the PCMCIA drivers (wpc54g-v2) because is the only way to connect to the internet and i need tu setup and configurethe server (only for file sharing in intranet). what do you think i should do? thanks

---

### Post by nick_h on 2007-12-30
Depending on the version of the wpc54g-v2 card you have you may have to install ndiswrapper.  See [here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) for supported cards.  There is also a thread [here](http://ubuntuforums.org/showthread.php?t=354465).

For an introduction to the command line - [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

