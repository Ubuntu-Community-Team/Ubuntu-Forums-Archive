---
title: "eth config"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by Compact on 2006-11-22
How do I edit the eth parameters (like ip, default gateway...) with the console?

---

### Post by davmac on 2006-11-22
You can change ip address and netmask with
"sudo ifconfig eth1 192.168.1.20 netmask 255.255.255.0"

You can change the gateway with
"sudo route add default gw 192.168.1.1"

Obviously you need to replace "eth1" and the IP numbers with the relevant info.

Hope this helps,

Dave Mac

---

### Post by willca on 2006-11-22
If you have a static IP you can do it this way.

Edit this file /etc/network/interfaces

autho eth1
iface eth1 inet static
        address 192.168.100.100
        netmask 255.255.255.0
        broadcast 192.168.100.255 
        gateway 192.168.100.1

Save. And restart networking. /etc/init.d/networking restart

HTH
Cheers
-W

[http://www.boondoons.com](http://www.boondoons.com)

---

