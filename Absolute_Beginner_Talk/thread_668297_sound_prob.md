---
title: "sound prob"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by saurabh srivastava on 2008-01-15
hi
my laptop sound is not working properly.when i start my laptop some time it works and some time ot not...mostly not.
and also vlc not working properly...video is not displaying in full screen and when i increase sound of vlc it display no video.
help me.:confused:

---

### Post by balaknair on 2008-01-15
Hi
Could you give a little more information about your system
The basic sound info can be obtained by typing the following commands in a terminal(Application menu > Accessories > Terminal)
aplay -l
lspci -v

Enter these two commands and please post the output here

---

### Post by saurabh srivastava on 2008-01-15
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d2000000-d3ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: d4000000-d40fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d4544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d4100000-d41fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d4544400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1375
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at d4000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 66, IRQ 20
        Memory at d4100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at d4101000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at d4101800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at d4101c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 11
        Memory at d4102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 11
        Memory at d4102400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by saurabh srivastava on 2008-01-15
now wat sud i do

---

### Post by balaknair on 2008-01-15
OK try this

Open a terminal and enter
```
sudo nano /etc/modprobe.d/alsa-base
```

scroll down to the bottom of the page(use the page down or down arrow key)
and paste this in the last line

```
options snd-hda-intel model=laptop-hp
```

Save and exit and reboot.

---

