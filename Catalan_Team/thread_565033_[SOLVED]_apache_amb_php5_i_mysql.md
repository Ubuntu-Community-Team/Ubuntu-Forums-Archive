---
title: "[SOLVED] apache amb php5 i mysql"
date: 2007-10-01
forum: Catalan Team
---

### Post by lpargemi on 2007-10-01
Hola

Em sap greu començar un altre fil, però vaig absolutament perdut.

Tinc instal.lat un Ubuntu 4.07 des de fa molt poc. Una de les coses que faig amb l'ordinador és mantenir unes pàgines web sobre la base de apache-php-mysql. Al windows ho tinc instal.lat amb php4 i va prou bé. El meu proveidor d'allotjament també té aquestes versions.

Al voler-ho instal.lar a Ubuntu, a través de Synaptic només he pogut trobar php5 (ai! - a mi no m'agrada actualitzar el soft només perquè n'hi ha un de més nou. De fet encara tiro amb W2000 i sense manies)

Les sospites s'han confirmat: cagada pastoret. Resulta que hi ha un conflicte de llicències entre php i mysql, que fa que no es pugui distribuir les funcions que jo faig servir tal qual. 

Es veu que si que funciona si ho compiles amb unes opcions (l'opció -- with mysql)

Anar trobant això m'ha costat suor i sang, perquè enlloc no està gaire ben explicat (almenys prou ben explicat per a inutils de la meva categoria).

Ara bé, aquesta meravellosa instrucció màgica **./configure --with -mysql=Pathmysql] && make && make install **, des d'on s'ha d'executar?

El problema és que no sé a quin direcotri hi ha instal.lats els programes: bé si... n'hi ha parts per tot arreu!

El mateix passa amb el Pathmysql... 

Us agraïré qualsevol suggeriment.

Lluís

---

### Post by papapep on 2007-10-02
Vols dir que et cal fer això? No en tens prou instal·lant el mòdul php5-mysql?
No estic molt al cas d'aquest tema, però m'estranya que hagis de compilar res.

---

### Post by Ferri on 2007-10-02
> **lpargemi said:**
> 
Ara bé, aquesta meravellosa instrucció màgica **./configure --with -mysql=Pathmysql] && make && make install **, des d'on s'ha d'executar?
Això t'ho sé contestar, de la resta, francament, ni idea.
Aquesta és la seqüència típica per compilar un programa que no tens instal·lat i que no pots (o no vols) instal·lar-lo des de les fonts de programari (perquè no hi és o perquè vols una versió més nova, habitualment).
Per poder-ho fer t'has d'haver baixat l'arxiu del programa a compilar (normalment en format comprimit bz2 o similar). Des de la carpeta on descomprimeixis l'arxiu, fent servir la consola, és on has d'introduir la seqüència que has posat.
Per evitar problemes, potser és millor que ho facis pas per pas, és a dir, primer el ./configure --with -mysql=Pathmysql] (Pathmysql és el camí on tingues mysql), després el "make" i, finalment, "sudo make install".
Per compilar programes sol fer falta un número important de paquets per complir dependències i tenir les eines necessàries. Tingues en compte que si et diu que li falta una llibreria determinada hauràs d'instal·lar el paquet que porta "-dev" al final.
Compilar programes pel teu compte és sempre una tasca una mica complicada, per tant t'aconsello que no ho facis si no tens clar del tot que no hi ha d'altres sistemes per solucionar el teu problema.

---

### Post by CarlesOriol on 2007-10-02
La idea esta bé però analitzem això:

La comunitat, els MOTUs (masters of the universe) i Cannonical co&#320;laborem per fer un sistema millor per a tots.

Quan descarregueu unes fonts amb apt-get source nomdelprograma podeu veure la quantitat de pedaços que s'han afegit a la versió original. Per què això?

Imaginem que l'ubuntu és un cotxe i decidim d'agafar el model i tots d'acord definim un ample d'eixos de roda gran per conseguir bona estabilitat i major velocitat. Per tal de fer-ho indiquem als programes com han de fer els eixos per que funcionin correctament al nostre xasis. Quan això ho fan els coneixedors dels programes i els coneixedors dels eixos tot funciona perfectament.

Però quan compilem directament unes fonts sense abans haver-nos documentat profundament ens podem trobar que malgrat que usem les darreres versions aquestes no encaixaran en el nostre vehicle.

Per tant si no us es absolutament necesari agafeu preferentment els programes dels repositoris "oficials".

---

### Post by lpargemi on 2007-10-02
Hola, i gràcies als tres pels aclariments:

El tema s'ha solucionat fent servir el mòdul php5-mysql. 

Ara bé, jo ja el feia servir, però per ves a seber quin motiu no funcionava i el php em deia que no reconeixia les funcions mysql. 

Reinstal.lant de cop tots els paquets relacionats amb php el sistema s'ha posat a funcinar.

Com que no en tinc gaire idea, potser l'havia instal.lat amb alguna seqüencia temporal incoherent, no ho sé.

Pel què fa a la compilació de fonts, doncs teniu raó, si no en saps gaire millor no tocar-ho; però buscant pels fòrums del sector i consultant al manual del php és l'opció que he trobat. I que per sort no he sabut fer anar.

Així que ja es pot posar el [Solved] a l'assumpte

Salut!

Lluís

---

