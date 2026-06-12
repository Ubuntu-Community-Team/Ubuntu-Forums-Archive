---
title: "Whant do I need to know in order to connect to a LAN?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-06-16
There is a local area network where I live. It is spanned around the neighbourhood, and there are ~500 computers connected. All of them are connected to the internet via a main server or gateway, I don't know what to call it (it runs Linux, of course).

Every user has an unique IP address. It is not to be automatically detected, instead the admin sends this information to each user. These are real IP addresses, not 192.168.0.1-style IP addresses.

So, basically, the info provided by the admin (the assigned IP address, the gateway address and the DNSs, I belive) should be enough to get me connected on a WinXP machine.

The question is, will this info be enough to connect to the local network (and to the internet) on Ubuntu? Is there any more info I need to know? Also, is setting up a network in Ubuntu just as easy as in XP (i.e. selecting Properties on the TCP/IP protocol and inserting a bunch of numbers)?

Sorry for the XP analogy, but it's the only way I've connected a PC to a LAN.

P.S. The PC runs Ubuntu Breezy, and the network card has been detected and installed (it's a plain old 10/100 Ethernet card, not for wireless nets, therefore with no wireless issues people complain on the forums - I just plug-in the UTP cable and it should work).

---

### Post by u.b.u.n.t.u on 2006-06-16
It is best to direct your questions to the people who run the network you want to join. 

You need a computer with ethernet capability, and a cable to the router that connects to the internet.  (As it applies to your situation as you have detailed it).

"Also, is setting up a network in Ubuntu just as easy as in XP (i.e. selecting Properties on the TCP/IP protocol and inserting a bunch of numbers)?"

To get on the internet with ubuntu 6.06 is very easy. Actually ubuntu all but automates the entire process during the install. Just make sure you have a live connection for ubuntu to process.

---

### Post by zugu on 2006-06-16
Thank you for the reply.

Maybe the way I formulated the question was vague. Let me also add some new details to the situation.

The network admin won't help me set up the network unless I'll run WinXP. Acutally, I know nobody running something else than XP in the network. If some issue were to appear, I would be 'on my own'.

I have a PC, an ethernet card, cables - everything hardware. I'm just concerned about the software tweakings I need to do in order to get a working connection once the UTP cable is plugged in.

AFAYK, the router/gateway assigns IP addresses based on network cards' MAC. I'm not asking for the exact addresse I need to know, of course the network admin is the only one who can provide me with them.

So there are two possibilities: if I need the gateway, ip, subnet mask and DNSs, I'll have them from the admin. Connecting using just these info works for XP machines. Will this be enough for getting a working connection on Ubuntu? Or do I need more tweakings etc. ? (more tweakings == things from the commandline, actually everything else NOT done through System >> Administration >> Network)

The second possibility it's something I heard from someone: if the network is using automatic IP assignmet, I won't need any tweakings at all and the connection will be working 'by itself' :) as long as I have the cable pluugged in at the both ends. Is this possible?

And the computer runs Breezy, not Dapper.

---

