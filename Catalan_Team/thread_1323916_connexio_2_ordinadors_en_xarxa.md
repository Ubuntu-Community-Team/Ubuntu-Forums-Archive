---
title: "connexio 2 ordinadors en xarxa"
date: 2009-11-12
forum: Catalan Team
---

### Post by botini on 2009-11-12
Hola a tots,
Tinc un dubte a l'hora de connectar 2 ordinadors en xarxa a través de l'ethernet. Tinc connexió Ono a un portàtil HP a través de l'USB i amb un cable de xarxa creuat vull que un altre ordinador tingui connexió. El meu dubte és quins paràmetres he de ficar quan edito la connexió eth0 en els 2 ordinadors. En concret a IPv4 fico manual, i quins valors he de ficar en els següents camps? Adreça, màscara, pasarel.la, DNS i Dominis de creca?

Gràcies!
Botini

---

### Post by akyra on 2009-11-12
Hola botini
Que tens connectat amb ONO? Un modem-router wifi, ho només un modem?
Jo ho tenia amb modem-router wifi que a la vegada també té un port ethernet, i li he donat a cada ordinador una adreça IP, de la xarxa 192.xxx.xxx.xxx. La mascara de xarxa la 255.255.255.0 i la porta d'enllaç  o pasarel·la l'adreça que té el router de ONO, normalment la 192.xxx.xxx.1.
El DNS he posat una altre vegada l'adreça del router 192.xxx.xxx.1, o també pots posar les que et doni per defecte ONO.
En els Dominis de cerca no he posat res.

El que sembla que vols és connectar-te amb el cable de xarxa creuat amb el port ethernet del portatil a l'altra ordinador, a les hores suposo que voldràs fer una xarxa tipus ad-hoc, i la pasarel·la hauria de ser la del ordinador portatil.


Salutacions

---

### Post by botini on 2009-11-12
Hola de nou, i gràcies per la resposta Akyra...
Doncs el que jo tinc és un modem, i per això a ell només li puc connectar un ordinador i fer-lo servir com a servidor de l'altre ordinador. A les meves connexions de xarxa de l'ordinador principal em diu que l' "auto et2" es connecta al modem i que l' "auto et0" està connectat a l'altre ordinador. Igualment a l'ordinador secundari m'apareix que "auto et0" està connectat, però en aquest segon  aparell no puc navegar... Si algú em dona un com de mà ho agraire molt. Quines adreces, passareles, etc he de posar al "et0" de cada aparell? Estic una mica peix.... 

Botini

---

