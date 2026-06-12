---
title: "Hello, will some one help me wireless"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Tlingit on 2007-11-05
Hello,
I am looking for my wireless card. I know i have one i found what is working on it and what is enabled but i cant find what kind or its chip set.

Do you think you could just help me find the chip set so i can find the windows driver for the ndiswrapper thank you very much

---

### Post by Whiffle on 2007-11-05
lspci -v     might help ya, is this a pcmcia   card or something else?

---

### Post by Atomic Dog on 2007-11-05
If you know the brand and model number you could google for the model and the word "chipset"  this may also yield a clue... but lspci should work fine.

---

### Post by Tlingit on 2007-11-05
Hello,

I was told the information i thought it was was not my card. Do you think some one could point it out for me please.

```
 lspci -v

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0



00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])

        Flags: bus master, fast devsel, latency 0

        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

        I/O behind bridge: 0000a000-0000afff

        Memory behind bridge: fa000000-fcffffff

        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff

        Capabilities: <access denied>



00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0

        Capabilities: <access denied>



00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0



00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel, IRQ 11

        I/O ports at 4c00 [size=64]

        I/O ports at 4c40 [size=64]

        Capabilities: <access denied>



00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: 66MHz, fast devsel



00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20

        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]

        Capabilities: <access denied>



00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        I/O ports at 09f0 [size=8]

        I/O ports at 0bf0 [size=4]

        I/O ports at 0970 [size=8]

        I/O ports at 0b70 [size=4]

        I/O ports at e400 [size=16]

        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])

        Subsystem: Hewlett-Packard Company Unknown device 2a38

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18

        I/O ports at 09e0 [size=8]

        I/O ports at 0be0 [size=4]

        I/O ports at 0960 [size=8]

        I/O ports at 0b60 [size=4]

        I/O ports at d000 [size=16]

        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>



00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])

        Flags: bus master, 66MHz, fast devsel, latency 0

        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128

        I/O behind bridge: 0000b000-0000bfff

        Memory behind bridge: fde00000-fdefffff

        Prefetchable memory behind bridge: fdd00000-fddfffff

        Capabilities: <access denied>



00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]

        Capabilities: <access denied>



00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16

        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

        I/O ports at cc00 [size=8]

        Capabilities: <access denied>



00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

        Flags: fast devsel

        Capabilities: <access denied>



00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

        Flags: fast devsel



00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

        Flags: fast devsel



00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

        Flags: fast devsel

        Capabilities: <access denied>



01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01dd (rev a1) (prog-if 00 [VGA])

        Subsystem: ASUSTeK Computer Inc. Unknown device 034b

        Flags: bus master, fast devsel, latency 0, IRQ 5

        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]

        Memory at e0000000 (64-bit, prefetchable) [size=256M]

        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]

        Expansion ROM at fcfe0000 [disabled] [size=128K]

        Capabilities: <access denied>



02:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])

        Subsystem: Hewlett-Packard Company Unknown device 2a54

        Flags: bus master, medium devsel, latency 32, IRQ 19

        Memory at fdeff000 (32-bit, non-prefetchable) [size=4K]

        Capabilities: <access denied>








```

---

### Post by Tlingit on 2007-11-05
[http://ubuntuforums.org/showthread.php?t=604005](http://ubuntuforums.org/showthread.php?t=604005)

---

### Post by oilchangeguy on 2007-11-05
don't start another thread on the same subject!

---

### Post by kast on 2007-11-05
have you tried the other option posted?

> Atomic Dog  	
Re: Hello, will some one help me wireless
If you know the brand and model number you could google for the model and the word "chipset" this may also yield a clue... but lspci should work fine.

i didn't see anything in your post, is this card not working, but you know its there? run a **ifconfig** and post that for me please.

---

### Post by Tlingit on 2007-11-06
Hello, thanks
I think i found the windows driver on the hp site but Ubuntu wont do anything with it. im not sure if it is even the one i need.   

```
eth0      Link encap:Ethernet  HWaddr 00:1A:92:99:E3:74  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:18 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)



wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:DF:B5:AF  

          inet6 addr: fe80::2c0:a8ff:fedf:b5af/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:576 (576.0 b)



wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-DF-B5-AF-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

---

