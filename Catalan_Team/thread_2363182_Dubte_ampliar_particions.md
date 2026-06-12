---
title: "Dubte ampliar particions"
date: 2017-06-07
forum: Catalan Team
---

### Post by asx1231 on 2017-06-07
Hola,

En primer lloc sóc nou a la comunitat. Tinc un ordinador amb Ubuntu 16.04 instal·lat junt a Windows 10 amb dual boot. El problema es que en el moment que vaig instal·lar l'Ubuntu vaig crear una partició d'uns 40 Gb que en el temps se m'ha quedat curta i m'agradaria ampliar (ja que windows l'utilitzo de manera molt residual, només per a coses concretes de la feina). M'agradaria saber si amb l'estructura de les particions seria possible ampliar la partició Ext4 amb elguna eina tipus Gparted.

Moltes gràcies!

---

### Post by wgarcia on 2017-06-08
Segons el que mostres, no veig cap partició de 40GB. Suposo que deu ser la de 33GB. 

En principi no sembla haver-hi problemes de reduir la partició gran de 958 gigas i fer més gran la de 33GB. Tot ha d'anar bé, però millor fer còpia de seguretat de tot abans de fer-ho. També convé defragmentar la partició des Windows, 2 o 3 cops, des de dins del Windows, abans de canviar la mida de les particions. 

El canvi de mida de les particions es pot fer amb gparted.

---

