---
title: "Realtek Headphone"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by gnama on 2006-11-20
I have a really generic headset. But when I call skype I get an error usually saying it isn't configured. I did some of the Comprehensive Sound Problem Solutions. When I do the first few I get this. 

warrion@warrion-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
warrion@warrion-laptop:~$ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at d2000000 (32-bit, prefetchable) [size=32M]
        Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: e0000000-efffffff

0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0001000 (32-bit, non-prefetchable) [size=4K]

0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0002000 (32-bit, non-prefetchable) [size=4K]

0000:00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 201
        Memory at d0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: 66MHz, medium devsel
        I/O ports at 8060 [size=16]
        Memory at d0004000 (32-bit, non-prefetchable) [size=1K]

0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 185
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8070 [size=16]

0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342 (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=168
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 50000000-51ffffff

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Toshiba America Info Systems: Unknown device ff01
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 193
        Memory at d0004400 (32-bit, non-prefetchable) [size=256]

0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 193
        Memory at d0004800 (32-bit, non-prefetchable) [size=256]

0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff02
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 185
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Askey Computer Corp.: Unknown device 7084
        Flags: bus master, medium devsel, latency 168, IRQ 209
        Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 128, IRQ 201
        I/O ports at a000 [size=256]
        Memory at d0210000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0211000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 52000000-53fff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

---

### Post by gnama on 2006-11-20
Help please!

---

