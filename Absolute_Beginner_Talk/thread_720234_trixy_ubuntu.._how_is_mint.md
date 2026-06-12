---
title: "trixy ubuntu.. how is mint?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-03-10
It seems as though every time i change something. some other unrelated thing changes as well. 

the tap to click mouse feature will suddenly engage (very unwanted) or the network icon will disappear or  the update manager will be gone. or better yet the menu bar will decide not to display.

the most recent tweak is my windows are all at the top of the screen to where i can't close  or move them with out right clicking them. (just annoying)

the most frustrating problem on Ubuntu is with the wifi... it works it doesn't it works it doesn't..](*,)

and it's all for no apparent reason.....:confused:

so what I'm wondering is if mint has similar quirks or is it really as wonderful as it's site says it is. and what are the draw backs (if any) to switching to mint.? 

MOST IMPORTANTLY how is it on laptops?.
i just want some personal feed back... or any helpful info for that matter..



thanx

---

### Post by jan quark on 2008-03-10
I worked with mint and can recommend it

it is based on the latest ubuntu distribution and has some codecs preinstalled which makes the start somewhat easier for the beginner

but the setup of the wlan has nothing to do with the graphical interface

have you tried another network manager like [WiCD]("http://wicd.sourceforge.net/")?
what is your wlan card?
please post the result of 
```

sudo lshw -C network
```

---

### Post by R13120(1&lt; on 2008-03-10
thanks i appreciate it... > *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:fd:95:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:1c:cf:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-386 ip=192.168.1.101 latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


---

### Post by R13120(1&lt; on 2008-03-10
any idea why i would be suddenly unable to move my windows around or turn off the tap to click mouse function?

---

### Post by jan quark on 2008-03-10
if you have ethernet cable connection on your ubuntu machine you can try to configure your wlan card with this method using the ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29)

> any idea why i would be suddenly unable to move my windows around or turn off the tap to click mouse function?

you cannot grap the windows and move them? weird 

have you compiz enabled? when did this start?

---

### Post by R13120(1&lt; on 2008-03-10
yes i do have compiz has that something to do with it? i just noticed both of these today.

---

