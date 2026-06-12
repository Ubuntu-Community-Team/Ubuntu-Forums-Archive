---
title: "Problema wifi 10.10"
date: 2010-12-28
forum: Catalan Team
---

### Post by gilcent on 2010-12-28
Hola,

Fa dies que estic provant l'ubuntu 10.10. Tot funciona correctament excepte que no em deixa connectar amb wifi. Surt l'icona, em detecta les xarxes sense fil, hi clico, fa l'intent,  però no m'hi connecta. Dubto d'instal.lar-lo ja que no sé si podré connectar-me, crec recordar que cal tenir connexió internet per instal.lar alguns paquets i jo només tinc connexió a través del wifi ja que per cable se'm va espatllar. Sabeu com ho puc resoldre?

fins aviat

---

### Post by wgarcia on 2010-12-29
Potser el primer que convindria és identificar la teva targeta WIFI. Si detecta xarxes ja tens molt guanyat, perquè vol dir que el sistema el detecta. Però per veure per què no és capaç de connectar-se convindria saber de quin tipus és. Per això obre una terminal al menú "Accessoris -> Terminal" i entre 

lspci

això permetrà veure quin tipus de targeta i amb quin chipset hi ha al teu ordinador.

---

### Post by gilcent on 2010-12-29
Hola Wgarcia,

He fet el que em deies i em surt això:

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:08.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

Cal que sàpigues que ara tinc instal.lat l'ubuntu 9.10 i el wifi em funciona correctament. Només no em funciona quan provo el live CD 10.10

Salut

---

### Post by wgarcia on 2010-12-29
Això ho has fet des del Live CD? Jo diria que el sistema no veu la targeta wifi, tot i que és estrany perquè dius que sí que veu les xarxes sense fil però no es connecta. 

Pots fer el mateix des de la versió que tens instal·lada a veure si surt el mateix?

---

### Post by gilcent on 2010-12-29
Hola de nou wgarcia,

El que t'he enganxat abans és el que em surt al terminal de la versió 9.10 que és la que tinc instal.lada. El que t'enganxo ara és el que em surt a la versió 10.10 del live CD;

  	 	 	 	 	 	  To run a command as administrator (user "root"), use "sudo <command>".  
 See "man sudo_root" for details.  
 

 ubuntu@ubuntu:~$ lspci  
 00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller  
 00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)  
 00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)  
 00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller  
 00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller  
 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]  
 00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)  
 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)  
 00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)  
 00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller  
 00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)  
 00:08.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller  
 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)  
 

 Un cop estic a l'escriptori del live Cd del 10.10, clico damunt la icona de les xarxes i m'anomena les dues xarxes sense fil que tinc vora de casa. clico damunt d'una d'elles, fa com que es vol connectar i em surt un signe d'exclamació en vermell. En l'altre em demana una contrasenya, la hi poso i tampoc em connecta. Tinc un adaptador wireless DLINK DWL-G122.

---

### Post by wgarcia on 2010-12-30
D'acord, ara veig perquè el teu adaptador WIFI no surt amb "lspci". És perquè és un adaptador USB.

Una altra cosa que he vist és que l'adaptador DLINK DWL-G122 no funciona amb les versions 2.35 del nucli. Sí funciona amb la versió 2.32 que també s'instal·la si actualitzes a Ubuntu 10.10 (és la segona línia que surt al grub). 

Així que si vols utilitzar ho podries fer, però hauries de començar des de la segona línia del grub en comptes de la primera. 

Potser et convé esperar un parell de mesos i veure si surt una actualització del nucli 2.35 amb la qual el DLINK DWL-G122 funcioni, o de moment actualitzar a 10.04 que és una versió de suport de llarg termini.

---

### Post by gilcent on 2010-12-30
Crec que de moment provaré d'actualitzar amb la 10.04 si em funciona ja m'estarà bé.
Merci pertot
Bon any

---

### Post by pezbaloo on 2011-01-07
Hola Glicent:

Jo vaig instal·lar xubuntu 10.04 amb un adaptador wifi usb i vaig tenir molts problemes amb la conexió. Finalment em va funcionar instal·lant uns paquets anomenats ndiswrapper. Aquest programa em va permetre adaptar els drivers de windows XP del meu adaptador wifi, i ara em funciona correctament.
No se si és la teva solució, pero he pensat que aquesta informacio et podria ser útil.
salut!

---

### Post by wgarcia on 2011-01-07
Això també és una bona idea, quan no hi ha controladors (mòduls en terminologia Linux) disponibles per a un maquinari, perquè l'empresa que els produeix sols dóna controladors de codi tancat i per a Windows (o per a Windows i Mac però no per a Linux), el programa "ndiswrapper" permet usar aquests controladors de codi tancat per fer córrer el maquinari a Linux. 

Això és una cosa que no he entès mai, perquè una empresa productora de maquinari pot estar interessada en mantenir en codi tancat els controladors del seus productes. Potser obrir el codi doni informació sobre les especificacions del seu maquinari i això li faci perdre la propietat intel·lectual, però molt cops es tracta de productes clonats i perfectament coneguts. Obrint el codi pots fer el teu producte accessible a més clients, i tot i que els usuaris de Linux de moment no sóm un mercat massa atractiu comparat amb el mercat dels usuari captius a Windows o MacOS, està més que demostrat que també es pot fer negoci amb nosaltres.

---

### Post by pezbaloo on 2011-01-07
wgarcia, completament d'acord. De fet, he instalat ndiswrapper i en veure que funciona bé, lo primer que he fet és enviar emails a la empresa que fabrica el meu adaptador wifi exigint uns 'drivers' per linux que funcionin bé. Animo a tothom que estigui en una situació similar a que faci aixó, per tal de que els fabricants s'adonin de que és necessari pensar en els usuaris de linux, no podem romandre invisibles.
salut!!

---

### Post by gilcent on 2011-01-10
Hola wgarcia i pezbaloo,
Disculpeu, feia dies que no entrava al fòrum i no m'he n'he adonat que el fil continuava. Vaig instal.lar el Lucid Linx i em va molt bé, no tinc problemes amb la connexió wifi, per tant no m'ha calgut instal.lar l'ndiswrapper. Tanmateix en prenc bona nota per a les properes ocasions. M'apunto a enviar el mail a l'empresa d-link.
Fins aviat!

---

