---
title: "[SOLVED] Problemes fent l'Upgrade"
date: 2007-10-18
forum: Catalan Team
---

### Post by kukat on 2007-10-18
Salutacions a tots els ubuntaires!!

Ja estava fent el upgrade a la versió nova, i m'ha donat el seguent error:

[I]"Failed to fetch cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nous
Failed to fetch cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz Si us plau, useu apt-cdrom per a que aquest CD sigui reconegut per APT. No pot usar-se apt-get update per afegir-ne de nous"[/I]

He baixta també el cd, he grabat l'imatge, però hem surt aquest missatje:
[I]"kukat@kukat:~$ gksu "sh /cdrom/cdromupgrade"

(gksu:16771): Gtk-WARNING **: No s'ha trobat el motor de tema al module_path: "ubuntulooks","[/I]



... L'Ubuntu Studio també es pot actualitzar a la nova versió???????????????????????????

Moltes gràcies a tots per adelantat.

Per cert, com van les ATi amb el NOu Ubuntu? Hi ha novetats? Hem sembla que per aquestes dates traurien els drivers per a les tarjes de la 300 a la 1900, ja que van traure de les tarjes superiors al mes de setembre.... Si algú sap alguna cosa que m'avise...

Gràcies!!:guitar:

---

### Post by papapep on 2007-10-19
Edita el fitxer /etc/apt/sources.list i comenta, o esborra, la línia que comença amb:

cdrom:[Ubuntu Studio 7.04 _Feisty Fawn

> L'Ubuntu Studio també es pot actualitzar a la nova versió???????????????????????????

Si et funciona serà que si. ;-)

---

### Post by kukat on 2007-10-19
deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main

deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main

Esborre aquestes dues linies????

Gràcies, ja tinc ganes de veure el nou sistema a veure si funciona la tarja ATI, i per veure els nous avantatges!!

---

### Post by kukat on 2007-10-19
Ja funciona!!! Gràcies, era únicament aixó.
Però dues preguntes:

Per què era aixó? (així vaig aprenent), i ... Puc navegar per internet (o fer alguna cosa) mentre s'instala l'Ubuntu? O pot causar greus problemes?????

---

### Post by papapep on 2007-10-19
Doncs per que en algun moment, o tu o l'instal·lació de la Feisty va posar com a font de programari al /etc/apt/sources.list el CD de la Feisty.
Com que al intentar actualitzar no el trobava es queixava... :-)

No tens perquè causar problemes. L'única situació que se m'acudeix que podria provocar entrebancs és que tinguéssis alguna altra connexió de xarxa (p.ex. amule i similars) que agafés tant d'ample de banda que no en deixés per l'actualització i petés.

Si el que fas són les coses "normals", navegar, correu, etc... cap mena de problema. Jo ho faig absolutament sempre.

---

### Post by kukat on 2007-10-19
Moltes gràcies!! Ja sé alguna cosa més, i ja no estic preocupat (de totes maneres jo ja estava navegant per internet, jejeje)

---

