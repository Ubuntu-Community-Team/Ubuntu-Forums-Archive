---
title: "problemes actualitzacions ubuntu intrepid"
date: 2009-02-27
forum: Catalan Team
---

### Post by grenyut on 2009-02-27
Hola,

ahir vaig actualitzar l'ubuntu hardy a ubuntu intrepid mitjançant el gestor d'actualitzacions. Tot funciona bé, aparentment (falta que provi algunes coses, però...)

El problema és ue avui m'ha aparegut la icona de que hi ha noves actualitzacions disponibles (640 actualitzacions!!!) però al provar d'instal·lar-les em dóna un error:

No s'han pogut instal·lar totes les actualitzacions...

em demana que executi una instal·lació parcial però aquesta també em dóna error, s'està molta estona "preparant la instal·lació" i finalment em diu
"S'ha produït un error en autenticar alguns paquets", i me'ls llista, no copio la llista perque són un munt!!! (tots??)

A veure qui em pot ajudar... mil gràcies per avançat!!

---

### Post by papapep on 2009-02-27
Enganxa el contingut del /etc/apt/sources.list

---

### Post by grenyut on 2009-02-27
Hola,

és xubuntu, no ubuntu, però suposo que la cosa serà molt semblant.

copio el sources.list:

# deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb [http://www.tcosproject.org/](http://www.tcosproject.org/) gutsy main
# deb-src [http://www.tcosproject.org/](http://www.tcosproject.org/) gutsy main
deb [http://ftp.es.debian.org/debian](http://ftp.es.debian.org/debian) sid main

Gràcies!

---

### Post by indiosincracia on 2009-02-27
Prova de posar els (supositoris) en "main server"

---

### Post by papapep on 2009-02-27
El que no em quadra, Grenyut, és que actualitzessis la versió i ara encara et vulgui actualitzar 640 paquets...no té cap ni peus. Estàs segur de que no es va aturar en algun moment l'operació, i va quedar a mitges?

---

### Post by grenyut on 2009-02-28
papaep, com ho puc saber??? vaig posar-lo a actualitzar i vaig anar a dormir.... la instal·lació va arrivar fins al final, però no sé si hi va haver errors entremig...

una altra cosa, he provat a fer 

sudo apt-get udate

i em dóna un error al final, després de carregar els paquets de la llista.

Pot ser que tingui alguna cosa a veure amb el meu problema inicial?

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  resticted/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kimet on 2009-02-28
Em sembla que aquesta fila hi sobra:

deb [http://ftp.es.debian.org/debian](http://ftp.es.debian.org/debian) sid main

Salut.

---

### Post by grenyut on 2009-02-28
bé, finalment he generat un nou sources.list a partir d'aquest generador de sources.list

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

l'he afegit substituint l'antiga (fent-ne una còpia de seguretat, per si les mosques) i ara funciona tot bé.

potser si que era només que sobrava la línia que diu en kimet, ara no la tinc...

Salutacions a tots,

---

