---
title: "Problema amb una impresora i un microfon"
date: 2010-10-24
forum: Catalan Team
---

### Post by Pimi on 2010-10-24
Hola
Acabo de començar a utilitzar Ubuntu, he instalat al meu netbook la versió Ubuntu 10.10 netbook, i tinc dos problemes: no em funciona el micròfon i no puc utilitzar la meva impresora.

Primer problema: al intentar parlar per l'Skype vaig veure que no em funcionava el micròfon. He intentat pujar el volum d'entrada anant a preferències de so, entrada, i pujant el volum, però no funciona. A més, al obrir la aplicació "enregistrador de so" i provant a veure si grava o no alguna cosa, només se sent un soroll agut. 

Segon problema: vaig a impressores, afegeixo una impressora nova, i Ubuntu em detecta la meva impressora (una HP Deskjet 3050) per Wi-Fi, clico endavant i em demana que esculli el controlador en una llista predeterminada, i aquí la meva impressora no apareix. També he intentat que per internet em busqui el controlador, però la cerca no dóna cap resultat. 

En resum, que estaria interessat en possibles solucions a aquests problemes.
Gràcies

---

### Post by kukat on 2010-10-26
Hola i benvingut!!!!

Et recomane que llisques primer les [Normes del Fòrum]("http://ubuntuforums.org/showthread.php?t=599965") i també que et presentes al nostre [Fil de Benvinguda]("http://ubuntuforums.org/showthread.php?t=562776"). 

Obrim sempre un fil per a cada problema! hehehe 

Bé, comencem per la webcam i l'Skype:

Ací tens una llista de Webcams i si funcionen o no a GNU/Linux:

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Si no funciona "del tot" hi ha diverses solucions que també els explica molt bé! 

Salut! 

PD: Skype fa temps que no actualitza la versió per a GNU/Linux i passen un poc de nosaltres, la veritat. 
[En aquest enllaç]("http://ubuntuforums.org/showthread.php?t=1595621") hi ha un problema semblant al teu recent. Igual t'interessa veure'l.

---

### Post by wgarcia on 2010-10-26
Per al micròfon seria convenient que indiquessis quin model d'ordinador fas servir i quina targeta d'àudio. Per a veure la targeta d'àudio pots donar la instrucció següent des d'una terminal:

lspci | grep audio

Quant a la impressora, has instal·lat "hplip"?

En cas contrari des d'una terminal instal·la:

sudo apt-get install hplip

I mira si ara pots configurar la impressora.

---

### Post by Pimi on 2010-10-28
Primer de tot gràcies per intentar resoldrem els problemes i sento haver tardat en contestar, però estava enfeinat.

Un cop dit això, vaig comprovar, com m'havia dit en wgarcia si tenia instal·lat el "hplip", si que el tenia ja instal·lat, i per tant no he pogut configurar encara l'impressora. 

Pel tema de l'audio i el microfon, doncs he provat de posar en la terminal perveure la targeta d'audio el que m'havieu dit:

lspci | grep audio

però no em diu ni em fa res...però puc aportar el model d'ordinador, és un Acer Aspire One 532h-2Br. De la targeta de so, doncs no en tinc ni idea XD

Apart d'això he tingut problemes instal·lant algunes aplicacions des del Centre de programari de l'Ubuntu, i també al instal·lar-ne des d'altres llocs, ja que al instal·lar-les em surt el missatge de "Aquesta acció requereix la instal·lació de paquets de fonts no autenticades." i no me les instal·la. 

A veure si a algú se li acudeix com puc intentar solucionar aquests problemes
Gràcies.

---

### Post by wgarcia on 2010-10-30
Doncs per acabar de veure quina targeta de so tens entra 

lspci 

sense l'altra part que t'havia suggerit, això ensenyarà tots els dispositius pci i hauria de sortir la targeta de so.

---

### Post by Pimi on 2010-10-31
[LEFT]Si, ara si que funciona.
[COLOR=Gray]
[/COLOR][SIZE=1][COLOR=Gray]00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
[/COLOR][/SIZE][SIZE=2][COLOR=Black]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)[/COLOR][/SIZE][SIZE=1][COLOR=Gray]
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)[/COLOR][/SIZE]

Diria que la targeta de so és el que destacat
[/LEFT]

---

### Post by wgarcia on 2010-11-01
Per la impressora millor obre un altre fil, i posa un resum del que ja has esbrinat allà, per continuar en fils separats els dos temes, sinó és un embolic. 

Per a l'àudio un parell de proves ximples abans de provar coses més complicades. Sembla que el problema ha de ser algun tema simple, perquè la targeta de so és coneguda i no sol donar cap mena de problema. 

1) Obre una terminal (Aplicacions -> Terminal), i entra aquí 
alsamixer
Mira a la columna que posa "Master" que a sota posi "OO" i no "MM". Si posa "MM" prem "m" per canviar-lo a "00". També assegura't que els volums estiguin donats (els pots incrementar amb la tecla de fletxa cap a dalt). 
Per sortir prem la tecla "Esc".

2)Ves al menú Sistema -> Administració -> Usuaris i grups. Clica sobre el teu usuari. Després clica sobre "Configuracions avançades". Escull la pestanya "Privilegis d'usuari", i aquí marca "Dispositius de so" si no està marcat.

---

### Post by Pimi on 2010-11-07
Hola de nou.

Al final vaig desinstal·lar l'Ubuntu 10.10 netbook edition i em vaig instalar l'Ubuntu 10.10 desktop edition. Amb això he aconseguit que el micròfon em funcioni quan faig servir l'enregistrador de veu, però quan utilitzo L'Skype continua sense funcionar... Alguna idea de com puc solucionar-ho?? 

Gràcies

---

