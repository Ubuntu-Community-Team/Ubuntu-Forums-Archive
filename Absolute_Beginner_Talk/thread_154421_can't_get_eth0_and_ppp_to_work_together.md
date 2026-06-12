---
title: "can't get eth0 and ppp to work together"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Bubba Ho-Tep on 2006-04-03
Can't figure this one out - 

I can't get my Breezy box to use the modem (ppp) and its ethernet card (eth0) at the same time.

The modem dials out ok authenticates blah blah but web browsing and pings time out. If I disable the eth0 connection, then disconnect and reconnect the modem it works fine.

I notice in the Network Tools gui thingo that eth0 is my default gateway device but there is no option to change it.

The ppp is used to dial out to the net while the eth0 connects to other Breezy boxen

Anyone any ideas?

BH-T

---

### Post by dcstar on 2006-04-03
[QUOTE=Bubba Ho-Tep]Can't figure this one out - 

I can't get my Breezy box to use the modem (ppp) and its ethernet card (eth0) at the same time.

The modem dials out ok authenticates blah blah but web browsing and pings time out. If I disable the eth0 connection, then disconnect and reconnect the modem it works fine.

I notice in the Network Tools gui thingo that eth0 is my default gateway device but there is no option to change it.

The ppp is used to dial out to the net while the eth0 connects to other Breezy boxen

Anyone any ideas?

BH-T[/QUOTE]
It is a routing issue, and the ppp script should change the default gateway when it connects.

Do a forum search for ppp connections and there may be a solution somewhere.

---

