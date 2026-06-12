---
title: "Copiar particions"
date: 2007-04-03
forum: Catalan Team
---

### Post by ernestux on 2007-04-03
Hola a tothom,

Tinc el linux escampat en 4 particions del portàtil:  /  , /usr , /home  i  swap-linux.  El problema és que la partició /usr  de 3,4 GB  ja està al 95% i la vull ampliar, però és la primera partició lògica (sda5) i el gparted no em deixa ..  Aleshores voldria copiar aquesta en la darrera partició sda8 que està lliure i té 4,5 GB , però necessito que algú em digui com puc fer-ho.  O potser seria millor fussionar home i usr ?

---

### Post by CarlesOriol on 2007-04-03
sudo cp /dev/sda5 /dev/sda8

Pot ser cal que ho facis iniciant des de l'instal·lador per tal que no estigui obert res.

---

### Post by basdala on 2007-04-03
L'únic que se m'acudeix és que cerquis el Hiren's Boot CD (diuen que hi ha una mula molt simpàtica que du tot tipus de programes, li podries demanar a veure si el té) que inclou el Partition Magic (*standalone*, sense Windows) i et permetrà destrossar tranquilament el teu disc dur.

De tota manera, jo faria un backup ben maco abans de res...

---

### Post by ernestux on 2007-04-10
Hola a tots,

He tingut èxit, per si a algú es troba amb el mateix dilema.  He fet córrer el gparted des del live cd i he marcat copiar sda5  a sda8, m'ha indicat que es crearà "copy of sda5". M'he arriscat i he dit que continués i al final he vist que sí, que ha copiat la sda5 a la partició sda8.  He esborrat la sda5 i he vist que m'ha conservat la /usr però a la sda8.

---

### Post by CarlesOriol on 2007-04-11
que no anava el que et vaig dir?

---

### Post by ernestux on 2007-04-11
Ei !

Ho vaig provar primer directament des de l'ubuntu, i és clar, no anava. I crec que des de la live tampoc, però no t'ho asseguro; potser no em donava permís....  Gràcies, però.

---

### Post by CarlesOriol on 2007-04-11
T'hauria d'haver anat en qualsevol dels dos casos que expliques. De fet jo he copiat tot el sistema engegant d'una live i fent sudo cp /dev/sda /dev/sdb totes les particions i particions simples indicant el nombre.

És possible que la sda8 tinguessis una partició muntada abans de fer la copia que impedis de fer-ho. Podies haver-ho lliurat fent un sudo umount /dev/sda8 i després la copia.

---

