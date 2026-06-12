---
title: "Can't get DHCP IP"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by bobberu on 2006-11-14
I have a dual boot Win/Ubuntu system. The Win side works fine with the Linksys router. But after I installed Ubuntu on top of Fedora Core 4 (which also worked fine with the router) I can't seem to get an IP from my router. Any suggestions welcome....!

Here's what happens when I try to get things going manually: 

bob@bob-desktop:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
bob@bob-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by CatKiller on 2006-11-14
I normally just use the graphical tool at System -> Administration -> Networking to set whether the IP address is static or dynamic. It's always worked fine for me.

---

### Post by jhenager on 2006-11-14
For one thing, ifdown eth0 does the opposite of what you are looking to do.
ifup - bring a network interface up

ifdown - take a network interface down   

Use the graphical tool as CatKiller suggests. Make sure the interface is activated, and tick DHCP. Should get you going.

---

### Post by marx2k on 2006-11-14
> **bobberu said:**
> I have a dual boot Win/Ubuntu system. The Win side works fine with the Linksys router. But after I installed Ubuntu on top of Fedora Core 4 (which also worked fine with the router) I can't seem to get an IP from my router. Any suggestions welcome....!

Here's what happens when I try to get things going manually: 

bob@bob-desktop:~$ sudo ifdown eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
bob@bob-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:80:ad:8a:30:d2
Sending on   LPF/eth0/00:80:ad:8a:30:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have the same exact problem with my setup.  I am able to get everything going through the graphical tools but I also would like an answer as to how to get this going through commandline.  

I am one of those people that want to know how to do EVERYTIHNG through the commandline that you can do via graphical interface.  Especially since I dont want to RELY on gnome if it breaks down

---

### Post by bmillsap on 2006-11-14
I don't know if this will help here, but I recall that when I was first messing around with different configurations, just doing ifdown/ifup would often lead to this kind of behavior, where it didn't seem to want to get a DHCP lease back (in this case from my ISP, I'm using the machine as a gateway).  I started always restarting networking (sudo /etc/init.d/networking restart) instead of just taking the interface up and down, and that always seemed to work, it would get an IP.  Might help you if the problem is specifically ifdown/ifup, won't help if you're saying that your machine doesn't get an IP address ever, even on startup.

---

### Post by marx2k on 2006-11-14
> **bmillsap said:**
> I don't know if this will help here, but I recall that when I was first messing around with different configurations, just doing ifdown/ifup would often lead to this kind of behavior, where it didn't seem to want to get a DHCP lease back (in this case from my ISP, I'm using the machine as a gateway).  I started always restarting networking (sudo /etc/init.d/networking restart) instead of just taking the interface up and down, and that always seemed to work, it would get an IP.  Might help you if the problem is specifically ifdown/ifup, won't help if you're saying that your machine doesn't get an IP address ever, even on startup.

I will give this a shot once I get home and post my results.

My main problem now is that the wireless connection seems to drop and resurface every 10 minutes or so.  During the drops I try to ping the router and get host unreachable, when it comes back up it's a <2ms ping time.

Lots of other people seem to get the same problem.  Installing wifi-radar seems to fix the problem but I also dont want to rely on an app to do what the system is supposed to do without it.

---

### Post by bobberu on 2006-11-14
Alas, I began with the GUI networking tool, which didn't work, and that's why I fell back to the command line, where it still didn't work. With the GUI, it showed eth0 as active, but the browser wouldn't connect to anything, even if I used an IP address. Couldn't even connect to the router (192.168.1.1). So I still have the same problem....:( Still open to suggestions!

---

### Post by CatKiller on 2006-11-14
> **bobberu said:**
> Alas, I began with the GUI networking tool, which didn't work, and that's why I fell back to the command line, where it still didn't work. With the GUI, it showed eth0 as active, but the browser wouldn't connect to anything, even if I used an IP address. Couldn't even connect to the router (192.168.1.1). So I still have the same problem....:( Still open to suggestions!

You could try disabling IPv6. I've heard that that can be problematical in some circumstances.

Also, that 255.255.255.255 looks peculiar to me - how is it configured?

---

### Post by bobberu on 2006-11-15
How do I disable IPv6?

I've also been playing around some more and discovered that I do get connectivity if I pull out the ethernet cable from the router and plug it back in - but only for about 1 min before it times out. I tried doing this several times and pinging the router, logging to my router, browsing a web page, and it always responds for 1 min then freezes. Whassup with that??!!

---

### Post by CatKiller on 2006-11-15
> **bobberu said:**
> How do I disable IPv6?

I don't know.

Apart from searching the forums for instructions, you could try [these]("http://doc.gwos.org/index.php/DisableIPV6"), although I've never had to do it.

---

### Post by bobberu on 2006-11-19
Just in case anyone's interested....I changed the kernel from 2.6.15-23 to 2.6.15-27 and the problem disappeared!

---

