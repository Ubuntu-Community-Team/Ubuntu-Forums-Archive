---
title: "PowerBook g3 wallstreet wireless card"
date: 2007-05-12
forum: Apple PPC Users
---

### Post by Bob Bobbio on 2007-05-12
I have a powerbook g3 wallstreet with linux Hoary Hedgehog on it with bootX and I want to buy a pci wirless card for.  Does anybody know what wireless card to buy and how to get it to work? Thanks a bunch.

---

### Post by gvigorus on 2007-07-29
Tried getting Lucent WaveLAN Silver Turbo 11Mb to work under Feisty Fawn on Lombard. PCIMCIA didn't work, so i went for the Ralink based Asus USB wifi dongle. Selling my WaveLAN PCard. Hope the Ralink one will work, because it's finally Open source!

---

### Post by walter_f on 2007-07-29
> **gvigorus said:**
> Hi. I've used Orinoco Silver (B speed 11Mbs) sucessfully on G3 Lombard Powerbook. I think it's got broadcom chip.

The Orinoco cards (be it the silver or gold variety) have a chipset by Lucent, called "orinoco".

As this is the same chipset as the one used in the original Apple Airport (11 Mb/s 802.11b) wireless card, the Orinoco cards have been very popular among Powerbook owners running Mac OS 8 or OS 9. An Orinoco card would be recognized as an Apple Airport 802.11b card by Mac OS Classic.

The next generation of Apple Airport cards, called "Airport extreme" and being 54 Mb/s 802.11g, has a Broadcom chip inside. Unfortunately, Broadcom is not known to be cooperative with the open source community.

As a user of Ubuntu, one might go for a solution using a chipset by Ralink, a very open-source friendly manufacturer. 

Here are the driver downloads for Linux, right on Ralink's web page:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Assuming that the Wallstreet has card bus (i.e., 32 bit) slots, the WL-107G by Asus, using Ralink's RT-2500 chipset, would be a nice wireless card.

For more recent PowerBooks that have USB (Lombard, Pismo, Titanium G4), the Asus WL-167G wireless stick (based on the same chip set) would be a possible option. For iBooks that don't have PC Card slots at all, an USB stick would be the only way to go. As far as I know, there is no USB 2.0, just USB 1.1 on most PowerBooks and iBooks, though.

Regards,

Walter.

---

### Post by Bob Bobbio on 2007-08-01
Oh. Thank you for your reply guys, I really appreciate it.  I will definately go with one of those Ralink pci cards.  (It has 2 pci card slots and no USB)  Thank you so much for your advice I would have had no idea what to do, thanks.

---

### Post by jruschme on 2007-08-01
The Ralink-based cards are nice in that they offer 802.11g and have MacOS drivers, as well.

FWIW, I also like the old Cisco Aironet 340 and 350 cards. They are only 16-bit PCMCIA and 802.11b, but also have drivers for both the classic MacOS and MacOS X.

---

