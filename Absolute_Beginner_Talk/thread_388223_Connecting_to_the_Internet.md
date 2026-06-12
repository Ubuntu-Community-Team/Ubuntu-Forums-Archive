---
title: "Connecting to the Internet"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by egle853 on 2007-03-19
I am trying to install a D-Link WDA-2320 Wireless card to connect to the Internet.  
I have followed the troubleshooting guide with the following results.  I still can not connect to the Internet.
Does anyone have a suggestion.

egle853@egle853-desktop:~$ sudo uname -r
2.6.17-10-generic
egle853@egle853-desktop:~$ 

sudo lshw -businfo

pci@00:1e.0                bridge      82801 PCI Bridge
pci@01:07.0     wifi0      network     AR5212 802.11abg NIC
pci@01:0c.0     eth0       network     82540EM Gigabit

egle853@egle853-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 7
       bus info: pci@01:07.0
       logical name: wifi0
       version: 01
       serial: 00:19:5b:65:c3:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fead0000-feadffff irq:177

egle853@egle853-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"ZoeNet2"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/94  Signal level=-49 dBm  Noise level=-95 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by dstew on 2007-03-19
What do you see in the network-admin window?

---

### Post by egle853 on 2007-03-19
It appears that the card is active.  I am at work and not in front of the machine so I can't tell you  which interface is active.  

as in "The interface ____ is active"

---

