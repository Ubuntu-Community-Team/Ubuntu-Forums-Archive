---
title: "Dell Latitude D520."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Yume on 2007-11-29
I just installed Ubuntu on my Dell Latitude D520 and I can't seem to get any connection. I've tried using the wireless and just plugging it into the modem, neither work. typing    cat /etc/network/interfaces gives me 

auto lo
iface lo inet loopback

iface eth1 inet dhcp
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid linksys


iface eth0 inet dhcp

auto eth1



typing ifconfig gives me
eth0     Link encap:Ethernet HWaddr 00:19:B9:71:C2:35
            UP BROADCAST MULTICAST  MTU:1500   Metric:1
            RX packets:0   errors:0   dropped:0   overruns:0   frame:0
            TX pacekts:0   errors:0   dropped:0   overruns:0   carrier:0
           collisions:0   txqueuelen:1000
           RX bytes:0  (0.0 b)    TX bytes:0 (0.0 b)
          Interrupt:17

eth1    Link encap: Local Loopback
           inet addr:127.0.0.1   Mask:255.0.0.0
          UP LOOPBACK RUNNING MTU:16436   Metrix:1
          RX packets:0 errors:0  dropped:0   overruns:0  frame:0
         TX packets:0  errors:0  dropped:0   overruns:0   carrier:0
         collisions:0    txqueuelen:1000
        Interuppt:11 Base Address:0x8000


If you need any ther information just let me know. Thank you in advance!

---

### Post by RomeReactor on 2007-11-29
Hi. What wireless card does your Latitude have? please run the following on a terminal:
```
sudo lshw -C network
```

---

### Post by Yume on 2007-11-29
I tried typing that in but I get "command not found"
I also tried      sudo pccardctl ident      and it told me              Socket 0: no product info available 

:(

---

### Post by RomeReactor on 2007-11-29
> **Yume said:**
> I tried typing that in but I get "command not found"

Make sure there are no typos as you write the command; or copy/paste it there.

---

### Post by Yume on 2007-11-29
I tried typing it in more then 10 times, even tried variations of it and I still get command not found....This cannot be good...

---

### Post by natehatewindows on 2007-11-29
try to copy/paste it

```
sudo lshw -C network
```

---

### Post by Yume on 2007-11-29
I apologize for being a complete newbie when it comes to Linux. So I got the command to work and here's what I get.

*-network DISABLED
    description: Wireless interface
    product: BCM94311MCG wlan mini-PCI
   vendor: Broadcom Corporation
   physical id:0
   bus info: pci@0000:0C:00.0
   logical name: eth1
   version: 01
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list ethernet  physical  wireless
   configuration: broadcast=yes  driver=bcm43xx  driverversion=2.6.22-14-generic latency=0   link=no
      

There is more information on there but not sure if you needed all of it and it's kind of a pain typing all that out.  I'm guessing the problem has something to do with the network being disabled, but I have no idea how to change that.

---

### Post by veloce on 2007-12-16
Did you get this sorted?

---

