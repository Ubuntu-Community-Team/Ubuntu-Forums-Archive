---
title: "Connecting to the Internet"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by jalfordvidman on 2006-05-30
Ok, on advice from a friend who mods at the SuSE forums, I ran these commands while connected to a cable modem to see if I could connect to the internet.

```
sudo cat /etc/resolv.conf
sudo ifconfig
sudo lspci -v
```

These are the results:

```
sudo lspci -v
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [40] AGP version 3.0
        Capabilities: [60] #08 [2001]

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)        Subsystem: Asustek Computer, Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [48] #08 [01e1]

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Asustek Computer, Inc.: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 5
        I/O ports at e000 [size=32]
        Capabilities: [44] Power Management version 2

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at e6002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at e6003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at e6000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] #0a [2080]
        Capabilities: [80] Power Management version 2

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: Asustek Computer, Inc. A7N8X Mainboard onboard nForce2 Ethernet
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at e6001000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e400 [size=8]
        Capabilities: [44] Power Management version 2

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Asustek Computer, Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: c0000000-dfffffff

0000:01:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs: Unknown device 1006
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at c000 [size=32]
        Capabilities: [dc] Power Management version 2

0000:02:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153 (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology: Unknown device 4050
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at d000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:02:00.1 Display controller: ATI Technologies Inc: Unknown device 4173
        Subsystem: Giga-byte Technology: Unknown device 4051
        Flags: 66MHz, medium devsel
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:549869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40606466 (38.7 MiB)  TX bytes:40606466 (38.7 MiB)

sudo cat /etc/resolv.conf
Password:
cat: /etc/resolv.conf: No such file or directory
```

Sorry this is so long, but I'd like to connect my Linux box to the internet if only to access this forum and perform get apt and such.

---

### Post by linuchsan on 2006-05-30
you have to load the forcedeth driver

---

### Post by jalfordvidman on 2006-05-30
Ok, extreeeeeeeeeme Linux noob here. How can I do this without my box being connected to the internet?

---

### Post by Sef on 2006-05-30
Are you running Dapper or Breezy?  Ubuntu or Kubuntu or other?

---

### Post by jalfordvidman on 2006-05-30
I'm running Ubuntu 5.10; which is Breezy, right?

---

