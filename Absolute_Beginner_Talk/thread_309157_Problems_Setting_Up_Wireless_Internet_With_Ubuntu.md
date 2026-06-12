---
title: "Problems Setting Up Wireless Internet With Ubuntu"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by rhyswynne on 2006-11-29
I installed Ubuntu last night as a dual boot from Windows XP. Setup went okay, but I have had problems setting up my wireless card with it to work with Ubuntu. So far I have installed the ndiswrapper module.

I have installed what I believe was the driver (my dongle is a Inventel UR054 (RO1) - it comes with Wanadoo Broadband, however I'm no longer on Wanadoo). I have used the ndiswrapper -l command and it says that the both the driver and hardware is present, however when I go to the Network Tools, the wireless connection is shown to be not configured.

I apologise for being a newbie, and I am currently at work (so I cannot access crucial data), however I would like some advice what I am doing wrong? I feel it could be the driver that is at fault. Any help would be grateful, failing that a list of things that I can do to provide you with further information on my problem, hardware, configuration etc.

Thanks in advance

---

### Post by rlozano on 2006-11-29
can you post your lspci -v result here?

and what do you have if do iwconfig?

---

### Post by drphilngood on 2006-11-29
You may find this information to be helpful:

[WifiDocs]("https://help.ubuntu.com/community/WifiDocs")

and this troubleshooting guide, in particular:

[Wireless TroubleShooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Good luck!

---

### Post by rhyswynne on 2006-11-29
Thanks for your help so far. I'll get back to you with the information.

I should point out though (if I may) that my device attaches to a USB port. Therefore (reading the guide), wouldn't you like to see the lsusb -v as opposed to the lspci -v command?

Apologies, I didn't mention it, just trying to save some time for everybody concerned :)

---

### Post by rhyswynne on 2006-11-29
Right, ran a few of the commands in the terminal, here's what I get for lspci -v

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
        Subsystem: ASRock Incorporation Unknown device 0741
        Flags: bus master, medium devsel, latency 0
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        Memory behind bridge: cdd00000-cfefffff
        Prefetchable memory behind bridge: bda00000-cdbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at 0c00 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
        Subsystem: ASRock Incorporation Unknown device 5513
        Flags: bus master, medium devsel, latency 128
        I/O ports at ff00 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at dc00 [size=256]
        I/O ports at d800 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 185
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 193
        Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASRock Incorporation Unknown device 0900
        Flags: bus master, medium devsel, latency 32, IRQ 201
        I/O ports at d400 [size=256]
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 30000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0a.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04) (prog-if 00 [Generic])
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 169
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d000 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev c1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at cfee0000 [disabled] [size=128K]
        Capabilities: <access denied>

```

lsusb -v is long, so I got lsusb. If anybody knows how I can get the entire of lsusb -v, please let me know!

```
Bus 003 Device 003: ID 1435:0427  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06a2:0033 Topro Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 093a:2460 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

And finally, iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

Anything else needed, as I'm home for a while.

---

