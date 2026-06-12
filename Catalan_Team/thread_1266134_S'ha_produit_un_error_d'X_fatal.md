---
title: "S'ha produit un error d'X fatal"
date: 2009-09-14
forum: Catalan Team
---

### Post by Mitsurugi on 2009-09-14
Hola a tothom últimament s'em congela de tan en tant el sistema al reproduir videos. No se el perquè, se m'ha acudit cercar als logs i l'únic que sembla que trobo es al syslog

```
Sep 14 14:59:45 didac-desktop gdm[2626]: WARNING: gdm_slave_xioerror_handler: s'ha produït un error d'X fatal - S'està reiniciant :0 
Sep 14 15:00:19 didac-desktop syslogd 1.5.0#5ubuntu3: restart.
```

Y d'altres ak kern.log i messages com

```
Sep 14 14:59:45 didac-desktop kernel: [  607.036807] Xorg[2633]: segfault at 6c47b4c ip 00000000004e0420 sp 00007fff033c8228 error 6 in Xorg[400000+1c3000]
```

El problema me l'he trobat al reproduir videos, al ficar-lo a pantalla completa fot el crash aquest de moment només amb el VLC.

Ha cercat errors com aquests i n'hi ha de molt variats, navegant amb opera, amb firefox, al polsar una combinació de tecles, però no troco cap concret amb el VLC, i entre bugsreports i fòrums, tampoc hi donen cap solució a part de "reinstalar"

Utilitzo la 9.04 64 bits controlador gràfic de propietat FGLRX d'ATI/AMD

kernel linux 2.6.28-15

No se si a algú li passa, ho creu quin podria ser el problema. A part de la típica opció de reinstalar.

Gràcies

PS Un altre tema, intento reiniciar mitjançant teclat i el ctrl + alt + del ja no funciona crec que he llegit que alt + impr pant + k es la solució?

---

### Post by quitus on 2009-09-14
En les targes ati el driver lliure sol funcionar molt bé, jo tinc una ati radeon x700 i no en tinc cap queixa.

Per desinstal·lar el driver propietari:

sudo apt-get remove xorg-driver-fglrx

Per instal·lar el driver lliure: (n'hi ha molts per que no se quina tarja tens)

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeon xserver-xorg-video-radeonhd 

Si la cosa no rutlla, sempre pots recuperar el xorg.conf des de el cdlive.

salut

---

### Post by Mitsurugi on 2009-09-23
Gràcies! De moment no tinc problemes, no se que deuria passar, (tampoc he tocat res), simplement, he deixat de tenir problemes, apunto el que m'has dit per si torna a passar ...

gràcies de nou!

---

### Post by Mitsurugi on 2009-09-25
Bé, han tornat els problemes, i he provat el que m'has dit, no sense reiniciar i trobar-me errors.

Ara un cop tot a lloc he tret els propietaris i vaig amb els xserver-xorg-video-radeonhd (tinc una ati radeon hd 4550)

Ara però, no se m'habiliten els efectes d'escriptori

---

### Post by quitus on 2009-09-27
Es estrany, ja que el driver lliure per les targes ati suporta acceleració 3D. penso que serà cosa del xorg.conf, la solució podria passar per posar el cdlive, comprovar que tinguis efectes, copiar el xorg.conf que genera el cdlive i aplicar-ho en sistema instal·lat. Jo sempre acabo donant el mateix consell, però es que es tant efectiu...


salut

---

### Post by Mitsurugi on 2009-09-27
M'ho apunto, on es generarà el xorg del live cd?

---

### Post by papapep on 2009-09-28
On sempre: /etc/X11/xorg.conf (del sistema de fitxers del live cd, clar).

---

