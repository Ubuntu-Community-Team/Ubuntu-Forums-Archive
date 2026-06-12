---
title: "Programa per controlar xarxes"
date: 2009-11-27
forum: Catalan Team
---

### Post by jdk9 on 2009-11-27
Bones!

M'agradaria saber si algú sap algun programa amb el qual pugui, estant tots els ordinadors connectats al mateix router, "desconectar" ordinadors, controlar l'ample de banda que gasta cadascun i que permeti configurar la connexió de programes P2P.

Gràcies!

---

### Post by papapep on 2009-11-27
El primer que caldria que tinguessis clar és que el que comentes no és especialment trivial :)
Primer cal que el dispositiu que fa aquesta tasca (normalment un ordinador) sigui la [pasarela de sortida]("http://es.wikipedia.org/wiki/Gateway_(informática)") dels ordinadors del tram de xarxa que vols controlar. Després cal tenir un tallafocs, en GNU/Linux són [IGU]("http://ca.wikipedia.org/wiki/IGU") de l'[iptables]("http://ca.wikipedia.org/wiki/Iptables") (o el mateix iptables a pèl), que gestioni l'accés de i a les màquines i als [ports]("http://es.wikipedia.org/wiki/Puerto_de_red") que tu vulguis, i pel tema del control de l'[ample de banda]("http://es.wikipedia.org/wiki/Ancho_de_banda_%28inform%C3%A1tica%29"), [protocols]("http://es.wikipedia.org/wiki/Protocolo_de_comunicaciones") i, fins i tot, programes, pots fer servir l'[squid]("http://es.wikipedia.org/wiki/Squid"). Però en cap cas serà especialment simple.
Hi ha distribucions especialitzades en temes semblants com [ipcop]("http://sourceforge.net/projects/ipcop/").
Per cert, t'havia comentat que no és un tema banal? :D

---

### Post by jdk9 on 2009-11-27
No sembla senzill, però es pot provar almenys de fer algun "apanyo" 
Gracies papapep!

---

