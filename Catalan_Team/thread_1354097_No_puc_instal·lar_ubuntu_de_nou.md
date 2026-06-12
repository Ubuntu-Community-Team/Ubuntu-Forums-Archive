---
title: "No puc instal·lar ubuntu de nou"
date: 2009-12-13
forum: Catalan Team
---

### Post by Urfe on 2009-12-13
Hola.

Vull instal·lar Ubuntu 9.10 de nou perquè la versió 9.04 me la vaig carregar provant de solucionar els problemes amb la targeta gràfica.

Però no entenc com s'ha de fer. A hores d'ara tinc una partició de 163 GB pel windows, una de 83 GB per l'Ubuntu i una de 3,5 GB per l'intercanvi. O això és el que surt en una de les pantalles del procés d'instal·lació.

En un altre fil he llegit que es parlava de particions arrel de al voltant de 10 GB o més. Perquè no la tinc ja? L'haig de crear pel 9.10?

En fi, no entenc de què va el tema.

Algú sap d'algun tutorial d'instal·lació per quan ja es té l'Ubuntu en una partició?

Gràcies.

---

### Post by SiscoGarcia on 2009-12-13
> **Urfe said:**
> Vull instal·lar Ubuntu 9.10 de nou perquè la versió 9.04 me la vaig carregar provant de solucionar els problemes amb la targeta gràfica.

Com de "carregada" la tens?

> **Urfe said:**
> A hores d'ara tinc una partició de 163 GB pel windows, una de 83 GB per l'Ubuntu i una de 3,5 GB per l'intercanvi. O això és el que surt en una de les pantalles del procés d'instal·lació.

Per què no ens adjuntes una captura del que et dóna el Gparted (o el particionador que sigui?) i podem veure millor com ho tens?

> **Urfe said:**
> En un altre fil he llegit que es parlava de particions arrel de al voltant de 10 GB o més. Perquè no la tinc ja? L'haig de crear pel 9.10?

Que no havíem quedat que t'has carregat l'ubuntu? Dependrà de com ho tinguis ;)

Explica'ns millor com ho tens ara i en podrem parlar.

---

### Post by Urfe on 2009-12-16
Sembla que es va instal·lar la versió 9.10, però tampoc funciona.

> Com de "carregada" la tens?

Me l'he carregada bastant, diria jo. No s'arriba a obrir la selecció de comptes. Abans surt un missatge que diu: (0,782770) Kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0) La paraula panic no m'agrada.

> Per què no ens adjuntes una captura del que et dóna el Gparted (o el particionador que sigui?) i podem veure millor com ho tens?

El Gparted diu el següent:

/dev/sda1       ntfs        152 GB  (aquí hi ha el windows)
/dev/sda2       extended    80,63 GB
    /dev/sda5   ext3        77,76 GB
    /dev/sda6   linux-swap  2,87 GB

Sembla que sda5 i sda6 estan dins la sda2

He llegit que convé tenir el sistema base linux en una partició d'entre 10 i 20 GB (/) i les dades en una altra partició (/home).  És correcte? I, té sentit això de tenir dues particions dins una altra com sembla que tinc ara?

Gràcies.

---

### Post by papapep on 2009-12-16
> El Gparted diu el següent:

/dev/sda1 ntfs 152 GB (aquí hi ha el windows)
/dev/sda2 extended 80,63 GB
/dev/sda5 ext3 77,76 GB
/dev/sda6 linux-swap 2,87 GB

Sembla que sda5 i sda6 estan dins la sda2


Així és: una partició estesa (sda2) i dues lògiques dins (sda5 i sda6) [1].

> He llegit que convé tenir el sistema base linux en una partició d'entre 10 i 20 GB (/) i les dades en una altra partició (/home). És correcte?

Pots no fer-ho, pero estalvia feina en reinstal·lar, ja que dient que no toqui la partició que conté el /home ja tens molta feina feta.

Així doncs, un cop tinguis les dades que t'importin desades en una còpia, pots triar per matxacar sda5 amb la nova instal·lació, o primer dividir sda5 en dues particions (una per / i l'altra per /home) i instal·lar el sistema operatiu a les dues noves particions i restaurar les dades de les que has fet còpia de seguretat dins /home un cop acabi la instal·lació.

[1] [Veure l'apartat "Tipos de particiones"]("http://es.wikipedia.org/wiki/Partición_de_disco")

---

### Post by Urfe on 2009-12-19
Una vegada aclarida la qüestió de les particions i havent decidit no dividir la partició sda5 (ja que el meu disc dur no és molt gran), he passat a provar d'instal·lar l'Ubuntu en la citada partició.

He arrencat amb el CD d'instal·lació i seleccionat "Instal·lar l'Ubuntu". Aleshores ha aparegut un gestor de particions. He seleccionat la partició sda5 i m'apareix la possibilitat de transformar-la a un altre format (no apareix l'opció d'instal·lar-hi l'Ubuntu). He provat a transformar la partició a ext4 i llavors ha aparegut una altra llista d'opcions. 

He escollit la selecció d'un punt de muntatge (hi posava cap) i aleshores ha aparegut una pantalla on deia: Starting the partitioner. En un segon a arribat al 50% i aquí s'ha aturat de manera indefinida. Aquest partitioner també m'ha sortit escollint alguna altra opció que no recordo i també s'ha clavat en el 50%.

Hem crida l'atenció que mai no veig com sortir del gestor de particions per instal·lar l'Ubuntu.

Gràcies pels comentaris.

---

### Post by SiscoGarcia on 2009-12-21
> **Urfe said:**
> He arrencat amb el CD d'instal·lació i seleccionat "Instal·lar l'Ubuntu". Aleshores ha aparegut un gestor de particions. He seleccionat la partició sda5 i m'apareix la possibilitat de transformar-la a un altre format (no apareix l'opció d'instal·lar-hi l'Ubuntu). He provat a transformar la partició a ext4 i llavors ha aparegut una altra llista d'opcions. [...]

Darrerament també he tingut algun problema que no entenc amb el particionador i el que m'ha funcionat millor és eliminar la partició on hi vull reinstal·lar l'ubuntu i després dir-li que s'instal·li a l'espai lliure continu més gran.

Amb això no fas les coses d'una manera elegant (el papapep em renyarà) però pots instal·lar-lo... això sí, sense separar l'arrel (/) de les dades (/home), que m'ha semblat entendre que és el que volies fer.

---

