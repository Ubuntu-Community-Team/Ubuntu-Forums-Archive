---
title: "Use as gateway"
date: 2013-12-27
forum: Any Other OS
---

### Post by brill.kennyzeniant on 2013-12-27
Hi,

I own a raspberry pi with raspbian (which is veeeeery similar to ubuntu, so I posted here), and I want to use it as a gateway so all traffic that goes through it is sent/received through a VPN, I did this process on my Mac earlier and works very well using this tutorial: [http://rodrigo.sharpcube.com/2010/06/20/using-and-sharing-a-vpn-connection-on-your-mac/](http://rodrigo.sharpcube.com/2010/06/20/using-and-sharing-a-vpn-connection-on-your-mac/) 

Which does this on the vpn-enabled computer: 
> natd -interface tun0
ipfw -f flush
ipfw add divert natd ip from any to any via tun0
ipfw add pass all from any to any
sysctl -w net.inet.ip.forwarding=1

Where:
tun0 = VPN interface

I have looked arround this forums and some other pages and the only tutorials on making a "gateway ubuntu server" I have found require TWO interfaces (eth0, eth1) which is impossible on my hardware...

Is there anyway to achieve this?

---

### Post by Bucky Ball on 2013-12-28
*Thread moved to **Other OS/Distro Support**.*

Similar, but not the same and not an officially supported derivative in the main support areas on these forums. Try here:

[http://www.raspbian.org/RaspbianForums](http://www.raspbian.org/RaspbianForums)

---

