---
title: "can not connect with my edimax wireless lan cardbus"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by wannabesurfer on 2006-06-16
Hi
I have just bought a new cardbus to connect wirelessly, but ubuntu does not recognice it, when looking in the netwoork, nothing comes up. When restart, the computer stalls until I remove the card.

What should I do?
The way I am connected now is thru the router with eth cable. 
any help or suggestions be greatly apreciated.

sam****

---

### Post by wannabesurfer on 2006-06-16
Here are some tests i did

 lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 128
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f4000000-f7ffffff

0000:00:03.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
        Subsystem: O2 Micro, Inc. OZ6812 CardBus Controller
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 9
        Memory at 24020000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00002000-000020ff
        16-bit legacy interface ports at 0001

0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 173, IRQ 11
        I/O ports at 1400 [size=256]
        Memory at f0000000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 24000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:05.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 00 [Generic])
        Subsystem: Uniwill Computer Corp: Unknown device 4000
        Flags: medium devsel, IRQ 10
        I/O ports at 1080 [size=64]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 02)
        Subsystem: ESS Technology: Unknown device 8898
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 1800 [size=64]
        I/O ports at 10c0 [size=16]
        I/O ports at 1070 [size=16]
        I/O ports at 1064 [size=4]
        I/O ports at 1060 [size=4]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 1050 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 10e0 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev a2) (prog-if 00 [VGA])
        Subsystem: Silicon Motion, Inc. SM720 Lynx3DM
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 9
        Memory at f4000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

plog
Jun 16 19:59:28 localhost pppd[3415]: Timeout waiting for PADO packets
Jun 16 19:59:28 localhost pppd[3415]: Unable to complete PPPoE Discovery
Jun 16 20:00:33 localhost pppd[3415]: Timeout waiting for PADO packets
Jun 16 20:00:33 localhost pppd[3415]: Unable to complete PPPoE Discovery
Jun 16 20:01:23 localhost pppd[4989]: Plugin rp-pppoe.so loaded.
Jun 16 20:01:23 localhost pppd[4991]: pppd 2.4.4b1 started by wannabe, uid 1000

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:C0:15:29
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x1400

sudo dhclient Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:a0:cc:c0:15:29
Sending on   LPF/eth0/00:a0:cc:c0:15:29
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21

---

### Post by wannabesurfer on 2006-06-16
moreover I tried this to check my connection in terminal>
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

people I need help

---

