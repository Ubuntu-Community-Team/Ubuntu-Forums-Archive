---
title: "Wireless cardbus"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Drizz on 2005-12-11
Hi All,
This is my second, but probably not last post on these forums ;) I never said hello before, so hello :rolleyes: 

Anyway I've installed ubuntu and I like what I've seen upto now. I say now as I can't get my wireless internet contection to work. I have a Belkin54g router but my pcmcia cardbus is a no name generic one. When I plug it in it appears in the network settings ([image](http://www.dropshipinfo.co.uk/images/card_found.jpg)) I then try to change the settings([image](http://www.dropshipinfo.co.uk/images/card_settings.jpg)) Please note I've tried static and DHCP. Then when I try to activate it I get an error ([image](http://www.dropshipinfo.co.uk/images/card_error.jpg)

I'm guessing I'll need to install something, a driver perhaps but I'm not sure which to get.

Connecting to the net via a cable works.

---

### Post by Lambert on 2005-12-11
If it's showing in the network list then the driver is working ok more then likely.

Are you running an open or share/restricted wep setting?

Post back the output of the following commands

sudo lshw -C network
lspci -v
iwconfig
ifconfig
sudo iwlist eth1 scan

---

### Post by Drizz on 2005-12-11
ok here's the results from the commands. in order.

> **sudo lshw -c network**
Hardware Lister (lshw) - B.02.03
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )


**lspci -v**
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400] Chipset Host Bri dge
        Subsystem: VIA Technologies, Inc.: Unknown device 7205
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge (prog-if 00 [N ormal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d1000000-d1ffffff
        Prefetchable memory behind bridge: f0000000-f3ffffff
        Capabilities: <available only to root>

0000:00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controlle r (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at 20000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

0000:00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at d0004000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 4
        I/O ports at 1c00 [size=32]
        Capabilities: <available only to root>

0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1c20 [size=32]
        Capabilities: <available only to root>

0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 80) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at 1c40 [size=32]
        Capabilities: <available only to root>

0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20  [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at d0004800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 4
        I/O ports at 1c60 [size=16]
        Capabilities: <available only to root>

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: medium devsel, IRQ 9
        I/O ports at 1000 [size=256]
        Capabilities: <available only to root>

0000:00:11.6 Communication controller: VIA Technologies, Inc. Intel 537 [AC97 Mo dem] (rev 80)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: medium devsel, IRQ 9
        I/O ports at 1400 [size=256]
        Capabilities: <available only to root>

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, medium devsel, latency 64, IRQ 4
        I/O ports at 1800 [size=256]
        Memory at d0004c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChr ome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0033
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 4
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT /Prism Duette] (rev 01)
        Subsystem: Intersil Corporation: Unknown device 0000
        Flags: bus master, medium devsel, latency 80, IRQ 5
        Memory at 20800000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>


**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:2C:8D:49
          inet6 addr: fe80::2c0:9fff:fe2c:8d49/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:205149 (200.3 KiB)  TX bytes:205149 (200.3 KiB)



**sudo iwlist eth1 scan**
eth1      No scan results

---

