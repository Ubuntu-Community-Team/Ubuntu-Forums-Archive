---
title: "Do i need to install drivers !!!"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-08-17
Well i installed my ubuntu .. but i find the sound workin' fine ..but i dunno if my vga card is set up .. how would i know what hardware is installed where to locate their files .. and how do i install drivers  if they need to !! 
Thanks in advance

---

### Post by tseliot on 2006-08-17
If the sound works fine there's no need to install other drivers for that.

Let's have a look at your graphic card:

Post the ouput of this command:
```
lspci -v
```

---

### Post by LadyDoor on 2006-08-18
To find out what hardware you have, you might install the pciutils package (just use apt-get/aptitude/synaptic) and then run the command **lspci**. And I'm sorry to point this out like the English-centric American I am, but for future reference, a question mark (?) is the proper way to show that you're asking a question in English, not an exclamation point (!). An exclamation point means something's not a question and that you're probably shouting.

--Door

---

### Post by D_frag on 2006-08-21
Ok i typed the command and this is what i got 
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 5000
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e000 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (p rog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at e3202000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (p rog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at e3203000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio C ontroller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at a800 [size=256]
        I/O ports at ac00 [size=256]
        Memory at e3205000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [M aster SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        Memory at e3200000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at dc00 [size=16]
        Memory at e3201000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 0 1 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e3000000-e30fffff
        Prefetchable memory behind bridge: e3100000-e31fffff

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at e3204000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e400 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00008000-00008fff
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <available only to root>

0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <available only to root>

0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: e0000000-e2ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dff00000
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
        Flags: fast devsel

0000:01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a )
        Subsystem: Creative Labs SBLive! 5.1 Digital Model SB0220
        Flags: bus master, medium devsel, latency 32, IRQ 58
        I/O ports at 9000 [size=32]
        Capabilities: <available only to root>

0000:01:06.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev  0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9400 [size=8]
        Capabilities: <available only to root>

0000:01:08.0 Communication controller: 3Com Corp, Modem Division WinModem
        Subsystem: 3Com Corp, Modem Division: Unknown device 0060
        Flags: medium devsel, IRQ 10
        Memory at e3118000 (32-bit, prefetchable) [size=64]
        Memory at e3100000 (32-bit, prefetchable) [size=64K]
        Memory at e3110000 (32-bit, prefetchable) [size=32K]
        Capabilities: <available only to root>

0000:01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link La yer Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at e3004000 (32-bit, non-prefetchable) [size=2K]
        Memory at e3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:05:00.0 VGA compatible controller: nVidia Corporation NV37GL [Quadro FX 330 /GeForce PCX 5300] (rev a2) (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology: Unknown device 310e
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
        Expansion ROM at e2000000 [disabled] [size=128K]
        Capabilities: <available only to root>

---

