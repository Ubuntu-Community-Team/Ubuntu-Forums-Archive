---
title: "Impossible extreure fitxers amb accents amb el Gestor de fitxers (File Roller)"
date: 2011-08-31
forum: Catalan Team
---

### Post by Aljullu on 2011-08-31
Hola, utilitzo l'Ubuntu 11.04 i des de fa bastant de temps tinc un problema. Quan intento extreure un fitxer .zip que conté una carpeta o fitxers amb accents (o qualsevol altre caràcter especial) em dóna el següent error:

> S'ha produït un error en extreure els fitxers:

caution: filename not matched:  Coratge/05 Perdut als carrers del mo\?\?n.m4a

He estat buscant per Internet i no he trobat cap solució. Sabeu com ho puc resoldre? Moltes gràcies!

---

### Post by kimet on 2011-08-31
Els caràcters especials i els espais, en els noms dels fitxers, solen ser problemàtics.
Si el .zip va ser fet amb un sistema windows, podries provar amb un descompresor de windows amb wine, 7zip o winzip o com es digui.

---

### Post by wgarcia on 2011-08-31
Se m'acut dues possibles solucions:

1) Obre una terminal, i utilitza l'utilitat de consola "unzip" per descomprimir el fitxer (unzip nom_del_fitxer)

2) Instal·la el paquet p7zip-full, em sembla que mostra els caràcters de forma diferent a l'habitual i et permet extraure aquests fitxers amb caràcters especials.

---

### Post by Aljullu on 2011-08-31
La primera manera ja m'ha funcionat. Moltes gràcies!

N'hauríem de reportar un bug?

---

### Post by wgarcia on 2011-09-01
És un problema d'usabilitat, així que em sembla justificat obrir un bug, ja el tancaran si no toca.

---

### Post by Aljullu on 2011-09-05
He vist que ja hi havia un bug creat:
[[https://bugs.launchpad.net/ubuntu/+source/unzip/+bug/580961](https://bugs.launchpad.net/ubuntu/+source/unzip/+bug/580961)]("https://bugs.launchpad.net/ubuntu/+source/unzip/+bug/580961")

I sembla ser que es va sol·lucionar el maig. Podria ser que per a la propera versió de l'Ubuntu ja funcionés bé?:P

---

### Post by wgarcia on 2011-09-06
Si està solucionat segurament sí. També és possible que si habilites els dipòsits "backport", si han actualitzat la versió en aquests dipòsits ja puguis tenir la versió corregida.

---

