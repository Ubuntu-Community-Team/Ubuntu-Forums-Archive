---
title: "Configuració teclat a Xubuntu"
date: 2011-12-02
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2011-12-02
Bones.
Tinc un Xubuntu 11.10 recent instal·lat que no em rutlle bé el teclat.
Al suport d'idioma hi tinc configurat Català Valencià (crec recordar que en altres instals. m'ha anat bé). Però el teclat està com desconfigurat: si premo una tecla, em surt una altra de diferent.
Eventualment ho "apanyo" amb Terminal: setxkbmap es
i funciona bé. Però en reiniciar PC torna anar malament.
Algú sap com fixar això del teclat? sisplau.

---

### Post by Miquel Ubuntero on 2011-12-02
Bé, finalment m'he hagut d'espavilar tot sol.
Per si li passa a algú altre, això és el que he fet amb el Terminal:

$ cd /usr/bin
$ sudo touch teclat
$ sudo nano teclat

Nano és per editar l'arxiu i afegir-li aquestes dues línies:
"#!/bin/bash"

"setxkbmap es"

Per desar l'arxiu creat i sortir:

$ alt + O (premeu la tecla alt i la lletra o)

$ alt + X

El següent pas és donar a l'arxiu permís d'execució com a programa:

$ chmod +x teclat

Ep! Cal que esteu ubicats a /usr/bin

Per acabar, només us farà falta dir al sistema que "teclat" s'executi cada cop que inicieu Ubuntu.

Heu d'afegir aquesta ordre: /usr/bin/teclat

Per fer-ho amb Ubuntu:

Aneu a Paràmetres del Sistema - Aplicacions d'inici

Amb Xubuntu:

Aneu al Gestor d'ajustaments - Sessió i engegada - Inici automàtic d'aplicació


Salut!
:)

---

### Post by Miquel Ubuntero on 2011-12-13
Tinc que rectificar l'anterior so&#320;lució, ja que no havia vist  no funcionava la ela geminada.
Fent la següent ordre (molt més senzilla) al Terminal, funciona també la ela geminada:

$ sudo dpkg-reconfigure keyboard-configuration

---

