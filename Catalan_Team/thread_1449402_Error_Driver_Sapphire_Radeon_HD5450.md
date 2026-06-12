---
title: "Error Driver Sapphire Radeon HD5450"
date: 2010-04-07
forum: Catalan Team
---

### Post by birdofparadise on 2010-04-07
Hola, el problema que tinc és el següent. Un cop instal·lat l'Ubuntu en el meu ordinador la ressolució de la pantalla és de 640x480 i no em dóna cap alternativa.

Des del Centre de programari he instal·lat l'*ATI Catalyst Control Center*. L'executo i em diu que no tinc cap tarja ATI al sistema.

Executo l'arxiu *ati-driver-installer-10-3-x86.x86_64.run* i em surt un error que diu : **ERROR: vcdk is missing. Installation aborted.**

El menú controlador de maquinari em diu que no tinc controladors de propietat.

Sóc usuari novell i encara no domino el sistema linux. Ara mateix no sé què he de fer per poder configurar la tarja gràfica.
[I][FONT=Arial]
El meu ordinador té una placa Intel P7 P55M amb processador i5 750 i tarja gràfica Sapphire Radeon HD5450 1 GB DDR3 HDMI. He instal·lat l'Ubuntu 9.10[/FONT][/I]

Si algú em pot guiar li estaré molt agraït

Moltes gràcies

---

### Post by wgarcia on 2010-04-08
Sembla que estàs intentant instal·lar el driver per 64 bits. El teu ubuntu és de 64 bits?

Per veure-ho obre un "terminal", entra la següent instrucció:
uname -m

i després indica què et diu el sistema. Si et diu "i686" és de 32 bits, i si et diu "x86_64" és de 64 bits.

---

### Post by birdofparadise on 2010-04-08
Hola wgarcia, doncs sí vaig instalar el de 64 bits perquè la màquina és nova i vaig pensar que valia la pena per "lo" que havia llegit per la xarxa.

em diu "x86_64"

Potser la versió beta 10.04 aniria millor?

---

### Post by wgarcia on 2010-04-08
Home, si no tens massa experiència, no sé si et convé començar amb una versió beta. Allò del 64 bits t'ho preguntava perquè no fos que t'haguessis baixat una versió incorrecta. 

Una cosa que pots provar és, des d'una terminal, donar la següent comanda:

dpkg-reconfigure xserver-xorg

i tornar a provar d'executar l'arxiu ".run" que t'has baixat. Això et netejarà els arxius de configuració del sistema gràfic X on potser tinguis alguna cosa desconfigurada d'altres proves que hagis fet.

---

### Post by birdofparadise on 2010-04-08
Quan arribi a casa faré neteja tal i com m'exliques... Veient que d'aquí a 3 setmanes arriba el nou Ubuntu, potser serà millor esperar-me. A veure si la nova versió m'aporta facilitats per configurar la tarja de manera senzilla.

Moltes gràcies

---

