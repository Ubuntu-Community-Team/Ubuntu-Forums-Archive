---
title: "Diferencies de tenir WinXP a la màquina virtual o compartint instal·lació"
date: 2011-09-21
forum: Catalan Team
---

### Post by Pelacanyes on 2011-09-21
Bona tarda a tothom:
Doncs, com diu el títol, voldria saber quina diferencia hi ha entre les dues possibilitats.
He de tornar a fer tota la instal·lació d'Ubuntu i, aprofitant l'avinantessa, podria fer també la instalació de guindous.
Ja se que em direu que no es necesari però tinc un programa que només funciona així (vaig probar amb wine i similars i no funcionaba). Pel que vaig veure amb la màquina virtual, s'ha de fer la instal·lació com si ho fessis en una partició i d'aquí que no hi veig la diferencia de fer-ho d'una manera o de l'altre.
Gracies per endavant pel vostre ajut.
Salutacions des de Tarraco

Pelacanyes

---

### Post by wgarcia on 2011-09-21
Un parell de diferències que se m'acuden:

1) potser no tot funcioni de la manera que el SO privatiu està instal·lat en la seva pròpia partició, però si et funciona el que necessites això no és un problema

2) és millor tenir-lo en virtualbox perquè pots simultanejar programes de Linux i córrer el programa privatiu que necessites, sense haver de sortir de Linux.

---

### Post by Pelacanyes on 2011-09-22
Bon dia a tothom:
Potser es que no ha vaig fer be, però amb el virtualbox només veia güindous. Sabeu d'algun tutorial/manual per fer anar virtualbox?
De nou moltes gracies pel vostre ajut.
Salut
 
Pelacanyes

---

### Post by wgarcia on 2011-09-22
No entenc el teu dubte. El "virtualbox" és un programa que fa una "màquina virtual", és a dir que dins un sistema operatiu qualsevol simula un ordinador on pots instal·lar un altre sistema operatiu i "pensarà" que està en una màquina amb els seus discos, pantalla, memòria, etc. 

El cas que comentem aquí és tenir Ubuntu, instal·lar virtualbox, i dins de virtualbox instal·lar per exemple Windows, sempre que tinguis una llicència perquè aquest sistema com tots sabem requerix comprar-se una llicència. 

També es podria fer a l'inrevès, instal·lar el virtualbox a Windows i dins d'aquest virtualbox instal·lar, per exemple, Ubuntu o qualsevol altra distribució de Linux.

---

### Post by Pelacanyes on 2011-09-22
Hola de nou
Quan deia > Potser es que no ha vaig fer be, però amb el virtualbox només veia güindous Em referia a que virtualbox omplia tota la finestra i perdia de vista l'Ubuntu. El meu dubte venia precisament per això, si habia de deixar ubuntu per poder veure güindous no hi veia diferencia entre les dues opcions.
Obviament tenia instalat el virtualbox dins Ubuntu, i el güindous estaba instalat dins el virtualbox.
Pel que estic veient, pels teus comentaris, alguna cosa debia fer malament quan vaig instalar virtualbox així que tindrè que mirar be com funciona per treure-li el màxim partit.
Gracies de nou.
Salut
 
Pelacanyes

---

### Post by wgarcia on 2011-09-22
La finestra de virtualbox és com qualsevol altra finestra, pot estar a pantalla completa o no. Tot i que normalment s'utilitza a pantalla completa perquè està simulant tot un escriptori...

Però aquí també pots jugar amb els escriptoris, posar per exemple el virtualbox en el segon escriptori i tenir tota la resta de finestres en el primer, tot i que encara sols podràs veure una pantalla a l'hora.

Però sí que s'entén el que dius, la diferència continua sent que tens totes les aplicacions linux que vulguis obertes i pots accedir ràpidament, mentre que si estàs executant un altre sistema operatiu a través de doble arrencada hauràs de sortir d'un per accedir l'altre, cosa que és molt més lent.

---

### Post by oriolsbd on 2011-09-22
A la documentació de GNULinux.cat hi tens tot un apart dedicat a VirtualBox:
[http://www.gnulinux.cat/documentacio/maquines-virtuals-amb-virtualbox/](http://www.gnulinux.cat/documentacio/maquines-virtuals-amb-virtualbox/)

Salut!

---

### Post by Pelacanyes on 2011-09-25
Hola a tothom:
Moltes gracies pels vostres consells i, com no podia ser d'una altra manera, ja he instal·lat el virtualbox i dintre d'aquest el WinXP.
Ara el problema es que no puc activar-lo des de la maquina virtual. Sembla com si falles la connexió a internet. Alguna idea del que pot estar passant?
Gracies de nou per tota l'ajuda que m'esteu donant.
Salut

Pelacanyes

---

### Post by wgarcia on 2011-09-26
Tens Internet per a altres coses? Com per exemple per obrir des del navegador alguna pàgina web que coneguis?

---

### Post by Pelacanyes on 2011-09-26
Bon dia Catalunya:
Doncs si, tinc connexió a internet. Des de la màquina virtual puc connectar-me amb el firefox i navegar, el que no entenc es que quan intento activar el winxp sembla que es quedi penjat i no s'estableixi la connexió.
Salut
 
Pelacanyes

---

### Post by wgarcia on 2011-09-26
Doncs ves-te a saber, potser detecta que s'està activant des d'una màquina virtual i tot i que has pagat la llicència no et deixat validar la teva pròpia propietat... Si vols portar-lo al jutjat, segur que perds perquè en algun lloc de la llicència amb lletra petita posarà que poden fer aquestes coses.

---

### Post by Pelacanyes on 2011-09-26
Per fi ho he pogut fer!!!! No se si ha estat casualitat o era on m'equivocava, la qüestió es que després de diversos intents he fet ometre en el pas on demana els paràmetres de connexió (detecció automàtica o posar el proxi) i desprès de comprovar la connectivitat m'ha confirmat l'activació.
Be, ara aniré provant els programes amb els que tinc que fer servir güindous per uef.
De fet estic molt satisfet de tot el que he aconseguit amb el vostre ajut, no se que hagués fet de no poder unificar tota la feina en un sol ordinador.
MOLTES GRACIES A TOTS!!!!
Salut

Pelacanyes

---

