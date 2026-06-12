---
title: "Belkin wireless G + ATI"
date: 2007-10-19
forum: Catalan Team
---

### Post by vvinuesaa on 2007-10-19
Hola a tothom,

podriem dir que tot just arribo a Ubuntu. Usuari de Windows per molts anys acabo de instalar Ubuntu 7.10 i sembla que rutlla. O no?
El que vull dir es que tinc access a internet i les coses es veuen prou be a la pantalla pero:
Tinc una tarja inalambrica Belkin wireless G (F5D7010) amb un chipset Atheros i sembla que es conecta a Internet pero em diu que es concecta amb un percentatge que varia entre el 10 i el 35 %.
Tinc una ATI Mobility Radeon 7500 que almenys en el driver de windows deia que tenia una certa capacitat de 3D. Quan he instalat ubuntu es queda per defecte en les opcions d'aparença més bàsiques.
He estat buscant i m'ha semblat trobar el seguent:
- per la tarja Belkin, tot i que he mirata molts llocs inclos:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
no en trec l'aigua clara. esta soportada aquesta tarja "out of the box"? o hauria de instalar ndiswrapper i el driver de windows? Ho pregunto per si el fet que tingui menys de un 35% pot ser degut al driver o com que tinc conexió vol dir que el driver que hi ha funciona i que els problemes de conexió son uns altres.
- per la ATI he buscat a x.org i a mesa. Sembla que ubuntu ja porta mesa instalat així que hauria de instalar el driver DRI de ATI i prou no?. No he fet servir en ma vida el terminal, de fet porto un dia en Linux així que si no em cal preferiria no fer-ho pero per altra banda voldria treure-li el maxim rendiment al meu hard.

En definitiva les preguntes serien:
- Val la pena que m'hi fiqui a instalar drivers, etc o es molt probable que no li tregui més rendiment del que tinc?
- Si es que si en tots dos casos o en algun d'ells, vaig ben encaminat o m'estic fent la pixa un lio?

moltres gracies,

vvinuesaa

---

### Post by jodufi on 2007-10-20
Hola vvinuesaa,

Tristament les targetes ATI són les que ofereixen un pitjor suport per a Linux, ja que tenen un drivers privatius que deixen una mica a desitjar i els lliures són pitjor. Per sort això sembla que canviarà en les properes setmanes / mesos.

La política de l'Ubuntu (i la majoria de distibucions Linux) és distribuir només programari lliure. En el cas de les targetes ATI aquest programari no té suport 3D (la causa és que ATI no dóna les especificacions per a fer-ho). Per sort, pots intentar instal·lar el driver privatiu (que té suport 3D) d'una manera molt fàcil, seleccionant "Sistema -> Administració -> Gestor de controladors restringits" et sortirà la llista de drivers privatius que hauries d'instal·lar al teu sistema (si n'hi ha).

Pel tema de la wireless, no sabria què dir-te, però a mi també m'oscil·la bastant la cobertura. Si tens connexió, jo no ho tocaria.

Salut

---

### Post by vvinuesaa on 2007-10-20
Gracies per la resposta. Ara les coses s’han complicat una mica. He intentat instalar el driver fglrx segons diu a [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
Fent:
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

despres vaig anar a sistema – administracio – pantalles i gràfics – tarja gràfica 
aquí vaig seleccionar per model el fabricant ati i el model radeon (fglrx) i em va demanar reiniciar. Aquí van començar els problemes ja que va dir que no reconeixia la tarja i va entrar fent servir el controlador “vesa – Generis VESA-compliant video cards” i amb una resolucio de pantalla de 640x480 i que no es pot canviar. 

He intentat tornar a la situació inicial (la que hi havia quan vaig instal.lar ubuntu pero no he pogut. Per començar no entenc massa la diferencia entre escollir un controlador pel nom o pel model pero no sembla que sigui la mateixa cosa.
Pel nom he provat:
- ati – ATI Mach8, Mach32, Mach64, and RageXL Cards , que crec que era la configuracio original pero no funciona.
- fglrx
- radeon-ATI Radeon cards, including Radeon Mobility an..
Pel model he provat:
- Radeon (fglrx)

En cap cas he aconseguit millorar la situació ni tornar a la situacio original. He pensat en reinstalar ubuntu pero he vist a Internet que en general es recomana intentar arreglar el problema abans de reiniciar.
Algú sap com instal.lar un controlador per aquesta tarja o almenys com tornar a la situació original?

Gracies,

vvinuesaa

---

### Post by papapep on 2007-10-20
En aquest mateix fòrum hi ha **moltes** referències a la configuració de les targes gràfiques. Fes-hi un cop d'ull, crec que pots trobar una bona base de casos resolts.

---

### Post by vvinuesaa on 2007-10-20
moltes gracies,

hi faré un cop d'ull a veure si m'en surto.

vvinuesaa

---

