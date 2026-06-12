---
title: "Ressolució del monitor"
date: 2009-05-14
forum: Catalan Team
---

### Post by lorencillo on 2009-05-14
Hola a tots,

us presento la meva duda.... ](*,)

fa res que he m'he comprat una nova adquisició informàtica, un monitor TFT panoramic de 21,5" :D exactament un Acer V223HQ. I estic molt content però necessito fer-lo aprofitar amb una resolució més fina, ara mateix està amb 1360x768 amb la que no s'aprofita tota la seva qualitat.

Crec que la meva nVidia GeForce 8600 GT pot agafar resolucions més grans!! però quan faig servir el programa de configurarió de Nvidia no puc agafar de més grans!!! 

He estat mirant els arxius de configuració del servidor X11 i el monitor que està es l'antic!! 

> Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Sony"
    ModelName      "Sony HMD-A240"
    HorizSync       30.0 - 70.0
    VertRefresh     48.0 - 120.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync

la veritat es que no sé com puc generar un nou fitxer amb el monitor correcte i les seves resoluccions, sense que afecti a res més o inclús modificar aquest mateix...

Algú en pot ajudar, gràcies!

Per cert la Festa Jaunty Jackalope va ser GENIAL!!!! ;)

---

### Post by kimet on 2009-05-14
Hola.

Si et baixes el paquet "nvidia-xconfig" i l'executes et genera un "xorg.conf" nou. És la manera, diguem-ne més "ubuntera" de fer-ho, però de vegades falla.(jo no me'n fio).
Si vols aprendre més poses en consola:
```
man xorg.conf
```
O busques a google un manual :D

Adeu.

---

