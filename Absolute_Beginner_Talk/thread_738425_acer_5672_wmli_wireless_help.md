---
title: "acer 5672 wmli wireless help"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-28
Hey guys, can anyone give me an idea of the steps needed to get my laptop wireless up and running? Any help is greatly appreciated. (802.11a/b/g wireless LAN)


eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20362942 (19.4 MB)  TX bytes:935980 (914.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        no wireless extensions.

eth0      no wireless extensions.

Wired works perfect but even though the wireless seems to detect on it's own i cant connect properly.

---

### Post by jan quark on 2008-03-28
can you please post the output of

```
iwconfig
sudo lshw -C network
```

---

### Post by Helios1276 on 2008-03-28
shane@Acer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

shane@Acer:~$ sudo lshw -C network
[sudo] password for shane:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:38:de:07
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5789-v3.49a ip=192.168.2.5 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
shane@Acer:~$

---

### Post by sneeks on 2008-03-28
do you get any connectivity to the router or the net,or does it drop out straight away.
a lot of ubuntu installs i have done have this problem(well i have only done 10 so far)
what seems to work for me is setting the router on to a set chanell,say 7,and useing wpa encrytion.

---

### Post by Helios1276 on 2008-03-28
it recognises it but i cant interact wireless. I'm unsure how to set a specific channel, would this interfere with others who use the router?

---

### Post by Helios1276 on 2008-04-01
Hey guys , I'm still pretty new to Linux, just did my first RE-install tonight and have everything bar wireless up and running. I've been given guides and told about ndiswrapper but was wondering if the following link applies to me as it seems pretty straightforward! Do i need to print ifconfig or similar to help. Thanks in advance for any help
[http://ubuntuforums.org/showthread.php?t=737549](http://ubuntuforums.org/showthread.php?t=737549)

---

### Post by bumanie on 2008-04-01
Hi Helios1276, it is worth a try after all the trouble you've had. Be aware that if you install hardy, there are still bugs being ironed out. At least being a beta release, there won't be any more new bugs getting introduced, only bugs that are already there will be fixed.

---

### Post by Helios1276 on 2008-04-01
Hey Bumanie, It only appliess to hardy users? dang, well I was gonna wait for a while for the Hardy upgrade, being my nooby self I'm wary of Beta lol

---

### Post by cliff astrand on 2008-04-01
Trouble with wireless connections.
I am using a netgear wpn511 and a Cable&Wireless wireless router which have been working OK with 7.04 but now are being tested with Hardy. The problem seems to be in the Network Settings, 1st there are only 4 settings, secondly you (I) cannot save any settings other than WPA Personal.
As soon as you click to [close] the settings that have been set and proven to work will revert to WPA Personal with the Network Password corrupted (I think).
I have downloaded all the updates (as of today)
I am a newbie but I have done this bit a few times before, but I am still mystified.

---

### Post by Helios1276 on 2008-04-03
bump

---

### Post by ugm6hr on 2008-04-04
Duplicate - closed.
[http://ubuntuforums.org/showthread.php?t=745070](http://ubuntuforums.org/showthread.php?t=745070)

---

