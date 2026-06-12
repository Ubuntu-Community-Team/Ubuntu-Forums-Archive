---
title: "wifi amb d-link dwl-g510 no funciona"
date: 2009-06-20
forum: Catalan Team
---

### Post by pobletex on 2009-06-20
Bones!

Torno a tenir problemes amb la connexió a internet. Anem a pams:
tenia instal·lat kubuntu 8.10 amb wifi funcionant, vaig haver de canviar el disc dur i he instal·lat kubuntu 9.04. Ara bé, el Network Management no em deixa seleccionar l'opció wireless. Només hi ha operatives el wired i el vpn.

Teclejo lspci a la terminal i veig que no em detecta la tarjeta de xarxa. Intento instal·lar el driver per a linux seguint les instruccions del readme i no puc:

$ sudo cp Makefile.6 ./Makefile
$ make all
make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/rabassut/DRIVER LINUX_DWL-G510_v1.0.3.0/RT61_Linux_STA_Drv1.0.3.0_200512230/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: *** No rule to make target `LINUX_DWL-G510_v1.0.3.0/RT61_Linux_STA_Drv1.0.3.0_200512230/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

He provat de posar el drivers .inf y .sys de windows tal i com vaig fer per l'ubuntu 8.10 i no me'n surto. També he retirat el hardware i tornat a col·locar per si hi havia una mala connexió.

Aquest cop no sé per on agafar-m'ho.

---

### Post by pobletex on 2009-06-20
Estic pensant que potser ficaré la versió anterior, que suposo que podré connectar-me com ja vaig fer, i llavors mirar d'actualitzar a la 9.04.
Però no entenc que passa que amb la 9.04 no pugui i amb l'anterior sí.

---

### Post by pobletex on 2009-06-22
Bé, ja estic connectat sense cap problema

---

### Post by SiscoGarcia on 2009-06-23
> **pobletex said:**
> Bé, ja estic connectat sense cap problema

Si expliques com ho has aconseguit podrà servir a d'altra gent.

---

### Post by pobletex on 2009-06-24
Doncs he fet el que he comentat més amunt. He instal·lat l'intrepid ibex, m'ha reconegut la tarjeta i he connectat sense cap tipus de problema i llavors he actualitzat a la jaunty.
Res que requereixi cap filigrana. El que no sé és per què directament amb la jaunty no vaig poder.

---

