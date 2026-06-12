---
title: "Com inhabilitar sintonitzadora tv?"
date: 2010-05-18
forum: Catalan Team
---

### Post by Black_02 on 2010-05-18
Hola,

Voldria inhabilitar la targeta tv, però no se com fer-ho.
El cas es que hem funciona, però em dona problemes. He provat el "gnome device manager" que és un programa molt similar al device manager de windows, però en aquest cas no té cap opció de desinstal·lar els drivers.

La targeta és la pinnacle 310i (Philips TDA10046H DVB-T).

---

### Post by wgarcia on 2010-05-18
Pots fer 

lsmod

des d'una terminal i ubicar el mòdul o mòduls  que controla la targeta, i després fer

sudo rmmod <nom del mòdul>

Si els vols cancel·lar permanentment has d'editar

/etc/modprobe.d/blacklist

i afegir una línia
blacklist <nom del mòdul>

per cada mòdul que vols eliminar.

---

### Post by Black_02 on 2010-05-18
Hola wgracia,

He fet el que has dit: blacklist videodev, però he reiniciat i igual tinc el problema.

Crec que el que faré el treure-la físicament, així segur que no fallo, encara que és llàstima tindre la targeta de petjapapers.

---

### Post by wgarcia on 2010-05-19
Penso que hauria d'haver-hi algun altre mòdul a més de "videodev".

---

