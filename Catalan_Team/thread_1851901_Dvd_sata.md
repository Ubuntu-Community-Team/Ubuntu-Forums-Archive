---
title: "Dvd sata"
date: 2011-09-29
forum: Catalan Team
---

### Post by L'os trenkat on 2011-09-29
Hola, he comprat un pc nou. sense sistema operatiu per poder-hi instalar el Ubuntu en Catala. 
Pero em sortia aquest misatge:..

busybox v1.17.1 (Ubuntu 1:1.17.1 -10ubuntu1) built-in shell (ash) 
enter 'help' for a list of built- in commands 

(initramfs) Unable to find a medium containing a live file system 

Finalment he conseguit instalar-lo, pero desde un CD-DVD extern USB.
he fet una actualitçacio del programari, pero el DVD-CD intern SATA no funciona.

¿que te alguna incompativilitat???

La placa base es una ASUS P8H 61-M LX
amb un INTEL DualCore i3-2100 3.1GHZ

---

### Post by L'os trenkat on 2011-10-01
AUXILI.... 
no funciona y haig de saber si val la pena esperar a que surti la solucio o tornar l'ordinador.
Tant la placa base de asus, com el chipset de intel, com la regravadora de LG no tenen drivers per linux, es important?????

---

### Post by wgarcia on 2011-10-01
Fent una cerca ràpida a Internet surten diverses referències a problemes amb aquest tipus de lectores de DVD. Un suggeriment que donen alguns és instal·lar la versió de 32 bits, però sembla més un problema del nucli de Linux que no reconeix els SATA. 

Però no ho prenguis com una resposta definitiva, no tinc cap mena d'experiència amb els SATA. 

Quina versió d'Ubuntu has provat?

---

### Post by L'os trenkat on 2011-10-02
Donç crec que aixo ja ho baig probar, inclos e probat amb la versio 11.10

---

### Post by L'os trenkat on 2011-10-04
Krek, pero nomes es una primera impressio que el problema es, que en la BIOS s-ha de configurar el SATA MODE com a AHCI o una cosa semblant, i no en las ja conegudes IDE, RAID...
De moment ja puc fer l'installacio desde el CD-DVD intern.

---

