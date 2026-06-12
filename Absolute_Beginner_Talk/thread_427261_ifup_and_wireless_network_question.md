---
title: "ifup and wireless network question"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by The Thinman on 2007-04-29
Hi,

after fruitless attempts at getting my Netgear WG111t USB card working, I bought a Ralink USB dongle from thelinuxemporium. I've installed the drivers and I am now connected to the internet via Ubuntu.

However I have  a couple of questions: I have to type in sudo ifup rausb0 to get the network connection to work. Can I just add 'auto rausb0' to the /etc/network interfaces  file to get this to come up automatically?

Secondly, even after issuing the ifup command the network won't work immediately. I have to wait about 5 minuted before I can connect. Does anyone know why this is?

Thanks

---

### Post by Kobalt on 2007-04-29
> **The Thinman said:**
> I have to type in sudo ifup rausb0 to get the network connection to work. Can I just add 'auto rausb0' to the /etc/network interfaces  file to get this to come up automatically?
Suposedly yes if you don't already have this "auto rausb0" line in your /etc/network/interfaces file then you can add it to activate your connection at boot time (**if you don't use Network-Manager though**).

Network-Manager can be the cause of the activation delay of your wifi connection (I have seen it several times...) : what is your encryption key method ?

---

### Post by The Thinman on 2007-04-29
> **Kobalt said:**
> Suposedly yes if you don't already have this "auto rausb0" line in your /etc/network/interfaces file then you can add it to activate your connection at boot time (**if you don't use Network-Manager though**).

Network-Manager can be the cause of the activation delay of your wifi connection (I have seen it several times...) : what is your encryption key method ?

I've got the network open at the moment while it settles in. "auto rausb0" was not in the interfaces file but I don't know if I'm using Network-Manager. I did look in the network option on the menu to see if the network was recognized but I haven't ran anything else.

Thanks

---

### Post by Kobalt on 2007-04-30
> **The Thinman said:**
> I don't know if I'm using Network-Manager
When you left-click on your network icon in the notification area, do you see a graphical list of networks available or does a window appear with your interface and your signal strength ?
The first choice is Network-Manager...

---

### Post by The Thinman on 2007-05-04
Hi,

interface and signal strength.

---

