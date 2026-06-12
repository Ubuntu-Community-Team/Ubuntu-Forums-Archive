---
title: "problemes amb XVID al VLC"
date: 2009-10-28
forum: Catalan Team
---

### Post by dmartinez116 on 2009-10-28
Be, pareix que després de trastejar prou amb el meu ubuntu 9.04 (instal·lació i posterior eliminació de: Cinelerra, openshot, ffmpeg, mobile media converter, i alguna coseta més, per exemple utilitzar el netejador del sistema) ara tinc problemes per a reproduïr videos al VLC:

```
No hi ha un decodificador adient:
El VLC no admet aquest format de video o àudio "XVID".
Malauradament no és possible solucionar-ho.
```

He tractat de desintal·lar-lo i tornar-lo a instal·lar... ara mateix tic la versió 1.0.2 Goldeneye.

Algu te alguna idea?

Amb el karmic es solucionarà?

---

### Post by socderafel on 2009-10-29
Has provat a instal.lar els ubuntu-restricted-extras?? 
Pareix que el problema siga que no tens els códecs... 

Posa-li a la terminal
sudo apt-get install ubuntu-restricted-extras

i si ja els tens mira d'actualitzar-los.

PD: de Carlet xeee!!!

---

### Post by dmartinez116 on 2009-10-31
> **socderafel said:**
> Has provat a instal.lar els ubuntu-restricted-extras?? 
Pareix que el problema siga que no tens els códecs... 

Posa-li a la terminal
sudo apt-get install ubuntu-restricted-extras

i si ja els tens mira d'actualitzar-los.

PD: de Carlet xeee!!!

Iee!! moltes gràcies fenomeno!

La teua solució no ha funcionat, però m'alegra vore que no soc l'unic de la ribera...

Al final, actualitzant al Karmic Koala... han desaparegut els problemes.

---

### Post by Mitsurugi on 2009-11-03
Hola que tal, jo tinc el mateix problema, no puc reproduir arxius, la qüestió es deu al **** openshot video, i si m'ho hagués llegit abans no m'hagues passat...

> WARNING: Our PPA uses a special version of FFmpeg, which does not work with VLC & Totem, and a few other movie players. This is due to how we are packaging FFmpeg in our PPA. We are working to fix this, but if you install via the PPA, you will not be able to run VLC at this time. 

Però bé, el mal ja està fet, he fet desaparèixer el openshot, així com els seus ppa i reinstalat el VLC i els restricted-extras, però segueix teninr problemes, algú te alguna solució?

estic a karmic!

---

### Post by Mitsurugi on 2009-11-03
la solució en aquest fil

[http://ubuntuforums.org/showpost.php?p=8179317&postcount=14](http://ubuntuforums.org/showpost.php?p=8179317&postcount=14)

---

