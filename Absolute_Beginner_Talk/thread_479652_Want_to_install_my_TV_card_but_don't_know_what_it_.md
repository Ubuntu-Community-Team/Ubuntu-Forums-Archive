---
title: "Want to install my TV card but don't know what it is"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Kouki on 2007-06-20
I've just downloaded tvtime and it doesn't detect my TV card.  I bought the card ages ago and I just cannot remember what it's called.

If I needed the driver in windows I'd go to device manager find out which card it is and then google for the drivers.  What's the equivalent method of doing this with Ubuntu.

In otherwords, I just need the ubuntu equivalent of device manager [-o<

---

### Post by jgrabham on 2007-06-20
Is there no serial number on the card?

---

### Post by orb9220 on 2007-06-20
open a term and enter: **lspci**

scroll thru list to see if it is there or copy and paste output here.

---

### Post by Kouki on 2007-06-20
> **orb9220 said:**
> open a term and enter: **lspci**

scroll thru list to see if it is there or copy and paste output here.

Sweet, that's what I needed:

stuart@stuart-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0b.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)



I'm guessing my TV card is the philips semiconductors video broadcast decoder.  Now lets see if I can find a driver.  Thanks for the tip!

---

### Post by orb9220 on 2007-06-20
Looks like it is a:

00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
which you can use goolge to track down card and website to get more info.

Or open up machine and pull the card out and look for manufacture info,

---

