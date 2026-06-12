---
title: "NIC Settings"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-12-19
Getting a bit confused with broadcast addresses and gateways.

I want to set up two NICs, one to connect to the router only and one to manage the local network.  I will put a firewall over both.

The existing NIC is configured as follows

eth0  (for router)
Fixed IP		192.168.5.101
Netmask		     255.255.255.0
Broadcast	    192.168.5.255 or should it be to eth1
Gateway		   192.168.5.1

and being configured

eth1 (for local network)
Fixed IP	   192.168.5.100
Netmask		 255.255.255.0
Broadcast	192.168.5.255
Gateway		192.168.5.101 or 192.168.5.1

But how should I set the eth1 gateway address?  Should I point it to the router or to eth0 IP?

Should the broadcast address be the same on both NIC's?  Presumably eth0 needs only to broadcast to the eth1 IP since that is the local network?

---

### Post by Hospadar on 2007-12-19
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
[http://david.decotigny.free.fr/libre/ibook2-debian/etc/network/interfaces](http://david.decotigny.free.fr/libre/ibook2-debian/etc/network/interfaces)
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/interfaces.5.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/interfaces.5.gz)

some good pages on configuring your /etc/network/interfaces file (which is what you'll have to do)

I'm not sure how running two internet connections at the same time works, you may have to remove the "inet" tag from the interface declaration of one of them.

Why do you really need two net connections anyways?

---

### Post by Cypher on 2007-12-19
Hmm..you do not want to have 2 NICs on the same machine in the same network, that's going to cause unnecessary loops and all sorts of messes.

Assuming your router is at 192.168.5.1, then ETH0 can be hooked up to the router and have the IP address you choose, what would ETH1 be connected to? If the same router, you now have 2 paths to get to the same place and packets will just run around in circles.

The idea of have 2 NICs in the same machine is to put them on entirely different networks..192.168.x.x and 10.0.x.x for example. That way Linux knows exactly which NIC to use for communication based on where you want to go.

Perhaps if you would tell us what your final intentions are we can best provide advice..

---

### Post by expatCM on 2007-12-19
What I want to do is to have one NIC to manage only the communication with the outside world through the router and that will do nothing else.

The other NIC to manage the local network only.

That way I have a functioning network when the Internet fails (happens here) and also I can manage security with precision.

So I think what you are saying is that eth0 is fine for communicating with the router(leave it alone) but eth1 needs a new network range.  IP address in that range is then easy, the netmask is a function of the IP and the broadcast address is the end of that range.  The gateway address is not quite clear to me though ....

---

### Post by expatCM on 2007-12-19
Hospadar - very interesting links .... a great find, thank you :)

---

