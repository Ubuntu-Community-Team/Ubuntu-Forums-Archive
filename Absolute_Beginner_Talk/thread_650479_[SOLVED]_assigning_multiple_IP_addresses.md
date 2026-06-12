---
title: "[SOLVED] assigning multiple IP addresses"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by bconner on 2007-12-26
Hi,

How do I assign more than one IP address to the Ubuntu server?  Seems like it would be easy, but I can't find it.  I've assigned 10.10.10.11 to the eth0 port but need to give it an external IP address that it will answer to as well.  That way I can route traffic to it through the firewall.

Thanks!

--Ben

---

### Post by Cypher on 2007-12-26
Each device can only have one IP address, so if you want a PC to be on both an internal network and also be directly connected to a modem to access the Internet, you'll need two network cards.

Better yet, you should put a router between the PC and cable modem and then you'll get an internal IP address, while the router will get the external IP address and manage the routing..

---

### Post by bconner on 2007-12-26
> **Cypher said:**
> Each device can only have one IP address, so if you want a PC to be on both an internal network and also be directly connected to a modem to access the Internet, you'll need two network cards.

Better yet, you should put a router between the PC and cable modem and then you'll get an internal IP address, while the router will get the external IP address and manage the routing..

Oh!  That will work.  I can just add another virtual IP address to the configuration.  Thanks!

--Ben

---

### Post by bconner on 2007-12-27
> **Cypher said:**
> Each device can only have one IP address, so if you want a PC to be on both an internal network and also be directly connected to a modem to access the Internet, you'll need two network cards.

Better yet, you should put a router between the PC and cable modem and then you'll get an internal IP address, while the router will get the external IP address and manage the routing..

Hi,

I got to thinking about this and am puzzled--if this is the case, how can Ubuntu act as a server to multiple websites with secure certs?  Each website that has a cert needs a unique IP address for the https protocol to find it. ??

--Ben

---

### Post by obfusco on 2007-12-28
As detailed in [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC) you can assign multiple IP addresses to a single physical interface using aliases like eth0:1 or eth1:2 where the part before the colon is the original interface and the part after is an integer.  Note that in Ubuntu the boot-time configuration file is /etc/network/interfaces

---

### Post by bconner on 2007-12-29
> **obfusco said:**
> As detailed in [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch03_:_Linux_Networking#Multiple_IP_Addresses_on_a_Single_NIC) you can assign multiple IP addresses to a single physical interface using aliases like eth0:1 or eth1:2 where the part before the colon is the original interface and the part after is an integer.  Note that in Ubuntu the boot-time configuration file is /etc/network/interfaces

Ok, now I understand.  80% of this is a language barrier.  While I'm pretty familiar with routing, interfaces, etc., I don't yet speak Ubuntu (or any Linux variant) yet. :)

Thanks much!

--Ben

---

