---
title: "Ubuntu 12.04 i Windows 8"
date: 2013-02-11
forum: Catalan Team
---

### Post by akyra on 2013-02-11
Hola,
tinc un amic que s'ha comprat un portatil que porta pre instal·lat el windows 8 i voldria instalar també Ubuntu.
Jo li he aconsellat que agafi el 12.04 ja que no té experiencia amb Ubuntu i crec que una versió LTS li portarà menys problemes.

Bé, he lelgit que la versió 12.10 si que es pot instal·lar junt amb Windows 8 però no sé res de la versió 12.04.

Algú ho ha probat ho té informació per instarlar-ho?

Gracies

---

### Post by wgarcia on 2013-02-11
Jo encara no m'he trobat però penso que el problema no és Windows 8 sinó la protecció que té l'arrencada i que substitueix l'antic BIOS (em sembla que es diu UEFI). Un altre abús permès de Microsoft és que requereix els fabricants que hi hagi una protecció signada per ells per no permetre la instal·lació d'altres sistemes operatius, que algú em corregeixi si ho estic dient malament, perquè com deia encara no m'ha tocat instal·lar us sistema amb aquesta protecció:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Si no té aquesta UEFI no hi hauria problema en instal·lar qualsevol versió d'Ubuntu o Linux en general al costat del Windows. 

També compte si és un Samsung recent perquè he llegit que hi ha hagut algun problema que fa que l'ordinador es torni no arrencable quan s'intenta instal·lar Ubuntu, no sé si ja ho han arreglat: 

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

No sembla ser un problema de Linux sinó de Samsung:

[http://mjg59.dreamwidth.org/22855.html](http://mjg59.dreamwidth.org/22855.html)

---

### Post by akyra on 2013-02-11
Sí, és això que dius tu el UEFI.
Sí que el té activat, al tenir el W8 pre-instal·lat ja el tens per defecte.

Era per saber si algú ja ho havia provat, però em sembla que és un bon merder.

---

### Post by wgarcia on 2013-02-11
Si no és un model Samsung dels que es mencionen a l'enllaç a l'error de Launchpad, en principi hauria de funcionar. Però si és Samnsung, tot i que no instal·li Linux, pot tenir problemes segons el que diu en un altre dels enllaços. 

Una altra possibilitat es tornar a insta·lar Windows sense UEFI, segons el que he llegit.

---

### Post by CarlesOriol on 2013-02-12
És important canviar a la bios el tipus de boot de uefi a bios.

---

### Post by akyra on 2013-02-13
Ok, Carles li ho diré.

Gracies

---

