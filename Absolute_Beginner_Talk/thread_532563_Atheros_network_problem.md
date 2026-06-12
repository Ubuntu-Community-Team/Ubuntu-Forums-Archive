---
title: "Atheros network problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by fumoffu on 2007-08-22
Howdy, I have an Atheros AR5005G for wireless, on my Toshiba Satellite a105 s2051. I installed Kubuntu 7.04 about a week or so ago, and for some reason it no longer recognises my card. Earlier when It did, it would stay connected for about 20 minutes then disconnect, and the only way to get it back was to reboot. I though that this was just a wireless problem, but it does the same thing with the wired connection.

I'm running kernel 2.6.22-9 generic. 

output of lspci

```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by igknighted on 2007-08-22
> **fumoffu said:**
> Howdy, I have an Atheros AR5005G for wireless, on my Toshiba Satellite a105 s2051. I installed Kubuntu 7.04 about a week or so ago, and for some reason it no longer recognises my card. Earlier when It did, it would stay connected for about 20 minutes then disconnect, and the only way to get it back was to reboot. I though that this was just a wireless problem, but it does the same thing with the wired connection.

I'm running kernel 2.6.22-9 generic. 

output of lspci

```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Are you sure that:
1)The version of Ubuntu is 7.04 (Feisty)
2)The kernel is 2.6.22-9
3)If 1 & 2 are true, that you compiled the Mad-Wifi driver from source?

The reason I ask is that 2.6.22-9 is a Gutsy kernel... Feisty uses a 2.6.21 kernel (2.6.21-16?).  So if you are sure that you have Feisty and that kernel, you must have gotten the kernel outside the repo.  Since Madwifi (the atheros drivers) uses a custom kernel module to fit a specific kernel, you need to compile it for that specific kernel.  The repos make this easy, because by using a standard kernel there is a proper module built in.  But the Feisty repos will not have the proper module for the Gutsy kernel.

Sorry for the long-winded answer... if you can, can you post the results of the command "uname -a" (no quotes)?

---

### Post by fumoffu on 2007-08-22
Long winded answer? No, I just appreciate someone giving me an answer :)
I'm pretty sure I'm still using feisty. I followed this tut on how to update my kernel 
[http://ubuntuforums.org/showthread.php?t=511974&highlight=simple+kernel+update](http://ubuntuforums.org/showthread.php?t=511974&highlight=simple+kernel+update)

Though even with the original kernel I still had the random disconnections of the network. :(

output of uname -a

Linux insane 2.6.22-9-generic #1 SMP Fri Aug 3 00:50:37 GMT 2007 i686 GNU/Linux

---

### Post by igknighted on 2007-08-22
Hmm, well, it looks as though that method solidly updated your restricted-modules package as well, so the drivers should be fine.  Did the kernel upgrade coincide with the drivers stopping to work?

---

### Post by fumoffu on 2007-08-22
> **igknighted said:**
> Hmm, well, it looks as though that method solidly updated your restricted-modules package as well, so the drivers should be fine.  Did the kernel upgrade coincide with the drivers stopping to work?
Well, not exactly, I was getting a wireless connection, but knetworkmanager was set to manual configuration. I'm not sure what that meant, but I wasn't able to change networks or anything. However, as soon as I uninstalled and reinstalled the fglrx driver for my ati 200M the networking ceased to work all together(the wireless that is). I'm a bit confused to say the least :(

---

### Post by fumoffu on 2007-08-23
Ok, cool, I took a look at adept manager and noticed that I only had the restricted drivers installed for my previous kernel. Not sure how I screwed that up, but I just installed the right drivers and it now recognises my atheros chip set. It has still yet to be seen if the random disconnections will occur or not. Thanks for the help guys, you have no idea what a life saver this forum is :)

---

