---
title: "How to do portforwarding?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by rons_rons on 2006-10-29
I have look through the forums but i just cant find an answer i want
basically i want to open a port first
i tried using iptables and firestarter .to open the port
but when i use ubuntu desktop port scan tool i scan the port is still not open

i read somewhere saids that you need to install some dameons for it to listen to then the port will be automatically opened

but what i actually want to do is just to open port 25 and forward it into my private pc port 25 which has the postfix server

how can i do this ...anyone can help?

---

### Post by bswilson on 2006-10-29
> **rons_rons said:**
> basically i want to open a port first
i tried using iptables and firestarter .to open the port
but when i use ubuntu desktop port scan tool i scan the port is still not open

You can't 'open' a port with Firestarter or iptables.  You can only ensure that a port is not blocked with these tools.  

> **rons_rons said:**
> but what i actually want to do is just to open port 25 and forward it into my private pc port 25 which has the postfix server

I understand what you're trying to do; but I don't understand why.  If you have a device like a linksys/netgear/belkin router, it can forward all the tcp/25 traffic to your Postfix server without touching your Ubuntu system in the first place.

Maybe you can post back some details of the network you have set up, so we can help you.

---

### Post by cptjaben on 2006-10-29
is this a home network? do you have a router, if so you may need to forward the ports using the router control panel. or perhaps you have a firewall on.

---

### Post by jd65pl on 2006-10-29
Configure your box to be a router see [this]("http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html")

---

### Post by JayTee on 2006-10-30
Firestarter will allow you to forward an external port on the ethernet interface to an internal port. On the policy tab at the bottom right click on a blank space and select Add Rule. The dialog that pops up is fairly self-explanatory.

---

### Post by rons_rons on 2006-10-31
sorry perhaps i neber clarify myself but the private pc is actually a guest os in VMWARE
can provide me further help on this issue?


> **bswilson said:**
> You can't 'open' a port with Firestarter or iptables.  You can only ensure that a port is not blocked with these tools.  



I understand what you're trying to do; but I don't understand why.  If you have a device like a linksys/netgear/belkin router, it can forward all the tcp/25 traffic to your Postfix server without touching your Ubuntu system in the first place.

Maybe you can post back some details of the network you have set up, so we can help you.

---

