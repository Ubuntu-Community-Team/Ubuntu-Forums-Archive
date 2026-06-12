---
title: "[SOLVED] local IP numbers: 127.0.0.1 or 192.168.0.1?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-09
Why does some documentation refer to a local machine as 127.0.0.N and others as 192.168.0.N? What is the difference between these two approaches? Can the same machine use both simultaneously?

---

### Post by tripokey on 2007-09-09
The local machine is 127.0.0.1.

192.168.0.1 is usually your gateway (your router) it can also reside on 192.168.1.1

192.168.X.X (replace X with a number between 0 and 255) are local ip addresses that is reserved for home use (Local Area Networks).

Your computer will always have the 127.0.0.1 ip it is called the loopback.
At the same time your computer (or to be more exact NIC) will have an external ip address that is shown to other computers on the network.

If your computer is on a LAN your external address should be in the 192.168.X.X range.

---

### Post by Bachstelze on 2007-09-09
127.0.0.1 is the loopback address, using this address, a machine can only connect to itself.

192.168.x.x is an adress on a Class C TCP/IP Local Area Network. Using this address, a machine can connect to all other machines on the same (sub-)network.

And yes, both must be active for the system's network capabilities to be fully functional.

---

### Post by will71110 on 2007-09-09
127.0.0.x  is a loop back address for testing the OSI layer on your machine or for local services  and only deals with the local host machine.  It cant be used for other machines to talk to each other over a LAN.  192.168 can however.

---

### Post by n3tfury on 2007-09-09
> **ginestre said:**
> Why does some documentation refer to a local machine as 127.0.0.N and others as 192.168.0.N? What is the difference between these two approaches? Can the same machine use both simultaneously?

127.x.x.x is a loopback connection.  see here :  [http://www.tech-faq.com/127.0.0.1.shtml](http://www.tech-faq.com/127.0.0.1.shtml)

192.x.x.x can be assigned via aDHCP server (your router) when on a home network or manually entered for a static IP if so desired.

---

### Post by ginestre on 2007-09-09
Thanks chaps. That was very quick, very clear and very helpful!

---

### Post by Bachstelze on 2007-09-09
> **n3tfury said:**
> 192.x.x.x can be assigned via aDHCP server (your router) when on a home network or manually entered for a static IP if so desired.

It *must* be 192.168.x.y. 192.x.y.z with x != 168 is a publc IP address and may not be used on LANs.

---

### Post by n3tfury on 2007-09-09
> **HymnToLife said:**
> It *must* be 192.168.x.y. 192.x.y.z with x != 168 is a publc IP address and may not be used on LANs.

don't look into the "x's" so much for this post, umkay?

---

### Post by bwhitaker on 2007-09-09
There are 2 other private address ranges that are sometimes used:
10.x.x.x
172.16-32.x.x

These ranges are more often used by businesses on their LANs but it is possible for a home router to use them as well, I've seen dsl modems with built in routers use 172.16.0.254 as their default address.

---

