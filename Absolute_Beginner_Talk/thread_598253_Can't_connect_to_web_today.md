---
title: "Can't connect to web today"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-10-31
I've Gutsy and XP on this laptop. Yesterday I was connected to the internet in Gutsy with no problems. When I logged on today I couldn't connect to the web! I didn't change any settings. 

Also, I can connect to the web via XP. These are wireless connections.

Any ideas on what the problem could be?

---

### Post by elliotjreed on 2007-10-31
I have this problem, it takes ages to initiate the internet connection program.

You just have to wait a very long time!

Or Ctrl - Alt - Bkspce, until it works! (restarts X)

---

### Post by ushills on 2007-10-31
What chipset does your wireless card have, I had connection & reliablity issue with Ralink ones following an upgrade to Gutsy

post the output of 

```
lspci
```

---

### Post by Padraig1 on 2007-10-31
There is a lot of info there so I'm just selecting the line i think you want:

0c:00.0 Network controller: Intel Corporation Pro/Wireless 3945ABG Network Connection (rev 02)

If it's not what you're looking for could you let me know what is.

In my situation where I have access to the web in XP but not in Ubuntu is there any way of getting the data from Ubuntu to XP?

---

### Post by Padraig1 on 2007-10-31
I've logged onto Ubuntu again and now I can access the web straight away and I haven't changed anything!

The full output to the lspci command is :
[COLOR="Navy"]
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
02:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[/COLOR]

Are other users out there having this problem?

---

### Post by ushills on 2007-11-01
It's not the same card I use so I don't know if there is an issues with the card in your PC.

Sounds like it's working now though, I found the Gnome Netmanager caused lots of issues so I manually configure /etc/network/interfaces to suit my wireless network.

---

