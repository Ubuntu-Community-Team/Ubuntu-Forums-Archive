---
title: "2 PC's + router with 1 port = trouble setting route"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Jh00 on 2006-06-24
Hi there!

First of all, although I'm trying to setup this network using Windows boxes, a) I plan to switch both of them to linux, b) I have faith in this community and c) I think it would be trivial to help me out with this.

Ok, here is the problem. I have PC1 (with 2 network cards) connected to 1 router. PC2 is connected to PC1. PC1 access to the internet is OK. However, I don't know how PC2 can talk with the internet through PC1 and the router...

Here is a diagram with my problem. I don't know what to write where the question marks are. (click to expand).

[[IMG]http://img456.imageshack.us/img456/9894/trouble5fz.png[/IMG]](http://imageshack.us)

REMARKS: 
a) I can't use DHCP with PC1 because I must route certain ports to it;
b) PC2 don't need to have a specific IP;
c) If anyone could tell me the IP's I need to fill into the question marks places and explain why it is that way, I would love to learn.

Thank you very much!

---

### Post by Kilz on 2006-06-24
[QUOTE=Jh00]Hi there!

First of all, although I'm trying to setup this network using Windows boxes, a) I plan to switch both of them to linux, b) I have faith in this community and c) I think it would be trivial to help me out with this.

Ok, here is the problem. I have PC1 (with 2 network cards) connected to 1 router. PC2 is connected to PC1. PC1 access to the internet is OK. However, I don't know how PC2 can talk with the internet through PC1 and the router...

Here is a diagram with my problem. I don't know what to write where the question marks are. (click to expand).

[[IMG]http://img456.imageshack.us/img456/9894/trouble5fz.png[/IMG]](http://imageshack.us)

REMARKS: 
a) I can't use DHCP with PC1 because I must route certain ports to it;
b) PC2 don't need to have a specific IP;
c) If anyone could tell me the IP's I need to fill into the question marks places and explain why it is that way, I would love to learn.

Thank you very much![/QUOTE]

Hook PC2 to router and not to PC1
Static routing instructions would be esier knowing the router brand and model

---

### Post by Jh00 on 2006-06-24
Router is a 3Com Hommeconnet. It was a ADSL modem, but I converted it into a router as I explained in another thread.

Hooking PC2 directly to the router isn't possible (it is downstairs). BTW, if I would follow your advice, PC1 (mine) would be offline, so it isn't acceptable...

Any other idea?

---

### Post by Kilz on 2006-06-24
[QUOTE=Jh00]Router is a 3Com Hommeconnet. It was a ADSL modem, but I converted it into a router as I explained in another thread.

Hooking PC2 directly to the router isn't possible (it is downstairs). BTW, if I would follow your advice, PC1 (mine) would be offline, so it isn't acceptable...

Any other idea?[/QUOTE]
Sorry I don't have any more ideas, most routers that I have used have multiple output sockets. Most of them also have a browser based configuration available. I know its theoretically possible to do it the way you are describing. But I have no knowledge about how to do it. You may be better off spending the $40 or so dollars on a router then plugging both computers into it. Linksys and other comercial routers make it easy.

---

### Post by Jh00 on 2006-06-25
Anyone else?

---

### Post by Jh00 on 2006-06-25
Hey, it can't be that difficult! I wish I knew where to look for more information myself, but I tried...

---

### Post by Apple 101 on 2006-06-26
Can't you just connect the router to PC1 and connect PC2 to PC1.  That way, by setting up the DHCP package for ICS (use the Firestarter package for this) you can route automatically through PC1.

---

### Post by Jh00 on 2006-06-26
PC2 is connected to PC1, and PC1 is connected to the router.

OK, I can use DHCP to set a IP in PC2. But which IP should NIC2 use in PC1 ?

---

### Post by bollix47 on 2006-06-26
Have you looked at using [ICS]("http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02july01.mspx")?

---

### Post by e_james on 2006-06-26
Assuming Windows XP, I know how I would do it. In network connections create a bridge joining nic1 and nic2. The bridge is then the object with the IP address. This works. I have done it. I expect Linux has an equivalent procedure but I have no idea what it is at this time.

---

### Post by Apple 101 on 2006-06-27
Open Synaptic and get Firestarter.  This will setup ICS for you.  I just tried it!

---

