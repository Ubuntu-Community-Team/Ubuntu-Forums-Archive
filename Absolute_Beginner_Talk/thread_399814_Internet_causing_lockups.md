---
title: "Internet causing lockups"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by GreyGoblin on 2007-04-02
Brand new to Linux, but enthusiastic to learn it... 8-[

After much toil I’ve learned enough to configure my wireless internet card and access the net, with out requesting assistance I’m proud to say.  However now that I can access the net, doing so seems to be causing lockups.  All input and output is frozen.  And this happens regularly within minutes of initiating any activity over the net, where as the system was incredibly while I explored for a few days it off line, and got the wireless card to work. :-k

Included is some terminal output I’m guessing might help diagnose the problem.  
* though the output included does not show it, I can connect to an access point and even view simple websites (google & this site) before it locks up... However I’m sad to say it locks up before I can post, so I’m posting now on a windows system. :mad:

Any help would be much appreciated, thanks [-o<

---

### Post by GreyGoblin on 2007-04-02
durstein@Hydro:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@02:06.0
       logical name: wlan0
       version: 20
       serial: 00:40:f4:c2:66:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 multicast=yes wireless=802.11b
       resources: ioport:d000-d0ff iomemory:f8025000-f80250ff irq:169
  *-network:1 DISABLED
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 9
       bus info: pci@02:09.0
       logical name: eth0
       version: 13
       serial: 00:01:29:fa:51:6c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge multicast=yes
       resources: iomemory:f8020000-f8023fff ioport:d100-d1ff irq:209
durstein@Hydro:~$ lsmod | grep rtl
ieee80211_rtl          85640  1 r818x
durstein@Hydro:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.432 GHz  
          Access Point: Not-Associated   Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:30/100  Signal level:-116 dBm  Noise level:-186 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

