---
title: "Dell Wireless problem"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by ipatec on 2007-12-20
I've just installed Ubuntu Studio 7.10 on my Dell Inspiron 6400 laptop.
The problem is that when I press Fn + F2 to activate my wifi card nothing happens... the led is closed...
Any advice?

---

### Post by jan quark on 2007-12-20
I aam not that experienced but I had to install the drivers for my wifi card on my Dell 1501 manually via fwcutter.

What wifi card do you have.?

Havent tried Ubuntu Studio yet, but try to type the following commands into the terminal and post the outcome:

iwconfig

ifconfig

sudo iwlist scan

lshw -C network

---

### Post by mukul_d on 2007-12-20
Hi ipatec,

The LED bein off suggests that the drivers for the wireless card has not been installed. Could post the output of
```
/sbin/iwconfig
```

You need to download the Intel(R) PRO/Wireless 3945ABG Network drivers for Ubuntu and install them. You can find additional pointer on my website at: [http://www.dharwadkar.com/weblog/linux_wlan_02](http://www.dharwadkar.com/weblog/linux_wlan_02)

---

### Post by ipatec on 2007-12-20
ipatec@ipatec:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ipatec@ipatec:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:B9:52:34:B3  
          inet addr:192.168.0.169  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe52:34b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1126197 (1.0 MB)  TX bytes:235085 (229.5 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ipatec@ipatec:~$ sudo iwlist scan
[sudo] password for ipatec:
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ipatec@ipatec:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:b9:52:34:b3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.169 latency=64 module=b44 multicast=yes
ipatec@ipatec:~$

---

### Post by ipatec on 2007-12-20
When I want to install ieee80211 it tells me to fix broken package first... I don't know which are the browken packages?

---

### Post by ipatec on 2007-12-20
The problem was from Ubuntu Studio... because on Gutsy or Vista it works well...

---

