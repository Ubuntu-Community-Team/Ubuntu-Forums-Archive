---
title: "Ubuntu 10.04 no detecta monitor i baixa resolució"
date: 2011-12-26
forum: Catalan Team
---

### Post by tocapelfoc on 2011-12-26
Tinc un monitor Acer Technologies 19''
Model Pantalla: G195HQV LCD Monitor

Si faig *lspci | grep VGA* em surt:

00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)

El problema és la resolució de la pantalla i el fet que  l'***Ubuntu 10.04 lucid*** no em reconeix el monitor. Adjunto un pantallasso perquè  vieu al què em refereixo.

[ATTACH]209725[/ATTACH]

La resolució òptima hauria de ser 1366x768,  però al no detectar la pantalla no em deixa fer-ho... Suposo que hauria  d'instal·lar drivers o alguna cosa semblant, però no he trobat res de  res pels fòrums ubuntaires. Els drivers d'Intel Graphics els tinc instal·lats.

Estic utilitzant Tango Studio amb un Kernel de baixa frequència.

A veure si em podeu ajudar!
Moltes gràcies!

---

### Post by CarlesOriol on 2011-12-26
Que jo sàpiga no hi ha suport del sandy bridge en la 10.04. No pots actualitzar la versió?

(per cert, de baixa "latència")

---

### Post by tocapelfoc on 2011-12-27
Ups, perdona, baixa latència, sí!

Doncs Tango Studio és una distribució basada en Ubuntu 10.04 i desconec si puc actualitzar alguna cosa si la gent de Tango Studio encara no ha tret cap versió nova de la distribució.

De totes maneres, això de Sandy Bridge què és, exactament? No es pot solucionar de cap manera?

Gràcies!

---

### Post by CarlesOriol on 2011-12-28
El sandy bridge és la manera com està parit el processador, que hi porta quins xips de suport li calen i en el cas que et dona problemes la gràfica adjunta.

Jo tinc un portàtil que té un i7 (sandybridge) amb la gràfica adjunta i amb una gràfica nvidia i encara no està perfectament solucionat en les darreres versions del linux com canviar entre una i l'altra. Les dues dibuixen simultaneament a la pantalla. Jo de moment executo els programes amb una eina (optirun64o32) quan vull canya i deixo la resta a la intel.

Vaja... que és un invent força nou. Desconec si està ben solucionat en altres sistemes per que no els uso.

Per tant si pots com a mínim actualitzar el sistema segur que l'ordinador et funcionarà força millor.

---

