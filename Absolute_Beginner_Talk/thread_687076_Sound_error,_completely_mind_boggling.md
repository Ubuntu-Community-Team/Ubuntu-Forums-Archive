---
title: "Sound error, completely mind boggling"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Sonastylol on 2008-02-03
Hey, first of all I'd like to say Im on Ubuntu, finally decided to give it a try on this old laptop.

I didnt even know that somewhere inside my speakers, noise could be emitted..

For some reason, while running ubuntu, when I play a song or watch a video, etc., etc., noise is playing from both inside the laptop and thru the speakers. If i mute my sound or lower the sound, the noise still plays from inside the laptop, just not thru the speakers.


This is really annoying. So I opened my volume control and noticed that if I drop Master Volume, the sound plays from inside the computer. If I drop the bar that says PCM the central sound stops playing, but SO DOES the sound from the main speakers.


What the **** is going on here? Haha thank you for all your help.

---

### Post by Crafty Kisses on 2008-02-03
> **Sonastylol said:**
> Hey, first of all I'd like to say Im on Ubuntu, finally decided to give it a try on this old laptop.

I didnt even know that somewhere inside my speakers, noise could be emitted..

For some reason, while running ubuntu, when I play a song or watch a video, etc., etc., noise is playing from both inside the laptop and thru the speakers. If i mute my sound or lower the sound, the noise still plays from inside the laptop, just not thru the speakers.


This is really annoying. So I opened my volume control and noticed that if I drop Master Volume, the sound plays from inside the computer. If I drop the bar that says PCM the central sound stops playing, but SO DOES the sound from the main speakers.


What the **** is going on here? Haha thank you for all your help.
Hmmm, post the following output: ```
lspci
```

---

### Post by Sonastylol on 2008-02-03
**Thanks Codename**

> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


---

### Post by Sonastylol on 2008-02-03
help?   :(

---

### Post by Sonastylol on 2008-02-04
last post of the night, thank you

---

