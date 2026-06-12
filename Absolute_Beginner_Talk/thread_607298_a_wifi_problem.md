---
title: "a wifi problem"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by webwurm99 on 2007-11-08
I just installed Ubuntu and have an issue.

I have a linksys wireless card and it sort of works.  The problem is that it sees the networks, mine and others, but when I try to connect to one my laptop freezes up.  Im new to linux and not sure what info you would need to help, but Ill do my best to provide whatever is needed.

thanks in advance

---

### Post by jwo7777777 on 2007-11-08
Too concise!

---

### Post by Barge on 2007-11-08
[Useful resources for beginners setting up your wireless connection]("http://ubuntuforums.org/showthread.php?t=596797&highlight=ndiswrapper")

That thread has quite a bit of useful stuff for getting started with wireless. It helped me get mine going. My guess is the ubuntu built in driver for you card just isn't up to it. If you can run the first command listed in the post and find the model of the chipset your card uses someone around here should be able to help more...

---

### Post by webwurm99 on 2007-11-08
00:00.0 Host bridge [0600]: VIA Technologies, Inc. P/KN266 Host Bridge [1106:3156]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
00:0a.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8375 [ProSavage8 KM266/KL266] [5333:8d04]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)

can someone help me make heads or tails of this??

---

### Post by Harpoon on 2007-11-08
You don't say what version of Ubuntu you are using, but I assume you are using the default network manager.  If this is correct, then get into the configuration an check to see that the settings are correct (static or dynamic dns, etc. )  Try changing the setting for roaming.

Run ifconfig from a terminal and check that the card - - eth0, ath0, . . . that is configured is the same as what network manager is trying to use.

still in th terminal, try sudo ifdown (your card) wait a few seconds and then try sudo ifup (your card).

if that doesn't get you connected, and you have a dual boot with Windows, boot into that and let it connect to the network.  Then restart (don't turn off the power) into ubuntu and try again.  This is idiotic, but for a while was the only way I could get things to work (no idea **why** it works).

Without getting you into reading logs and such, there is a documented bug in network manager that is receiving no attention from the developers.  My workaround solution was to remove it (using synaptic) and installing wi-fi radar, or wicd.  I tried both.  Neither are great, but they were both more reliable than the installed network manager.

---

### Post by webwurm99 on 2007-11-09
Im using ubuntu 7.10 and everything is default, Ive changed nothing.  I installed 3 days ago and haven't done anything, besides try to get this wifi card to work.  I have no useful exp in linux so Im really quite clueless!

Thanks again for your patience

---

