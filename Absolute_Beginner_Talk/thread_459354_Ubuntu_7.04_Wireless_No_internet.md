---
title: "Ubuntu 7.04 Wireless No internet"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Paddatjie on 2007-05-30
I intalled Ubuntu 7.04 and cofigured my wireless network.  The wireless network is working 100%, as I can access the other WIN XP machines via the wireless. The problem I have is that when connecting to the internet via Firefox, this is unsuccessful. I have checked that there are no proxy settings, as I don't have a proxy server. PLEASE Help:(

---

### Post by kernel tom on 2007-05-30
which wireless card do you have installed? is your wireless network WEP/WPA/WPA2 secured?

is your wireless device turned on?
check this by going into your Network settings and seeing if it is checked off as enabled

---

### Post by DJ Wings on 2007-05-30
Fire up the terminal, and post the results of ```
lspci -v
```

---

### Post by Paddatjie on 2007-05-30
nat@nat:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, fast devsel, latency 0 
        Capabilities: <access denied> 
 
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
        I/O behind bridge: 00002000-00002fff 
        Memory behind bridge: b8100000-b81fffff 
        Prefetchable memory behind bridge: c8000000-cfffffff 
        Capabilities: <access denied> 
 
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, fast devsel, latency 0, IRQ 16 
        Memory at b8000000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
        I/O behind bridge: 00003000-00003fff 
        Memory behind bridge: bc000000-bfffffff 
        Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff 
        Capabilities: <access denied> 
 
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
        I/O behind bridge: 00004000-00004fff 
        Memory behind bridge: c0000000-c3ffffff 
        Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff 
        Capabilities: <access denied> 
 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 19 
        I/O ports at 1800 [size=32] 
 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 20 
        I/O ports at 1820 [size=32] 
 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 18 
        I/O ports at 1840 [size=32] 
 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 16 
        I/O ports at 1860 [size=32] 
 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 19 
        Memory at b8004000 (32-bit, non-prefetchable) [size=1K] 
        Capabilities: <access denied> 
 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216 
        I/O behind bridge: 00005000-00005fff 
        Memory behind bridge: c4000000-c40fffff 
        Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff 
        Capabilities: <access denied> 
 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0 
 
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 0, IRQ 18 
        I/O ports at 01f0 [size=8] 
        I/O ports at 03f4 [size=1] 
        I/O ports at 0170 [size=8] 
        I/O ports at 0374 [size=1] 
        I/O ports at 1880 [size=16] 
 
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: medium devsel, IRQ 11 
        I/O ports at 18e0 [size=32] 
 
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600] (prog-if 00 [VGA]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, fast devsel, latency 0, IRQ 16 
        Memory at c8000000 (32-bit, prefetchable) [size=128M] 
        I/O ports at 2000 [size=256] 
        Memory at b8100000 (32-bit, non-prefetchable) [size=64K] 
        [virtual] Expansion ROM at b8120000 [disabled] [size=128K] 
        Capabilities: <access denied> 
 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10) 
        Subsystem: LG Electronics, Inc. Marvell 88E8036 Fast Ethernet Controller (LGE) 
        Flags: bus master, fast devsel, latency 0, IRQ 16 
        Memory at bc000000 (64-bit, non-prefetchable) [size=16K] 
        I/O ports at 3000 [size=256] 
        Capabilities: <access denied> 
 
06:00.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 168, IRQ 16 
        Memory at fedff000 (32-bit, non-prefetchable) [size=4K] 
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176 
        Memory window 0: 30000000-33fff000 (prefetchable) 
        Memory window 1: 34000000-37fff000 
        I/O window 0: 00005000-000050ff 
        I/O window 1: 00005400-000054ff 
        16-bit legacy interface ports at 0001 
 
06:00.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller (prog-if 10 [OHCI]) 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 32, IRQ 16 
        Memory at c4004000 (32-bit, non-prefetchable) [size=2K] 
        Memory at c4000000 (32-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
 
06:00.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller 
        Subsystem: LG Electronics, Inc. Unknown device 000e 
        Flags: bus master, medium devsel, latency 57, IRQ 16 
        Memory at c4005000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied> 
 
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05) 
        Subsystem: Intel Corporation Unknown device 2702 
        Flags: bus master, medium devsel, latency 32, IRQ 18 
        Memory at c4006000 (32-bit, non-prefetchable) [size=4K] 
        Capabilities: <access denied>

---

### Post by kernel tom on 2007-05-30
ok so your wireless card is recognized by ubuntu, thats great

make sure it's enabled tho in your Network settings, and you may have to type in the exact name of your network for first time connectivity... 

after your connected i'd get an app like wlassistant or something you fancy that will scan for networks in the area that you can connect to

---

### Post by Paddatjie on 2007-05-30
I have a dual boot system, with Windows XP. The wireless network works fine as well as the internet if I am in XP, with Ubuntu the network part is fine but it does not connect to the internet. This is installed on a LG Laptop, thanks for the help!

---

### Post by kernel tom on 2007-05-30
confused a little now,

so you are connected to your network?
but not connected to the internet?
you can't use any other apps like an IM client or email?

---

### Post by Paddatjie on 2007-05-30
No, I have a network set up in my house with two other pc's. I can see these pc's and go on to their harddrives, but I can not connect to the internet using ubuntu. If I however use XP on my Laptop I can connect to the other pc's and to the internet.

---

### Post by Paddatjie on 2007-05-30
so you are connected to your network? Yes
but not connected to the internet? Yes
you can't use any other apps like an IM client or email? Yes

---

### Post by sharperguy on 2007-05-30
I can't think why this would happen

The only thing I can think of is that the router you are using requires unusual configuration on the client machines to let them onto the net. (do they exist?)

Did you have to run any sort of setup program on XP after the router was configured?

Also it might help to tell us the name of the router,

---

### Post by Paddatjie on 2007-05-30
The only thing I can think of is that the router you are using requires unusual configuration on the client machines to let them onto the net. (do they exist?)[COLOR="Red"] Not that I no of1[/COLOR]

Did you have to run any sort of setup program on XP after the router was configured? [COLOR="red"]No![/COLOR]

Also it might help to tell us the name of the router, [COLOR="red"]LG LWG 5404R[/COLOR]

---

### Post by sharperguy on 2007-05-30
:/ oh well there goes that idea,

Ill google the router anyway and see if it throws up anything

---

### Post by kernel tom on 2007-05-30
if you did not correctly enter your WEP code, you can still be connected to your network and not be connected to your internet.  So make sure you try all of the keys associated with your network, you can find them by logging into the router from a browser on one of your other computers.  Without the WEP key you won't get internet service but you can still view other computers on your network.

Linux will think it's connected even if the wrong WEP is enterred

---

### Post by Paddatjie on 2007-05-30
where can I re-enter the wep code?

---

### Post by Paddatjie on 2007-05-30
Thanks, I have it.

Network was set on roaming mode!! Sorry thanks for your help!!

---

