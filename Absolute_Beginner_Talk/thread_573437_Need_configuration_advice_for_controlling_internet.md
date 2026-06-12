---
title: "Need configuration advice for controlling internet traffic"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by jbullman on 2007-10-11
I am helping a small Mayan city in the Guatemalan highlands with their computers.  We have a satellite connection to the internet, that is limited to 375Mb per day.  The satellite is connected to a modem (DW4020) that has DHCP but no other capabilities.  I have one Dell PowerEdge server with Ubuntu 6.06 server installed.  It currently has one working ethernet card.

I have available one Netgear WGR614v5 wireless router with 4 wired ports, one D-Link DGL-4100 router, several switches, and several ENL832-TX-RENT ethernet cards, and can use these in any configuration I see fit.  

The goal is to provide internet access, even though it may be slow, to about 50 computers, but to limit them so we do not go over our 375Mb/day limit.  If we go over, our access is cut for 24 hours.  

One possibility is to run all requests through Squid.  I can get Squid to monitor traffic, but I cannot get the traffic to go there!

Questions:

1. Will Squid, if I configure it properly, limit total upload and download amounts?
2. Is there a different mechanism I should consider instead?

Suppose I choose mechanism "M".  

3. How should I force the traffic through M?
a) I tried to connect all computers to the Netgear router, and to set port forwarding for port 80  to the Ubuntu server.  I thought if that worked, I could then use iptables to take the traffic and redirect it to Squid via port 3128.  But the port forwarding didn't seem to work.

b) I thought of putting a second network card into the server, and having all traffic go from the router to the server to the satellite.  However, ubuntu does not seem to recognize the network card.

I'm experienced enough to get this far, but really new to Ubuntu and Unix, so I'm stumped by all sorts of things, large and small.  I'm also not knowledgeable about routers and stuff except at the basic level.  If you could guide me to a configuration that we know should work, I can then work with you to get it functioning.

Thanks so much!

---

