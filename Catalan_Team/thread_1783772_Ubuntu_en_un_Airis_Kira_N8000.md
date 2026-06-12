---
title: "Ubuntu en un Airis Kira N8000?"
date: 2011-06-16
forum: Catalan Team
---

### Post by lavinia.gac on 2011-06-16
Amb la promoció de La Vanguardia he adquirit aquest netbook que porta com a SO l'Android 2.2. Disposa de 512 MB de RAM i una capacitat d'emmagatzematge de 4GB en targeta nanflash. El processador és un ARM 11 d'1GHz. Disposa de 3 ports USB i un lector de targetes SD.
L'Android 2.2 i les aplicacions que venen de sèrie en el netbook no m'acaben d'agradar: no és multiusuari, el navegador és bastant dolent, no disposa d'una suite ofimàtica com OO (sol inccorpora ThinkFreeOfficce que amb prou feines et permet visualitzar documents de MS-Office), el maneig és poc àgil, etc. Per tot plegat voldria instal-lar Ubuntu.
Atès que l'arquitectura no és i386-intel, algú em podria dir si hi ha cap versió d'Ubuntu per a xips ARM? En cas afirmatiu, com podria instal-lar-la?
Moltes gràcies ubuntaires.

PD: el netbook no arrenca des dels ports USB i les actualitzacions, segons el fabricant, es fan des del lector SD.

---

### Post by kukat on 2011-06-20
al segon resultat de Google expliquen una mica com fer-ho, tot i que jo no ho he provat: 

[http://lmgtfy.com/?q=ubuntu%20arm](http://lmgtfy.com/?q=ubuntu%20arm)

;)

---

### Post by lavinia.gac on 2011-06-20
Gràcies per l'enllaç però sóc d'aquells que ho vol tot ja mastegat i llest per pair :-)

Pensava que algú ja s'havia trobat amb el mateix problema en un netbook de similars característiques i em podria ajudar en el procés d'instal-lar la iso en una targeta SD o en un pendrive USB.

De fet, ja ho he intentat des del pendrive amb una iso i386 per a 32 bits de la 10.04 però no ho he aconseguit (no arrenca des de l'USB en el Kira mentre si que ho fa des d'altres pc's perquè he suposat que la plataforma no li escau).

Gràcies i salut!

PD: l'enllaç ja l'havia consultat però el meu anglès és molt dolent i buscava alguna ànima caritativa pròxima língüísticament parlant i que ja ho hagués provat.

---

### Post by kukat on 2011-06-21
ostres, em sap greu. Sense voler ja llegeixo anglès indiferentment...xD 

No puc traduir-ho tot, però bàsicament gravar una imatge del Maverick a una targeta SD de 4GB mitjançant aquesta comanda: 

sudo dd bs=4M if=ubuntu-netbook-10.10-preinstalled-netbook-armel+<omap image>.img of=/dev/<device name> 

Espera que la comanda et torne: sync   per assegurar que es passen totes les dades. 


Després engegues des de la targeta SD. T'Explica diferents mètodes de fer-ho si no pots de la forma tradicional. No se amb aquest com anirà, però tot es provar!



;)

---

### Post by lavinia.gac on 2011-06-21
Gràcies. Ho provaré amb la comanda i la Maverick per a ARM. 

No obstant, ¿creus que podria servir també l'eina gràfica de creació de pendrives arrencables amb la mateixa imatge i una taja SD? Ho he de provar.

I tot aquest percal perquè sembla que aquests netbooks no puguin bootar des dels USB. No? Podria fer-se que arrenquessin entrant en la BIOS com en un PC?

---

### Post by kukat on 2011-06-21
no he vist l'eina gràfica, però si et dona com a opció una targeta SD, es perfectament valid! ja que el programa utilitzarà aquesta aplicació de LInux anomenada "dd". 
Prova-ho amb l'aplicació gràfica, que serà més fàcil. 

Clar, si les actualitzacions es fan mitjançant una targeta SD, supose que a la BIOS li pots indicar que arranque de la targeta SD, si no està ja posat per defecte!! 

Recorda que és aquesta imatge la que tens que gravar:
[http://cdimage.ubuntu.com/ubuntu-netbook/ports/releases/10.10/release/ubuntu-netbook-10.10-preinstalled-netbook-armel+omap.img.gz](http://cdimage.ubuntu.com/ubuntu-netbook/ports/releases/10.10/release/ubuntu-netbook-10.10-preinstalled-netbook-armel+omap.img.gz)

I que la comanda d'abans, quan posa: 

if="ruta/a/la/imatge" of="ruta/a/la/targeta/SD". 

Eixes dues parts són prou importants! ;) 

Salut

---

### Post by lavinia.gac on 2011-06-22
Ho provaré i ja us contaré del meu èxit o fracàs.

Moltes gràcies.

---

### Post by monhtruo on 2011-06-27
Ei! hola
Ho has pogut provar? i què tal?
Ahir se'm va presentar la meva germana també amb aquest Notebook de la vanguardia que li posés l'openoffice i el iTunes i em sembla que va una mica equivocada.....

---

### Post by dmele97 on 2012-06-13
Ja fa temps que es va publicar aquesta entrada, però aqui ve la sol.lució:
	
	Aquest neetbook funciona de manera un tant singular, no disposa de BIOS, sinò que té capacitat d'arrancar des d'una SD (u-boot)

No hi ha Ubuntu disponible (de moment) però si Debian, que en esència ve a ser gairebé el mateix. És una distro live perquè instalarla al HD suposa el risc de fer un brick al terminal.
Per a descarregar-la vés a [www.geekconsolas.com](www.geekconsolas.com) , la página del desenvolupador.
La he provat jo mateix, i té un rendiment força acceptable.
espero haver sigut d'utilitat.

---

