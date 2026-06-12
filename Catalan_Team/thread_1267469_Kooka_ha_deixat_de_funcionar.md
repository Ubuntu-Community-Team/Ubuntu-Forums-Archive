---
title: "Kooka ha deixat de funcionar"
date: 2009-09-15
forum: Catalan Team
---

### Post by jinglada on 2009-09-15
Durant el mes de juliol passat vaig estar utilitzant Kooka per escanejar un llibre i altres fulls i ara quan el poso en marxa em diu: 

Problema: no s'ha trobat cap escàner.(1) El vostre sistema no disposa d'una instal·lació del SANE (Scanner Acces Now Easy), necessària per permetre l'ús de l'escàner al KDE. Instal·leu i configureu correctament el SANE al vostre sistema.

El SANE està instal·lat en la versió 1.0.14-7

joan@joan-laptop:~$ whereis sane
sane: /etc/sane.d /usr/lib/sane /usr/lib64/sane /usr/share/sane /usr/share/man/man7/sane.7.gz

Reinstal·lo el SANE?

Salutacions, Joan Inglada
PS: (1) tinc l'escàner connectat.

---

### Post by pauelmaco on 2009-09-16
Comprova que no hi hagi hagut una actualització del nucli recent, no sigui que els drivers de l'escaner ja no et serveixin en aquest nucli. Per altra banda, pots instentar de compilar un altre cop els drivers, a veure si tiren.

---

### Post by jinglada on 2009-09-16
> **pauelmaco said:**
> Comprova que no hi hagi hagut una actualització del nucli recent, no sigui que els drivers de l'escaner ja no et serveixin en aquest nucli. Per altra banda, pots instentar de compilar un altre cop els drivers, a veure si tiren.

Gràcies per la resposta. El problema és que no sóc gens expert en linux. Si et refereixes al nucli del kooka, pel que he vist en diferents llocs, sembla ser que ja no el mantenen. Per altra banda, no tinc ni idea de com es fa això de compilar els drivers de l'escànner. Em pots ajudar a fer-ho? No deu ser pas reinstal·lar SANE per mitjà del synaptic?
Gràcies.

---

### Post by orestesmas on 2009-09-18
> **jinglada said:**
> Durant el mes de juliol passat vaig estar utilitzant Kooka per escanejar un llibre i altres fulls i ara quan el poso en marxa em diu: 

Problema: no s'ha trobat cap escàner.(1) El vostre sistema no disposa d'una instal·lació del SANE (Scanner Acces Now Easy), necessària per permetre l'ús de l'escàner al KDE. Instal·leu i configureu correctament el SANE al vostre sistema.


El Kooka és una aplicació basada en KDE3 (i les seves llibreries) i, encara que teòricament pot funcionar dins el KDE4, els d'ubuntu deuen haver fet alguna cosa estranya perquè a mi tampoc no em funciona d'un temps ençà.

Com que no escanejo gaire no li he donat més importància. Caldrà esperar que algú s'animi a portar-lo a KDE4. 

Potser la solució al problema no és massa complicada, però no he pogut dedicar temps a investigar-ho. Mentrestant jo estic usant l'Xsane directament. Et recomano que facis el mateix.

---

### Post by pauelmaco on 2009-09-19
> **jinglada said:**
> Gràcies per la resposta. El problema és que no sóc gens expert en linux. Si et refereixes al nucli del kooka, pel que he vist en diferents llocs, sembla ser que ja no el mantenen. Per altra banda, no tinc ni idea de com es fa això de compilar els drivers de l'escànner. Em pots ajudar a fer-ho? No deu ser pas reinstal·lar SANE per mitjà del synaptic?
Gràcies.

Quant deia una actualització de nucli, hem referia al nucli de linux. Hi ha vegades, quan instales un driver per a un dispositiu, s'ha de tornar a compilar quan hi ha una actualització del nucli linux (també anomenat "kernel") perquè la instalació feta només afectava al nucli antic. Però pel que dius, entenc que no vas instalar cap driver, que ja funcionava sol.

Crec que hauries de fer com diu en Orestesmas, utilitzar l'Xsane i esperar que la gent d'Ubuntu faci alguna cosa.


S'haurà de tenir paciència !!

Pau

---

### Post by jinglada on 2009-09-19
> **orestesmas said:**
> Mentrestant jo estic usant l'Xsane directament. Et recomano que facis el mateix.

Gràcies a tots dos, però, Orestesmas, fas servir l'Xsane per a OCR? Si és així, quin OCR li poses?

---

