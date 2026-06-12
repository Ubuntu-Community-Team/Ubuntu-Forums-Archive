---
title: "i have lost network connections."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by hlekat on 2008-01-21
without doing anything suspicious i have lost the connection with the network card.

in network settings @ location there are not network adapters.

and when i select the combo box to see if its any adapter available nothing happens.

---

### Post by njparton on 2008-01-21
Post your /etc/network/interfaces file please.

You could also try:

```
sudo ifconfig up eth0
```

replace "eth0" with the number of your network interface (from the interfaces file).

---

### Post by hlekat on 2008-01-22
@ etc/network/interafaces :
auto lo
iface lo inet loopback


When i typed sudo ifconfig eth0:

 Link encap:Ethernet  HWaddr 00:1B:FC:6C:BF:9C  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe6c:bf9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:6534 (6.3 KB)  TX bytes:4221 (4.1 KB)

---

### Post by njparton on 2008-01-22
You should have an eht0 entry in that file too.  Sounds like you have a hardware problem of some kind.  Try adding the following to that file:

```

iface eth0 inet dhcp
auto eth0
```

then restart networking:

```

sudo /etc/init.d/networking restart

```

If that doesn't work I either got the eth0 bit a little wrong (at work at the moment) or you have a more serious problem.

---

### Post by hlekat on 2008-01-22
* Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5378
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:fc:6c:bf:9c
Sending on   LPF/eth0/00:1b:fc:6c:bf:9c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:fc:6c:bf:9c
Sending on   LPF/eth0/00:1b:fc:6c:bf:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.13 -- renewal in 124317 seconds.

,
but still offline.

thanks for your patience

---

### Post by rosegarden78 on 2008-01-22
Do you have little wireless bars and/or system dock on your kicker?  If not type at a terminal or press Alt-F2

**nm-applet**

Sometimes the modem and router will freeze or the ISP drops you.  In that came, simply power-down or unplug your router/modem.  Then plug them it.

---

### Post by lintoon on 2008-01-22
You could try booting off the Ubuntu cd to test your lan card.

---

### Post by njparton on 2008-01-23
What sort of network card is it? Onboard, PCI card, USB etc? Can you give us the specs?

You may be able to find drivers for it and compile them into the kernel to get it working again.  I did this with my intel pro PCI-E card and it's really easy.

---

### Post by hlekat on 2008-01-23
> **rosegarden78 said:**
> Do you have little wireless bars and/or system dock on your kicker?  If not type at a terminal or press Alt-F2

**nm-applet**

Sometimes the modem and router will freeze or the ISP drops you.  In that came, simply power-down or unplug your router/modem.  Then plug them it.

i don't full understand what are you telling about, i have restart the router i typed the commands but nothing, the router is working fine for my other pc. and the network adapter is working (i use the live cd)

i have asus p5k with onboard network adapter:
Attansic L1 Gigabit Ethernet 10/100/1000Base-T Controller.

---

### Post by njparton on 2008-01-24
Never heard of it I'm afraid and I'm out of suggestions...

I suggest you start a new thread under the networking section of the forum or try a re-install.

It may sound a bit drastic, but a 20 min re-install may save you a lot of time in the long run!

Good luck.

---

### Post by szr4321 on 2008-01-26
Seeing that you have an Attansic L1 chipset, you might find the following posts helpful:
[http://ubuntuforums.org/showthread.php?t=498778]("http://ubuntuforums.org/showthread.php?t=498778")
[http://lkml.org/lkml/2007/6/21/435]("http://lkml.org/lkml/2007/6/21/435")
[http://ubuntuforums.org/showpost.php?p=4211766&postcount=83]("http://ubuntuforums.org/showpost.php?p=4211766&postcount=83")

---

### Post by jstableford on 2008-01-27
Hi there - pardon the interruption, but I'm having a similar issue. I bought a new motherboard/CPU yesterday (ASUS PK5 SE/Core 2 Duo 2.66) and the onboard gigabit LAN has never worked. I can't even get a light indicating a connection. My next idea was to pull an old 10/100 PCI card out of my old box and try installing that, and it worked.

While I was then working out display adapter issues, I restarted, and the network card no longer worked. This time, instead of seeing no eth0 adapter with ifconfig, I would see one, however it could not see my network. DHCP is broadcasting properly, and even a manual ip configuration set.

Help, please! I am trying to discern whether or not I got a bum motherboard, and with no connectivity it's nearly impossible.

Thanks in advance,

J

---

