---
title: "Why won't they talk?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by D_D_T on 2007-07-24
Help me please! I'm completely new to Ubuntu and am having some problems with my wireless connection. I've got a Sitecom WL-140 v1 wireless card which needed a CD installation in XP. The problem is that the CD doesn't work in Ubuntu and I can't get my card to work. The card isn't even recognised in the PCMCIA port. :( Can anybody help me?
Thank you!!
Nick

---

### Post by Cypher on 2007-07-24
Ubuntu/Linux != Windows, so the CD meant for Windows will have no effect in Linux. That being said, how have you checked to see if the card is detected or not in the PCMCIA port?

---

### Post by Rocket2DMn on 2007-07-24
Can you please post the output of
```
lspci
```This will list a lot of detected hardware.

---

### Post by D_D_T on 2007-07-24
The "lspci" code resulted in this:
Thank you so much for helping.
Nick

00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
recordnick@laptopnick:~$

---

### Post by Rocket2DMn on 2007-07-24
Some wireless device manufacturers don't release specs that allow them to be used in other operating systems, this seems to be the case with you.
The wireless card is picked up in lspci > 03:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
You will need to use ndiswrapper to get the card setup, but unfortunately, I don't know anything about setting that interface.
This is the best I can do for you now: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) but note that it says it's not for desktop installations - take that as you will. 
You should surf around and see if you can get help from previous posts about installing ndiswrapper using a driver from a cd.  In short, ndiswrapper will use the windows drivers to make the card work, but it's not perfect.
Another option is to simply go buy a new card that *is* supported in linux.
If you can't find any threads to help you out, you may want to start a new one and start off by saying what you did here, post the lspci output with the network controller line highlighted, and ask if anybody can help you setup ndiswrapper.
Good luck, sorry I couldn't help further.

---

### Post by D_D_T on 2007-07-24
pants! Oh well, thank you anyway. Will investigate ndiswrapper and see what I can do. Thanks for all your help.
All the best,
Nick

---

