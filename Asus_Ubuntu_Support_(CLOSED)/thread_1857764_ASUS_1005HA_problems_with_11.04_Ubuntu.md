---
title: "ASUS 1005HA problems with 11.04 Ubuntu"
date: 2011-10-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by GenericGirlName on 2011-10-10
[s]
I have horrible luck with installing Ubuntu on my computers. This is my third computer and this time I really need Linux...let's hope I can get it right this time!

I went through Wubi and installed Ubuntu on my ASUS 1005HA and immediately tried to connect to the wireless here on campus. At first the wireless would attempt to connect and then fail, but upon reboot it just doesn't pick up any wifi signals. The blue Wifi light is on and when I switch to windows the wifi works fine.
[/s]

I posted this from my desktop as I was rebooting the nextbook for the fourth time and as soon as this posted the netbook picked up the wifi. Is there any reason this might have suddenly worked/didn't work? 

[s] I looked in another thread and ran[/s]
> sudo lshw -c networkbut I get 
> *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:c8:cd:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:96:be:c1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
Which is not what I saw in that thread and im stumped. :I I would be really glad if someone would point me in the direction of some necessary drivers or some such (I can just flash drive it over from my desktop)

---

### Post by An Sanct on 2011-10-11
Welcome to the forums!

Glad to hear, that it works now! :)

PS. Try using a Live USB first and then install. I have no experience with WUBI, but from what I heard it is a little "limited" ... and can cause problems from time to time <- just my opinion ... again, I have no experience with it

---

