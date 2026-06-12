---
title: "Wireless Card not Detected on Eft"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-01-28
I've gone between Ubuntu (6.06), Windows, and Kubuntu (6.06, 6.10) for months now on this computer. I finally have settled on Kubuntu (6.10) - aince this was the latest release when I finally decided to switch to one OS permanently.

Everything's been running really well except that my wireless card is no longer recognized. It worked with Ubuntu and Kubuntu in 6.06, but it doesn't work in Kubuntu 6.10.

I read another psot and ran the following command in my terminal: lspci
I'm not sure where to from here...
Thanks in advance!

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

---

### Post by Happy_Man on 2007-01-28
Can you give us some exact model numbers for what you've got on your computer?

---

### Post by lazyrussian on 2007-01-28
I have a Toshiba Satellite A105-S2102 Laptop. I can't seem to find the model of my card though.

---

### Post by lazyrussian on 2007-01-28
THough I didn't buy my computer form walmart, I found all the specs on their site [http://www.walmart.com/catalog/product.do?product_id=4948023#Specifications](http://www.walmart.com/catalog/product.do?product_id=4948023#Specifications)

---

### Post by Pobega on 2007-01-28
It looks like your wireless card isn't being recognized.

Is this card internal or external?

Also, could you boot from the Kubuntu 6.06 LiveCD and post the output of the lspci command here.

---

### Post by lazyrussian on 2007-01-28
internal
I'll boot from it in a second and repost

---

### Post by lazyrussian on 2007-01-28
Here it is from Kubuntu 6.06

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a62
0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001c (rev 01)
0000:0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


I'm now going to boot from ubuntu 6.06 and post as well

---

### Post by Pobega on 2007-01-28
Is your wireless activated by default on Kubuntu 6.06? I can't find it on that list either, but it does interest me that you have two Eternet controllers.

---

### Post by lazyrussian on 2007-01-28
From Ubuntu 6.10 Live

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

I have two ethernet ports? really? heh. I have one ethernet for the broadband connection (eth0) and I should have a wireles card that should be detected, usually eth1.

---

### Post by lazyrussian on 2007-01-28
I know this line is wireless: 
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

I just found a linux driver on sourceforge made for all Atheros cards - MADWIFI.

I'm checking it out.

---

### Post by Pobega on 2007-01-28
After looking it up, you're probably going to need to install [Madwifi](http://madwifi.org/).

**Edit:** Woops, didn't notice that you found it yourself already. Disregard this post.

---

### Post by lazyrussian on 2007-01-28
hehe, thanks for helping. So far the only trouble I'm having is trying to install it. I've downlaoded all the restricted modules and read some (out of date) ubuntu installation guides but I'll keep trying for a few days. If anything I'll repost here.

Thanks again!

---

### Post by Pobega on 2007-01-28
> **lazyrussian said:**
> hehe, thanks for helping. So far the only trouble I'm having is trying to install it. I've downlaoded all the restricted modules and read some (out of date) ubuntu installation guides but I'll keep trying for a few days. If anything I'll repost here.

Thanks again!
What guide are you using? Probably an obvious answer, but would it by chance be [url=http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]this guide?[/quote]

You can always search through the "Tutorials & Tips" section of the forum and find docs directly related to Ubuntu if the official HowTo doesn't work:

[http://ubuntuforums.org/showthread.php?t=75451&highlight=Madwifi](http://ubuntuforums.org/showthread.php?t=75451&highlight=Madwifi)

---

### Post by lazyrussian on 2007-01-28
I tried a few tutorials from Ubuntu forums but I forgot to look through madwifi's FAQ/Wiki. Thanks for that link!

I'll check it out later tonight

---

