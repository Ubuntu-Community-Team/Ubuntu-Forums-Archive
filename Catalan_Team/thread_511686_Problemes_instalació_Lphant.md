---
title: "Problemes instalació Lphant"
date: 2007-07-28
forum: Catalan Team
---

### Post by pserra on 2007-07-28
[FONT="Verdana"][COLOR="Navy"][SIZE="3"]Hola companys, 
soc  bastant novell amb Ubuntu i fa dies que  intento instal·lar una alternativa a Emule,  el Lphant perquè estic tip de tenir sorpreses quan obro l'arxiu que descarrego no es el que posa el nom.....
com que no puc fer-ho des de   synaptic ho faig des de consola però em surten aquests problemes:
[/SIZE][/COLOR][/FONT]
pere@Ubuntu:~$ cd Desktop/
pere@Ubuntu:~/Desktop$ dir
lphant-CmdLine-v3.02.zip_FILES  Mophant20070522
pere@Ubuntu:~/Desktop$ cd lphant-CmdLine-v3.02.zip_FILES/
[email]pere@Ubuntu:~/Desktop/lphant-CmdLine-v3.02.zip[/email]_FILES$ chmod +x [email]LphantCmdLine.exepere@Ubuntu:~/Desktop/lphant-CmdLine-v3.02.zip[/email]_FILES$ ./LphantCmdLine.exe
Starting lphant!

** (./LphantCmdLine.exe:18604): WARNING **: The following assembly referenced from /home/pere/Desktop/lphant-CmdLine-v3.02.zip_FILES/eLePhant.dll could not be loaded:
     Assembly:   System.Runtime.Remoting    (assemblyref_index=2)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/pere/Desktop/lphant-CmdLine-v3.02.zip_FILES).


** (./LphantCmdLine.exe:18604): WARNING **: Could not load file or assembly 'System.Runtime.Remoting, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Runtime.Remoting, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
  at <0x00000> <unknown method>
  at ad.a (System.String[] A_0) [0x00000] 
[email]pere@Ubuntu:~/Desktop/lphant-CmdLine-v3.02.zip[/email]_FILES$ 

[COLOR="Navy"][SIZE="3"][FONT="Verdana"]Algú em podria explicar que faig malament?[/FONT][/SIZE][/COLOR]

---

### Post by papapep on 2007-07-28
I què et garanteix que amb Lphant aquest no et passarà el mateix que amb l'amule?? Com t'assegura el contingut dels fitxers?

---

### Post by patrickfromspain on 2007-07-28
en aquest sentit.. lphant te el mateix problema que l'emule: comparteix la red e2dk... no guanyaras res. 

I encara una cosa mes: lphant per linux, NO te una interfice grafica, sino que es maneja per web.. i no es, ni de lluny, tan estable com l'amule.

salut!

---

### Post by pserra on 2007-07-28
Merci pels vostres consells, però si vull baixar un arxiu  tipus torrent, que feu servir? quin és el millor? jo he probat amb azureus.... però no em surto de com fer que quan des de una pàgina on hi han aquests tipus d'arxius i poso descarregar se'm pasin a azureus......  com funciona això?   crec que els arxius tipus torrents son bastant més fiables en quan a contingut que el amule... es aixi? 
Gràcies.

---

### Post by pserra on 2007-07-28
Ara acabo de llegir l'enllaç del  papaPep, veig que m'haure de documentar millor, per fer les preguntes més 'inteligents'. Disculpeu... soc bastant 'novell' en Ubuntu..
Gracies.

---

### Post by papapep on 2007-07-28
Doncs per a baixar torrents, pots fer servir el **gnome-btdownload**, que t'instal·la com a dependència el **bittorrent**, que és qui realitzarà realment la descàrrega. A mi em va molt bé (tot i que també t'haig de dir que no el faig servir gaire).

Sobre l'enllaç que tinc a la signatura, l'hi has de fer el cas just. No pretèn ser de cap manera una reprimenda. ;-)
És simplement un text històric de la xarxa el qual crec que té un valor pel qual val la pena llegir-lo, com a mínim, un cop.

---

### Post by CarlesOriol on 2007-07-29
> **pserra said:**
> estic tip de tenir sorpreses quan obro l'arxiu que descarrego no es el que posa el nom.....

Quan estas descarregant mira les propietats de l'arxiu - Els noms amb que tothom té aquest arxiu a l'ordinador -, mira també els comentaris. (tot això ho fas amb el butó dret damunt de l'arxiu que estas descarregant).

No et garanteix res... però normalment veus les "troles" abans.

---

### Post by pserra on 2007-07-29
[FONT="Verdana"][SIZE="4"]Merci  CarlesOriol, aquesta opció no l'havia fet servir mai, he vist que sí que em serà util....
Gràcies per el teu ajut.
A reveure[/SIZE][/FONT]

---

