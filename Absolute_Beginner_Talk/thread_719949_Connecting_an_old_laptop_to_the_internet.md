---
title: "Connecting an old laptop to the internet?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by nogoodreason on 2008-03-09
Hi there.

I've recently installed Xubuntu on a very old laptop ([Samsung V20 cXTD]("http://www.samsungpc.com/products/v20/v20_specification/v20_specification.htm")).  I'm trying to get it to connect to the internet using my Netgear WG111T Wireless Dongle, and have seen several other threads about problems with this dongle in Linux. [[1]]("http://ubuntuforums.org/showthread.php?t=151256")[[2]]("http://www.linuxquestions.org/questions/ubuntu-63/wireless-nightmare-wg111t-usb-and-linux-442864/")

However, all these solutions involve first connecting to the internet, which I can't do.  I can download things onto a  USB pen and transfer them over, but I'm a total Linux newbie and really would appreciate some advice as I currently don't know what to do, what to download, or where to start :?


*Sidenote: I can plug the laptop directly into my LAN for a little while if that'll be the simplest way to download things to it, only this baffled me slightly as well... when I plug it into the LAN, the laptop says it's connected to a network yet I'm not able to load any websites.  (Possibly an unsigned modem driver?)*

---

### Post by Daveski on 2008-03-09
> **nogoodreason said:**
> 
However, all these solutions involve first connecting to the internet, which I can't do. 

This machine does have an integrated Intel 10/100 NIC which is certainly supported 'out of the box'. If you are not getting any websites, then you either have some security on your network, or the network settings are not being given to the latop when plugged into your LAN. I suspect DNS settings - do other machines just work on your internet connection or do you have to tweak any settings?

---

### Post by nogoodreason on 2008-03-09
Daveski,

I have a Linksys WRT54GS router with the latest firmware.  All other computers in the house connect instantly to the net as soon as the LAN cable is plugged in - and that includes my own computer when I dual-boot into Ubuntu.  There's MAC Address Security on the wireless, but nothing on the LAN cable.


When I installed Xubuntu on this laptop, it mentioned an unsupported driver which I believe was a modem.

---

### Post by louieb on 2008-03-09
Boot to Ubuntu with the Ethernet cable plugged in. That should get you an internet connection.
IF that fails open a terminal window. [B]Applications>Accessories>Terminal.
[/B]and try to get an IP address via DHCP.
```
sudo dhclient
```

---

### Post by nogoodreason on 2008-03-09
> **louieb said:**
> Boot to Ubuntu with the Ethernet cable plugged in. That should get you an internet connection.
IF that fails open a terminal window. [B]Applications>Accessories>Terminal.
[/B]and try to get an IP address via DHCP.
```
sudo dhclient
```


Sorry, maybe I wasn't clear.  I dual-boot Ubuntu on my main (Vista) PC - both Vista and Ubuntu connect to the net fine.

It's Xubuntu, on the laptop, that I'm having trouble with.  I've tried booting the laptop with the ethernet cable already plugged in, but still had no success accessing to the internet (even though it seems to think it's connected to *something*)

---

### Post by louieb on 2008-03-09
Check to see if you have an IP address
```
ifconfig
```should see something like this (my ip is in red)
```
eth1      Link encap:Ethernet  HWaddr 00:07:E9:78:B3:80  
          inet addr[COLOR="Red"]:192.168.1.7[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe78:b380/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12940824 (12.3 MB)  TX bytes:1637400 (1.5 MB)

```at least you'll be able to tell if it sees your  network card.
Did you try **sudo dhclient** ?

If you have an IP address you should disable ipv6 an see if that helps. 
[http://louboldt.com/ilinuxmisc.htm#ipv6](http://louboldt.com/ilinuxmisc.htm#ipv6)

---

