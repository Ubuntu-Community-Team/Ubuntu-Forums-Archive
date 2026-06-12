---
title: "Is It True (Network Wired)?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-09-03
would anyone be able to tell me if having wired is easier setting up than wireless example network card driver wise as i read it in a Personal Computer World Magazine that had an article in it about Ubuntu 6 and has anybody had any problems with wired network  card

---

### Post by Miademora on 2006-09-03
Most wired networkcards work out of the box and make no problems at all. It is easier to setup, more secure and more reliable.

---

### Post by daemonoid on 2006-09-03
Far far easier to have a wired network!

In fact i drilled hole through my wall and hooked direct to my router in less time than it takes most people to get wireless working :)

---

### Post by insane_alien on 2006-09-03
wireless is fine. WPA seems a bit shoddy but thats probably just me not being able to get it to work. WEP 128 is good enough encryption for me.

---

### Post by Episteme on 2006-09-03
all depends on the network card - but in general, I've found wired easier to set up (no wireless security to set up, hardware more likely to work out of box, but the cables can be unsightly).

---

### Post by daemonoid on 2006-09-03
to expand on my last post...

Wireless can be fairly straight forward if you have the right card:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Other than that though, you need to use windows drivers with a wrapper. Which of course is more painfull, not least because you have no network connection to connect to the net to read tutorials and download the correct drivers...

Most wired chipsets are supported because it's such an established standard.

---

### Post by a-musing amazon on 2006-09-03
Wireless can be a particular pain in 64-bit if you have the 'wrong' network card. If your 32-bit solution only works using nsdiswrapper you will need a 64-bit Windows driver - and Netgear, for example, don't do them.

Having banged my head on this wall with my Netgear WG311v2 I changed to using a Wireless Bridge i.e. from the computer's POV a wired solution. Installing this (i.e. enabling the ethernet port) was very simple. This also put all the WEP/WPA negotiation on the Netgear firmware rather than trying to do it on the PC.

You can still get problems with wired if its implemented in an new motherboard chipset - I previously had this problem with my current motherboard, an AsRock 939-56M, with a SiS chipset, before I installed Ubuntu and when it was new simply because the chipset wasn't then known to the open source community. This was when I was using a 32-but Knoppix distro.

---

### Post by tc3racer on 2006-09-09
Thanks every one that has voted and posted it is clearly that linux works best with wired also thanks to the user "daemonoid" for leaving that link will keep that in my favorites in can i need it for when i get the linux up and running;)

---

### Post by az on 2006-09-09
If you are not using a router, and your broadband ISP uses pppoe, you have to use the command line.

More than half of the broadband users here in Québec connect that way.  I think it is much less in the rest of the world...  Which is why it is not easier in Linux/Ubuntu.

---

### Post by theoneandonlywheeler on 2007-01-28
Ussually a case of plug n' play but some wireless cards can be as easy

---

### Post by Enverex on 2007-01-28
Wireless is always harder than wired because wired "just works". At most you need to specify an IP address, route for NAT internet. Wireless requires you to scan for a network, connect, figure out any authentication (WEP, WPA, AES, TKIP, etc) and connect with that and that's assuming you can even find a driver for your wireless network card in the first place.

---

