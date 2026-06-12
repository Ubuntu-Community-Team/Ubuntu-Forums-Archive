---
title: "[SOLVED] grep not working"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-12-16
I'm trying to check on some things using the "grep" command and its not showing me anything.  For instance if I type into terminal this 

lspci | grep audio

you would expect a list of devices etc., but I get nothing.  I've checked and synaptic says I have "grep" installed.

Any ideas?

---

### Post by llamakc on 2007-12-16
Is there an entry with "audio" when you just run `lspci`?

---

### Post by Riffer on 2007-12-16
there is no entry.  It goes right back to the command prompt.

---

### Post by Riffer on 2007-12-16
Sorry it took me awhile to really understand what you were asking me, here is the output

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

From what I can see you're right there is no audio.  Which makes little sense to me as I have sound.

---

### Post by handaxe on 2007-12-16
Edited: sorry I see  now what you mean. You know what grep does.

Can you see anything about audio under Device Manager aka Hardware Information (under Gnome)?
HA

---

### Post by Riffer on 2007-12-16
Yes I do :).  Its listed as an usb audio device.  Thanks foir your help.  I'm marking this solved.

---

