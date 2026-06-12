---
title: "Wireless chipset issues"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by drunkardivan on 2007-11-12
OK, I'm a total n00b. I admit that freely. This is my first linux experience. 

I have Gutsy running on an emachines w340, and it has an RT8180 wireless chipset.

Here's the thing- when I run lspci -nn | grep Network , nothing pops up. How can I work around this?

---

### Post by reckless2k2 on 2007-11-12
do use a favor and post the results of this:

```
lspci -vv
```

---

### Post by drunkardivan on 2007-11-12
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fa100000-fa8fffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000bfefffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2) (prog-if 00 [VGA])
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at b2000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at b1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 10
        Region 4: I/O ports at 3040 [size=64]
        Region 5: I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at b0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at b0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at b0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (750ns min, 250ns max)
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        Region 4: I/O ports at 3080 [size=16]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=64
        I/O behind bridge: 00006000-00006fff
        Memory behind bridge: b3400000-b34fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR+
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 19
        Region 0: Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Gateway 2000 Unknown device 0317
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at b0006000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at 3090 [size=8]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 6000 [size=256]
        Region 1: Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

---

### Post by drunkardivan on 2007-11-12
Oh, and I don't know if this matters or not, but I can get on unencrypted networks with these settings, just not encrypted ones- either WEP or WPA.

---

### Post by houstonbofh on 2007-11-12
A quick search found this.  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86149](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86149)  You may be out of luck with this card.  You can try ndiswrapper as there seem to have been some successes with that.

---

### Post by guillelo11 on 2007-11-12
Try to search your chipset [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by drunkardivan on 2007-11-12
> **houstonbofh said:**
>  You may be out of luck with this card.

So, would an external card be my only hope then?

---

### Post by houstonbofh on 2007-11-12
> **drunkardivan said:**
> So, would an external card be my only hope then?
Let me start with **this is only my opinion, not fact.** :)  Some WiFi cards are a pain in the *** under any OS.  And some can only be made to work in Linux by sacrificing a young goat, or some such.  Others can work easily, but have flaky performance, or are not supported by all the tools (WPA supplicant, Network Manager, kismet, hibernation...) or just do not function well with some apps.  I value my sanity more than this!

Additionally, why support vendors that do not support us?  I just have a problem giving money to someone who does not value me as a customer.  So, some links...

Philosophy
[http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html) (note that HP/Compaq also blacklist minipci)
There are other well supported cards (Atheros and the like) but they have closed firmware.  I figure if you are buying a card anyway, buy an open one.

A list
[http://ralink.rapla.net/](http://ralink.rapla.net/)

Every time I buy a card it is on the list above.  Every time it just works out of the box with full functionality.  It runs native in Linux which means less overhead, and better speeds.  I am currently connected with this card. [http://www.airlink101.com/products/awlc5025.html](http://www.airlink101.com/products/awlc5025.html)  Setup was limited to inserting the card. Done.

---

### Post by rustybronco on 2007-11-12
> 06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
[http://ubuntuforums.org/showthread.php?t=571188&highlight=RTL-8185](http://ubuntuforums.org/showthread.php?t=571188&highlight=RTL-8185)

---

### Post by rustybronco on 2007-11-13
look at [http://ubuntuforums.org/showthread.php?t=580309](http://ubuntuforums.org/showthread.php?t=580309)

---

