---
title: "Powerbook G4 PCMCIA 802.11g"
date: 2008-02-25
forum: Apple PPC Users
---

### Post by Cows on 2008-02-25
I have a 2001 Titanium Powerbook G4 codename : Onxy.

I was wondering if 802.11g cards work in the PCMCIA slot of the Powerbook because I have a DWL-G650 Card.

DWL-G650 : D-Link
Chipset : Atheros
802.11g

Anyways I have that and it doesn't work. I tried it on Debian Etch 4.0 , Ubuntu and I currently have Yellow Dog Linux 5.0.1 and it still doesn't turn on. The CardBus slot is being detected in the "lspci" but my DWL card doesn't even boot up.

---

### Post by stmiller on 2008-02-25
I use a PCCard for wifi in my 867Mhz Tibook. (Edimax EW-7108PCg)
 Some wifi cards take a lot of power which older laptops cannot handle so well. But anyways, it should work...

---

### Post by stream303 on 2008-02-26
Heh, I was just looking into cardbus issues..

If you add the kernel parameter

pci=assign-busses

at the boot: prompt, does it work?  If so, we can add that to the append= line of /etc/yaboot.conf and do a sudo ybin -v to make it permanent.

---

### Post by Cows on 2008-03-04
I can't try it now since  I don't have Ubuntu installed on my Powerbook. I'm selling it on ebay.. here is the link :

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MESEX:IT&item=170198959274&_trksid=p3984.cSELL.m315.lVI](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MESEX:IT&item=170198959274&_trksid=p3984.cSELL.m315.lVI)

---

