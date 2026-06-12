---
title: "wireless headaches, SHOULD be a quick fix..."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by kraigory on 2007-06-30
Hokay, so...

I've got me a dell e1505 with a brand new dual boot of xp and feisty, everything is working like a charm... except... wireless...

Ubuntu sees the wireless card, and it even sees my network. 

```
kraigory@elihu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:D2:90:D8
                    ESSID:"Private Home"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-32 dBm  Noise level=-32 dBm
                    Extra: Last beacon: 56ms ago

```

Ubuntu refuses to connect to my network, and I can't even find a good way to do so. It does have WEP security, and I do have MAC filtering on, although through wired I got my MAC and added it, so that shouldn't be a problem?

I have noticed that it reads my wireless card as eth1 instead of what I assume is the standard wlan0, is that a problem?

Any advice or tips would be appreciated- I have tried WiFi Radar, Network Manager, etc etc. Should I disable MAC filtering totally, even though my computer is on the list?

---

### Post by kevdog on 2007-06-30
Disable it - Yes and then report back.  Your wireless and wired card have different MAC addresses.

---

### Post by kraigory on 2007-06-30
alright, disabled mac filtering, and now it gets closer, but still no real connection...

Now next to the network icon in the upper-right (the two computers), when i switch it to eth1, there appears a green vertical bar next to it, and it says 100% connection etc, but still no internet.

[http://img72.imageshack.us/my.php?image=networkstuffrg2.jpg](http://img72.imageshack.us/my.php?image=networkstuffrg2.jpg)

it also says it's "disconnected"

Any ideas?

---

### Post by kevdog on 2007-06-30
Disable WEP for now!!

You cant have a wired and wireless connection at the same time.  So if/when you reboot you have to reboot with only wireless card in slot, or wired card activated.

Post
lshw -C network

How did you install the drivers for the card??

---

### Post by kraigory on 2007-06-30
heh, i didn't, thats the funny part. It recognized the card and even SSID from the start.

```
kraigory@elihu:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:55:6d:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:dfcff000-dfcfffff irq:16
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:a5:b4:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.0.102 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:df9fe000-df9fffff irq:22

```

---

### Post by oilchangeguy on 2007-06-30
try this, if you've already gone to system, admin, networking, and correctly enabled the card. then right click the top or bottom panel, add to panel. and locate the network manager. add it to the panel, then open it. the default setting is l0. change it to wlan0. and you should be able to connect.

---

### Post by kevdog on 2007-06-30
Ok just in case you were interested, here is the driver for your card
driver=ipw3945

I have no ideas if there are any issues with this driver (we will pretend like there is not!)
Your wireless interface is eth1

Please post
/etc/network/interfaces
iwlist scan

---

### Post by kraigory on 2007-06-30
Well i'm at my local mall now, and i succesfully connected to some free wifi. Had to reboot after getting the settings right though. Couldn't ever get wireless assistant to connect to it either. 

/etc/network/interfaces isn't doing anything... can't find command. 

Now, iwlist scan is:

```
kraigory@elihu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:B8:61:12
                    ESSID:"J.Buck's Wireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=63/100  Signal level=-69 dBm  Noise level=-69 dBm
                    Extra: Last beacon: 36ms ago

```

so its working, although i had to reboot to get it to connect. Is this a common problem?

When I get home i'll try setting my wifi to 100% open, no WEP or anything, and see if i can get it to work. Then, gradually introduce WEP and MAC filtering...

---

### Post by nick24 on 2007-06-30
When you decide to use WEP later on make sure you choose 'Shared key' instead of 'Open System' on the drop down menu option. I had to pull my hair with frustration all weekend trying to connect to my own network before I finally figured it out :)

---

### Post by kraigory on 2007-06-30
EXCELLENT- thanks so much- I believe that was the key. I got it to work with no security, and then found the mac and enabled mac filtering, and then did "shared key" wep, and it's peachy. Thanks so much!

---

