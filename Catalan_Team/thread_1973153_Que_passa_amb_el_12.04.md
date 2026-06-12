---
title: "Que passa amb el 12.04"
date: 2012-05-04
forum: Catalan Team
---

### Post by dmolner on 2012-05-04
Hola,
Us explico el que m'ha passat amb el Ubuntu 12.04

Vaig actualitzar dilluns de la 11.10, el resultat, no hi va haver manera de executar-lo, hem vaig quedar sense 11 i sense 12.
La única sol.lució va ser instal.lar de 0 el 12.04

Avui m'ha sortit una actualització que he vist que era d'idiomes per al Thunderbird.
He actualitzat i m'ha demanat re-iniciar, resultat, Ubuntu no arrenca.
Surt una pantalla amb diferents opcions (Versió 24, versió 24 recovery, altres Linux aqui surt la 23), qualsevol opció te el mateix resultat pantalla morada.
Ara hem funciona gràcies a que he posat el CD i així si que arrenca, no en Live.

Que haig de fer per deixar-lo que arrenqui sol? suposo que entrar en recovery i fer servir alguna de les opcions que dona que només surten si tinc el CD posat, no?

Gràcies,

---

### Post by wgarcia on 2012-05-04
Jo el que faria seria assegurar que està tot actualitzat, tot si és com dius que vas instal·lar fresc tot, i l'instal·lació va acabar bé, en principi hauria de ser així. 

Però si d'un cas entraria en mode recuperació, intentaria accedir a una consola de comandes (si estàs a la pantalla morada, intentaria Alt-F1 a veure si pots accedir una consola de comandes), i aquí donaria les següents instruccions:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo dpkg --configure -a

```

Això assegurarà que està tot al dia, i que no ha quedat alguna dependència sense instal·la o algun paquet mal configurat. 

Després intentaria:

```
sudo service lightdm restart
```

i a veure si això et dóna accés a la pantalla d'inici, o dóna algun error.

---

### Post by dmolner on 2012-05-04
Moltes gràcies wgarcia per la informació.

Per ara després d'arrancar varies vegades amb el CD ara ja arrenca sol (no cal CD).

Tot i això hem quedo amb les instruccions que m'has donat per si hem fan falta.

---

