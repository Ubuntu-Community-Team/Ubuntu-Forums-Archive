---
title: "Fonts de programari recomanades"
date: 2010-05-25
forum: Catalan Team
---

### Post by albertdelleida on 2010-05-25
Hola a tots i totes,

arran d'un altre fil obert m'ha sorgit el dubte de saber quines fonts de programari em recomaneu que tingui activades. Utilitzo l'Ubuntu 10.04 i a "altre programari" tinc activades les següents fonts de programari:

- [http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) lucid main
- Medibuntu - Ubuntu 9.10 "karmic koala" ([http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free)
- [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main

Alhora, també em surten les següents fonts de programari però no les tinc marcades:

- [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
- [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner (Codi font)
- Medibuntu (source) - Ubuntu 9.10 "karmic koala" ([http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free  non-free)
- [http://ppa.launchpad.net/kernel-ppa/pre-proposded/ubuntu](http://ppa.launchpad.net/kernel-ppa/pre-proposded/ubuntu) lucid main

Què us sembla? Afegiríeu o eliminaríeu alguna font de programari? Merci :)

---

### Post by wgarcia on 2010-05-25
El Medibuntu de Karmic koala no t'hauria de sortir, hauries de desactivar-lo i instal·lar el Medibuntu de Lucid, entrant des de la terminal tota aquesta parrafada:

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

Si vols que els programes de Medibuntu et sortin en el "Centre de Programari Ubuntu", també hauries de donar la següent instrucció:

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

Tot això, i més informació sobre Medibuntu, s'explica a la pàgina en anglès:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by albertdelleida on 2010-05-25
Moltes gràcies wgarcia :)

Ho acabo de fer i ja em surt el Medibuntu del Lucid i el del Karmik Koala ha desaparegut :)

---

### Post by jofern on 2010-05-26
També pot interessar-te la font de getdeb, on hi ha una col·lecció molt gran de programes.

[http://www.getdeb.net/updates/ubuntu/10.04/](http://www.getdeb.net/updates/ubuntu/10.04/)

afegeix a les fonts de programari:
								deb  [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps 								

i desa la clau per la terminal
								wget -q -O-  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

---

### Post by albertdelleida on 2010-05-29
Moltes gràcies a tots i a totes per les recomanacions! 

Cada dia que passa m'agrada més l'Ubuntu! :D

---

