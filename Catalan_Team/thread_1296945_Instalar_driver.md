---
title: "Instalar driver"
date: 2009-10-21
forum: Catalan Team
---

### Post by tukapamaru on 2009-10-21
Hola a tothom,

Us explico breument el meu cas: sóc nou a ubuntu, acabo d'instal·lar la versió 9.04 d'Ubuntu, que vull utilitzar com a eina de treball habitual. Tot em funciona bé, excepte un receptor perifèric de wireless. A la pàgina web del fabricant (edimax) hi he trobat un driver de codi obert. El problema és que no sé com instalar-lo. Suposo que no és gens complicat, però em falten coneixements. També hi ha un readme, però la veritat és que no l'entenc. He buscat a l'ajuda i a d'altres forums, però no me'n surto. Algú em podria explicar clarament com instalar-lo?

Salut!

---

### Post by Comuner on 2009-10-21
hola tupakamaru- Benvingut! Jo també fa poc q m'he instal·lat ubuntu i fins ara era usuari windows i com tu vaig perdut. Has probat a obrir el terminal i fer un un update i despres un upgrade? Quan vaig instal·lar ho vaig fer i em va reconeixer tot el maquinari sense problema.
 Sort.

---

### Post by papapep on 2009-10-21
Benvingut, tukapamaru.

Caldria saber exactament quin dispositiu és.

Hauries de fer a un terminal, si és USB:

```
lsusb -v
```

si és PCI:

```
lspci -v
```

i com que, suposo, que el que sortirà és molt llarg, ho enganxes a 
[http://pastebin.ubuntu.com](http://pastebin.ubuntu.com) i ens enganxes aquí la adreça que et dongui per a poder-ho mirar.

Quan tinguis una estona, no estaria de més que fessis un cop d'ull a l'enllaç (el de les normes d'or) que hi ha a la meva signatura ;)

---

### Post by tukapamaru on 2009-10-23
Hola,

Al final ha estat molt més fàcil del que em creia. Al final l'ubuntu ha reconegut automàticament l'aparell. Ja està solucionat i va de meravella. Gràcies i disculpeu les molèsties!

---

