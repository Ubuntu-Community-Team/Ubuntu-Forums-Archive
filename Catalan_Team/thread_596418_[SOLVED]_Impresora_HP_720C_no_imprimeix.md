---
title: "[SOLVED] Impresora HP 720C no imprimeix"
date: 2007-10-29
forum: Catalan Team
---

### Post by ventma on 2007-10-29
Des de que vaig instal·lar l'UBUNTU 7.10 la impresora no imprimeix; està instal·lada, la reconeix, diu que està preparada però res no va.

---

### Post by papapep on 2007-10-29
Ostres Ventma, no dones gaires pistes....

La pàgina de prova de l'impresora, surt correctament? 

Si al navegador d'internet fiques la url:** [http://localhost:631](http://localhost:631)**, t'apareix l'impresora com a configurada i preparada? 

Has provat a canviar el cable?

---

### Post by Tomàs M. on 2007-10-30
Quina impressora tens?
Pots provar això: [https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537](https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/152537)
o [http://ubuntuforums.org/showthread.php?t=192651](http://ubuntuforums.org/showthread.php?t=192651) si fos una  HP Deskjet 720C o similar com la meva, que també em va deixar d'imprimir amb l'actualització. 
Al final ho vaig solucionar eliminant totes les impressores (aquesta, la d'imprimir a PDF -que ara és molt més fàcil d'afegir amb Gutsy- i la mateixa en xarxa per si la tinc físicament connectada a una altra màquina), esborrant el fitxer de configuració (en el meu cas /etc/pnm2ppa.conf) i afegint-la de nou (en cap moment me la va arribar a detectar automàticament com aquí: [http://www.kumbaworld.com/blogs/?p=19](http://www.kumbaworld.com/blogs/?p=19) )
Sort!

---

### Post by ventma on 2007-11-07
SOLUCIONAT. Gràcies per la vostra ajuda. Resulta que la meva impressora és també HP 720C, per tant he fet el que Tomàs M. ha dit i ha funcionat.

---

