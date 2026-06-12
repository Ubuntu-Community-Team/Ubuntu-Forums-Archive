---
title: "Synaptic no funciona al Gutsy"
date: 2007-10-27
forum: Catalan Team
---

### Post by Dilov on 2007-10-27
Bon dia (o nit) ubuntaires!

Acabo d'actualitzar al Gusty Gibbon avui mateix i sembla que tot va genial, millor que abans i tot!

El problema el tinc amb el Synaptic, que em diu que tinc 2 actualitzacions noves (de compiz, -core i -plugins) però qaun intento descarregarles aparentment no fa res i em dona l'error següent:

[INDENT][I]W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.0+git20071008-0ubuntu1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.0+git20071008-0ubuntu1_i386.deb)
  No es pot iniciar la connexió amb es.archive.ubuntu.com:80 (2001:720:c10:d::7). - connect (101 Network is unreachable) [IP: 2001:720:c10:d::7 80]


W: No s'ha pogut obtenir [http://es.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.0+git20071008-0ubuntu1_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.0+git20071008-0ubuntu1_i386.deb)
  No es pot iniciar la connexió amb es.archive.ubuntu.com:80 (2001:720:c10:d::7). - connect (101 Network is unreachable) [IP: 2001:720:c10:d::7 80][/I][/INDENT]

Quan clico a l'opció "Comprova" la descàrrega s'atura al fitxer 46 de 53...

Quina pot ser la causa?

Moltes gràcies!

---

### Post by pieisgood4589 on 2007-10-27
Post in the spanish speaking forums. Duh. get off the english ones.

im not racist, its the rules. :popcorn:

---

### Post by orestesmas on 2007-10-27
Probablement el repositori d'on intentes agafar els programes (l'espanyol) estigui sobresaturat i/o trencat.

Jo ho provaria amb el repositori d'un altre país. A mi l'alemany em va anar molt bé en fer l'actualització. Altres em comentaven que l'anglès també els anava bé.

---

### Post by jaume69 on 2007-10-27
jo hi tinc el servidor Principal i em va bé.
Abans feia servir el Spain,no sé.

---

### Post by Dilov on 2007-10-28
Sembla que canviant el servidor el problema segueix igual... 

Ara estic al servidor principal, està descarregant la informació dels paquets, però la descàrrega s'atura al paquet 46 de 50.
Si vaig a "Mostra el progrés per a fitxers individuals" a l'Estat em diu a alguns "Trobat" a altres "Fallat" i també "Fet".

Després d'una estona em diu:

[SIZE="1"]No s'ha pogut descarregar tots els fitxers d'índex

El repositori pot no estar ja disponible o no s'ha pogut contactar per problemes de xarxa. Si és disponible, s'utilitzarà una versió més vella de l'índex que no s'ha pogut descarregar. Si no, es descartarà el repositori. Comproveu la vostra connexió de xarxa i que l'adreça del repositori està ben escrita a les preferències.

[http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg:](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg:) No s'ha pogut connectar amb es.archive.ubuntu.com:80 (32.1.7.32), temps de connexió excedit
[http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-ca.bz2:](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-ca.bz2:) No s'ha pogut connectar amb es.archive.ubuntu.com:80 (32.1.7.32), temps de connexió excedit
[http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-ca.bz2:](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-ca.bz2:) No s'ha pogut connectar amb es.archive.ubuntu.com:80 (32.1.7.32), temps de connexió excedit
[http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-ca.bz2:](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-ca.bz2:) No s'ha pogut connectar amb es.archive.ubuntu.com:80 (32.1.7.32), temps de connexió excedit
[http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-ca.bz2:](http://es.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-ca.bz2:) No s'ha pogut connectar amb es.archive.ubuntu.com:80 (32.1.7.32), temps de connexió excedit[/SIZE]

---

### Post by Ferri on 2007-10-28
El servidor principal és:
[http://archive.ubuntu.com](http://archive.ubuntu.com)
No [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) com poses.

---

### Post by papapep on 2007-10-28
O tu o el servidor teniu algun problema, perquè la ip que poses pel servidor no és la que em dóna a mi un ping:

```
papapep@awacs:~$ ping  es.archive.ubuntu.com
PING ubuntu.cica.es (150.214.5.135) 56(84) bytes of data.
```

Tot i això, no em retorna cap paquet, o sigui que alguna cosa li deu passar.

Prova a posar el principal, com ja t'han dit (treu l"es" del davant).

A més, entre el primer i segon post la resposta és del mateix servidor (es.archive...) i dius que has canviat de servidor, o sigui que alguna cosa no quadra.

T'has repassat bé el /etc/apt/sources.list??

---

### Post by Dilov on 2007-10-29
Sobre això de repassar sources.list... la veritat es que no sóc un entès en el sistema com per conèixer aquestes coses...

Us adjunto el sources.list que diu el papapep per si us el podeu mirar:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse restricted universe main**

## Major bug fix updates produced after the final release of the
## distribution.
**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse restricted universe main**

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
**deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse**
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

**deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse restricted universe main**
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

[B]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports multiverse restricted universe main[/B]


#AUTOMATIX REPOS END

Gràcies!

---

### Post by papapep on 2007-10-29
A veure, primer de tot, si vols assegurar la jugada deixa d'utilitzar l'Automatix que, bàsicament, porta problemes.

Segon, deixa el sources.list així:

```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
##deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘commercial’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

## ‘commercial’ repository in Gutsy is not working yet
# deb http://archive.canonical.com/ubuntu gutsy commercial
# deb-src http://archive.canonical.com/ubuntu gutsy commercial

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
##deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
##deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

i prova a actualitzar a veure com et funciona.

---

