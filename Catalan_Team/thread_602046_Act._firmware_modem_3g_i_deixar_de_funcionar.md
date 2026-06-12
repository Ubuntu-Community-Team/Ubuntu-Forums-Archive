---
title: "Act. firmware modem 3g i deixar de funcionar"
date: 2007-11-03
forum: Catalan Team
---

### Post by manelolesa on 2007-11-03
He tingut que actualitzar el firmware del modem usb 3g de movistar per necesitat de fer-lo anar enun windows vista.

Desde que he fet aixó que no puc connectar desde linux.

Al carregar el modul del modem surt un erro dump o core dump.

Algú s'ha trobat ?

Slt]

(*,)

---

### Post by RainCT on 2007-11-04
Hola,

T'he contestat al [bloc](http://bloc.eurion.net/archives/2007/ubuntu-i-programari-lliure/vodafone-mobile-connect-3g-ubuntu/#comment-216):

> No sabia ni que es pot actualitzar xD.

Però bé, si tens la Gutsy prova anant a Sistema -> Administració -> Xarxa i allà configura la connexió mòdem així:
- Pestanya General: Habilita la connexió i omple els camps número de telèfon, nom d'usuari i contrasenya (els mateixos que tenies a l'arxiu wvdial.conf).
- Pestanya Mòdem: Port «/dev/ttyUSB0», marcatge per tons i sense volum

Un cop fet això torna a encendre l'ordinador amb el mòdem 3G posa't i si tot va bé se t'hauria de connectar sol (jo és així com ho faig ara, el script ja només el tinc per si algun cop no me l'agafa automàticament, però no sé si l'actualització aquesta també ho espatllarà).

---

### Post by manelolesa on 2007-11-07
Hola RainCT.

He instal.lat la Gutsy i el problema continua igual.

Tan fent la connexió amb script o amb el GnomePPP ( o algo aixi ) continuo igual.
El que he observat es que desde que he fet l'actualizatció de firmware del modem m'apareix com a unitat de CD.
Ja he provat a desmontar.la, etc...

Esta clar que el sistema no veu el modem per que he vist que amb el GnomePPP ( o algo aixi ) em diu que no troba el dispositiu TTYUSB o algo semblant. Si vaig al Administrador de Hardware el modem si que existeix inclus si desmonto el tema del CD.

Existeix alguna comanda de terminal per veure on carai tinc montat el capullo de modem aquest.

Slt i gracies

---

### Post by RainCT on 2007-11-09
És normal que t'apareixi com a CD, a mi també m'hi surt (i no canvia res si el desmontes).

En quant a ho segon, no tinc ni idea de com fer-ho :(.

---

### Post by Kosimo on 2007-11-10
> **manelolesa said:**
> Hola RainCT.

He instal.lat la Gutsy i el problema continua igual.

Tan fent la connexió amb script o amb el GnomePPP ( o algo aixi ) continuo igual.
El que he observat es que desde que he fet l'actualizatció de firmware del modem m'apareix com a unitat de CD.
Ja he provat a desmontar.la, etc...

Esta clar que el sistema no veu el modem per que he vist que amb el GnomePPP ( o algo aixi ) em diu que no troba el dispositiu TTYUSB o algo semblant. Si vaig al Administrador de Hardware el modem si que existeix inclus si desmonto el tema del CD.

Existeix alguna comanda de terminal per veure on carai tinc montat el capullo de modem aquest.

Slt i gracies

Per que no probesde fer un "downgrade" i passar a la versio anterior de firmware?

---

### Post by manelolesa on 2007-11-19
El tema del Downgrade no tinc ni idea de com fer-ho.

Es trist pero per fer anar el modem  tinc que engegar el Windows dels cullons.

Tambe tinc l'opció de fotra-li la wireless al veï, pero em sap greu i poc etic.

A veure si algu m'ajuda.
El modem estic segur que es munta, pero a on ? ni punyetera idea.


Slt

---

