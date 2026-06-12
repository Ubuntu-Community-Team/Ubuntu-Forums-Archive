---
title: "Bad Sound Quality"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by xs123 on 2007-10-25
I had good sound quality before.. but I was messing around trying to get 5.1 surround enabled.. with no luck getting that done I also managed to somehow make the sound quality on it really really crappy

Is there any way to reset sound settings, or.. get decent quality?

---

### Post by julian67 on 2007-10-25
To get any helpful answer you'll need to let people know at minimum what soundcard you are using and what it's connected to. Also useful would be to know which version of Ubuntu/Kubuntu/Xubuntu you are using so people know what tools you are using to configure sound. And how is the sound being output?  Analog? Via digital out?

---

### Post by xs123 on 2007-10-26
Integrated AC'97 8 chanel Audio (GA-M55SLI-S4 Mobo)

Ubuntu 7.10 

Analogue Out to Logitech X-530's

---

### Post by Crafty Kisses on 2007-10-26
> **xs123 said:**
> Integrated AC'97 8 chanel Audio (GA-M55SLI-S4 Mobo)

Ubuntu 7.10 

Analogue Out to Logitech X-530's

You should post the following output:
```
lspci
```

---

### Post by xs123 on 2007-10-26
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

---

### Post by xs123 on 2007-10-26
any ideas?

---

### Post by panteraz on 2007-10-26
I have exactly the same problem! 

I have Asus A8N-E with CK804 AC'97 Audio Controller and Logitech X-540 5.1 speakers.

I tried to enable 5.1 surround with no luck and now sound is bad quatity...

Can you plz help me enable the surround and fix the sound? Thanks!

lspci:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
05:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
05:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

thanks in advance!

e.g. xs123 it seems we have pretty the same hardware configuration! :D

---

