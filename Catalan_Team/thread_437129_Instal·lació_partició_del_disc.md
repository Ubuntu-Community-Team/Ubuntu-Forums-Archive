---
title: "Instal·lació/ partició del disc"
date: 2007-05-08
forum: Catalan Team
---

### Post by ventma on 2007-05-08
He arrancat sense problemes ubuntu des del CD i he passat a instal·lar-lo, però m'he encallat en les particions del disc dur. M'explico: tinc dos discs durs, un de 40 GB on hi ha el Windows instal·lat i un altre de 160 GB partit en dos, una pertició de 100 GB i una altra de 60 GB. La meva intenció és instal·lar l'ubuntu en aquesta última i utilitzar-la sensera pel LINUX. Algú podria dir-me com fer-ho? Tinc por que hem fagi particions rares i perdi dades (a la partició de 100 GB hi tinc tots els arxius de dades). Quin format he de dir-li?: fat, nft,...?

HELP!!

---

### Post by CarlesOriol on 2007-05-08
Si ets nou nou, elimina la partició de 60 amb el windows i despres un cop engegat el instal·lador gràfic li dius que usi l'espai lliure del 2on disc.

Si ja ets una mica més curradet quan estiguis a l'instal·lador tries de fer el particionat manualment, elimines la partició en windows de 60 i crees una de 59 ext3 muntada a / i una de swapfile amb el restant

---

### Post by ventma on 2007-05-09
Gràcies Carles per la teva informació.
La veritat és que jo soc nou nou, però el que jo voldria és usar el particionat manual, si no és massa complicat, és molt difícil fer el que hem dius??

---

### Post by CarlesOriol on 2007-05-09
no crec que ho trobis massa dificil. Però unes probes en un ordinador on no tinguis res a perdre no estarien de més.

---

### Post by ventma on 2007-05-10
Aquest és el problema que si tinc a perdre. Perdona si soc massa pessat però tu no me'n podries fer cinc cèntims?, vull dir donar-me unes instruccions, un procediment per a rucs, a partir de quan li pico "manual"

---

### Post by CarlesOriol on 2007-05-10
Aquest cap de setmana et preparo un video... però no et recomano mai de la vida fer un canvi de sistema (ni tan sols de versió) en un ordinador on tinguis res a perdre...

---

### Post by ventma on 2007-05-11
Ets molt amable Carles. Jo el que voldria fer és tenir instal·lats els dos SO, Windows i Linux, en dos discs diferents, i a l'arrancar tenir la possibilitat de fer-ho amb el que jo vulgui; voldria fer una transició paulatina. Hi ha moltes eines que funcionen amb el windows i que necessito; poc a poc segurament podré anar canviant però necessitaré temps. He pensat en copiar tot el que tinc al disc gran al petit, en el qual tinc el Windows (hi cap bé), i després dir-li a la instal.lació automàtica de l'Ubuntu que s'instal·li al disc gran que, encara que hi hagi dos particions fetes amb Windows, quedarà sense dades. Que et sembla?, tinc el dubte de si d'aquesta manera l'Ubuntu m'agafarà molt espai o em permetrà fer una nova partició d'aquest disc i guardar l'espai que jo vulgui.

---

### Post by lluisanunez on 2007-05-12
Si arrenques linux desde el CD, sense instal·lar, veuràs el gparted al menú de sistema, l'arrenques i t'ensenyarà tot el que veu i com ho veu. Si aleshores no ho veus clar, envia la info al forum i t'aconsellaran.

CarlesOriol: un video de "particions sense dolor" seria un gran què :-)

---

### Post by orestesmas on 2007-05-12
Potser et resulta útil llegir-te prèviament el següent tutorial:

[http://microteknologias.cl/linux_particiones.html](http://microteknologias.cl/linux_particiones.html)

Salut.

---

### Post by CarlesOriol on 2007-05-14
Au com vaig prometre:

[http://www.archive.org/details/Particionant_el_disc_amb_ubuntu](http://www.archive.org/details/Particionant_el_disc_amb_ubuntu) Baixeu el video sencer, la qualitat en la finestra petita no serveix per a res.

---

### Post by ventma on 2007-05-14
Gràcies Orestes, he aprés molt amb el tutorial que m'has indicat.
Moltes gràcies Carles, això si que és un bon assessorament  :) :) :)

---

### Post by lluisanunez on 2007-05-14
archive.org és un bon lloc per guardar projectes CC, no?

una canya de tutorial :guitar:

---

### Post by CarlesOriol on 2007-05-14
És el primer cop que l'uso però m'ha agradat força.

És una mica "preguntaire".

---

### Post by ventma on 2007-05-17
La instal·lació ha sigut un èxit PERÔ:
He instal·lat l'ubuntu a una partició lògica de 60 GB d'un disc on hi tinc una altra partició de 100 GB  feta amb Windows (nfst); aquest partició el linux la identifica com hdb1 (localitzada a \media), però no em deixa escriure-hi res, com tampoc al disc hda1 (el C on està instal·lat l' XP). Això és normal?.
Per una altra banda, quan arranco amb Windows la partició del l'ubuntu (home) no es veu.
A les particions de Windows no es pot grabar amb linux i a l'inrevés??

---

### Post by CarlesOriol on 2007-05-17
instala el ntfs-config i configura el disc per llegir i escriure.

En windows pots muntar les particions linux amb programes controladors de disc de extf3. Microsoft passa totalment d'això.

*Per cert... és important que a cada "Thread" toquem sols un tema: 1 - Insta&#320;lació 2- Llegir i escriure en discs ntfs... etc ... així després quan algú cerqui informació sobre el que ja em vist vegi una discusió que parla d'això i no un poti poti.*

---

