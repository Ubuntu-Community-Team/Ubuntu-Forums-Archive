---
title: "Basic wireless config help? :("
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by devi on 2007-08-21
Maybe I can get better help over here, no one's answering on wireless..

I am having trouble getting my wireless working and would appreciate some assistance. I'm a big fan of the OSS concept, but totally new to Linux in general and I've never had wireless before, so please don't assume "she should know that," as I might not. 

I am running: Xubuntu Feisty on a Dell Latitude C510/610. The wireless card is a Netgear WG111v2 (authentic v2, not fake v2 as some people have found.) I have gotten it to the point where iwlist wlan0 scan will recognize nodes by using the following threads:


[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...hlight=rtl8187](http://ubuntuforums.org/showthread.p...hlight=rtl8187)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)
[http://ubuntuforums.org/showthread.p...ighlight=WG111](http://ubuntuforums.org/showthread.p...ighlight=WG111)

However, once I get it to that point, it doesn't connect to the network. I *know* there's another step I'm missing, but I don't know what it is. This is likely something that's going to make someone go "the internet is full, go home!" to be honest. Since I've never configured a computer for wireless before, though, could someone give me a pass and help? 

Thanks so very very much. I love my little Xubuntu box, and I'd like to be able to use her everywhere... including away from my trusty ethernet connection.  This is the only thing still not working!
__________________

---

### Post by kevdog on 2007-08-21
Strategies 

You need to find or discover the chipset of the device.  This can be done with the following commands

lspci -nn
lshw -C network

Based on the chipset, sometimes (not all but most) you need to install or update a driver, for example
Broadcom chipset  --> bcm43xx driver or ndiswrapper with WinXP driver
Atheros chipset --> Ndiswrapper or (in rare cases) madwifi driver, some work out of the box with restricted madwifi driver
Ra chipset --> Upgrade to rt serial monkey drivers
rt818x -->> Big time problems with card install (works great once configured), ndiswrapper with win98 driver, or native driver with aircrack patch, or fake essid with native driver
intel (ipw) ---> Mostly works out of box but some problems with power management, Acer 

Probably more, but those chipsets are the biggies

---

### Post by mikeyphi on 2007-08-21
Don't know if you have a similar menu screen as Ubuntu...if you have System/Administration/Network.....what do you see?
Is your wireless there? is it enabled? are the settings OK?

This is USB ? It's supposed to work out of the box under 7.4!

---

### Post by devi on 2007-08-21
The output of lsusb is:

Bus001 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

lshw -C network gives:

*-network
      description: Wireless interface
      physical id: 1
      logical name: wlan0
      serial: 00:18:4d:c3:ca:97
      capabilities: ethernet physical wireless
      configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek Semiconductor Corp., 04/ multicast=yes wireless=IEEE 802.11g

Under System->network, I have:
wlan0
Address DHCP
It's checked, so I assume it's enabled. 

Yes, this is supposed to work out of the box. It doesn't. :(

---

### Post by devi on 2007-08-21
Are there any graphics-based scanners I can use to maybe get this working? I'll only be using wireless at places like libraries and coffee shops. I can see the networks there when I do iwlist wlan0 scanning, but I don't know what to do from there.

---

### Post by devi on 2007-08-23
**bump**

New data: 

I downloaded WiFi Radar and it can see networks, but I still can't connect. I put the address in and nothing changes.

Thoughts?

---

### Post by perce on 2007-08-23
St the beginning you said you see the networks with iwlist wlan0 scan. Then to connect the commands are:

iwconfig wlan0 essid ... key ... 

where you should put the name of the network in place of ... after essid, and the password (if any) in place of the ... after key (this will work will WEP encription, I don't know how to configure WPA from command line). Sometime you have to tell the card that the password in aschii, in this case you should type 
key s:... 
instead of 
key ...
Also if the essid is made of more than on word, you should enclose the name in quotes " ".

after that, you should give the command

dhclient wlan0


I don't know about GUI for Xubuntu, Ubuntu has network manager which is quite good. Maybe try to use the live CD of Ubuntu just to check.

---

