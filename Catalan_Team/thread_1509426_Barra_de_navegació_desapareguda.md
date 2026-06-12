---
title: "Barra de navegació desapareguda"
date: 2010-06-14
forum: Catalan Team
---

### Post by tanreb20 on 2010-06-14
Hola!

Fa uns dies vaig actualitzar els repos i des d'aleshores m'ha desaparegut la barra de navegacio del nautilus, i tots els botons!!!!
Actualment només tinc la subfinestra lateral, i el menú superior.

Quan vaig visualitzar m'apareix com a marcat la opció Barra d'ubicació i barra d'eines principal. Quan intento desmarcar-les no em deixa :S

Alguna idea?

---

### Post by lluisanunez on 2010-06-15
I si obres el menú "View" tens aquestes opcions activades (la barra de navegació, els botons...)??

edito: sorry, no havia vist la segona part del teu post. Has mirat a les preferències?

---

### Post by wgarcia on 2010-06-15
Pots provar d'esborrar un directori que tens al teu "home" que es diu .nautilus, on es desen les preferències i sessions recordades per nautilus, a veure si t'ho arregla. El nautilus recrearà aquest directori quen el tornis a iniciar.

---

### Post by tanreb20 on 2010-06-15
Ho he provat i no ha modificat res :(

---

### Post by wgarcia on 2010-06-15
I si entres amb algun altre usuari també et passa? No hauràs instal·lat l'aplicació des d'un repositori ppa?

---

### Post by tanreb20 on 2010-06-15
Hola Wgarcia!

Diria que vaig instalar alguna modificació del Nautilus a través d'un PPA. com puc esborrar-lo i deixar el que bé per defecte?

---

### Post by wgarcia on 2010-06-16
Doncs si havies instal·lat algun ppa relacionat amb nautilus, deshabilita'l des de Sistema -> Administració -> Fonts de programari -> Altre programari, i després intenta reinstal·lar el nautilus:

sudo apt-get reinstall nautilus

A vegades això no ho arregla del tot perquè el nautilus interrelaciona amb altres elements de l'escriptori gnome, però és el més senzill de provar primer.

---

### Post by tanreb20 on 2010-06-16
Em surt aixó:


```
Els paquets següents es tornaran a instal·lar:
  nautilus rhythmbox 
0 paquets a actualitzar, 0 a instal·lar, 2 tornats a instal·lar, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
E: No s'ha trobat un fitxer pel paquet nautilus. Això podria significar que haureu d'arreglar aquest paquet manualment.
S'està escrivint la informació d'estat estesa... Fet
E: No s'ha trobat un fitxer pel paquet nautilus. Això podria significar que haureu d'arreglar aquest paquet manualment.
E: S'ha produït un error intern, no s'ha pogut generar la llista de paquets a baixar
```

---

### Post by wgarcia on 2010-06-16
Perdona, la instrucció que t'he donat no és correcta, la correcta és:

sudo apt-get install --reinstall nautilus

i assegura't a "Sistema -> fonts de programari" que tens habilitats els repositoris main i universe

---

### Post by tanreb20 on 2010-06-16
Em diu una cosa força extranya

```
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
No es possible la reinstal·lació del paquet nautilus, no es pot baixar.
No es possible la reinstal·lació del paquet rhythmbox, no es pot baixar.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 1 no actualitzats.

```

---

### Post by wgarcia on 2010-06-17
Adjunta sisplau el fitxer:

/etc/apt/sources.list

---

### Post by tanreb20 on 2010-06-17
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
## Major bug fix updates produced after the final release of the
## distribution.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid universe
deb http://es.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://es.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
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
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb-src http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb http://linux.dropbox.com/ubuntu lucid main
# deb-src http://linux.dropbox.com/ubuntu lucid main

```

```
[504][alorma:apt]$ cd sources.list.d/
[505][alorma:sources.list.d]$ ls
am-monkeyd-nautilus-elementary-ppa-lucid.list
am-monkeyd-nautilus-elementary-ppa-lucid.list.save
bean123ch-burg-lucid.list
bean123ch-burg-lucid.list.save
dockbar-main-ppa-lucid.list
dockbar-main-ppa-lucid.list.save
docky-core-ppa-lucid.list
docky-core-ppa-lucid.list.save
dropbox.list
dropbox.list.save
gnome-media-player-development-development-lucid.list
gnome-media-player-development-development-lucid.list.save
google-chrome.list
google-chrome.list.save
gottcode.sources.list
gottcode.sources.list.save
matthaeus123-mrw-gimp-svn-lucid.list
matthaeus123-mrw-gimp-svn-lucid.list.save
shutter-ppa-lucid.list
shutter-ppa-lucid.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.save
webupd8team-rhythmbox-lucid.list
webupd8team-rhythmbox-lucid.list.save
```

---

### Post by wgarcia on 2010-06-17
El fitxer sources.list es veu bé.

En eliminar el repositori ppa vas actualitzar les fonts de programari? Prova de fer 

sudo apt-get update

i després tornar a donar la instrucció de reinstal·lar nautilus.

---

### Post by tanreb20 on 2010-06-17
El primer cop que actualitzao em diu:

```
S'està llegint la llista de paquets... Fet
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_multiverse_binary-i386_Packages)
W: Potser voldreu executar apt-get update per a corregir aquests problemes

```

Després ho actualitzo i tot ok, peor no em modifica rés al fer el reinstall.

Seria possible esborrar-lo i  instalar-ho un altre cop?¿

---

### Post by wgarcia on 2010-06-17
> **tanreb20 said:**
> Després ho actualitzo i tot ok, peor no em modifica rés al fer el reinstall.

Seria possible esborrar-lo i  instalar-ho un altre cop?¿

Sí, però no volia recomanar-te això, perquè com et deia el nautilus està força imbricat amb la resta de l'escriptori. Però el següent intent seria:

sudo aptitude purge nautilus

i després intentar reinstal·lar. 

La següent cosa més radical seria des de fora de l'escriptori desintal·lar i tornar a instal·lar "gnome-desktop". Però de moment prova això de desintal·lar sols el nautilus a veure si ho arregla.

---

### Post by tanreb20 on 2010-06-17
Bé!

Després de uns quants intents, de forçar la versio a instalar i uns quants maldecaps.. he tornat a tenir la barra d'ubicació!!! Grácies WGarcia!

Ara l'unic que em manca é spoder configurar-la, alguna opcio?

---

### Post by wgarcia on 2010-06-18
Quina configuració vols introduir?

---

### Post by tanreb20 on 2010-06-18
Modificar els botons d'ordre i tot això...

---

### Post by wgarcia on 2010-06-18
Potser que demanis en un altre fil nou exactament el que vols fer (quins botons, com els vols posar, etc).

---

