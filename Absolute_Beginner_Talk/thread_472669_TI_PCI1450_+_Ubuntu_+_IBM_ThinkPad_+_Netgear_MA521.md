---
title: "TI PCI1450 + Ubuntu + IBM ThinkPad + Netgear MA521 wireless laptop card"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-06-13
Ok - I am an absolute noob, and[ failed to get the wired connection]("http://ubuntuforums.org/showthread.php?t=471971")(thanks to all that helped me - MR. Crane!) - and I really hope someone can help me with the wireless connection!

I have the netgear wireless MA521 card, windows driver, instructions, which I hope to connect to an actiontec router. My chip set is: Intel Corporation 8257/8/9 [Ethernet Pro 100] (rev 09) 

IBM thinkpad a21m
256mb RAM
Previously had 2000 installed
9gb HD
Pent 3 700mhZ

Any ideas?

---

### Post by danny_kay1710 on 2007-06-13
If you have the windows driver you can install ndis wrapper you should be able to install it using this in terminal

```
sudo apt-get install ndiswrapper-utils
```

this should let you use your windows drivers in linux - not sure if your card would work tho 

hope it helps
danny-kay1710

---

### Post by ajskhan on 2007-06-13
EDIT: at this point I have no clue what I am doing!




Some more info:

:~$ lspci -v | grep -A 4 Eth

00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)

        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI

        Flags: bus master, medium devsel, latency 66, IRQ 11

        Memory at f4120000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at 1800 [size=64]

        Memory at f4100000 (32-bit, non-prefetchable) [size=128K]





:~$ sudo apt-get ndiswrapper-utils

Password:

E: Invalid operation ndiswrapper-utils

:~$ sudo apt-get install ndiswrapper

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package ndiswrapper








 lspci -v

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

        Flags: bus master, medium devsel, latency 64

        Memory at f8000000 (32-bit, prefetchable) [size=64M]

        Capabilities: <access denied>



00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, medium devsel, latency 128

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

        I/O behind bridge: 00002000-00002fff

        Memory behind bridge: f4200000-f5ffffff

        Prefetchable memory behind bridge: 30000000-300fffff



00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)

        Subsystem: IBM Thinkpad T20/T22/A21m

        Flags: bus master, medium devsel, latency 168, IRQ 11

        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]

        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176

        Memory window 0: 20000000-23fff000 (prefetchable)

        Memory window 1: 24000000-27fff000

        I/O window 0: 00001400-000014ff

        I/O window 1: 00001c00-00001cff

        16-bit legacy interface ports at 0001



00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)

        Subsystem: IBM Thinkpad T20/T22/A21m

        Flags: bus master, medium devsel, latency 168, IRQ 11

        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]

        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176

        Memory window 0: 28000000-2bfff000 (prefetchable)

        Memory window 1: 2c000000-2ffff000

        I/O window 0: 00003000-000030ff

        I/O window 1: 00003400-000034ff

        16-bit legacy interface ports at 0001



00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)

        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI

        Flags: bus master, medium devsel, latency 66, IRQ 11

        Memory at f4120000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at 1800 [size=64]

        Memory at f4100000 (32-bit, non-prefetchable) [size=128K]

        [virtual] Expansion ROM at 30100000 [disabled] [size=1M]

        Capabilities: <access denied>



00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem (prog-if 02 [16550])

        Subsystem: Intel Corporation Unknown device 2408

        Flags: medium devsel, IRQ 11

        I/O ports at 1840 [size=8]

        Memory at f4121000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

        Subsystem: IBM ThinkPad A20m

        Flags: bus master, slow devsel, latency 64, IRQ 11

        Memory at f4122000 (32-bit, non-prefetchable) [size=4K]

        Memory at f4000000 (32-bit, non-prefetchable) [size=1M]

        Capabilities: <access denied>



00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

        Flags: bus master, medium devsel, latency 0



00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])

        Flags: bus master, medium devsel, latency 64

        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]

        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]

        I/O ports at 1850 [size=16]



00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])

        Flags: bus master, medium devsel, latency 64, IRQ 11

        I/O ports at 1860 [size=32]



00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)

        Flags: medium devsel, IRQ 9



01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])

        Subsystem: IBM ThinkPad A20m/A21m

        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11

        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]

        I/O ports at 2000 [size=256]

        Memory at f4200000 (32-bit, non-prefetchable) [size=4K]

        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]

        Capabilities: <access denied>

---

### Post by ajskhan on 2007-06-13
More info:

:~$ lspci -v | grep -A 4 Eth

00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)

        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI

        Flags: bus master, medium devsel, latency 66, IRQ 11

        Memory at f4120000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at 1800 [size=64]

        Memory at f4100000 (32-bit, non-prefetchable) [size=128K]





:~$ sudo apt-get ndiswrapper-utils

Password:

E: Invalid operation ndiswrapper-utils

:~$ sudo apt-get install ndiswrapper

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package ndiswrapper








 lspci -v

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)

        Flags: bus master, medium devsel, latency 64

        Memory at f8000000 (32-bit, prefetchable) [size=64M]

        Capabilities: <access denied>



00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])

        Flags: bus master, 66MHz, medium devsel, latency 128

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

        I/O behind bridge: 00002000-00002fff

        Memory behind bridge: f4200000-f5ffffff

        Prefetchable memory behind bridge: 30000000-300fffff



00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)

        Subsystem: IBM Thinkpad T20/T22/A21m

        Flags: bus master, medium devsel, latency 168, IRQ 11

        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]

        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176

        Memory window 0: 20000000-23fff000 (prefetchable)

        Memory window 1: 24000000-27fff000

        I/O window 0: 00001400-000014ff

        I/O window 1: 00001c00-00001cff

        16-bit legacy interface ports at 0001



00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)

        Subsystem: IBM Thinkpad T20/T22/A21m

        Flags: bus master, medium devsel, latency 168, IRQ 11

        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]

        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176

        Memory window 0: 28000000-2bfff000 (prefetchable)

        Memory window 1: 2c000000-2ffff000

        I/O window 0: 00003000-000030ff

        I/O window 1: 00003400-000034ff

        16-bit legacy interface ports at 0001



00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)

        Subsystem: Intel Corporation EtherExpress PRO/100+ MiniPCI

        Flags: bus master, medium devsel, latency 66, IRQ 11

        Memory at f4120000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at 1800 [size=64]

        Memory at f4100000 (32-bit, non-prefetchable) [size=128K]

        [virtual] Expansion ROM at 30100000 [disabled] [size=1M]

        Capabilities: <access denied>



00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem (prog-if 02 [16550])

        Subsystem: Intel Corporation Unknown device 2408

        Flags: medium devsel, IRQ 11

        I/O ports at 1840 [size=8]

        Memory at f4121000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

        Subsystem: IBM ThinkPad A20m

        Flags: bus master, slow devsel, latency 64, IRQ 11

        Memory at f4122000 (32-bit, non-prefetchable) [size=4K]

        Memory at f4000000 (32-bit, non-prefetchable) [size=1M]

        Capabilities: <access denied>



00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)

        Flags: bus master, medium devsel, latency 0



00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])

        Flags: bus master, medium devsel, latency 64

        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]

        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]

        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]

        I/O ports at 1850 [size=16]



00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])

        Flags: bus master, medium devsel, latency 64, IRQ 11

        I/O ports at 1860 [size=32]



00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)

        Flags: medium devsel, IRQ 9



01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64) (prog-if 00 [VGA])

        Subsystem: IBM ThinkPad A20m/A21m

        Flags: bus master, stepping, medium devsel, latency 66, IRQ 11

        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]

        I/O ports at 2000 [size=256]

        Memory at f4200000 (32-bit, non-prefetchable) [size=4K]

        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]

        Capabilities: <access denied>

---

### Post by ajskhan on 2007-06-13
Anyone?

---

