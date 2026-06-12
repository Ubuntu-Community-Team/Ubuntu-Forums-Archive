---
title: "Paquests trencats en  libimobiledevice"
date: 2011-02-20
forum: Catalan Team
---

### Post by jutipiris on 2011-02-20
Tinc instal·lat l'Ubuntu 10.10 Maverick Meerkat i l'estic intentant sincronitzar el meu **iphone 3Gs**. 

A través del synaptic he volgut instal·lar: [**libimobiledevice**]("http://www.libimobiledevice.org/") però de tots els fitxers no m'ha permès instal·lar el següent, diu:
> 
**Els següents paquets tenen dependències que no es poden resoldre**

libimobiledevice1-dbg:
  Depèn: libimobiledevice1 (=1.0.1-1) però s'instal·larà 1.0.4-1ubuntu1~lucid1

Quan he volgut instal·lar-me el programa **sbManager** d'acord amb [aquestes instruccions]("http://120linux.com/sbmanager-ubuntu/"):

> sudo apt-get install build-essential automake autoconf libtool libgnutls-dev libglib2.0-dev libxml2-dev libreadline5-dev swig python-dev libusbmuxd-dev libplist-dev libplist++-dev libplist++1 libzip-dev libclutter-1.0-dev libclutter-gtk-0.10-dev intltool

m'ha sortit el següent missatge una altra vegada:

> S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
libxml2-dev ja es troba en la versió més recent.
S'ha marcat libxml2-dev com instal·lat manualment.
build-essential ja es troba en la versió més recent.
libglib2.0-dev ja es troba en la versió més recent.
S'ha marcat libglib2.0-dev com instal·lat manualment.
libgnutls-dev ja es troba en la versió més recent.
S'ha marcat libgnutls-dev com instal·lat manualment.
libplist++1 ja es troba en la versió més recent.
S'ha marcat libplist++1 com instal·lat manualment.
libusbmuxd-dev ja es troba en la versió més recent.
S'ha marcat libusbmuxd-dev com instal·lat manualment.
libplist-dev ja es troba en la versió més recent.
S'ha marcat libplist-dev com instal·lat manualment.
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu emprant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.
La informació següent pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
 libplist++-dev : Depèn: libplist1 (= 1.3-1) però s'instal·larà 1.3-1ubuntu1~ppa1
E: Paquets trencats

**Com puc arreglar aquests paquets que diu que estan trencats?**

En [aquest fil]("http://ubuntuforums.org/showthread.php?t=1524416") també s'han trobat amb algun problema, però crec que no és el mateix.

Moltes gràcies!

---

### Post by kukat on 2011-02-20
si fas

sudo apt-get install -f

l'opció "-f" arregla els paquets que estan trencats.

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by jutipiris on 2011-02-23
gràcies, kukat. he fet: sudo apt-get install -f
i el resultat ha estat:

> S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.


i després he provat de tornar a instal·lar: 

> sudo apt-get install build-essential automake autoconf libtool libgnutls-dev libglib2.0-dev libxml2-dev libreadline5-dev swig python-dev libusbmuxd-dev libplist-dev libplist++-dev libplist++1 libzip-dev libclutter-1.0-dev libclutter-gtk-0.10-dev intltool
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
libxml2-dev ja es troba en la versió més recent.
S'ha marcat libxml2-dev com instal·lat manualment.
build-essential ja es troba en la versió més recent.
libglib2.0-dev ja es troba en la versió més recent.
S'ha marcat libglib2.0-dev com instal·lat manualment.
libgnutls-dev ja es troba en la versió més recent.
S'ha marcat libgnutls-dev com instal·lat manualment.
libplist++1 ja es troba en la versió més recent.
S'ha marcat libplist++1 com instal·lat manualment.
libusbmuxd-dev ja es troba en la versió més recent.
S'ha marcat libusbmuxd-dev com instal·lat manualment.
libplist-dev ja es troba en la versió més recent.
S'ha marcat libplist-dev com instal·lat manualment.
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu emprant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.
La informació següent pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
 libplist++-dev : Depèn: libplist1 (= 1.3-1) però s'instal·larà 1.3-1ubuntu1~ppa1
E: Paquets trencats


què puc fer més?

---

### Post by wgarcia on 2011-02-23
Segons l'últim missatge que mostra sembla que tens un dipòsit "ppa" habilitat que interfereix amb el programa que vols instal·lar. 

Mira en els dipòsits que tens en "Altre programari" al synaptic si pots veure aquest dipòsit ppa i si pots deshabilitar-lo.

---

### Post by jutipiris on 2011-02-23
gràcies, wgracia. no sé quin dipòsit deu ser:

[IMG]http://farm6.static.flickr.com/5300/5472370372_74f0d21ef6_z.jpg[/IMG]

---

### Post by wgarcia on 2011-02-24
Tot i que tens tots els ppa desactivats, sembla que el paquet libplist-dev no està ben instal·lat. Fent un "sudo apt-cache search libplist-dev" surt

libplist-dev - Library for handling Apple binary and XML property lists

Així que ara pots provar primer

sudo apt-get install --reinstall libplist-dev

a veure si s'arregla. Si no s'arregla també pots fer 

ls /var/cache/apt/libplist*

veure el nom exacte del fitxer "deb" on ve aquest paquet, i fer

dpkg-deb -I /var/cache/apt/<nom del fitxer deb de libplist-dev>

i et mostrarà les dependències, i repassar-les a veure si les tens tots instal·lades.

---

### Post by jutipiris on 2011-02-24
he fet:

> sudo apt-cache search libplist-dev
libplist-dev - Library for handling Apple binary and XML property lists


> sudo apt-get install --reinstall libplist-dev
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
No es possible la reinstal·lació del paquet libplist-dev, no es pot baixar.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.


> ls /var/cache/apt/libplist*
ls: no s’ha pogut accedir a /var/cache/apt/libplist*: El fitxer o directori no existeix


he buscat si hi haiva algun fitxer en un altre lloc i he trobat aquest:

> dpkg-deb -I /var/cache/apt**/archives/libplist++1_1.3-1_i386.deb**
 paquet de debian nou, versió 2.0.
 mida 26166 octets: arxiu de control= 888 octets.
     712 octets,    17 línies     control              
     212 octets,     3 línies     md5sums              
     135 octets,     7 línies  *  postinst             #!/bin/sh
     132 octets,     7 línies  *  postrm               #!/bin/sh
      25 octets,     1 línies     shlibs               
 Package: libplist++1
 Source: libplist
 Version: 1.3-1
 Architecture: i386
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 Original-Maintainer: Julien Lavergne <julien.lavergne@gmail.com>
 Installed-Size: 116
 **Depends: libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1), libplist1 (>= 0.16), libstdc++6 (>= 4.1.1)**
 Section: libs
 Priority: optional
 Homepage: [http://github.com/JonathanBeck/libplist](http://github.com/JonathanBeck/libplist)
 Description: Library for handling Apple binary and XML property lists
  libplist is a library for reading and writing the Apple binary and XML
  property lists format. It's part of the libiphone stack, providing access
  to Ipod and Iphone devices.
  .
  This library is the C++ implementation of the libplist API.


he d'instal·lar els fitxers següents o poden estar en algun altre lloc?

Depends: libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1), libplist1 (>= 0.16), libstdc++6 (>= 4.1.1)

---

### Post by wgarcia on 2011-02-24
Al Gestor de paquets Synaptic del menú Sistema, prova d'entrar "libplist" al quadre de cerca, i mira si pots reinstal·lar el paquet des d'aquí. 

Una altra possibilitat és amb "sudo apt-get install" intentar instal·lar les dependències que has trobat.

---

### Post by jutipiris on 2011-02-24
no hi ha manera. el synaptic diu el següent:

[IMG]http://farm6.static.flickr.com/5211/5474503411_0f6770ed61.jpg[/IMG]

i si instal·lo la resta de dependències em diu el següent per a cadascuna:
> 
ja es troba en la versió més recent.
El paquet següent s'ha instal·lat automàticament i ja no serà necessari:
  ipheth-dkms
Empreu «apt-get autoremove» per a suprimir-los.

alguna altra suggerència? gràcies!

---

### Post by wgarcia on 2011-02-25
Pots mostrar el que tens a la carpeta /etc/apt/souces.list.d:

ls /etc/apt/sources.list.d

i adjuntar el fitxer

/etc/apt/sources.list

?

---

### Post by jutipiris on 2011-02-25
el que hi ha a la carpeta **sources.list.d**:

> ls /etc/apt/sources.list.d
bisigi-ppa-lucid.list              google-chrome.list.save
bisigi-ppa-lucid.list.distUpgrade  libreoffice-ppa-lucid.list
bisigi-ppa-lucid.list.save         libreoffice-ppa-lucid.list.distUpgrade
dropbox.list                       libreoffice-ppa-lucid.list.save
dropbox.list.distUpgrade           pmcenery-ppa-lucid.list
dropbox.list.save                  pmcenery-ppa-lucid.list.distUpgrade
google-chrome.list                 pmcenery-ppa-lucid.list.save
google-chrome.list.distUpgrade     pmcenery-ppa-maverick.list


no em deixa adjuntar el fitxer **sources.list**. conté el següent:

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
## Major bug fix updates produced after the final release of the
## distribution.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free # desactivat en actualitzar a maverick
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free # desactivat en actualitzar a maverick
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps # desactivat en actualitzar a maverick
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps # desactivat en actualitzar a maverick
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # desactivat en actualitzar a maverick
# deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # desactivat en actualitzar a maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

---

### Post by wgarcia on 2011-02-27
Jo he intentat instal·lar libplist1++-dev i a mi se m'instal·la perfectament. 
 
Em sembla que en el teu sistema pot estar interferint amb algun dels dipòsits ppa que tens habilitats a /etc/apt/sources.list.d

Una possibilitat, que no sé si t'ho arreglarà, és instal·lar aquest paquest "a mà", i veure si pots continuar amb l'instal·lació que estàs intentant. 

Per això pots anar a buscar el paquet directament a :

[http://packages.ubuntu.com/maverick/libplist++-dev](http://packages.ubuntu.com/maverick/libplist++-dev)

escollir el que correspongui per al teu sistema (32bits o 64bits), baixar-te el "deb" i instal·lar-lo amb:

sudo dpkg -i <nom-del-deb>

Si et continua dient que hi ha problemes de dependències pots tornar a provar

sudo apt-get install -f

i si encara no funciona forçar la instal·lació:

sudo dpkg -i --force-all <nom-del-deb>

Però com et deia, no sé si acabará funcionant tot plegat.

---

### Post by jutipiris on 2011-03-02
moltes gràcies, wgracia,

al final vaig decidir anar al synaptic, marcar tots els paquets de libplist, els vaig desinstal·lar i els vaig tornar a instal·lar. amb la nova instal·lació, enlloc de guardar-se com a "ppa" ho van fer amb la versió 1.3.1. simplement, i així ja va funcionar

les darreres comandes que em vas dir tu no em van funcionar

---

