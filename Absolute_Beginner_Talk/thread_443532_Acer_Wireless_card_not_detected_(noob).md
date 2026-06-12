---
title: "Acer Wireless card not detected (noob)"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by timmy toad on 2007-05-14
Hi all, i have just installed Ubuntu, with the intention of leaving  Win XP  completely at some time in the future, i have a Acer Aspire 1363 WLMi, i can easily get the Internet with a Network Cable, i would prefer to use the Wireless Connection that my Lap Top uses with WinXP, but sadly UBUNTU doesnt detect my Wireless card which the laptop has.

I did enter a command into the the Terminal , starting with "sudo  etc."  but, the two thingies it was supposed to find couldnt be found !.

so back to square one. any ides anyone.

tim

---

### Post by wormser on 2007-05-14
Put the following command into the terminal and post the results.

```
lspci
```

---

### Post by Pulka on 2007-05-14
try installing ndiswrapper

---

### Post by timmy toad on 2007-05-14
timp@timp-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
timp@timp-laptop:~$ 


phew does that help ?, it's as clear as mud eh.

tim

---

### Post by timmy toad on 2007-05-14
> **Pulka said:**
> try installing ndiswrapper

ok, i have installed now what ?????   please..

tim

---

### Post by Pulka on 2007-05-14
either download it from:

[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

or put the ubuntu cd in, go to system - administration - synaptic package manager
edit - add cdrom
refresh
search ndiswrapper
right click - mark for installation

---

### Post by Pulka on 2007-05-14
it was a nightmare for me to put wireless working on my acer. When i found this page, it worked immediatly. I strongly recomend doing like it says:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

---

### Post by timmy toad on 2007-05-14
> **Pulka said:**
> it was a nightmare for me to put wireless working on my acer. When i found this page, it worked immediatly. I strongly recomend doing like it says:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

thanks for that buddy, that looks a mite tricky, i shall chicken out for today, i have to go to bed, LOL, and it's only 9.30pm  LOL.

tim

---

