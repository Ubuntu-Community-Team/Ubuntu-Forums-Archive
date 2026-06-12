---
title: "Drivers Nvidia"
date: 2010-04-25
forum: Catalan Team
---

### Post by grundt on 2010-04-25
Hola, 

Feia servir l'ubuntu en una partició amb windows, he aprofitat el disc dur i me l'han instal·lat en un altre ordinador.

La targeta grafica es vga geforce mx440 agp

A l'entrar a ubuntu ( no recordo si es 8.10 ) m'ha dit de seguida que havia de posar uns drivers 
nvidia, li he dit que si, i al reiniciar, un cop poso nom i contrassenya la pantalla es queda en negre
i el monitor en modo de baix consum.

He vist fils semblants, però no estic segur que siguin el mateix cas.

Gràcies

---

### Post by ICTINEU on 2010-04-25
hOla!, quan reiniciis la màquina, al menú d'arrencada del grub, entra amb el (recovery mode) en comptes del normal i mira si tens instal·lat el paquet nvidia-glx-new (es a dir, controladors nous per targetes antigues). Amb K/Ubuntu 8.04 funciona a la perfecció, suposo que hauria de ser igual amb els altres. Tot i que aquestes alçades ,no et valdria més esperar-te quatre dies i possar-te la 10.04?, les versions LTS tenen un plus de estabilitat estimable.
Tot i que aquesta gràfica tan antigueta que vols fer servir, no li demanis massa, com li activis els efectes d'escriptori es probable que vagi a tronpicons i d'HD ni parlar-ne.

---

### Post by grundt on 2010-04-25
Hola, he entrat en el recovery mode, li he dit resume boot
lesinformacions que surten passen molt de pressa i no he sabut veure si tinc aquest controlador, 

si que surt la paraula nvidia kernel en algun moment.

Posar-me la 10.4? passa que l'ultim cop que em vaig actualitzar l'ubuntu, vaig tenir alguns problemes, crec que amb el so, i per tant com que ja em funcionava doncs ho he deixat així,
a més cada cop que surt un ubuntu nou i l'intento instal·lar, em demana de crear una particio nova,  i no m'interessa carregar-me l'antiga (crec)

La targeta és molt vella? vaja doncs a l'ordinador anterior (2003)-(2010) en pau descansi. la targeta era una cosa molt simple enganxada a la placa base i  a mi ja em servia (es veritat, no podia fer servir els efectes d'escriptori)

merci de nou   ah per cert és ubuntu (8.04) el que tinc

---

### Post by ICTINEU on 2010-04-25
Ja, però el que passa, és  que tal com ha evolucionat el tema de la imatge, ara s'ha triplicat el cabal de dades que han de processar aquestes gràfiques, es a dir, que en els últims tres anys el maquinari a envellit com als sis anteriors.
   Personalment et recomano tenir un disc dur amb la versió LTS més recent i un altre per fer animalades. Per tal d'evitar-me problemes, instal·lar en net (baixar el CD, cremar, verificar, instal·lar), no des de una versió anterior, (es el meu sistema) i sobre tot crear manualment una partició /home , perqué així pots reinstal·lar el sistema o posar-hi un altre mantenint; sempre que no toquis aquesta partició en instal·lar; les teves dades i les configuracions que tinguessis guardades, que el nou sistema pogués assumir, cosa que et pot estalviar molta feina si ets tiquis miquis amb les configuracions.
   Per cert, aquest problema amb l'àudio, jo també l'he tingut, primer l'mplayer va començar a no detectar el dispositiu d'àudio, després el Totem i vlc, vaig reinstal·lar el sistema ràpidament, mercès a la partició /home que t'he explicat abans, i tema solucionat, dràstic, però eficacísim.
Salutacions.

---

### Post by grundt on 2010-04-26
Ok,

crec que et faré cas,

clar , tinc una partició però la vaig fer des del menú basic on pots moure una barra per assignar tants gigues a cada partició.

Suposo que el que em dius es que s'ha de fer manualment, (cosa que veia complicada), però si és així ara m'informaré del tema.

Gràcies per l'ajuda.

---

### Post by ICTINEU on 2010-04-26
És molt menys complicat del que sembla. I per extrany que sembli, a mi me's més fàcil fer-ho amb la imatge de CD alternate, que amb la desktop, potser perqué és més esquemàtica?.
Però puc entendre que la majoria prefereixi el mode gràfic de la desktop.
Inclús si haguessis de crear una partició /home, prèvia a la instal·lació per tal de salvar dades, ho pots fer en mode gràfic, amb el Gparted.
Aquets fils et poden ser d'ajuda:

[http://www.kubuntu-es.org/foro/200805/instalacion-conservando-el-home-aparte](http://www.kubuntu-es.org/foro/200805/instalacion-conservando-el-home-aparte)
[http://www.ubuntu-es.org/?q=node/68288](http://www.ubuntu-es.org/?q=node/68288)
[http://www.ubuntu-es.org/index.php?q=node/75626](http://www.ubuntu-es.org/index.php?q=node/75626)

Em sembla que ens em desviat bastant del enunciat del tema. 
Però desde l'empatía, m'he vist en lo obligació de dir-te el que jo faria en el teu cas, per si et puc estalviar algún problema, que ja he patit.
De totes maneres la teva pregunta primigenea, per si t'hi tornesis a trobar, està magníficament explicada al fòrum d'una d'questes dos webs, ara no recordo quina.

No t'arruguis, que és bastant sencill i tens tota una comunitat per ajudar-te.
Salutacions.

---

### Post by grundt on 2010-04-29
Ok, 

de fet ja havia començat a mirar per fer això de la partició amb el / home, sembla interessant.

El que passa es que m'esperava una resposta en plan - Tens la pantalla en negre ah doncs mira, 

tecleja això i problema resolt.

Però suposo que el que em dius te la seva raó de ser, i es millor reinstalar un sistema nou.

Ara tinc dubtes sobre en quin dels dos discs es millor fer la instalació del nou ubuntu en el que

ve amb l'ordinador (que porta windows7) o amb el que tenia jo que està com a segon (que porta 

windows xp i l'ubuntu 8.10)  Però això seria millor comentar-ho en un altre post oi?

Merci , qui siguis

---

