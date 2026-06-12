---
title: "Per reproduir .avi em demana DivX MPEG-4 Version 4 decoder"
date: 2010-05-22
forum: Catalan Team
---

### Post by RicardKp on 2010-05-22
Hola, a tothom,

No puc veure vídeos en format.avi en cap reproductor, ni en el VLC... Al començar a reproduir em demana el connector ***DivX MPEG-4 Version 4 decoder*** me'l busca ell mateix i no me'l troba. Em sembla que tot provant de fer anar el flash dec haver desinstal·lat algun paquet que necessito, però el Gstreamer el tinc instal·lat correctament. Crec que dec d'haver instal·lat algun altre paquet obsolet i que aquest connector que em demana també és obsolet, de totes maneres, no n'estic segur.
Què puc fer? em podeu ajudar?

Gràcies per endavant, Ricard

---

### Post by PatrickVogeli on 2010-05-23
sudo apt-get install ubuntu-restricted-extras

---

### Post by RicardKp on 2010-05-23
Gràcies PatrickVogeli,

Ja tenia instal·lat l'ubuntu-restricted-extras. De totes maneres, l'he reinstal·lat i aleshores ja em reproduïa, però només amb el VLC. Per tant he desinstal·lat i tornat a instal·lar el totem així com l'ubuntu-restricted-extras, tot seguia igual, VLC sí, totem no. Finalment he optat per provar amb un altre reproductor, m'he instal·lat el gnome mplayer i també funcionava correctament.
Crec que ara ja puc anar tirant, però tinc el cuquet de saber què coi passa amb el totem i poder-lo arreglar. Si algú em dóna un cop de mà estaré content, però no és pas urgent.
De moment opto per no posar Solved, perquè encara que ja puc reproduir, alguna cosa no acaba de funcionar.

Gràcies, de nou,
Ricard

---

### Post by PatrickVogeli on 2010-05-23
pots comprovar si tens instalats el paquets gstreamer0.10-plugins-ugly, ..-bad i ..-ugly-multiverse i ..-bad-multiverse?

---

### Post by RicardKp on 2010-05-23
Noi, sí que estan instal·lats...

---

