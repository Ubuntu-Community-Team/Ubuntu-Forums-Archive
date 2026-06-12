---
title: "Dell Inspiron 1100 Ubuntu 7.10"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Rabin007 on 2008-02-14
I just installed Ubuntu 7.10 in Dell Inspiron 1100. At the time of installation, my wireless card was in the computer, but as it was installing, the system was not able to access the update. I hit continue despite the message. Once the computer fully installed the OS, I hard wired the computer and did the update and upgrade using the comand: sudo apt-get update; sudo apt-get upgrade. 

Everything looks fine. 

However, I have two main issues.

Wireless: How can i configure wireless internet access. I have Linksys Wireless G Notebook Adapter Model No: WPC54G ver.4. 

Text: When I look at text in the OS at some places the text seems to be italic and sometime distorted so much that it is hard to read what it means. Anybody has any idea as to why it is doing this? Thank you very much for your help.

---

### Post by jan quark on 2008-02-14
please post the result of this terminal command 

```
sudo lspci
```

thank you

---

### Post by Rabin007 on 2008-02-14
thank you Jan.

what line in particular do you need? that computer is not online, so i will have to go there and hand write in my note pad and type it in my working pc.

---

### Post by Rabin007 on 2008-02-14
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by jan quark on 2008-02-14
is it perhaps an usb device ?

because the only network related hardware I see in the output is

```
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

ok lets find out what usb devices you have
```

lsusb
```

and in the meantime you can look at this page
your wlan adapter is probably listed there but I just wanted to be sure
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by halfhearted on 2008-02-14
Bearing in mind I know next to nothing about Ubuntu, but judging from my own experiences with my Belkin N1 wireless PCMCIA card it is a bit hit and miss whether or not you'll get your card working. If Ubuntu 7.10 likes a card it just finds it - and there it is - ready to go. It all gets much harder if the OS can't find the card. It seems to like Atheros chipsets. I couldn't get my Belkin N1 to work at all or figure out how to do anything about it. I don't think that Ubuntu supports 802.11N standard in any way at all. Please correct me if I'm wrong.

---

### Post by Rabin007 on 2008-02-14
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
03:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

For further review, i forgot to have the card in the pc while running the first command.

here is the result of the second command:
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by jan quark on 2008-02-14
sry I must disappoint you

>  Linksys
	

WPC54G (Ver.4)

This card type is very tricky to get working, must have drivers for the SPECIFIC version of the card.

I have taken this from here
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

there are all wlan cards which are supported by ubuntu

---

### Post by Rabin007 on 2008-02-14
Can you tell me anything about the text issue where the text is fudgy to the point where i can not read few lines here and there?

---

