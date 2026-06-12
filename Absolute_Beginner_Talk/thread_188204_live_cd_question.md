---
title: "live cd question"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by skinnygmg on 2006-06-03
if the dapper live cds for k/ubuntu don't work with my wifi card, will installing dapper hose my connection.  i tried upgrading from breezy (everything worked out of the box, even the wifi) but got an error half way through.  i had to finish manualy.  i got dapper installed, but my wifi and wired connections didn't work.  i tried to get it working, but without help from you guys, i couldn't get it working.  i did a fresh install of breezy, and downloaded k&u dapper.  when i run them live, no network connections work.  will things be different if i do an install?  why would breezy have drivers for my hardware, but not dapper?  any input would be great.  thanks.

---

### Post by adam.tropics on 2006-06-03
Not ideal and probably not what you're after, but if you are not sure, then before installing, just save to media whatever driver packages you need from the computer you are using now, and install them once the install has finished. Keep an eye on dependancies.

---

### Post by skinnygmg on 2006-06-03
where can i find the driver package?

---

### Post by taurus on 2006-06-03
What is the make and model of your card then???

---

### Post by skinnygmg on 2006-06-03
it's kind of generic.  it doesn't even say the brand name on it.  i got it off ebay for 15 bucks shipped.  breezy worked w/o any problem.  in device manager it says unknown device type net.80211.  i may d/l the breezy live cd and see if it configures it correctly.  i just don't know if the functionality of the live cd is a good indication of a hdd install's functionality

---

### Post by deevnil on 2006-06-04
Does the lspci (lspci -v) utility say what kind of network card you have? I think you can get a command prompt from the live cd by hitting ctrl-alt-f2?

---

### Post by skinnygmg on 2006-06-04
this is what i get in breezy (where connection is working)

```

lspci -v
0000:00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev 04)
        Flags: bus master, medium devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e8100000-edffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 16, IRQ 9
        Memory at fff70000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:04.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Hewlett-Packard Company: Unknown device 0018
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 10000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10400000-107ff000 (prefetchable)
        Memory window 1: 10800000-10bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:00:04.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Hewlett-Packard Company: Unknown device 0018
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 10001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 10c00000-10fff000 (prefetchable)
        Memory window 1: 11000000-113ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
        Flags: medium devsel

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
        Subsystem: ALi Corporation ALI M1533 Aladdin IV ISA Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
        Subsystem: Hewlett-Packard Company: Unknown device 0018
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 8400 [size=256]
        Capabilities: <available only to root>

0000:00:08.1 Communication controller: ESS Technology ESS Modem (rev 12)
        Subsystem: Hewlett-Packard Company: Unknown device 0018
        Flags: medium devsel, IRQ 5
        I/O ports at 8800 [size=256]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if 8a [Master SecP PriP])
        Subsystem: ALi Corporation M5229 IDE
        Flags: bus master, medium devsel, latency 64, IRQ 255
        I/O ports at 1000 [size=16]
        Capabilities: <available only to root>

0000:00:10.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
        Subsystem: Accton Technology Corporation EN2242 10/100 Ethernet Mini-PCI Card
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 8c00 [size=256]
        Memory at e8001000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 0018
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at ec000000 (32-bit, non-prefetchable) [size=32M]
        Memory at e8400000 (32-bit, non-prefetchable) [size=4M]
        Memory at ea000000 (32-bit, non-prefetchable) [size=32M]
        Memory at e8100000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <available only to root>


```

and this issue is with all connections.

---

