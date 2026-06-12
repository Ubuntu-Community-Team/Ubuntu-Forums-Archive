---
title: "Problemes amb l'Amarok 2"
date: 2009-08-30
forum: Catalan Team
---

### Post by ferry11 on 2009-08-30
Hola, m'he instalat la versió de l'Ubuntu 9.04 (crec que es aixi), i em va perfecte, però l'únic problema el tink amb l'Amarok. Com a conseqüencia de l'actualització de l'Ubuntu veig que el reproductor també s'ha actualitzat (la versió vella m'anava prfecte) i el que em passa es que només d'iniciar-lo ja em diu: "el dispositiu de reproducció d'àudio HDA VIA VT82xx (AD198x Analog) no funciona. Es recorre al default". Un cop em diu això l'inici-ho i quan reprodueixo les cançons em fica a sota que s'estan reproduint, però no fa res, es a dir ni se sent res, ni a la barra del play i el pause apareix res... (tot i això, hi ha agut un cop que una canço si que s'ha sentit bé, però quan le volgut tornar a reproduir ja no funcionava...)


En fi, espero la vostra ajuda...



Gracies :)

---

### Post by PatrickVogeli on 2009-08-30
em sembla que has d'instal·lar el paquet phonon-backend-gstreamer o phonon-backend-xine

Salut

---

### Post by papapep on 2009-08-30
També pots continuar amb la versió antiga instal·lada, fent:

```
sudo aptitude install amarok14
```

---

### Post by ferry11 on 2009-08-30
Moltes gracies!! Ara ja em va bé. Estic molt agraït jeje



Salut!!:P

---

### Post by SiscoGarcia on 2009-08-30
> **ferry11 said:**
> Moltes gracies!! Ara ja em va bé. Estic molt agraït jeje

Me n'alegro, però podries dir quina de les dues solucions t'ha funcionat, de manera que pugui aprofitar-se'n qui vingui al darrere, no?

---

### Post by ferry11 on 2009-09-12
Si tens tota la raó jeje!

Al final he instal·lat el paquet phonon-backend-xine i em va de cine.:D

---

### Post by papapep on 2009-09-12
> Me n'alegro, però podries dir quina de les dues solucions t'ha funcionat, de manera que pugui aprofitar-se'n qui vingui al darrere, no?

És que les dues funcionen, Sisco. Només és que amb la del phonon et funciona la 2, amb tot el que no va, i amb l'altra tens la 1.4 amb el seu aspecte antic funcionant, amb tots els afegits rutllant. Per gustos, els colors.

---

