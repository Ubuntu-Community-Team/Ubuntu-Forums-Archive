---
title: "Video ordinador Dell &amp; KDE Kubuntu 14.04"
date: 2014-10-08
forum: Catalan Team
---

### Post by jallapart on 2014-10-08
Com que la meva aposta ha esta finalment per el software lliure a nivell empresarial tots els ordinadors que tinc a la feina els mourem a poc a poc  a Linux. 

He aconseguit instal·lar sense cap problema tres ordinadors tipus torre, però ara al instal·lar en un quart ja tinc la primera de front, l'ordinador fa coses rares amb el vídeo, surt mitja pantalla o senzillament queda del tot blocat sense poder fer res més que apagar. El procés de instal·lació he aconseguit que acabes en un parell d'ocasions, però no puc fer un canvi en la resolució de vídeo, doncs desapareix la barra de navegació i no sembla respondre l'equip. No crec que sigui un problema propi de la maquina doncs fins ara l'havia utilitzat perfectament amb Windows 7.

He pensat que d'alguna manera he de iniciar el sistema per tal de fer un canvi de driver per la placa PCI Express integrada i vaig una mica perdut. Potser aquest problema es típic doncs recordo fa temps els problemes de sempre de les plaques. Aquest ordinador no nou ja té 4 anys i crec que no hauria de tenir cap problema. Els vostres consells seran benvinguts.
Gràcies.

---

### Post by jmaspons on 2014-10-08
Mira si l'aplicació ubuntu-drivers t'ajuda a configurar algun driver propietary que necessites. Si tens accés a l'entorn gràfic prova d'executar Driver manager. Sinó, com sembla que és el cas, ves a la terminal (Ctrl+Alt+F1), obre una sessió amb el teu usuari i executa la comanda *sudo ubuntu-drivers autoinstall*. Si no funciona mira diu *ubuntu-drivers devices*.

Salut!

---

### Post by wgarcia on 2014-10-08
Aniria bé saber quina targeta gràfica té l'ordinador. Per reconfigurar la gràfica pots entrar en mode recuperació, i et surt un menú que et permet reconfigurar la gràfica, això a vegades ho arregla.

---

