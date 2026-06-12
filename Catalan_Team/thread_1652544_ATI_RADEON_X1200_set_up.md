---
title: "ATI RADEON X1200 set up"
date: 2010-12-25
forum: Catalan Team
---

### Post by venusfenix on 2010-12-25
buenas,

tinc un Intel core 2 Quad 1.6 and una ATi radeon X1200, i no hi ha manera de poguer instalar el seu driver.
he trobat en AMD el corresponent i quan començo a instal.lar em torna el següent missatge:

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-26-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.ELydS2


que puc fer?

---

### Post by wgarcia on 2010-12-26
El problema sembla ser que ATI ha interromput suport per a targetes gràfiques antigues en els seus mòduls propietaris. Hi ha, sembla, dues opcions. 1) Si et funcionen, usar els controladors de codi obert que proporciona Ubuntu. 2) Baixar-se l'últim programa d'instal·lació que trobis al lloc d'ATI, i córrer-lo per exemple d'aquesta manera:

./ati-driver-installer-9-3-x86.x86_64.run --listpkg

canviant apropiadament segons si tens 32 o 64 bits.

Això et llistarà una sèrie de versions, i escollir l'última o la que s'apropi més a la teva versió d'Ubuntu, per exemple:

./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/maverick

Tot això he de dir que no ho puc provar perquè no tinc cap ordinador amb targeta ATI, però a veure si serveix.

---

