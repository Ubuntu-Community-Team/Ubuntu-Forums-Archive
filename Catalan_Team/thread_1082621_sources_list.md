---
title: "sources list"
date: 2009-02-28
forum: Catalan Team
---

### Post by tanques on 2009-02-28
Hola que tal : després de tant de temps fa temps que ting un petit que mal temps se converteix en un malt de cap , no puc actualiztar el programari ni baixar cap programa nou, el motiu es:

Per una mala manipulació : en 'E:El tipus «rom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/» no és conegut en la línia 2 de la llista de fonts /etc/apt/sources.list, E:No s'ha pogut llegir la llista de les fonts

com ja fa temps de aixo ja o arreglaré i ara que me he possat , no me enrecordo del  com o vaig fer, posso:

 sudo gedit /etc/apt/sources.list
 me surt una llista que no reconeixo d'abans i no puc arreglar aquesta famosa segona linea,

a veure si em pogueu ajudar a arreglar el sources list 
:popcorn:

---

### Post by tanreb20 on 2009-02-28
el primer seria enganxar aqui el **sources.list**

---

### Post by tanques on 2009-02-28
Hola que tal :
 no t'entenc que pegui el sources list a on

---

### Post by torracastanyes on 2009-02-28
Aquí perquè el veiem.

Així:

[http://ubuntuforums.org/showthread.php?t=1082216](http://ubuntuforums.org/showthread.php?t=1082216)

---

### Post by tanques on 2009-02-28
Aqui esta : # deb cd
rom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/](http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/) stable main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

---

### Post by PatrickVogeli on 2009-03-01
has d'esborrar les 2 primeres linies.. guardes, tanques y sudo apt-get update

salut

---

### Post by tanques on 2009-03-02
Hey fantastic:

130 dies sense renovacions 2 hores de baixades i actualitzacions

gracies

---

