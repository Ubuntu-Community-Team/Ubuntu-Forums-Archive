---
title: "Need Help Pleasee!!!!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by yiggaman on 2007-04-28
Could someone help me please......
i dont have an internet connection on my ubuntu computerr ,  my wirless doesnt work that is my problem.
what do i have to do too get it working properly please? what do i have to download?

Ubuntu 7.04 Feisty Fawn

arch 
i686
lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

---

### Post by bobplano on 2007-04-28
you need to download ndiswrapper most likely. post your wireless card here so people can help you more. ndiswrapper btw "wraps" windows drivers so linux can use them

---

### Post by yiggaman on 2007-04-28
what do i type to get info on my wireless card?

---

### Post by kittyhawk63 on 2007-04-28
> **yiggaman said:**
> what do i type to get info on my wireless card?

Will downloading and running Belarc Advisor give what he is looking for? Belarc Advisor is free and runs in Windows.
kh

---

### Post by yiggaman on 2007-04-28
Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 0, IRQ 6 
        I/O ports at 1820 [size=32] 

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI]) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 0, IRQ 6 
        I/O ports at 1840 [size=32] 

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI]) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 0, IRQ 10 
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K] 
        Capabilities: <access denied> 

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode]) 
        Flags: bus master, fast devsel, latency 0 
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64 
        I/O behind bridge: 00003000-00003fff 
        Memory behind bridge: e0200000-e04fffff 
        Prefetchable memory behind bridge: 30000000-33ffffff 

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
        Flags: bus master, medium devsel, latency 0 

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP]) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 0, IRQ 6 
        I/O ports at 01f0 [size=8] 
        I/O ports at 03f4 [size=1] 
        I/O ports at 0170 [size=8] 
        I/O ports at 0374 [size=1] 
        I/O ports at 1810 [size=16] 
        Memory at 34000000 (32-bit, non-prefetchable) [size=1K] 

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: medium devsel, IRQ 10 
        I/O ports at 1860 [size=32] 

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 0, IRQ 11 
        I/O ports at 1c00 [size=256] 
        I/O ports at 1880 [size=64] 
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512] 
        Memory at e0100800 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic]) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: medium devsel, IRQ 11 
        I/O ports at 2400 [size=256] 
        I/O ports at 2000 [size=128] 
        Capabilities: <access denied> 

02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 168, IRQ 10 
        Memory at e0400000 (32-bit, non-prefetchable) [size=4K] 
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176 
        Memory window 0: 30000000-33fff000 (prefetchable) 
        Memory window 1: 38000000-3bfff000 
        I/O window 0: 00003000-000030ff 
        I/O window 1: 00003400-000034ff 
        16-bit legacy interface ports at 0001 

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
        Subsystem: Toshiba America Info Systems Unknown device ff31 
        Flags: bus master, medium devsel, latency 64, IRQ 6 
        I/O ports at 3800 [size=256] 
        Memory at e0401800 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 

02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
        Subsystem: AMBIT Microsystem Corp. Unknown device 0310 
        Flags: bus master, medium devsel, latency 64, IRQ 10 
        I/O ports at 3c00 [size=32] 
        Memory at e0401c00 (32-bit, non-prefetchable) [size=32] 
        Memory at e0401000 (32-bit, non-prefetchable) [size=2K] 
        Capabilities: <access denied> 

does this help at all???

---

### Post by annda on 2007-04-28
you already have the info. that's what lspci is for:

> Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

i'm sorry i don't know the card so i can't tell you if it needs ndiswrapper or whether there are linux drivers for it. search the forums.

---

### Post by yiggaman on 2007-04-28
it is not this computer that has Ubuntu on it this is a family comp and i want to put a linux OS on this too but first i got to make it work soo there will be no arguments ;+)

---

### Post by yiggaman on 2007-04-28
thank you annda, now could you possibly point me in the direction of how to install ndiswrapper via another pc that would be much appriciated.....

---

### Post by annda on 2007-04-28
a very quick search returned among others this howto:
[http://ubuntuforums.org/showthread.php?t=179270](http://ubuntuforums.org/showthread.php?t=179270)

but your computer has the linksys card? i'm a little confused here...

anyway, you will have to download the packages mentioneed in this howto from
[http://packages.ubuntu.com](http://packages.ubuntu.com)
and burn them to cd or save on a usb key and transfer them to the computer with ubuntu installed.

---

### Post by yiggaman on 2007-04-28
sounds promising ill check it out and get back 2 you

---

### Post by annda on 2007-04-28
here is more about ndiswrapper without an internet connection:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-25f7f86dc646b1632ab4b82830a7e26dd5cefc2c](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-25f7f86dc646b1632ab4b82830a7e26dd5cefc2c)

go ahead and read the entire guide, too :-)

---

### Post by yiggaman on 2007-04-29
what do i need to do from here???


yiggaman@y1:~$ sudo ndiswrapper -i /home/yiggaman/WPC54G v4 driver rev 1.22.1.2004/WLIPNDS.INF 
Usage: ndiswrapper OPTION 

Manage ndis drivers for ndiswrapper. 
-i inffile        Install driver described by 'inffile' 
-d devid driver   Use installed 'driver' for 'devid' 
-e driver         Remove 'driver' 
-l                List installed drivers 
-m                Write configuration for modprobe 
-da               Write module alias configuration for all devices 
-di               Write module install configuration for all devices 
-v                Report version information 


where 'devid' is either PCIID or USBID of the form XXXX:XXXX

---

