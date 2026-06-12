---
title: "Router not detected"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jyu617 on 2007-10-31
I have read numerous posts about people trying to troubleshoot with their internet but have not come across any incidences where the router was NOT detected.

I recently installed Ubuntu (straight up, no dual boot with Windows)  on my new computer and have been trying to get the internet working for about two weeks now to no avail.

The Setup:
Intel Core 2 Duo CPU E6550 with onboard ethernet card
2Wire 2701HG-B Gateway Wireless Router with DSL Modem
The PC is hooked to the router with an ethernet cable
The router is hooked to the phone jack.

I know that the router works because I have a laptop that is using the wireless capability of the router.

The Network Settings shows a 'Modem Connection' but no 'Wired Connection'

The output of *ifconfig * on the command line is:

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


Any suggestions?
Thanks in advanced!

---

### Post by greenlegacy on 2007-11-01
Sounds like your ethernet driver is not loaded properly.  What chip (or card) are you using for ethernet?

You'll have to then use a sudo modprobe command once you figure out what to put after modprobe.

After that you should see "eth0" in addition to "lo"

---

### Post by jyu617 on 2007-11-02
> What chip (or card) are you using for ethernet?

I have a built-in ethernet card, so how would I find out this information?

Thanks for the response!

---

### Post by greenlegacy on 2007-11-02
Can you post the results of
```

lspci -v

```

It should be in there.

---

### Post by jyu617 on 2007-11-02
```

00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02) (prog-if 00 [VGA])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 90200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 2140 [size=8]
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	Memory at 90100000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [d0] Power Management version 2

00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 90284900 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 20c0 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 20a0 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2080 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at 90284400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
	Subsystem: Intel Corporation Unknown device 0001
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 90280000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: 90300000-903fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Intel Corporation Unknown device 2940
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 90000000-900fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Intel Corporation Unknown device 2942
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: 90400000-904fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Intel Corporation Unknown device 2944
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: 90500000-905fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Intel Corporation Unknown device 2946
	Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: 90600000-906fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Intel Corporation Unknown device 2948
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 2060 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2040 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2020 [size=32]
	Capabilities: [50] Vendor Specific Information

00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at 90284000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] Vendor Specific Information

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
	Capabilities: [50] Subsystem: Intel Corporation Unknown device 5044

00:1f.0 ISA bridge: Intel Corporation Unknown device 2912 (rev 02)
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 2138 [size=8]
	I/O ports at 2154 [size=4]
	I/O ports at 2130 [size=8]
	I/O ports at 2150 [size=4]
	I/O ports at 2110 [size=16]
	I/O ports at 2100 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information

00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
	Subsystem: Intel Corporation Unknown device 5044
	Flags: medium devsel, IRQ 9
	Memory at 90284800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 2000 [size=32]

00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Intel Corporation Unknown device 5044
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 2128 [size=8]
	I/O ports at 214c [size=4]
	I/O ports at 2120 [size=8]
	I/O ports at 2148 [size=4]
	I/O ports at 20f0 [size=16]
	I/O ports at 20e0 [size=16]
	Capabilities: [70] Power Management version 3
	Capabilities: [b0] Vendor Specific Information

02:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Marvell Technology Group Ltd. Unknown device 6101
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 1018 [size=8]
	I/O ports at 1024 [size=4]
	I/O ports at 1010 [size=8]
	I/O ports at 1020 [size=4]
	I/O ports at 1000 [size=16]
	Memory at 90000000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

```

---

### Post by greenlegacy on 2007-11-02
This problem may be beyond me.  It doesn't look good that your ethernet controller was not listed there or that everything said "unknown device".  There may be an issue with the kernel.

One last thing to try though.

Type this in the terminal:

```

dmesg > ~/boot.msg

```

Which should save a file called "boot.msg " to your home directory.  Just attach that to a post here (it'll be kind of long which is why I'm having you do it this way).

---

### Post by jyu617 on 2007-11-03
Any other suggestions?

---

### Post by jyu617 on 2007-11-13
Bump

---

