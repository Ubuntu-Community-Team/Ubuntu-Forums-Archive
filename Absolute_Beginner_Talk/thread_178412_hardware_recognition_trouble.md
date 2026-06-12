---
title: "hardware recognition trouble"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by &amp;)ky#)^ on 2006-05-17
I'm worried about my Breezy system I just created because there are still many unknown devices listed in the device manager.  I know one is my wireless card, but the rest are a mystery to me.

Three of them are on the PCI bus.  0x1204, 0x0204, 0x2204, 0x3204, 0x4204, and 0x7204.  All of their vendors are VIA Technologies.

Next is on the IEEE 1394 bus.  Its vendor is unknown.  If that is firewire, I have no firewire devices connected.  I don't even own any.

There's a device listed as 0x001a.  Its vendor is Atheros.  It has a networking interface, so I figure it's my Dlink DWL-520+.

Finally, there's a device known as 0x00f4.  Its vendor is nVidia, so it's my 6600LE on AGP.

Why can't Ubuntu correctly identify these parts of my system?  How can I fix that?

---

### Post by KingBahamut on 2006-05-17
is that an lspci output? 

and if not, can you give that?

---

### Post by &amp;)ky#)^ on 2006-05-17
That isn't lspci output.  This is.

```
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0204
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1204
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2204
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3204
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4204
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7204
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]0000:00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f4 (rev a2)
```

---

### Post by Sef on 2006-05-17
> Next is on the IEEE 1394 bus. Its vendor is unknown. If that is firewire, I have no firewire devices connected.

Yes that is firewire.  It may just be detecting a  firewire port on your computer.  If you don't have one, then there is that option on your motherboard.

---

### Post by &amp;)ky#)^ on 2006-05-17
I do have a firewire port and a mini firewire port on my computer, but the question remains as to why it's listed as unknown.

---

### Post by &amp;)ky#)^ on 2006-05-18
Correction: My wireless card is a DWL-G510 Rev. B1. I've been able to use ndiswrapper to install the correct drivers. It confirms that the hardware is present. However, nothing has changed. Ubuntu still doesn't recognize it.  Plus, the card is still fussy sometimes. WTF?

---

### Post by &amp;)ky#)^ on 2006-05-18
I've upgraded to Dapper and here's my updated lspci info:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f4 (rev a2)

```

What I really need is for my graphics card and my wireless card to be recognized.  Please help.
It would be nice to have my firewire bus recognized, too.  Does Linux even support firewire?

---

