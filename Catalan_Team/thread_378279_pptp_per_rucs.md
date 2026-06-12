---
title: "pptp per rucs"
date: 2007-03-07
forum: Catalan Team
---

### Post by CarlesOriol on 2007-03-07
Algú sap on trobar informació de la configuració del pptp per rucs ( 4 dummies).

Tota la que veig parla del pptpconfig que per fer-lo rutllar en edgy fas primer la connexió, després peta i et fas a maneta les rutes.

---

### Post by CarlesOriol on 2007-03-12
...aquesta me la responc jo per a qui pugui interessar...

vpn
 Les connexions configurades amb el pptpconfig poden activar-se i desactivar-se amb:
 
 
pon nomvpn
     ...
poff nomvpn


 Després es poden afegir les rutes manualment tipus: (xarxa tipus 192.168.8.X)
 
 route add 192.168.8.131  dev ppp0 
      o tota una xarxa
route add -net 192.168.8.0/24 dev ppp0

---

