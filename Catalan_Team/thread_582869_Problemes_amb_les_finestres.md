---
title: "Problemes amb les finestres"
date: 2007-10-20
forum: Catalan Team
---

### Post by nickpage on 2007-10-20
Hola companys,

ahir al vespre vaig fer una instal·lació neta de la nova versió d'Ubuntu, la Gutsy. La instal·lació va anar força be.

El primer pas que vaig fer va ser habilitar els controladors restringits per la meva targeta gràfica, que es una ATI Radeon 9550 i va anar ok.

Just després d'instal·lar les aplicacions que faig servir normalment vaig habilitar els efectes d'escriptori que també van funcionar després de instal·lar xserver-xgl.

Per últim vaig instal·larr Emerald  via Synaptic i aquí van començar els problemes.

En primer lloc el gestor de Emerald no baixa cap tema del servidor... i avui matí quan he tornat a engegar el PC no m'apareixen els bordes de les finestres... a més a més ja no disposo d'acceleració gràfica.

Agrairé qualsevol ajuda... gràcies

---

### Post by manelolesa on 2007-10-20
A mi m'ha passat el mateix, tinc una NVIDIA i al habilitar el modul restringit també he perdut les vores de les finestres.

De moment he inhabilitat el modul.

slt

---

### Post by nickpage on 2007-10-20
Efectivament, si desinstalo els drivers restringits torno a tenir els bordes, ara be, també deixo de veure els efectes.

---

### Post by jodufi on 2007-10-20
No entenc perquè vas instal·lar el xserver-xgl o el emerald. No et funcionaven els efectes 3D?

Si desactives els efectes 3D segurament tornaran els bordes, però et quedaràs sense efectes.

Jo provaria de desinstalar l'emerald...

---

### Post by nickpage on 2007-10-20
Per tenir els efectes vaig tenir que instalar el xserver-xgl.

He provat de desinstalar l'emerald i continuo amb els mateixos problemes de no veure els bordes de les finestres.

---

### Post by nickpage on 2007-10-20
Be companys,

he reinstalat tot, he activat els controladors restringits de l'ATI i instal·lat el xserver-xgl... amb això he aconseguit que funcioni el compiz-fusion prou be.

Ara el meu dubte és instalar l'emerald o no, que me recomaneu????

---

### Post by papapep on 2007-10-20
Jo crec que no et cal per a res l'Emerald. Feia falta abans pel Beryl, però pel CompizFusion no.

---

### Post by nickpage on 2007-10-21
La veritat es que l'emerald me dona igual, el que vull es canviar l'aspecte de les finestres i altres, el que passa es que tot el que trob al gnome-look no m'acaba de funcionar.

Per cert, algú ha provat d'instal·lar els screenlets i l'avant window manager al gutsy, perquè jo no m'ensurto.

---

### Post by trinkus on 2007-10-21
A mi em va passar el mateix amb un portatil i vaig premer F11 (potser dos cops) i ja apareixen els bordes... prova-ho!

---

### Post by CarlesOriol on 2007-10-21
> **trinkus said:**
> A mi em va passar el mateix amb un portatil i vaig premer F11 (potser dos cops) i ja apareixen els bordes... prova-ho!

Aquest missatge ve de la dimensió desconeguda. :confused:

---

### Post by nickpage on 2007-10-21
Doncs tens l'emerald instal·lat???

Et carreguen el temes que hi ha als repositoris???

---

### Post by jaume69 on 2007-10-21
Si vols instal.lar AWN et diria la web on ho vaig trovar però no ho recordo...

Fes a consola:
sudo gedit /etc/apt/sources.list
Afegeix:
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
La Clau:
wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get upgrade

A repositoris o des de consola:sudo apt-get install
avant-window-navigator-bzr
awn-core-applets-bzr

(Només Gutsy)
______________________________________

Sobre el emerald-themes jo el tinc instal.lat a Gutsy però ara tampoc recordo com ho vaig fer.
Si no fos que els temes de Metacity no van tan bé com un voldria,no instal.laria Emerald però ja et dic que amb Metacity la barra superior em queda de color blanc depèn de com...,i si passes el cursor pel cim torna al seu color.
Recordo que ja ho feia amb Feisty i no sé si te sol.lució.

El que jo tampoc tinc és poder configurar per treure o canviar Emerald per Metacity o sigui que vaig sempre amb Emerald,o desinstal.lar-lo.

No sé..

---

### Post by nickpage on 2007-10-21
Gràcies per la resposta,

el tema es que si instal·lo l'emerald sembla que no me carregui cap tema... només l'he pogut fer funcionar un cop i me posava la barra de titol de la finestra en vermell...

---

### Post by jodufi on 2007-10-21
Per a utilitzar l'avant sembla que hi ha problemes amb el Gusty, però pots provar el que et recomana aquesta pàgina:

[http://www.linuxhispano.net//index.php?option=com_content&task=view&id=533&Itemid=9](http://www.linuxhispano.net//index.php?option=com_content&task=view&id=533&Itemid=9)

---

### Post by trinkus on 2007-10-22
POtser si que ve de lluny pero va funcionar... de veritat!!! Un colega passava per alla (sap alguna cosa de linux) i va dir prova F11 i va funcionar... altrament... digue'm mentider company!!! jeje

---

### Post by jaume69 on 2007-10-22
[QUOTE="nickpage"] Gràcies per la resposta,
el tema es que si instal·lo l'emerald sembla que no me carregui cap tema... només l'he pogut fer funcionar un cop i me posava la barra de titol de la finestra en vermell... [/QUOTE]
Hola,si encara no tens els temes Emerald,prova això:
1-Instal.la el programa** Subversion**,--synaptic o apt-get.
2-Posa a la consola(sense sudo):svn ls [https://svn.generation.no/emerald-themes](https://svn.generation.no/emerald-themes)
3-Ves a Emerald i Ajustes temas,Repositorios,prem els dos repositoris que hi ha perquè es carregin.

Adéu.

---

