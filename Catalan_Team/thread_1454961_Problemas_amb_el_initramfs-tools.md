---
title: "Problemas amb el initramfs-tools"
date: 2010-04-15
forum: Catalan Team
---

### Post by tanreb20 on 2010-04-15
Hola amics! Avui he decidit actualitzar-me a la beta 2 del Lucid, per alló de anar solventant bugs i tot aixo...

Després d'un intensiu d'actualitzacions etc... resulta que tinc un error en aquets paquets, i no hi ha manera d'actualitzar-los... alguna idea o solucio?

```
Els paquets següents s'han apartat:
  evolution-data-server-common initramfs-tools 
Els paquets següents s'actualitzaran:
  ttf-indic-fonts-core 

```

He provat e fer sudo dpkg --configure -a, update-initramfs -k ... i res funciona, en principi l'ubuntu funciona, pero...

---

### Post by wgarcia on 2010-04-16
Ho has tornat a provar? Al Launchpad hi ha molts informes semblants al teu, però sembla que ja hi ha hagut alguna actualització que ho ha arreglat. Per tant 
sudo dpkg --configure -a
ho hauria d'arreglar.

---

### Post by tanreb20 on 2010-04-16
Si, ho vaig provar i no feia aboslutament rés aquesta comanda, semblaba que funciones pero no retornava cap frase per pantalla aixi que no puc estar segur.

Pro =ment ho feia i seguia sense poder actualitzar

---

### Post by PatrickVogeli on 2010-04-17
has provat a borrar-los amb dpkg --purge i despres, abans de reiniciar, tornar-los a instalar?

---

### Post by tanreb20 on 2010-04-17
Hola! Diria que si vaig provar-ho (ara estic al KK)

Pero encas que no hi hagi provat, em fa bastanta por desinstalar aquestes coses... jeje! Demá ho ptovo i us dic quelcom.

---

