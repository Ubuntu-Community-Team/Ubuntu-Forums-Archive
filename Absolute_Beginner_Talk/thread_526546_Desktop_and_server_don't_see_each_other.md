---
title: "Desktop and server don't see each other"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by perryoh on 2007-08-15
I've installed Edubuntu Desktop and Server 7.04 on two machines, connected with an old Linksys hub. and I can't get them to see each other.  I've checked the cables and switched hubs, but they still seem blind to each other.  Looking at Network Tools, I see that the desktop shows it's static ip address associated with the ethernet device and ipv4.  On the server, Network Tools doesn't show the ip address with the ethernet device nor does it show ipv4.  What do I need to check to figure out what is causing the problem?

---

### Post by dougfractal on 2007-08-15
> I see that the desktop shows it's static ip address associated with the ethernet device and ipv4. On the server, Network Tools doesn't show the ip address with the ethernet device nor does it show ipv4. What do I need to check to figure out what is causing the problem?

did you setup a static ip for the server? 
is the network card working?

> dmesg # check for network card
lsmod #   check network driver
ifconfig     # network setup

---

### Post by perryoh on 2007-08-15
Yes, I did set up a static ip address for the server.  I just ran dmesg |grep eth and got the output "eth0: setting half-duplex"
"eth0: no IPv6 routers present"

Running dmesg|grep eth on the desktop give this output:
[   91.948303] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:11:43:a5:70:a9
[   91.948312] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[   91.948316] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[  101.803304] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  103.596757] tg3: eth0: Link is up at 100 Mbps, half duplex.
[  103.596761] tg3: eth0: Flow control is off for TX and off for RX.
[  103.596956] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  114.485521] eth0: no IPv6 routers present

Does that mean the network card is not working?

---

### Post by dougfractal on 2007-08-15
Your card is loaded.

sudo ifup eth0 # switch on eth0

ifconfig # network setup 

shows your ip and netmask and broadcast?
 example addr:192.168.26.94  Bcast:192.168.26.255  Mask:255.255.255.0

ping localhost -c 4 
ping <IP> -c 4
ping <edubuntu IP> -c 4

---

### Post by perryoh on 2007-08-16
ifup eth0 on the server gave an error message about problems in /etc/network/interfaces and ifconfig did not show the ip address and gateway mapped to eth0.  I edited /etc/network/interfaces and was able to successfully run ifup.  Now ifconfig shows the ip address and other information mapped to eth0.  I can now ping the server.  I think that may have fixed it.  Thanks so much for your help.

---

