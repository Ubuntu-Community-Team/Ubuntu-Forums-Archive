---
title: "help installing  network card"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2007-03-13
help installing broadcom corporation BCM4306 802.11b/g wireless LAN network drivers...canot get to internet so please help, i can transfer programs from my other comps, thx

p3wn3r n00b signing out, lol

---

### Post by c0d4041292 on 2007-03-13
ello?

---

### Post by Najand on 2007-03-13
check this out: [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=BCM4306")
hope it works.

---

### Post by DaveyG on 2007-03-13
Wich version of Ubuntu are you using?

---

### Post by c0d4041292 on 2007-03-13
6.10 i think
the latest stable version

---

### Post by DaveyG on 2007-03-13
Did any software come with it? like the cd?... is the card displayed in the network tools?

---

### Post by c0d4041292 on 2007-03-13
no cd, and it is not displayed in tha internet tools

---

### Post by c0d4041292 on 2007-03-13
help me please

---

### Post by silhouette on 2007-03-13
Did you try the link that was given you?

What is the output of "lspci -n" (this gives us the device ID in case we need it)?

[More info about Broadcom 43xx cards](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html#Broadcom)
[Home page for bcm43xx chipset driver](http://bcm43xx.berlios.de/)
[A list of known devices that carry the chipset](http://bcm43xx.berlios.de/?go=devices)

Did you know also that there was an [article in the Wiki](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) about the bcm43xx driver?

---

