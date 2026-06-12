---
title: "actualització i aMSN no va..."
date: 2007-05-18
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-05-18
Ei, ara mateix he acceptat l'actualització.

Doncs tenia l'aMSN 0.96 i s'ha posat l'aMSN 0.97. Doncs vaig a obrir-lo, i primer veig que els caràcters amb accents i tot això es veuen malament.. I després intento connectar-me i em diu que falta un mòdul TLS per la connexió segura. Vaja, que ara no puc ni em deixa entrar al messenger...

Solucions, i tampoc ser com instal·lar la versió antiga, si aquesta és la solució..

Gràcies!

---

### Post by PellRoja on 2007-05-18
et recomano que instal·lis això de tsl, que si no recordo malament o fa automàticament, o es busca al synaptic i crec que hi és. El problema de els accents també he sentit molta gent que te aquest problema, jo incluit i encara no he pogut arreglar-ho. 

Pero el nou aspecte de el 0,97 està molt be.

---

### Post by patrickfromspain on 2007-05-18
Hem sembla que amb l'amsn et puc ajudar...

El que tu dius, hem passa amb l'amsn 0,97 i el tcl/tk 8.5a6. La solucio que he trobat es tornar a fer servir el tcl/tk 8.8a5

salut!

---

### Post by bikerbaixcamp on 2007-05-18
Automàticament em diu que falta això del tls i que m'ho descarregui, li dic que si, però dóna error i no ho fa. 

Patrick, del que m'has comentat no m'he assabentat de res.. No sé que és ni com es fa..

Merci..

---

### Post by patrickfromspain on 2007-05-18
com vas instal·lar l'amsn?

---

### Post by bikerbaixcamp on 2007-05-18
Pel ATP i s'ha actualitzat per les actualitzacions automàtiques..

---

### Post by patrickfromspain on 2007-05-18
s'ha actualitzat per apt??? Hi ha alguna cosa que no hem quadra. Si s'ha actualitzat per les actualitzacions d'ubuntu, deu tenir algun repo especia. T'importa ensenyarnos el teu /etc/apt/sources.list?

Si s'ha actualitzat desde l'amsn, vol dir que l'obres com a root, i aixo es entre poc i gens recomanable. Reinstal·lal i llestos, suposo

Salut!

---

### Post by bikerbaixcamp on 2007-05-18
He reinstal·lat amb l'ATP  i segueix fent el mateix.

el source.list :

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by bikerbaixcamp on 2007-05-18
He reinstal·lat també el tema de paquets.. i res..

Ara he reiniciat l'ordinador, i no sé perquè m'ha sortir el calendari de dalt mogut cap a la dreta (una mica) i el que estava al seu costat doncs tocant a l'inrevés.

mmm...

---

### Post by patrickfromspain on 2007-05-18
al repo de l'automatix hi ha la versio svn de l'amsn... alla esta l'error. Amb synaptic, força la versio 0.96 i ja esta, despres bloquejes el paquet i llestos.

EDITO: abans de desinstal·lar l'amsn 0.97, proba a instalar libssl0.9.7 i mira si et va be.

salut!

---

### Post by bikerbaixcamp on 2007-05-18
El que has editat tampoc m'ha anat.

He trobat això: [http://www.ubuntu-es.org/index.php?q=node/29102](http://www.ubuntu-es.org/index.php?q=node/29102) en fòrums veïns, on un dia deia que s'ha d'afegir un 0 en un arxiu... 

Ho he fet i va...!!!

El que passa es que continuo veient alguns caràcters amb accents de manera estranya..

Merci de totes maneres!

---

### Post by CarlesOriol on 2007-05-18
L'automatix és un niu de problemes. Segur que el problema ve d'allà.

---

### Post by patrickfromspain on 2007-05-18
mm CarlesOriol, a l'automatix li tens una mica de tirria, o soc jo que ho pillo malament? ;)

Podries explicar perque?

Jo no el faig servir perque total, el que insta&#320;la ja esta tot (o casi tot) als repos i tampoco costa tant de buscar i insta&#320;lar-ho... i no es tarda res tampoc.

---

### Post by bikerbaixcamp on 2007-05-18
> **CarlesOriol said:**
> L'automatix és un niu de problemes. Segur que el problema ve d'allà.

No ho sé, però l'amsn me'l vaig baixar per l'ATP i després es va actualitzar mitjançant l'estrella aquella que surt a l'Ubuntu...

Menys els caràcters "rars" dels menus de l'amsn, la resta va perfecte!

---

### Post by patrickfromspain on 2007-05-18
proba a posar d'idioma el castella... es per la versio. hem sembla. En versions posteriors ja es veu be.

---

### Post by CarlesOriol on 2007-05-18
"tirria" ... be anomena-ho com vulguis... però com tu has dit:

- No cal per res. Si de cas pots usar un repositori com [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

- Si mires la majoria dels problemes en actualitzacións, migracions i problemes als repositoris veuras que el 99% son produïts per aquest insta&#320;lador.

Si la comunitat global gestiona els paquets i les insta&#320;lacions, així com els problemes que puguin tenir... quin sentit té de tancar-se usant un sistema mantingut no co&#320;lectivament?

És així o no Patrick?

---

### Post by bikerbaixcamp on 2007-05-18
> **patrickfromspain said:**
> proba a posar d'idioma el castella... es per la versio. hem sembla. En versions posteriors ja es veu be.

Tens raó, en castellà es veu bé. Així que per veure-ho bé en català, s'haurà d'esperar, no?

Bé, ho segueixo posant en català i ja s'arreglarà...

---

### Post by patrickfromspain on 2007-05-19
En el meu, ho vaig arreglar compilant una versio d'svn.. en el teu cas, segurament tardi una mica a arreglar-se: fins que el paquet que hi ha al repo d'automatix s'actualitzi.

---

