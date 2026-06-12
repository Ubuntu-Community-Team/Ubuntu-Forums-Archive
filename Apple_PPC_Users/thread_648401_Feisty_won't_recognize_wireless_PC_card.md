---
title: "Feisty won't recognize wireless PC card"
date: 2007-12-23
forum: Apple PPC Users
---

### Post by ubuntubrian on 2007-12-23
I refurbished my wife's Lombard G3 which does not have wireless but has the PC card slot. I have Macwireless PC Card, 32mV, 11b and it works great with Debian Etch installed but doesn't show up at all in my networks. I have checked the forums and while there are some similar posts I can't figure this out. I ran:

$ lsmod | grep orinoco
orinoco_cs             18180  0
orinoco                44340  1 orinoco_cs
hermes                  8224  2 orinoco_cs,orinoco
pcmcia                 43472  2 orinoco_cs,hostap_cs
pcmcia_core            47128  5 orinoco_cs,hostap_cs,pcmcia,yenta_socket,rsrc_no nstatic
$ lsmod | grep hostap
hostap_cs              80468  3
hostap                123460  1 hostap_cs
ieee80211_crypt         6816  1 hostap
pcmcia                 43472  2 orinoco_cs,hostap_cs
pcmcia_core            47128  5 orinoco_cs,hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic

so I think I know that the Macwireless PC Card is an Orinoco card. Any ideas on how I can get Feisty to recognize it?
Feisty Live Cd boots up fine on the old G3 and I would love to install it but without the PC Card being recognized it's no good.
BTW, all of the pcmciautils, udev, and other packages are installed on the live CD so there's no hope there. The pcmciautils should be recognizing the card.

Thanks!

---

