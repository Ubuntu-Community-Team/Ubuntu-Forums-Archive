---
title: "Instal·lar debian lenny amb ubuntu 9.04"
date: 2009-06-17
forum: Catalan Team
---

### Post by Diegstroyer on 2009-06-17
Salutacions a tots!

Últimament he estat provant debian lenny i m'ha agradat molt la seva estabilitat (a més de poder utilitzar bé al càmera web que no funciona en Jaunty degut a un bug del kernel gspca).

La meva pregunta és senzilla, puc intal·lar debian en una partició del disc sense perill de perdre les de Ubuntu? Ja que tinc la 9.04 amb sistema ext4 a l'arrel.

El home el tinc en ext3 en una partició diferent, el puc posar també com a home per al debian encara que els versions dels programes no siguin les mateixes?

Salutacions :popcorn:

---

### Post by oriolsbd on 2009-06-17
Sí que pots instal·lar Debian sense perill de perdre Ubuntu (sempre i quan creïs bé les particions, clar).

El "home", suposo que sí que el pots utilitzar a les dues, però jo no t'ho recomanaria, sobretot pel tema que comentes de les diferents versions dels programes.

Salut!

---

### Post by Diegstroyer on 2009-06-17
mmmm... gracies per la resposta, el que em fa més por es perdre el grub, ja que amb Jaunty i el sistema de fitxers ext4 canviava alguna que altra cosa en la forma d'arrencar...

Ho provaré d'aquí unes hores i ja us comentaré com ha anat, mentrestant esperaré a veure si apareixen més comentaris al respecte.

Salutacions.

---

### Post by oriolsbd on 2009-06-18
Si no vols perdre el Grub de Jaunty, suposo que des de la instal·lació de Debian li pots dir que no l'instal·li (a la instal·lació d'Ubuntu segur que se li pot dir). Però això vol dir que llavors hauràs d'entrar manualment les entrades per arrancar en Debian en en fitxer "/boot/grub/menu.lst" de Jaunty.

Salut!

---

### Post by Diegstroyer on 2009-06-18
jejejejeje... ja ho he vist... massa tard! Quin cacao, ara ja està tot bé, el GRUB de Debian no m'ha acabat de rutllar bé (em sembla que te a veure amb el sistema de fitxers ext4, que no el reconeix).

Ara ja tinc els dos SO al GRUB sense problemes.

Salutacions i gracies.:popcorn:

---

