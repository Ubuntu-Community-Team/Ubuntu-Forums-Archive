---
title: "emissores radio per internet"
date: 2009-10-29
forum: Catalan Team
---

### Post by mggg on 2009-10-29
hola,

no aconsegueixo escoltar els arxius d'àudio guardats en la web d'una emissora de ràdio (concretament Catalunya Radio). Se m'obre una finestra emergent del Mozilla, però es queda penjat, sense carregar-se del tot. 

Les emissions en directe si que les he aconseguit escoltar, a través de links com aquest: [http://www.catradio.cat/directes/catradio_wm.m3u,]("http://www.catradio.cat/directes/catradio_wm.m3u")

però no els arxius amb links semblants a aquest [http://www.catradio.cat/reproductor/audio.htm?ID=385783](http://www.catradio.cat/reproductor/audio.htm?ID=385783)

em falta algun component del mozilla per instal·lar?

gràcies

---

### Post by jdk9 on 2009-10-29
Aixó és degut a que et falta el paquet ubuntu-restricted-extras. A l'altre post que has creat t'ho he respost ;)

---

### Post by mggg on 2009-10-30
he instal·lat el restricted extras, però segueix sense funcionar. Amb el youtube he aconseguit reproduir el primer video (encara que bastant lent), però els següents ja no es poden reproduir.

En en cas de les emissores per internet, segueix igual: s'obre un mozilla però no es reprodueix, la nova pantalla queda d'un color més pàlid, com si no s'acabés d'obrir.

---

### Post by jdk9 on 2009-10-30
Mmm val, d'acord. Prova instal·lant (anant al Centre de Programari de l'Ubuntu si uses la 9.10 (Quina uses? Ubuntu 9.10? Kubuntu?)) i hi instal·les: Connector flash d'adobe i Extensió flashblock per al firefox. Et tindria que anar bé, sinó els meus coneixements d'ubuntu no arriben gaire més enllà...

---

### Post by mggg on 2009-11-01
doncs si, sembla que el problema està en que em falta instal·lar el flash adobe, però quan intento instal·lar-lo em dona aquest missatge: "Adobe Flash Plugin 10 no es pot insta&#320;lar al vostre tipus d'ordinador (amd64). Pot ser que l'aplicació requereixi maquinari especial o bé el proveïdor ha decidit no oferir compatibilitat amb el vostre tipus d'ordinador."
Em diu el mateix si intent instal·lar-lo des de aplicacions de tercers

---

### Post by rroca1 on 2009-11-29
Prova una eina que funcioni fora del navegador. Et recomano  Rhytmbox que et permet configurar tot el que vulguis des de potcasts, emissores, ... Jo el faig servir sempre i hi tinc totes les de catradio, les icats i una pila més.

---

### Post by kinmye on 2010-10-28
Ahir vaig descubrir un paquet, el Rhythmbox-radio-browser ; pot-ser el coneixeu; jo no, i m'agrada molt: permet trobat ordenades emissores, per país (ex: Spain->Barcelona amb catmusic, catradio, ... rac1, flaixbac, RNE4), per genere, etc.


[LIST]
[*]Instal·lar paquet
[*]Arrancar Rhythmbox
[*]En "edita -> connectors" marcar el "Internet radio station browser"
[/LIST]

A mi, amb Lucid s'em pentxa al triar algunes (pot-ser em falten coders ...) però tot i així, ho trobo genial. De moment he provat només dues (a part de les catalanes), una chillout i una altra de classica (venice ...), i totes dues sense cap paraula, només música, i bona.

A disfrutar-ho.

---

### Post by tanreb20 on 2010-10-28
L'enllaç de cat. radio per rhythmbox es:

```
http://www.catradio.cat/directes/catradio_wm.m3u
```

Una bona idera per tenir radios espanyoles es:

Descarregues:

```
https://sites.google.com/site/mellinas314/radios.sh
```

tanques el rhythmbox

terminal:

```
cd carpeta

chmod +x radios.sh

./radios.sh
```

I ja ho tens!

---

### Post by kinmye on 2010-10-29
tanreb,
Jo en particular això que dius si el coneixia. El que no coneixia és el que comentava, instal·les el paquet radio-browser i ja et surten en Rhythmbox moltissimes (>5000) emissores de tota mena, amb 18 catalanes i 5 (RNE) espanyoles. Es veritat que en el teu script surt alguna (com la cope, canal sur) que no surt en el browser.

Salutacions,

---

