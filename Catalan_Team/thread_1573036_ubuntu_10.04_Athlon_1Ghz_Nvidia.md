---
title: "ubuntu 10.04 Athlon 1Ghz Nvidia"
date: 2010-09-12
forum: Catalan Team
---

### Post by venusfenix on 2010-09-12
buenas,
m'he instalat un ubuntu 10.04 en una maquina antiga, un athlon a 1ghz, i funciona força be.

el sistema m'indica d'instalar el maquina restrictiu per la tarja de vidio Nvidia, pero al fer-ho, la resolucio es queda a 640x480, i no puc treballar a 1024 o 1200, quan el monitor i tarja ho podem fer.
m'agradaria saber com desconectar el controlador restrictiu del maquinari i desde  el terminal, doncs amb la resolucio que tinc ara, no puc accedir per les finestres, doncs no es veu els botons.

moltes gracies,

---

### Post by quitus on 2010-09-12
Pots provar això 

"sudo aptitude remove --purge nvidia"

però no se pas quin serà el resultat.

Jo tinc un portàtil amb el driver lliure nouveau i estic molt content, amb el propietari la gràfica s'hem penja, penso que per un problema amb la temperatura de la tarja.

salut

---

### Post by Quepotser on 2010-09-12
Potser et seria més fàcil anar a *Sistema-->Administraciö-->Controladors de maquinari* i un cop allà cliquis a sobre del botó "Suprimeix". Crec que amb això en tindràs prou. Ja diràs què.

---

### Post by venusfenix on 2010-09-12
buenas,

gracies, necessito la manera per terminal, gracies Quitus, no puc fer-ho per la banda visual o finestres perque tinc la resolucio fixada a 640 i tot es massa gran i no deixa veure practicament res.

sembla que el driver de nvidia esta tret pero continuo a 640.
hi ha alguna altre manera?

gracias,

---

### Post by quitus on 2010-09-12
No se si el driver propietari t'haurà creat l'arxiu xorg.conf, fes-hi una ullada.

Potser reconfigurant les x

sudo dpkg-reconfigure xserver-xorg

salut

---

### Post by venusfenix on 2010-09-14
Buenas

finalment, ho he fet, ja está, no tinc instal.lat cap driver restrictiu i puc treballar a 1024.

gracies a tots!

---

