---
title: "conceptronic usb-wifi c54ru"
date: 2007-09-05
forum: Catalan Team
---

### Post by pespin on 2007-09-05
Fa algun temps ja vaig intentar instal·lar aquest dispositiu (versió 3c22) al portatil-carraca pero no tenia ni idea del que feia i ho vaig acabar deixant.

M'hi he tornat a posar, instal·lant els ultims drivers serialmonkey: ([http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com"))

els controladors que toquen per al meu dispositiu son els rt73.

Tot funciona bé; cap problema per veure les rets o connectar-me.... fins que tot es penja. Aquest es el problema, no aguanto mes de 10 minuts amb el dispositiu funcionant que se'm queda tot l'ordinador penjat, sense poder fer res.

Normalment les pillades aquestes es solen produir al obrir una connexió com per exemple connectar-me al IRC, entrar amb el navegador a les pagines.

Doncs això era mes aviat per si algú li havia passat alguna cosa semblant, si algú te alguna idea de com solucionar-ho o té alguna proposició indecent :).

Si ningú té cap solució provaré amb el ndiswrapper, tot i que no m'acaba de convèncer la idea. Em recomaneu aquesta opció?

El Gutsy incorpora ja el kernel 2.6.22? si cap de les anteriors funciona també puc esperar a fer servir la noca generació de controladors (2x00) que requereixen mínim aquesta versió del nucli.

Per si algu no sap ven bé de que va el tema:
[http://www.carlosatares.com/2007/06/15/conceptronic-c54ru-en-ubuntu-fesity]("http://www.carlosatares.com/2007/06/15/conceptronic-c54ru-en-ubuntu-fesity")
He provat aquest howto i també les instruccions del manual dels controladors.

portatil carraca:
Ubuntu 7.04 (2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux)
Intel Celeron 1Gh 128Kb caché
108 Mb RAM

PD: També he provat d'instal·lar el controlador 2570 tot i que aquest es per una altra versió del dispositiu. Resultat: igual que el rt73.

---

### Post by patrickfromspain on 2007-09-08
ei! probar ndiswrapper es una solucio?

---

### Post by papapep on 2007-09-08
Pespin, a tots els articles que trobo a internet al respecte d'Ubuntu i el c54ru parlen de que a partir de Dapper ja porta suport "de fàbrica" pel xip del teu dispositiu. Igual estàs fent feina en va :-)

---

### Post by pespin on 2007-09-08
Pel que he llegit el controlador que porta per a la targeta està en fase beta i no acaba de funcionar. Em sembla que detecta la targeta però no deixa connectar-se a cap xarxa.

Provaré amb el ndiswrapper a veure que tal.

En lo referent a la branca del nucli utilitzada pel Gutsy algú en te cap idea? es la 2.2.X?

---

