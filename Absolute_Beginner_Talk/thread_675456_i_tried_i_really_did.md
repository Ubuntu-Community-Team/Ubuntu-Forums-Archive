---
title: "i tried i really did"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by stevensonfire on 2008-01-22
i tried to use wine to open a few of the files and search the site for help but i give up so please i got the camera to install but when i try to use it i get a blank grey mini screen with the cancel button.. and i  installed the wlan but when i turn on the switch to turn on the wireless connection i get nothing...... also music from frostwire won't play on the music apps is there something i have to do on terminal?

ispci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by stevensonfire on 2008-01-22
help????
bump i know..

---

### Post by Dark Hornet on 2008-01-23
I'm sorry, can you be more specific about what your issues are...what camera, what are you trying to do, etc?

---

### Post by Mogurijin on 2008-01-23
Okay, WINE is for running windows software, not hardware. I don't exactly understand the camera issue, but the Wireless is kind of complicated. Try and see if [_this_]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wifi%29%7C%28support%29") helps. And for the music, find the xmms player. You can try this at the terminal:

```
sudo apt-get install xmms
```

---

### Post by sumguy231 on 2008-01-23
> also music from frostwire won't play on the music apps is there something i have to do on terminal?
You need to install the ubuntu-restricted-extras package to be able to listen to most media formats. You can do it from Synaptic or from the command line like so (this is assuming you get your network connection working):
```
sudo aptitude install ubuntu-restricted-extras
```

---

### Post by stevensonfire on 2008-01-23
from what i can tell my notebook has a 

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

which on [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)
claims should have been auto detected by ubuntu.. but no such luck.. 
i have no idea if im suppose to somehow manually set it up
or something

the camera is a built in Integrated 1.3 Megapixel Camera that i just can't seem to get working...
i have no idea what kind it is.. it's built in like the imacs etc...

---

