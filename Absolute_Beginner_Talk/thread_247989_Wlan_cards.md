---
title: "Wlan cards"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by dude11245 on 2006-08-31
I'm having problems with finding my wlan device drivers. I'm using a Dell insperon 600m, can/may you tell my the name/location of my wlan device driver?

Thanks in advance
-Dude

P.S. If you want to send it to my e-mail it's, [email]demosthenes59@yahoo.com[/email]

---

### Post by Architeuthis on 2006-08-31
If you use the command "iwconfig" in a terminal you see if your card is detected. Then you can use ifup "name of card", something like rausb0, to activitate that connection. But with ifup you only use that connection for one session. After using ifup you can make that connection start up at start up by adding it to a list, cant remeber its location.

---

### Post by dude11245 on 2006-08-31
Thanks

---

### Post by dude11245 on 2006-08-31
I did the iwcnfg and it told me that I don't have a card, but the main problem is that I don't know where my card is located, if I did know i could fix it.

---

### Post by Papa-san on 2006-08-31
Can't do the walk-through just yet, but the links in my signature helped me out. Try the 'wireless help' one, and it should walk ya through the whole process in a way a n00b (me)could understand!

When the developers put 6.06 together, they built in the drivers for the bcom cards, but they don't work for all of us... We still get to do them the hard way...

EDIT: try to run:
```
 sudo lshw -C network
```

---

### Post by Architeuthis on 2006-08-31
oh yes i forgot this: [http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz), if your card isnt in this list, it wont work under linux. Not (yet) compatible with the kernel.

---

### Post by dude11245 on 2006-08-31
You see I don't know what my card is called, you probably can't help me with this but dell stoped selling this computer so I can't get any information on it.

---

### Post by dude11245 on 2006-08-31
I've found a way to use windows device drivers but I need to know where my card is and what it's called.

---

### Post by dude11245 on 2006-08-31
It comes up with a reply that looks like this,   *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:d2:98:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=full ip=192.168.0.5 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faffe000-faffffff irq:11
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:5c:54:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-26-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:faffc000-faffdfff irq:5

---

### Post by Architeuthis on 2006-08-31
you should check the wiki on ubuntu.com there is a lot info about that. I read about a command how you could check the name of your card, but i cant find it back.

---

### Post by Architeuthis on 2006-08-31
BCM4401-B0 100Base-TX, that must be the name of your card?

---

### Post by dude11245 on 2006-08-31
Thank you guys/girls (I don't know.)

---

### Post by dude11245 on 2006-08-31
No the name of my card is, BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

---

### Post by dude11245 on 2006-08-31
...I think...

---

### Post by Architeuthis on 2006-08-31
why BCM4318 if the shell says BCM4401-B0?

---

### Post by dude11245 on 2006-08-31
I think that the one you're talking about is my ethernet card.

---

### Post by Architeuthis on 2006-08-31
Ok now you know what name it has, i reccomend you search the wiki on ubuntu.com, for more information. But for the exact location (you mean like /dev/location?) you will need the help of an more advanced user.

---

### Post by dude11245 on 2006-08-31
I'll try that thanks.

---

### Post by dude11245 on 2006-08-31
I have another question, how do I "plug in" a built in card?

---

### Post by compwiz18 on 2006-09-01
Hi...

If you run **lspci | grep Broadcom\ Corporation** and the output has bcm4318 in it, try [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Good luck

---

