---
title: "Zorin 6.3 &amp; Wifi"
date: 2013-08-06
forum: Any Other OS
---

### Post by kkoz83 on 2013-08-06
Hello everybody, how are you?

Yes this is an Ubuntu forum and I'm asking about Zorin ***_but _***I'm doing it here because
1)   I can't register into Zorin's forum because of an unknown e-mail issue
2)  Zorin states it is based on Ubuntu 12.04 LTS.

So my problem - I can't get WiFi.  There's no icon on the taskbar *but* when I turn the laptop on, a pop-up stated "disconnected" with what looks like the WiFi icon next to the words.
Ethernet has no problem & there's nothing found when I check for additional drivers.

I found the following code:
[COLOR=#DFE9F1][FONT=Verdana]
[/FONT][/COLOR]lspci -nn | grep 0280
lsusb
lshw -c network
sudo rfkill list all

Should I do that? 

[COLOR=#DFE9F1][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by joeymac2011 on 2013-08-06
If you can run those commands through and attach it. That'd be great.*Just out of curiosity, is there a hardware switch that enable/disables the wireless adapter?

---

### Post by kkoz83 on 2013-08-06
I'll run it Wednesday & yes there's a physical switch but I'm 99.9% sure it's in the ON position.  By the way, it's an Acer Aspire 5100-5840.

---

### Post by kkoz83 on 2013-08-07
janusz@janusz-Aspire-5100-5840:~$ lspci -nn | grep 0280
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
janusz@janusz-Aspire-5100-5840:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0100 Acer, Inc Orbicam
Bus 002 Device 002: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
janusz@janusz-Aspire-5100-5840:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:cc:a6:e3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.108 latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:21 ioport:a000(size=256) memory:b0202000-b02020ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=wl latency=64
       resources: irq:22 memory:b0200000-b0201fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
janusz@janusz-Aspire-5100-5840:~$ sudo rfkill list all

---

### Post by kkoz83 on 2013-08-07
WiFi switch is ON (light is also on).

---

### Post by Cheesemill on 2013-08-07
*Thread moved to **Other OS/Distro Support**.*

---

### Post by kkoz83 on 2013-08-08
hello?  anybody?  joeymac2011?

---

### Post by joeymac2011 on 2013-08-10
Hi mate,

It looks like you have the incorrect driver installed. 

Infomation can be found at 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)


 sudo apt-get install firmware-b43-installer[FONT=courier][SIZE=4][COLOR=#000000]
[/COLOR][/SIZE][/FONT][COLOR=black][FONT=Arial]
[/FONT][/COLOR]



Let me know how you go.

---

### Post by kkoz83 on 2013-08-11
I got it working using

sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

---

