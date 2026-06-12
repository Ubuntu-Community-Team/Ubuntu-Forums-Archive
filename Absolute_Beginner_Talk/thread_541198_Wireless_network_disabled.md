---
title: "Wireless network disabled"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by suc5ct on 2007-09-02
I have an old IBM Thinkpad with a wireless PCMCIA card. Complete novice -- it's day 2 with Feisty Fawn. I've followed the wireless troubleshooting guide, card seems to be supported, driver seems to be recognized. I've configured the card ESSID, etc. using the system/administration/network interface, and double-checked the WEP settings, that the wireless router is working with another (windows) computer and the same settings (and the ESSID is being broadcast). But I'm not connected and the wireless symbol shows in red in the network interface.

lshw gives this:

 *-network DISABLED
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 1
          bus info: pci@03:00.0
          logical name: eth1
          version: 02
          serial: 00:14:bf:3a:35:61
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:d4000000-d4001fff irq:11

And iwconfig gives this:

eth1      IEEE 802.11b/g  ESSID:"0"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can anybody recommend what I should try next? Many thanks in advance...

---

### Post by Kolfinna on 2007-09-02
What's the output of:
nano /etc/network/interfaces

---

### Post by suc5ct on 2007-09-02
iface eth1 inet dhcp
wireless-essid 0607864903

Thanks!

---

### Post by Kolfinna on 2007-09-02
Hmm... sometimes Linux has its own generic drivers for wireless cards, but they rarely work. By saying that it recognizes the driver, do you mean that you've installed it using ndiswrapper or a similar program?

---

### Post by suc5ct on 2007-09-02
After reviewing other posts, I got the impression that Feisty Fawn supported the card "out of the box" -- and the wireless troubleshooting guide seemed to be saying that the output of lshw showed that a/the driver was installed, and that the trouble was more in the "network disabled" part -- typically a sign that the wireless card inside the computer must first be enabled somehow, but in this case, it's an external PCMCIA card, so doesn't really apply, unless I have to enable it in some other way... 

And by the way, I just realized that what I posted doesn't include the WEP info I mentioned -- I'd turned off WEP to see if it made any difference -- but no joy...

---

### Post by bonesniddle on 2007-09-02
I'm a bit of a newby at this but I also ran into wireless issues on an older Vaio. I did the research to get the most "out of the box" PCI card I could get and I never got it to work with network manager. Through an  earlier thread I found out about Wicd and downloaded and ran with that. It ended up being quicker and easier than when I was a Windows user. I wish I could give proper credit where it's due but I've forgotten who I actually found the information from, but Wicd was a very simple quick fix. Like I said, I'm a bit of a noob so hopefully someone else can give better details, but that's my suggestion-Wicd. Good luck, Jim.

---

### Post by peebly on 2007-09-02
> **suc5ct said:**
> I have an old IBM Thinkpad with a wireless PCMCIA card. Complete novice -- it's day 2 with Feisty Fawn. I've followed the wireless troubleshooting guide, card seems to be supported, driver seems to be recognized. I've configured the card ESSID, etc. using the system/administration/network interface, and double-checked the WEP settings, that the wireless router is working with another (windows) computer and the same settings (and the ESSID is being broadcast). But I'm not connected and the wireless symbol shows in red in the network interface.

lshw gives this:

 *-network DISABLED
          description: Wireless interface
          product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
          vendor: Broadcom Corporation
          physical id: 1
          bus info: pci@03:00.0
          logical name: eth1
          version: 02
          serial: 00:14:bf:3a:35:61
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master ethernet physical wireless
          configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
          resources: iomemory:d4000000-d4001fff irq:11

And iwconfig gives this:

eth1      IEEE 802.11b/g  ESSID:"0"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can anybody recommend what I should try next? Many thanks in advance...

Have you seen this thread.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

