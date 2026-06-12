---
title: "Sense Conexió 10.04"
date: 2011-03-03
forum: Catalan Team
---

### Post by prostata on 2011-03-03
Companys: he hagut de canviar el PC sobre taula per un de nou, el vell em va abandonar...RIP, i ara em passa el següent amb la distro Ubuntu 10.04

He fet una partició per al finestres, i altre per ubuntu 10.04.
al finestres si que hi tinc connexió a Internet, però amb Ubuntu no, surt l'icone pero diu"sense connexió a la xarxa"... haig de dir que ara treballo amb 64 bits, per si serveix de res i que vaig amb ONO amb el router modem-TCW 710

?podeu ferme un cop de mà...??, gràcies

Salut

---

### Post by wgarcia on 2011-03-05
Pots provar de donar aquesta instrucció des d'una terminal 

sudo dhclient

i si enganxes el que es veu es podrà veure què és el que està veient la teva targeta de xarxa.

---

### Post by prostata on 2011-03-09
Gràcies per la teva atenció. Tinc dues respostes,una polìticamente correcte, l'altre no tant. Però com que m'estimo millor no ferir susceptibilitats,diré que ja ho tinc arreglat. Gràcies per la teva resposta.

Salut

---

### Post by prostata on 2011-03-12
> **wgarcia said:**
> Pots provar de donar aquesta instrucció des d'una terminal 

sudo dhclient

i si enganxes el que es veu es podrà veure què és el que està veient la teva targeta de xarxa.


Doncs mira les respostes que em dona segons la versió ubuntu que instal-li:
Ubuntu Koala:

Internet System Consortium DHCA Client v3.1.3
Copyright reserved.
For more info visit.......
No boradcast interface found -exiting

Aquesta resposta em diu que falta quelcom per poder reconèixer la xarxa, que visiti xxx i ..

Ara la versió amb Ubuntu Maverick, em dona això:

josep@josep-casa:~$ sudo dhclient
[sudo] password for josep: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/1c:6f:65:7b:8e:c9
Sending on   LPF/eth0/1c:6f:65:7b:8e:c9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.13 from 192.168.0.1
DHCPREQUEST of 192.168.0.13 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.13 from 192.168.0.1
bound to 192.168.0.13 -- renewal in 293400 seconds.
josep@josep-casa:~$ 

Aquí tot sembla correcte i detectat perfectament. Ara, es clar, em pregunto, ¿com és que una instal-lació neta d'una versió ubuntu no reconeix la xarxa i altra si...?? es que m'agradaria saber-lo per aprendre...i en el primer cas com ho podria sol-lucionar...??

Gràcies

---

