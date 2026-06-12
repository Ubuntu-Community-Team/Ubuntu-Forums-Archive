---
title: "Do I Have A Video Card?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-05-04
Hey guys. I'm not sure if I quite have a video card installed in my laptop. Whenever I watch videos on YouTube or look at a bunch of hi-res photographs, the processor fan goes to full speed (which is really loud on this Averatec laptop). Also, whenever I try to play an emulator, the video and the sound both drag immensely, and the fan also goes to full speed. It did this when I had Windows too, so I don't think it's a driver issue.  It seems like due to the lack of a video card, the graphics are being rendered through the processor instead. What is the command I would run to check and see if I even have a video card?

---

### Post by Bachstelze on 2007-05-04
You do have some kind of video adapter, or else you would see nothing on your screen. *lspci* will help you find out what it is.

---

### Post by k1001001 on 2007-05-04
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:00:0b.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

It looks like I do have a video adapter. Does this also mean I don't have a video card?

---

### Post by Bachstelze on 2007-05-04
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

This is your video card. Now, you need to install drivers for it.

---

### Post by k1001001 on 2007-05-04
OK I've got the driver from the manufacturer. (Thankfully they have open source drivers.) Where would I find information as to how to install this driver?

---

### Post by fenian on 2007-05-04
Install the openchrome drivers following the instructions[ here]("https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29").

---

### Post by rich.bradshaw on 2007-05-04
It's a built in "card", not a seperate one. Laptops are almost always like that.

---

