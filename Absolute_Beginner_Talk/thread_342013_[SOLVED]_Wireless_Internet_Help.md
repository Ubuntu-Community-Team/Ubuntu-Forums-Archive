---
title: "[SOLVED] Wireless Internet Help"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by dorkdork777 on 2007-01-19
Hi, before I get started, I'd just like to say that I am a *complete newb* to Ubuntu and Linux. The only time I've ever used it before was when my computer died from a virus, which is precisely the reason I'm looking to make the switch to Ubuntu, from Windows.

Anyway, I've been trying to get my wireless adapter to work with Ubuntu, with no success. I've done a few searches, but all I found was that putting 'lspci' into the terminal would help the people who will answer my question (please?). So I did that, and this is what I got - 

```
00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)
```

Now, I have no idea what most of that means, but I hope someone here can make sense of it.

One more thing that I found that might come in handy is what my wireless config program says my wireless card is - 

NETGEAR WG311 802.11g Wireless PCI Adapter


Oh, just one more thing, I'm posting this from Windows, so to get into Ubuntu I'm gonna have to do a complete system shutdown and restart, which will take a while, so I don't really want to have to do it too often. I've not yet installed Ubuntu to my system, I'm using the Live CD version. I just wanna find out if it's possible to get my card working without having to replace it, or open up my computer.

Thanks to all who reply in advance.

EDIT, 26/11/2007 - The problem turned out to be a faulty router, nothing to do with Ubuntu. All is working fine now, and thread marked as solved. :)

---

### Post by celem on 2007-01-19
1. You'll get more feedback if you move this post to the " Networking & Wireless" section.
2. Indicate if you are you using  Dapper or Edgy?
3. Read :
[http://www.ubuntuforums.org/showthread.php?t=317402&highlight=Atheros+AR5212](http://www.ubuntuforums.org/showthread.php?t=317402&highlight=Atheros+AR5212)

and

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by mand0 on 2007-01-19
You may need to install "ndiswrapper"

Try looking here for more info: [http://ubuntuforums.org/showthread.php?t=312640&highlight=NETGEAR+WG311](http://ubuntuforums.org/showthread.php?t=312640&highlight=NETGEAR+WG311)

---

### Post by davebgimp on 2007-01-19
Your card seems to be supported out of the box.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

Tell me, is your wireless network encrypted? If so, what are you using? WEP? WPA?

---

### Post by shane634 on 2007-01-19
Looks like the Atheros chipset. Try this site:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

  Should get it up and running with MadWifi.

---

### Post by dorkdork777 on 2007-01-19
[quote=davebgimp]
Your card seems to be supported out of the box.
[https://help.ubuntu.com/community/Ha...CardsNetge](https://help.ubuntu.com/community/Ha...CardsNetge) ar

Tell me, is your wireless network encrypted? If so, what are you using? WEP? WPA?
[/quote]
I looked there, and it didn't have my card (WG311 v1). And the network is unencrypted.

And I think I'll try that MadWiFi thing first, then ndiswrapper if it doesn't work. Thanks everyone for the prompt responses! :D

---

### Post by shane634 on 2007-01-21
So may we safely assume one of the fixes here worked for you? It could be helpful to other users if you posted which if any of these worked. If not fire away with further questions.

---

### Post by dorkdork777 on 2007-01-22
Sorry, I made a new thread in Network and Wireless after I found that my card was working fine in Dapper, not Edgy, but in Dapper it couldn't find my home network, which is unencrypted and was easily found by my Windows, a Mac, my PSP and my Wii. It could only find some other ones in my area. You can find the thread [here]("http://ubuntuforums.org/showthread.php?t=342013").

---

