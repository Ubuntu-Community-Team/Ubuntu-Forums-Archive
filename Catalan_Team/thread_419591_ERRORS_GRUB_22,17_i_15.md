---
title: "ERRORS GRUB 22,17 i 15"
date: 2007-04-23
forum: Catalan Team
---

### Post by manelolesa on 2007-04-23
Bones.

Divendres vaig instal.lar la Feisty  en una partició que tenia lliure i OK l'ordinador engega correctament. ( Aquest Disc Dur també te Finestres 2003 Server )

Faig un traspas de fitxers personals de la partició on tenia el Edgy i veïent que ja no el necessitaria carrego la partició. Trono a engegar l'ordinador i** GRUB ERROR 22**. 

Seguint un post instal.lo el Grub desde el CD de Ubuntu 5.10 engego i ** GRUB ERROR 17**.

Decideixó instal.lar el Feisty en la partició buida on tenia el Edgy, engego i ** GRUB ERROR 15**.

Resumint, estic desesperat es evident que la vaig cagar eliminant la partició del Edgy. 

Salut i gracies

Manel

---

### Post by basdala on 2007-04-23
L'error bàsic que has comés ha sigut eliminar la partició que tenia la informació necessaria per a que el GRUB arranqui.

La sol·lució més senzilla és unir les dues particions -la de l'edgy i el feisty- en una sola -fes servir un Hiren's Boot CD o un Ubuntu Live- i reinstalar tot el Feisty de nou. Si tens sort, això restaurarà el GRUB. Si no tens sort, fes un backup del disc sencer i reinstala tot (eliminant prèviament tota la taula de particions).

Per cert, pensa a deixar 512-1024 MB pel swap quan uneixis les particions (o no toquis la partició swap que ja tens, bàsicament).

A tot això, ¿saps que la teva sol·lució era tan senzilla com actualitzar l'edgy al feisty amb el propi gestor d'actualitzacions?...

---

### Post by manelolesa on 2007-04-24
Arreglat.
Engegant amb Ubuntu LIVE copìan documents de la partició bona cap un USB, esborrant totes les particions i instal.lant Feisty de nou.
Tot ok.

PREGUNTA: Els posts es poden tancar d'alguna manera ? o es pot posar al titul del post que ja está solucionat.

Salut

Manel

---

### Post by manelolesa on 2007-04-24
Arreglat.
Engegant amb Ubuntu LIVE copìan documents de la partició bona cap un USB, esborrant totes les particions i instal.lant Feisty de nou.
Tot ok.

PREGUNTA: Els posts es poden tancar d'alguna manera ? o es pot posar al titul del post que ja está solucionat.

Salut

Manel

---

### Post by CarlesOriol on 2007-04-24
El fòrums son llocs de debat i una sol·lució no implica un tancament definitiu de cap missatge. Pot ser que d'aquí un temps algú torni a veure aquest missatge i ofereixi una nova sol·lució per qui ho vegi després.

Si mai tens una incidéncia que requereix una solució i prou pots anar al launchpad.net on la relació problema -> solució és molt més prioritaria.

---

### Post by manelolesa on 2007-04-25
Perdoneu, es que encara porto la "L" dels Fòrums.

Salut

Manel

---

### Post by CarlesOriol on 2007-04-25
No pateixis, d'aquí dos dies ja estarás com tots ajudant a d'altres que pateixen dels mateixos problemes que ja has passat. I et entiras bé fent-ho.

---

