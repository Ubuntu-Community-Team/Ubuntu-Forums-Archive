---
title: "No entra a l'Ubuntu (pantalla en negre)"
date: 2010-02-13
forum: Catalan Team
---

### Post by lluisalguero on 2010-02-13
Hola companys,
intentaré explicar el problema a veure si podem solucionar-ho.

Ahir vaig instal·lar una aplicació (no recordo el nom) on podia canviar diverses coses del grub. Com que la lletra es (era) bastant gran, vaig canviar la resolució (al mateix programa) a 1280x1024 (o vaig fer a dos llocs diferents del programa).

Doncs be, aquest migdia al ficar en marxa el pc, ha canviat la resolució del menu on triar quin SO vols triar (per defecte tinc Ubuntu) i perfecte, un cop sel·leccionat ubuntu, es queda la pantalla en negre i no fa res mes...

He provat amb el "recovery mode", però entrem en la fase de picar a la consola i aquí vaig perdut.

Gràcies per la vostra comprensió i ajuda

Lluís

---

### Post by lluisalguero on 2010-02-13
el programa en questió crec que es diu "start-up manager"

Gràcies
LLuís

---

### Post by lluisalguero on 2010-02-13
He aconseguit entrar a la configuració del grub2

nano /etc/default/grub

he mirat per allà si hi havia alguna resolució de pantalla fora de lloc i tot sembla correcte, però encara no puc entrar

Si algú em vulgués ficar com té ficat aquest arxiu per a poder comparar amb el meu, em faria un gran favor, penseu que vaig molt perdut.

Mentre algú em tira un cable, vaig buscant possibles solucions per internet.

Gracies

lluís

---

### Post by kimet on 2010-02-13
/boot/grub/grub.cfg Es el ficher de configuració de grub.
Pots canviar aquí la resolució de pantalla i fer update-grub després.

salut

---

### Post by lluisalguero on 2010-02-14
> **kimet said:**
> /boot/grub/grub.cfg Es el ficher de configuració de grub.
Pots canviar aquí la resolució de pantalla i fer update-grub després.

salut

Gracies kimet, però el més que aconsegueixo és canviar la resolució del grub. El problema ve després que quan trio l'ubuntu no entra, és queda la pantalla en negre.

Lluís

---

### Post by PatrickVogeli on 2010-02-14
has provat entrant amb un kernel mes antic?

---

### Post by kimet on 2010-02-14
Pensaba que era la resolució de grub que volies canviar.

Per canviar resolucio de pantalla desde consola 

```
$ xrander

```
i pr seleccionar una resolucio:

```
$ xrandr -s [n]
``` 
 
n = numero de la linia hon es troba la resolució, començant desde cero.

Salut

---

### Post by lluisalguero on 2010-02-14
He provat un kernel més antic i continua igual.

kimet, provaré aquesta nova opció que em dius.

gracies

---

### Post by lluisalguero on 2010-02-14
Ja torno a ser al meu estimat Ubuntu. Gràcies a tots dos per l'ajuda.

Us explico una mica

he mirat el /boot/grub/grub.cfg i segons un exemple ficava això:

> menuentry "Ubuntu, linux 2.6.28-13-generic" {
        linux   /boot/vmlinuz-2.6.28-13-generic root=UUID=b02e1934-12dd-418a ro  quiet splash** vga800**
        initrd  /boot/initrd.img-2.6.28-13-generic

i jo tenia ficat **vga775**, he canviat això, he reiniciat i ara ja he entrat.

Ara tornaré de provar de reiniciar a veure si no hi ha cap problema.

Moltes gràcies pel vostre suport,

Lluís

---

### Post by lluisalguero on 2010-02-14
Reiniciat i cap problema. Dono el tema "zanjat i punto" :P

---

