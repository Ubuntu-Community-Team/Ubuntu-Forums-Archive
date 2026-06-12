---
title: "Problemes amb l'Adobe Flash Player"
date: 2010-11-27
forum: Catalan Team
---

### Post by ferry11 on 2010-11-27
Hola a tots,

Després d'una temporada sense Ubuntu, me l'he instal·lat de nou, i quan he volgut ficar-me l'Adobe em diu que hi ha una error. Ho he provat pel Synaptic i pel Gestor d'archius, us ficu el que em diu quan ho he intentat pel Gestor: "This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time." 


La veritat es que no tinc ni ideia de com solucionar-ho, espero que em pogueu ajudar.

---

### Post by wgarcia on 2010-11-28
Prova el següent. Obre una terminal i entra la instrucció següent:

sudo aptitude search flash |  grep ^i

A la terminal s'escriurà si tens instal·lat alguna aplicació per al flash, suposadament no la tens pel missatge que et surt. però si et sortís l'hauries de desinstal·lar. Per exemple a mi em surt:

iB  flashplugin64-installer         - Adobe Flash Player plugin 64 bit alpha ins

Això vol dir que tinc instal·lat el "Flash plugin" per a 64 bits. Per remoure'l la instrucció seria:

sudo apt-get remove --purge flashplugin64-installer

on poso "--purge" perquè es remoguin també els arxius de configuració si n'hi ha. Si no surt res a la terminal aquest pas anterior no l'has de fer.

Un cop fet això prova ara:

sudo apt-get install ubuntu-restricted-extras

Ara s'hi haurien d'instal·lar no sols el flash plugin sinó alguns altres codecs i programes propietaris que no venen a les imatges d'instal·lació per motius obvis.

---

### Post by ferry11 on 2010-11-28
Ho he provat, però quan intento fer "sudo apt-get install ubuntu-restricted-extras" em diu "No s'ha trobat el paquet ubuntu-restricted-extras"

Que hauria de fer ara?

---

### Post by ferry11 on 2010-11-28
No sé si us serviria d'ajuda dirvos que quan intento instal·lar-lo a través d'aquell missatge que et surt quan vas a una web i et diu que hi falten connectors i hi intento descarregar l'Adobe des d'allà em diu el següent: 

"No es pot instal·lar <<flashpluguin-installer>> (E.No es poden corregir els problemes, teniu paquets retinguts que estan trencats"

---

### Post by wgarcia on 2010-11-29
Respecte als "paquets retinguts" prova de fer

sudo apt-get dist-upgrade

Quant a "ubuntu-restricted-extras" mira si tens habilitat el dipòsit de programari corresponent, anant al menú "Sistema -> Administració -> Gestor de Paquets Synaptic -> Repositoris" i aquí mira el menú "Configuració" i a la primera pestanya "Programari d'Ubuntu", mira si tens marcat "Programari protegit per copyright o problemes legals (multiverse)". Un cop marcat tanca el Synaptic, i torna a provar d'insal·lar "ubuntu-restricted-extras".

---

### Post by Automat2 on 2010-12-09
Prova [Flash-Aid]("http://flash-aid-extension.blogspot.com/") o directament al web de [Flash]("http://get.adobe.com/flashplayer/") per installar-lo.

---

### Post by rmtrias on 2011-09-21
M'he comprat un Efika i no hi ha manera de posar el flash. He fet tot el que he trobat a la xarxa i porto moltes hores fent proves. No me'n surto. Algú que tingui un EFIKA em pot dir si ho ha aconseguit? Em sembla impossible que no es pugui veure videos de youtube, per exemple.

---

### Post by quitus on 2011-09-22
Com t'ha dit en Automat2, prova flash aid

Es un complement del firefox que et facilita moltíssim tenir el flash totalmen actualitzat. Jo en un portàtil amb ubuntu 64 bits va ser l'única manera d'aconseguir-ho.

salut

---

### Post by wgarcia on 2011-09-23
He mirat per Internet i m'ha semblat veure que aquest aparell Efika té processador ARM (com els mòbils), per aquí potser puguis trobar la versió de Flash adequada.

---

### Post by rmtrias on 2011-10-05
He instal·lat Flash-aid i res de res. Sembla que ho fa tot be, però quan vaig a una pàgina on cal instal·lar els connectors de flash, no hi ha manera. He llegit la documentació, he fet tot el què hi diu i no ho aconsegueixo. 

Tampoc ho aconsegueixo amb el que em diu wgarcia del móbils. 

Us agraeixo molt les respostes, però, de moment, estic igual. Ningú més té un EFIKA i li passa això?

Gràcies i perdoneu les molesties

Rosa Maria Trias

---

