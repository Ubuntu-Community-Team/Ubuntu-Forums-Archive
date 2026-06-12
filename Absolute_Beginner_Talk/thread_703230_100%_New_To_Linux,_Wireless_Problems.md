---
title: "100% New To Linux, Wireless Problems"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by darKStorm on 2008-02-21
Hey :)

I installed linux on my PC yesterday, and have hit a brick wall while trying to set it up. I spent 6 straight hours trying to set up wireless networking for the broadcom bcmw. 

This computer only has wireless access to the internet, so I cannot try wired, as a lot of the tutorials seem to need. So I can download stuff from Vista (the reason I am switching to Ubuntu) when I boot to that, copy to flash drive, then reboot into Ubuntu and use those files.

I need help on how to do this, step by step, as I have pretty much no idea how to work with Ubuntu (its 7.10 by the way, thought you'd need to know), so any help would be REALLY appreciated. 

  Thank you,
                   Danny

---

### Post by jan quark on 2008-02-21
try this guide
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

but first post the result of```
 lspci
```

thank you

---

### Post by Neilisgreat on 2008-02-21
i Had same problem with my speedtouch 121g, I gave up and bought 
3Com OfficeConnect Wireless 11G (54Mbps) USB Adapter which works straight out of the box.

i bought it from amazon:- 
[http://www.amazon.co.uk/3Com-OfficeConnect-Wireless-54Mbps-Adapter/dp/B00064C594/ref=sr_1_1?ie=UTF8&s=electronics&qid=1203589560&sr=8-1](http://www.amazon.co.uk/3Com-OfficeConnect-Wireless-54Mbps-Adapter/dp/B00064C594/ref=sr_1_1?ie=UTF8&s=electronics&qid=1203589560&sr=8-1)


you could have a look also at the wireless cards supported page:-

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28cards%29%7C%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28cards%29%7C%28wireless%29)

---

### Post by darKStorm on 2008-02-21
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)


Those are the results that you want, and so you know, if I take a while to reply, its because I need to constantly swap between Vista and Ubuntu, and Vista takes a little while to startup.

---

### Post by pedro_orange on 2008-02-21
I've seen alot of people have alot of problems with Broadcom.

Did a quick google and came up with this: [http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

Did you try that out?

---

### Post by darKStorm on 2008-02-21
I've tried something similar to that, however I probably done something wrong last time, that is put a lot simpler than what I found. 

Thanks, I'll let you know if it works :)

---

### Post by jan quark on 2008-02-21
give also these guides a try

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28WifiDocs%2FDevice%29)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29)

---

### Post by darKStorm on 2008-02-21
@ pedro_orange
While trying to use the guide you gave me, when installin ndiswrapper utils, I get an error message saying "error: dependency is not satisfiable", anyone know why this is?

---

### Post by pedro_orange on 2008-02-21
That just means it needs some libraries to install itself.

I'm presuming you can't do it from apt-get; so I guess you'll have to google it for the .tar.gz / .deb package

---

### Post by darKStorm on 2008-02-21
> **pedro_orange said:**
> That just means it needs some libraries to install itself.

I'm presuming you can't do it from apt-get; so I guess you'll have to google it for the .tar.gz / .deb package

Im looking for it now :)

---

### Post by darKStorm on 2008-02-21
I need help installing ndiswrapper, I  just cannot get it sorted :(
Remember I have no internet access on Ubuntu

---

### Post by darKStorm on 2008-02-21
Can anyone help?

---

### Post by darKStorm on 2008-02-21
I have sorted it, thanks to anyone who helped me :D

EDIT* I rebooted the PC to make sure it would stay fixed, but now it is back on, the wireless connection option in System > Administration > Network has gone, does anyone know why?

---

