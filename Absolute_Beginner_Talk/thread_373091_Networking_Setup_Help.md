---
title: "Networking Setup Help"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by punzak on 2007-02-28
Hello everyone,

I've just successfully completed a dual boot installation of ubuntu with xp.  It went relatively easily.  However I'm unable to get online at all.  I've tried a couple of things from some of these forums and the documentation to no avail.  One thing I tried was:

```
lspci -v | less
```

and found out that many of my drivers or whatever are:

capabilities: <access denied>

but I don't know what that means.  I need some hand holding.  Where should we start?

---

### Post by rccharles on 2007-02-28
> **punzak said:**
> Hello everyone,

I've just successfully completed a dual boot installation of ubuntu with xp.  It went relatively easily.  However I'm unable to get online at all.  I've tried a couple of things from some of these forums and the documentation to no avail.  One thing I tried was:

```
lspci -v | less
```

and found out that many of my drivers or whatever are:

capabilities: <access denied>

but I don't know what that means.  I need some hand holding.  Where should we start?

Many Ubuntu administrative commands require root level privileges to use.  To see everything add the sudo command in front of the actual command, so do:
sudo lspci -v | less

  enter you logon password when asked.


Now to your networking question...

1) How are you connecting to the internet?  Modem, dsl, cable, router, etc.

2) How did  you configure your network?

3) You need to post the results of two commands to this forum

applications > accessories > terminal

ifconfig

cat /etc/network/interfaces

one way to do that is to create a file of the results. Do:

script seedata
ifconfig
cat /etc/network/interfaces
exit

This will create the file seedata in your current directory.  You need to copy the results here.  To see the results in Ubuntu do, gedit seedata.

Robert

---

### Post by punzak on 2007-02-28
> 1) How are you connecting to the internet?

I have a wireless home network with a cable ISP.

> 2) How did you configure your network?

I'm not sure I understand what you're asking here

> 3) You need to post the results of two commands to this forum

Here's the printouts you asked for:

> sudo lspci -v | less

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5f00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5f00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5f00000
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
        Capabilities: [100] Virtual Channel
        Capabilities: [180] Unknown (5)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 225
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: medium devsel, IRQ 10
        I/O ports at 18c0 [size=32]

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at da000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number d8-a6-83-ff-ff-02-13-00

07:06.0 CardBus bridge: Texas Instruments Unknown device 8039
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at dc007000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=07, secondary=08, subordinate=0b, sec-latency=176
        Memory window 0: 68000000-69fff000 (prefetchable)
        Memory window 1: 6a000000-6bfff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

07:06.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a (prog-if 10 
[OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 169
        Memory at dc006000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

07:06.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

07:06.3 Class 0805: Texas Instruments Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

07:06.2 Mass storage controller: Texas Instruments Unknown device 803b
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

07:06.3 Class 0805: Texas Instruments Unknown device 803c (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 128, IRQ 185
        Memory at dc006800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

07:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 66, IRQ 58
        Memory at dc005000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 4000 [size=64]
        Capabilities: [dc] Power Management version 2
```

> ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:43:66:66  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe43:6666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17718 (17.3 KiB)  TX bytes:2422 (2.3 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:83:A6:D8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34699 errors:0 dropped:4629 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xa000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

> cat /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by punzak on 2007-03-01
I've been doing some reading about my wireless network card the Intel PRO 3945 ABG which I gather is a Centrino thing.  It seems that they either work or they don't within Ubuntu.  Again from what I gather it seems that I have two options.

1. Install Windows Drivers (ndiswrapper) or
2. Install Driver from [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

It seems to me that the second option is a "better" way to do things whereas the first option is the "easier" way to fix this.  Anyone want to weigh in on this?

In the meantime, I'll be reading through the installation instructions for both.

---

### Post by punzak on 2007-03-31
I was never able to get any of those methods to work, but when I upgraded to fiesty to works like magic.  This is awesome!

EDIT: I upgraded to the latest fiesty beta. 7.04 I believe

---

