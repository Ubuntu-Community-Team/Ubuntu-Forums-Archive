---
title: "external address versus static"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-07-01
Hi,

I did something like the following to make my address static

iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


Does that mean the external address of my router is also static?  I dont understand how the two relate to each other.  Could someone please explain.  It would help a lot.

Thanks in advance.

---

### Post by annda on 2007-07-01
it just means that you will get the same IP from the router - 100, and not sometimes 101, sometimes 100 or so. it's important only if you have many computers connecting to the same router. the real external IP is new everytime the router connects to your ISP.

---

### Post by steve.horsley on 2007-07-01
In a DHCP environment, all those values you configured would be provided by the DHCP server. So you have made the router's IP address static in that your PC will always expect to see the router on .1. But I guess you had to configure the router's IP address in to the DHCP server anyway, so it is pretty-much static (meaning unchanging).  

In principle, your IP address and your routers IP address relate to each other in that they must be on the same subnet, but must not be the same. Also, the DHCP server will normnally both assign an address to your PC and tell you what the router's address is. 

If this doesn't clear up your confusion, perhaps you can put the question in different way? I'm not really clear what the confiusion is about.

---

### Post by prostock3 on 2007-07-01
Thanks guys.

I am trying to create a home website with godaddy providing the domain name.  I read I needed to provide a static ip address to go daddy or i have to use dynamic dns.

My current setup is i have a lynksys router, and multiple computers behind my router.  Also, I installed bind9 on my linux machine

Also, If i have one external ip address, can I still use multiple computer in my subnet?

Im confused how to configure all of this.

---

### Post by annda on 2007-07-01
if you need your server to be accessible from outside your home network, you will have to use [dyndns]("http://www.dyndns.com/services/dns/dyndns/"). the static IP you get from your router is local only (your subnet, or the network served to clients connecting via your router).

---

