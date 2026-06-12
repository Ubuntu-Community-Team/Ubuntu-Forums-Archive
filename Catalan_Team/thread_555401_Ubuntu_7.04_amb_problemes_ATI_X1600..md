---
title: "Ubuntu 7.04 amb problemes ATI X1600."
date: 2007-09-20
forum: Catalan Team
---

### Post by qerote on 2007-09-20
Vaig instal·lar la versió 7.04 de Ubuntu i em va sortir un error fent esment a la gràfica. He llegit a diversos llocs que la ATI X1600 dóna problemes. M'han dit que provi amb un script però no tinc idea de quan poder-lo aplicar. Quan començo la instal·lació en cap moment em dóna l'opció d'entrar comandes... es queda carregant fins que surt el missatge d'error. En quin moment he d'entrar aquest script? El script és el següent: 

Codi: 
#!/bin/sh tiro Elimina antics paquets fglrx.......................................... suo apt-get remove fglrx* tiro tiro restaura xorg.conf original:............................................. #suo dpkg-reconfigure -phigh xserver-xorg #deshabilitat ara com ara tiro tiro actualitza repositorios:.................................................. suo apt-get update tiro tiro descàrrega i instal·la driver i restricted modulis:.......................... suo apt-get install linux-restricted-modulis-$(uname -r) suo apt-get install xorg-driver-fglrx #aquest és el driver suo depmod -a actualitza # dependències tiro tiro configura:............................................................... suo aticonfig --initial suo aticonfig --overlay-type=Xv tiro tiro deshabilta "composite"................................................................ dc=$(suo grep "\"Composite\" \"Disable\"" /etc/X11/xorg.conf | grep -v \#) if %[ "$dc" = "" ]; then printf "Section \"Extensions\"" | suo tee -a /etc/X11/xorg.conf tiro \ | suo tee -a /etc/X11/xorg.conf printf " Option \"Composite\" \"Disable\"" | suo tee -a /etc/X11/xorg.conf tiro \ | suo tee -a /etc/X11/xorg.conf tiro Endsection | suo tee -a /etc/X11/xorg.conf else tiro composite ja estava desabilitado fi tiro tiro re-habilita modulo "fglrx" en linux/restricted/modulis/common............. lr=$(suo grep fglrx /etc/default/linux-restricted-modulis-common | grep -v \#) if %[ "$lr" = "" ]; then tiro modulo "fglrx" habilitat exit else suo cp /etc/default/linux-restricted-modulis-common /etc/default/lrmc tiro re-habilitant fglrx..... suo grep \# /etc/default/lrmc > /etc/default/linux-restricted-modulis-common suo grep -v DISABLEDMODULIS /etc/default/lrmc | grep -v \# | tee -a /etc/default/linux-restricted-modulis-common suo grep fglrx /etc/default/lrmc | grep -v \# | sigueu s/fglrx// | tee -a /etc/default/linux-restricted-modulis-common tiro .....fglrx re-habilitat fi 

He llegit que la versió Alternate no instal·la entorn gràfic... puc provar aquesta versió i així no tenir problemes amb la ATI i l'acceleració 3D? Què em recomaneu ferr? 

Una salutació i gràcies!

---

### Post by CarlesOriol on 2007-09-20
Has fet una traducció automàtica d'aquest text oi?

El suo en lloc del sudo m'ha a&#320;lucinat!!

Penja el codi sense traduir.

Per cert la "alternate" si que insta&#320;la el mode gràfic però ho fa en mode text. Si pots insta&#320;lar des de la normal no cal que ho facis amb l'altra.

---

### Post by qerote on 2007-09-20
jeje és veritat, no ho havia vist.

El cas és que amb la versió desktop no puc instal·lar-lo perquè després em surt el missatge d'error. Per això deia de provar la versió Alternate. És posible que la versió 7.04 no sigui compatible amb la X1600? He vist algun vídeo amb un Kubuntu 6.10 a una ATI X1600. Ja no sé què fer. Gràcies.

---

### Post by xoldy on 2007-09-20
Hola qerote, jo tinc la gràfica que dius en un portàtil HP NC8430, i amb el post que et [linco]("http://ubuntuforums.org/showthread.php?t=510985&highlight=fglrx"), ho he aconseguit solucionar.
Primer vaig fer la instal·lació en el [dvd ]("http://es.archive.ubuntu.com/cdimage/releases/feisty/release/ubuntu-7.04-dvd-i386.iso")en mode text per poder configurar els paràmetres de xarxa i que pugui tenir connexió a internet. Quan hauria d'engegar el sistema de finestres un cop fet el primer reinici després de la còpia dels fitxers, surt l'error que comentes.
Un cop passes tots els errors t'hauria de quedar una finestra de terminal, i segueixes les instruccions que el mateix Carles Oriol posa després del "cagada pastoret" del post que t'he posat.

A mi m'està funcionant perfectament d'aquesta manera. No se si és la millor manera de fer-ho però a mi m'ha funcionat.

Espero haver-te ajudat.

---

### Post by qerote on 2007-09-20
Moltes gràcies Xoldy. Tinc una pregunta. Al link que m'has escrit, Carles Oriol diu que no és possible instal·lar-hi el Beryl. És això cert? Com és llavors que al Youtube hi ha vídeos de ATI X1600 amb Beryl funcionant? Una salutació i gràcies de nou.

---

### Post by xoldy on 2007-09-20
Hola de nou, el tema Beryl, jo no l'he provat amb la Feisty ni amb aquest portàtil que tinc ara, però pot ser que no funcioni, ja que quan li vols demanar que et faci els efectes d'escriptori, (sense haver instal·lat el Beryl), et diu que no és possible.
Espero que es pugui amb la nova versió la gutsy, que encara no m'he atrevit a posar-lo a una altre partició del pc.

Espero que et vagi bé la referència.

---

### Post by CarlesOriol on 2007-09-20
Les coses estan canviant molt al mon amd/ati de fa pocs dies.

El gutsy realitza una bona insta&#320;lació amb xgl que segurament serà obsoleta a mitjans del proper mes quan surti aquest.

El controlador lliure permet usar beryl amb aixgl el privatiu sols amb xlg i en feisty es força més complicat de fer-lo rutllar.

En aquests moments és dificil d'afirmar res en el mon ati que pugui durar més d'una setmana així que la meva recomanació de moment és: PACIÈNCIA.

---

