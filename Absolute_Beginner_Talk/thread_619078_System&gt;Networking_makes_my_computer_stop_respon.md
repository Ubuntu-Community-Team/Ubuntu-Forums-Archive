---
title: "System&gt;Networking makes my computer stop responding..."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by fulgencio on 2007-11-21
Hi,
I use ubuntu dapper, on a amd64 HP Pavilion, when I connect to internet I usually select the network using System then networking, after I select click on properties and select the network (wireless) I want, half of the times  Ubuntu stops responding, everything, even the mouse icon stops responding, So I turn off the computer and when I restart it internet works perfect. I should say that the wireless connection has worked "mysteriously" fine because when it doesn't freeze everything works estupendo!
Just another thing I've tried installing the network manager applet many times and it just cant work. please, please help! I'm afraid that one of this times when I turn off the computer I get something like Data corruption (not that I know what that means).

---

### Post by MaximusTG on 2007-11-21
Do you know which wireless card you are using? 
If not, could you post an output of the 
```

lspci

```

command in a terminal?

That will list all devices in your computer.

On a side note, maybe it's a good idea to upgrade to the latest Ubuntu release? Or do you feel more comfortable running 6.06, the LTS edition? You could try running the latest live cd, good chance the problem you are having has been fixed in a newer edition.

---

### Post by fulgencio on 2007-11-23
I prefered this version of Ubuntu because of a sticky posted on this forum, basically it did not recommend the latest version of ubuntu for HP laptops.
my lspci:

[PHP] lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:05.0 PCI bridge: ATI Technologies Inc: Unknown device 5a37
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 A udio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev  02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 2 00M 5955 (PCIE)
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)
0000:06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Ho st Controller
0000:06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated Flash Media Controller
0000:06:04.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411 , PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
root@magico-laptop:/home/magico# lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:05.0 PCI bridge: ATI Technologies Inc: Unknown device 5a37
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
0000:06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:04.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/PHP]

thanks.

---

### Post by MaximusTG on 2007-11-24
I see you have a broadcom 4318 wireless card. Are you using the linux native driver, or ndiswrapper. If you are using the native driver, try using ndiswrapper.

---

### Post by fulgencio on 2007-11-30
I'm using ndiswrapper, any more suggestions

---

