---
title: "Com recuperar Linux després de formatejar i instalar windows"
date: 2009-08-25
forum: Catalan Team
---

### Post by rocky67 on 2009-08-25
Bones , tinc al meu ordinador dos disc durs , en un tinc instal·lat Ubuntu i en l'altre tinc Windows. Ara he formatejat el disc dur on tenia windows per fer neteja , formateig i nova instal·lació de windows. Bé la emva sorpresa que al iniciar l'ordinador només em detecta el windows.
 
HE llegit pels forums que el que ha passat que m'ha desaparegut el grub al fer el formateig del disc i la nova instal·lació de windows, i que puc utilitzar una aplicació des de windows per crear el GRub tal i com wingrub. HE executat aquesta aplicació però no entenc com ho haig de fer, ja que no he trobat res ni cap lloc on m'ho expliqui. 
 
Alguna persona em podria dir com ho tinc que fer per a que em sorti de nou el grub i pugui arrancar amb el sistema operatiu que vulgui ? 
 
salutacions cordials i moltes gràcies

---

### Post by Daerun on 2009-08-25
Jo en aquest cas vaig fer servir supergrub:

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Ho graves en un cd-rom, arrenques des del CD, et deixa escollir el català i tot. Després selecciones linux,  Recuperació (o una cosa així), després em sembla que et demanarà que seleccionis la partició on tens el grub instal·lat, i teòricament ha de funcionar si no és que el grub s'ha esborrat del tot (en principi no).

---

