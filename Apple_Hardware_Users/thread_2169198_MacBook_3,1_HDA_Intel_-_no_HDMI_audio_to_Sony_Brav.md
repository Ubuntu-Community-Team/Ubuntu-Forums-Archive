---
title: "MacBook 3,1 HDA Intel - no HDMI audio to Sony Bravia"
date: 2013-08-21
forum: Apple Hardware Users
---

### Post by connie-q on 2013-08-21
I've searched all through this forum and thought I've founds similar problems, none of the "solutions" seem to be able to help me.  I've even searched this [thread]("http://ubuntuforums.org/showthread.php?t=1625402&highlight=HDMI+Macbook"), but it hasn't been updated in a couple of years and none of the fixes have solved my problem.

I am currently running Ubuntu 12.04 LTS on my MacBook 3,1 and I'm trying to connect to my Sony Bravia HDTV through HDMI.  I'm actually using a miniDVI - HDMI adapter, but the video is perfect.  However, I am unable to get sound to work.  PulseAudio doesn't read the HDMI as an audio output, and neither does Sound Settings.  Below are the results I get from various terminal commands.

lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at 90100000 (64-bit, non-prefetchable) [size=1M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: intelfb, i915


00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, fast devsel, latency 0
	Memory at 90200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 30c0 [size=32]
	Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 30a0 [size=32]
	Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at 90704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 90700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel


00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: 90600000-906fffff
	Prefetchable memory behind bridge: 0000000090b00000-0000000090cfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: 90500000-905fffff
	Prefetchable memory behind bridge: 0000000090000000-00000000900fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 90400000-904fffff
	Prefetchable memory behind bridge: 0000000090800000-0000000090afffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 3080 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3060 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3040 [size=32]
	Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at 90704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Memory behind bridge: 90300000-903fffff
	Capabilities: <access denied>


00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt


00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 30e0 [size=16]
	Kernel driver in use: ata_piix


00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Apple Inc. Device 00a1
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 30f8 [size=8]
	I/O ports at 311c [size=4]
	I/O ports at 30f0 [size=8]
	I/O ports at 3118 [size=4]
	I/O ports at 3020 [size=16]
	I/O ports at 4000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix


00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Apple Inc. Device 00a1
	Flags: medium devsel, IRQ 10
	Memory at 90705000 (32-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801


02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
	Subsystem: Apple Inc. Device 0088
	Physical Slot: 4
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 90500000 (64-bit, non-prefetchable) [size=16K]
	Memory at 90000000 (64-bit, prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb


03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
	Subsystem: Marvell Technology Group Ltd. Device 00ba
	Physical Slot: 5
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at 90400000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Expansion ROM at 90800000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2


04:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 61) (prog-if 10 [OHCI])
	Subsystem: LSI Corporation FW322/323
	Flags: bus master, fast Back2Back, medium devsel, latency 248, IRQ 19
	Memory at 90300000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci



```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

If you need more info, or know of a workaround that will help, please let me know.  Thank you! :)

P.S. As an aside, I had upgraded through to 13.04 and not even video would work through HDMI, so I ended up reinstalling 12.04 LTS so I could at least have that much.  Any idea why 13.04 would've have supported HDMI?  Or is it just because it's still new?

---

