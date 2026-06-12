---
title: "Finding My Router's IP Address"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by corypina on 2007-01-07
I installed Dapper yesterday for the first (official) time.  I have an SMC wireless router that has given me problems in the past, and I want to log into it to see if I can find some solutions.  But I don't know the IP address.

Is there some command I can use to find all the IP addresses on my network?

---

### Post by crispy_420 on 2007-01-07
Use:

> ifconfig

It will list your IP as "inet addr:***********"

Your router will be end in either 0 or 1.

So if your ip is:  192.168.0.5

Your router will be: 192.168.0.0 or 192.168.0.1

Or you can always go to the manual that came with it or the manf website.

---

### Post by blair on 2007-01-07
By convention, an IP address that is the base address in a subnet refers to the subnet as a whole, and is not an IP address of a specific node. 

Your typical home router is configured with one of the following private IP addresses on its LAN port:

192.168.0.1
192.168.1.1
192.168.2.1 (rare)

These are all Class C addresses. Thus the addresses

192.168.0.0
192.168.1.0
192.168.2.0

are NOT addresses of specific nodes, but rather refer to the 

192.168.0.*
192.168.1.*
192.168.2.*

subnets.

---

### Post by Maxcribbin on 2007-01-07
in dos for windows its "ipconfig" to display ip ad.
... sorry, i know that's no help unless ur running a dual boot.

u can see ur ip on lots of credit card sites, pay pal accounts, p2p programs especially.

Hope this is of some help.

Carl.

---

### Post by kent41 on 2007-01-07
> **corypina said:**
> I installed Dapper yesterday for the first (official) time.  I have an SMC wireless router that has given me problems in the past, and I want to log into it to see if I can find some solutions.  But I don't know the IP address.

Is there some command I can use to find all the IP addresses on my network?

Hi
 When I want to find what my router's IP address is I enter    *nslookup localhost*. in a command line on a terminal session.
The first address will give the server address and pc name this is the router address I think. 

You could enter the server name listed (ie  nslookup <server name> ) and get the router address.

I hope this helps.

---

### Post by Tuomas on 2008-07-06
Thanks, kent41!

---

