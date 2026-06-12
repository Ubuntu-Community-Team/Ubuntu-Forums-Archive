---
title: "ajuda per crear una Xarxa estandard"
date: 2007-03-13
forum: Catalan Team
---

### Post by ilku on 2007-03-13
Voldria crear una xarxa estandard.
Això vol dir un servidor que mitjançant una targeta de xarxa (eth1) ex connecti a Internet amb ip fixe XXX.XXX.XXX.XXX amb uns dns del isp.
I una targeta de xarxa (eth0) connectada a un switch que dona servei als clients de DHCP I DNS. El meu problema bé donat en la configuració correcte del dhcp-server i el Bind9 de forma correcte.
He aconseguit rebre ip i dns en els clients però les zones (buscar ip locals i reverse ip) no hi ha manera que funcionin al igual que la cache (a la mateixa maquina).

Potser es un pregunta molt evident, però no me'n surto. Si algú em pot donar un cop de mà.

---

### Post by ilku on 2007-03-13
Potser la solució mes rapida seria el dnsmasq.

Que en penseu?

---

