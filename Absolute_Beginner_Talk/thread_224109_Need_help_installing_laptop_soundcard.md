---
title: "Need help installing laptop soundcard"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by kdogar on 2006-07-27
hi folks...

im a total n00b when it comes to Ubuntu... ive been following ur threads and it helped me install my ubuntu OS... however im have a weird problem now... i cant seem to install my sound card!! 

i read the guide to installing sound cards on the forums... heres all the output i can provide u

**on typing aplay - l**

aplay: device_list:221: no soundcards found...

**on typing lspci -v **

0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Me mory Controller Hub (rev 11)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)  (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: f7f00000-fdffffff
        Prefetchable memory behind bridge: 14000000-140fffff

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03) (pro g-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0a, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f7d00000-f7dfffff
        Prefetchable memory behind bridge: 10000000-13ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 (rev 03) (prog-i f 80 [Master])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0
        I/O ports at cff0 [size=16]

0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 03)  (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at cf80 [size=32]

0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 03)  (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at cf60 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Au dio (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ce00 [size=256]
        I/O ports at cdc0 [size=64]

0000:00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem (rev 03) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ca00 [size=256]
        I/O ports at c980 [size=128]

0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=32M]
        Memory at fbc00000 (32-bit, non-prefetchable) [size=4M]
        Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
        Memory at f7ff8000 (32-bit, non-prefetchable) [size=32K]
        Expansion ROM at 14000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
        Subsystem: Intel Corporation EtherExpress PRO/100 VE
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f7dff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at df40 [size=64]
        Capabilities: <available only to root>

0000:02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbu s Bridge with ZV Support (rev 31)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at f7d00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=0
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

0000:02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbu s Bridge with ZV Support (rev 31)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at f7d01000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=0
        Memory window 0: 12000000-13fff000 (prefetchable)
        Memory window 1: 18000000-19fff000
        I/O window 0: 0000d800-0000d8ff
        I/O window 1: 0000dc00-0000dcff
        16-bit legacy interface ports at 0001

and finally when i try to run 

alsamixer i get a[COLOR="DarkOrange"]lsamixer: function snd_ctl_open failed for default: No such device[/COLOR]

so now i have no idea whatsoever on how im suppossed to install this piece of hardware that is detected but not installed... any help or insight into this problem would be much appreciated... id hate to stop using Ubuntu just coz of this minor innconvenience...

ciao

---

### Post by EnochRoot on 2006-08-07
Hi there,

the problem with alsamixer you reported
> alsamixer i get alsamixer: function snd_ctl_open failed for default: No such device
is quite simple: You must have root privileges to do this. Either login as root or type in a "sudo alsamixer".

HTH

---

