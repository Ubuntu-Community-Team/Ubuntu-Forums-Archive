---
title: "Wireless Disabled"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Robespierre08 on 2007-05-21
I've been trying to get my PRO/Wireless 2200BG working, and it seems to be disabled as the following code can attest to. How do I enable the card?

```
becky@Spud:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d7:9a:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.105 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfdfe000-dfdfffff irq:201
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:98:a8:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=radio off
       resources: iomemory:dfdfd000-dfdfdfff irq:177

```

---

### Post by bukwirm on 2007-05-22
Try "sudo ifup eth1".

---

### Post by Robespierre08 on 2007-05-22
Thanks for the reply. Unfortunately...

```
sudo ifup eth1
Ignoring unknown interface eth1=eth1.
```

---

### Post by Robespierre08 on 2007-05-22
OK, contrary to my previous post, it did enable network 1:

```
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d7:9a:3a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.105 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfdfe000-dfdfffff irq:201
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:98:a8:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=radio off
       resources: iomemory:dfdfd000-dfdfdfff irq:177

```

However, I still cannot see or connect to any wireless networks.

---

### Post by Ferrat on 2007-05-22
Fiesty has alot of WiFi support, especially for pci cards, are you using gnome? in that case you should have a network (two comps one behind the other) icon on your upper right taskbar, left click that one and see if you got the right connection selected (if you got more than one) if you do, pick **Manual Configuration** , this brings up your networksettings, make sure your wireless connection is there, that it's the only connection that has been **[_v_]** checked and that it's set to the right settings, default is roaming I think, you might need to change that, and select dhcp or static IP ect

---

### Post by bukwirm on 2007-05-22
What output do you get from:
"sudo iwconfig"
"iwlist scan"

and what network are you trying to connect to?

---

### Post by Robespierre08 on 2007-05-22
```
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Robespierre08 on 2007-05-22
I'm trying to connect to an open network.

---

### Post by bukwirm on 2007-05-22
Are you sure that the wireless card is turned on? Most laptops have some kind of switch that lets you turn the wireless card off to conserve power.

---

### Post by verymagicalguy on 2007-05-22
> **bukwirm said:**
> Are you sure that the wireless card is turned on? Most laptops have some kind of switch that lets you turn the wireless card off to conserve power.

I was going to say, try "Fn+F2" if you're on a laptop, that usually enables/disables the wifi card.

---

