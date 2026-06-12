---
title: "New to Linux in general - Need help Networking"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by DC4Less on 2008-04-19
Hello everyone.

I have Ubuntu 7.10 server intalled on 2 computers.

Setup Now = Cable Modem - wireless router - server1 - server2

Setup Later =Cable Modem - server1 - server2 - wireless router

**server1**
onboard nic eth0 with crossover cable to server2

2ea
dual nic cards eth1 - eth 4

I am going from router IP 192.168.10.1 into eth1 with static IP 192.168.10.2

**server2**
onboard nic eth0 with crossover cable from server1
static IP 192.168.10.4

single nic eth1

My internet works fine on server1 but I cant seem to get server2 working.

Any help would be apreciated.
Thanks

If you are wondering why this setup I am building servers for a wireless ISP.
We will have 3 different internet connections Cable - DSL - T1
We have 136 clients now

Server 1
Web Server
Firewall/Gateway
NAT
Load balancing

Server 2 
Network monitoring
Client Load Balancing
Squid Proxy server
DNS server
DHCP server

I am setting up everything at home for testing.

---

### Post by shahrc on 2008-04-20
> **DC4Less said:**
> ...............

2ea
dual nic cards eth1 - eth 4

I am going from router IP 192.168.10.1 into eth1 with static IP 192.168.10.2

**server2**
onboard nic eth0 with crossover cable from server1
static IP 192.168.10.4

single nic eth1

My internet works fine on server1 but I cant seem to get server2 working.

Any help would be apreciated.
Thanks
................

Correct me if I'm wrong ... server2 is being connected to your server1 right. .. I'm not an expert but if yes aren't you supposed to use different IP ... say 192.168.11.1....
:)

---

### Post by frup on 2008-04-20
> **shahrc said:**
> Correct me if I'm wrong ... server2 is being connected to your server1 right. .. I'm not an expert but if yes aren't you supposed to use different IP ... say 192.168.11.1....
:)


Don't you then need to make the subnet 255.255.0.0 or the like?

---

### Post by diablo75 on 2008-04-20
> **frup said:**
> Don't you then need to make the subnet 255.255.0.0 or the like?

Well... you could do that, but it wouldn't help anything.  It would be best to stick with the default 24 bit address, 255.255.255.0.

---

