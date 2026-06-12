---
title: "Amarok,traducció"
date: 2009-04-24
forum: Catalan Team
---

### Post by jaume69 on 2009-04-24
Doncs això,que m´he instal.lat l´Amarok 2.0.2 de la **Jaunty Jackalope**,i em surt amb anglés.
Hi ha alguna manera de posar-lo en Spain?
Gràcies.

---

### Post by oriolsbd on 2009-04-24
Si és el primer programa de KDE que instal·les en aquesta instal·lació, és perquè encara no tens instal·lats els paquets de llengua per als programes d'aquest escriptori. La manera més fàcil de fer-ho és anar a l'aplicació de configuració de la llengua ("Sistema>Administració>Suport d'idioma"). Quan t'obri l'aplicació, automàticament et dirà que et falten aquests paquets per al KDE, i que si els vols instal·lar. Li dius que sí, i quan tornis a engegar l'Amarok ja el tindràs en català.

Salut!

---

### Post by LitusMayol on 2009-04-24
Jo he tingut dos problemes amb el meu estimadíssim **Amarok**.

[LIST=1]
[*]**El primer: idioma.** He instal·lat els paquets *language-pack-kde-ca* i *language-pack-kde-ca-base*, doncs ja m'havia passat altres cops i sempre se m'ha solucionat així.

Per tan:
```
sudo apt-get install language-pack-kde-ca	language-pack-kde-ca-base
```


[*]**El segon: no reproduïa.** Aparentment reproduïa perfectament, però les cançons no sonaven per enlloc (i no, no era el volum! xD). Total:
```
sudo apt-get remove phonon-backend-gstreamer
sudo apt-get install phonon-backend-xine

```
[/LIST]


Espero que serveixi! ;)

---

### Post by jaume69 on 2009-04-25
> sudo apt-get install language-pack-kde-ca	language-pack-kde-ca-base

**Perfecte!.**

> # El segon: no reproduïa. Aparentment reproduïa perfectament, però les cançons no sonaven per enlloc (i no, no era el volum! xD). Total:
Code:

sudo apt-get remove phonon-backend-gstreamer
sudo apt-get install phonon-backend-xine

Jo em sembla que vaig instalar **libxine1-ffmpeg** i codecs **gstreamer**

A mi també m'agradava més l'antic,però bé,ja ens hi acostumarem..
Crec que aquest està molt bé també.

Merci!!.:)

(SOLVED)

---

