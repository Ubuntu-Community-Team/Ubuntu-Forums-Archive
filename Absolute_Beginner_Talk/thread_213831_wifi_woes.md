---
title: "wifi woes"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Djorn on 2006-07-11
Hello

I have been trying to set up my wifi and have been plunking along... at this point I have two questions.

1) when i open Wireless Assistant (W.A.) it gives me this message:[CENTER][quote="Information -Wireless Assistant"] [CENTER]You might have insufficient permissions for Wireless Assistant to function properly.

Did you run it using 'sudo'?[/CENTER][/quote][/CENTER]
So I would like to know how to do that... I think i would be able too if I knew where the W.A. program files were...

2) I cant turn off WEP encription at my hub... is this a problem?

Thanks for all of your help ^.^

~Djorn

---

### Post by Djorn on 2006-07-11
And I am back.

---

### Post by Kilz on 2006-07-11
> **Djorn said:**
> And I am back.

[Maybe this page will be of some help.]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by Djorn on 2006-07-12
I am so lost..

I am willing to work with linux and all but i cant seem to figure out how to use it... I tried installing wireless tools and i want to know how but I have no clue what i am doing...](*,) ](*,) ](*,)  This makes me feel stupid and it shouldn't... I know I can figure this out...I tried to follow the install instructions but I don't know what they are talking about...

( I have put like 20 some hours into linux in the past week or so and my brain is fried.)

---

### Post by Djorn on 2006-07-12
wow I feel dumb... my wifi card = incompadible... and here i thought it was just a bad PCI slot .. got a 20 dollar wifi card that *is* on the compadiblity list... so it should work now... sorry for the mess...:rolleyes:

---

### Post by brentoboy on 2006-07-12
djorn,

you should read up on ndiswrapper.  it is a "wrapper" driver that wraps a windows ethernet driver (which happens to be an "ndis" driver)

it is a decent way to overcome "windows only" hardware.

I would help more, but I dont currently have a wireless card that needs it so I cant be of much more help, but if you go to here...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
it covers the use of ndiswrapper thouroghly.

---

### Post by Djorn on 2006-07-13
Alright i still need some help with all of this.. 

I have a Linksys Wireless-GS pci adapter (WPC54GS) It is not listed on the compatiblity list. so I bought a Linksys wireless-B pci adapter (WMP11 v.4)

I use the iwconfig command and it gives me: ```
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"andy"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth0      no wireless extensions.

```Note both cards are currently in pci slots... after that when i run lspci i get this:```
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:07.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
0000:01:08.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:08.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)
0000:01:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

In 'Network Settings'  Wireless connection is not active and will not stay active... i ativate it then quit... open up 'Network Settings'  it is listed as inactive...

I used ndiswrapper and installed everything related to that.. I used ndisgtk to put in the drivers for both cards... I still cant figure this one out....

---

### Post by Djorn on 2006-07-13
> **brentoboy said:**
> djorn,

you should read up on ndiswrapper.  it is a "wrapper" driver that wraps a windows ethernet driver (which happens to be an "ndis" driver)

it is a decent way to overcome "windows only" hardware.

I would help more, but I dont currently have a wireless card that needs it so I cant be of much more help, but if you go to here...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
it covers the use of ndiswrapper thouroghly.

yeah this worked.... sry for the mess guys ... I dont have a WPC54GS .. it is  a *WMP*54GS ... got the drivers right and it all works... seems like i need to slow down abit... and not try to be hyper... thanks for being patient....

Ya for wifi!!!

---

