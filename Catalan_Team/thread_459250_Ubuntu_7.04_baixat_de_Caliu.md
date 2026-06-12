---
title: "Ubuntu 7.04 baixat de Caliu"
date: 2007-05-30
forum: Catalan Team
---

### Post by jaume primer on 2007-05-30
Algú ha provat de baixar-se aquesta versió traduïda al català de la web de Caliu? És que jo ho fet varies vegades, tant la baixada, com la gravació de la imatge, però en engegar l'ordinador amb el CD a la unitat lectora no hi ha manera que carregui el Linux. També és curiós que no hi ha l'arxiu md5 per verificar la integritat de la imatge iso traginada. A veure si algú en sap alguna cosa.
Gràcies a tots.

---

### Post by orestesmas on 2007-05-30
Bé, cal dir que aquest CD el vaig generar jo, i a mi m'ha arrencat bé arreu on l'he instal·lat. Potser em vaig deixar de pujar l'MD5. Per si de cas, aquí te l'envio adjunt.

Salutacions,

Orestes.

---

### Post by pisuke on 2007-05-31
Per verificar-la

$openssl md5 nom_de_la_.iso

---

### Post by orestesmas on 2007-05-31
oh, jo sempre faig

md5sum nom_del_fitxer

més curtet :-)

---

### Post by AlexMuntada on 2007-05-31
Quan tingueu un arxiu amb els MD5 d'un o més arxius i vulgueu comprovar-los fàcilment:
```
md5sum -c livecd.iso.md5.txt
```

---

