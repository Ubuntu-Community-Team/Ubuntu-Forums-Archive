---
title: "com entrar directament en mode consola"
date: 2009-07-27
forum: Catalan Team
---

### Post by indiosincracia on 2009-07-27
Tinc una cassola de pentium III amb 190Mb sense disc dur, el xubuntu jaunty s'engega però va mooooo... ...ol't lent, m'he fet un remastesys de xubuntu jaunty amb l'ssh, lynks, i altres punyetes que no venen amb els CD-Live's.
hi ha alguna combinació de tecles que permeti entrar directament en mode consola abans que s'engeguin les X?
en algunes distribucions et surt la opció al "Boot:" (ex: al knoppix, "Boot: knoppix 2" entra directament a la terminal), però al meu menú no hi es.

Gràcies d'avantmà.

---

### Post by SiscoGarcia on 2009-07-27
Si entres a les opcions d'arrencada no hi ha la possibilitat d'entrar en "recovery mode"?

---

### Post by indiosincracia on 2009-07-28
El menu que m'apareix és aquest:
For the default live system, press ENTER or enter 'live'
To start in safe graphics mode, enter 'xforcevesa'
To start the installer directly, enter 'install'
To verity the CD for errors enter 'check'
To run memtest 86+ enter 'memtest'
To boot from the first hard disk, enter 'hd'

fent Control+Alt+F1 o Control+F2 no passa res, potser m'he d'instal·lar algun mòdul al kernel?

---

### Post by pauelmaco on 2009-07-28
En Ubuntu no sé com es fa, però pots provar de fer servir una altra distribució, Slax ([www.slax.org](www.slax.org)), que pot engegar-se en mode només consola, en fluxbox o en KDE, tu tries. En mode live cd gasta 30mb de ram en mode consola, així que et funcionaria bastant bé, i en fluxbox, necessita 96mb. A part, es pot instalar en un pendrive.

Per provar no hi perds res :)

Sort!

---

### Post by indiosincracia on 2009-07-28
Ja ho vaig provar, pero com necessito intalar nous programes, no vull instalar-los cada cop, encara que siguin modulars, per cert, slax tampoc no es deixa instal·lar al disc dur per fer unes quantes reformes.

---

### Post by papapep on 2009-07-28
Has provat a editar la línia d'arrencada del nucli i afegir-li el paràmetre "single"?

---

### Post by pauelmaco on 2009-07-29
No pateixis, slax si que es pot instalar al disc dur. Segueix els passos que et diuen aquí. Es pot instalar en grub:

  - [http://www.slax.org/forum.php?action=view&parentID=37269&highlight=hard%20disk%20install%20jcsoh](http://www.slax.org/forum.php?action=view&parentID=37269&highlight=hard%20disk%20install%20jcsoh)

També, pots modificar la iso per a tenir els mòduls que t'agraden sempre que arrenquis el sistema. Simplement et descarrègues l'slax per a usb, el descomprimeixes, poses els moduls que vols a la carpeta /slax/modules o /slax/base i executes l'script "make_iso.sh" que trobaras o a la carpeta "boot" o a la carpeta "slax". D'aquesta manera tindras una iso personalitzada amb els mòduls que vulguis que sempre estaran activats quan l'engeguis. Per altra banda, amb una instalació al pendrive o al disc dur, els mòduls que hagis activat un cop, per la pròxima vegada que ho engeguis, ja estaran activats.

Sort!:P

---

### Post by anigwei on 2009-07-30
> **indiosincracia said:**
> Tinc una cassola de pentium III amb 190Mb sense disc dur, el xubuntu jaunty s'engega però va mooooo... ...ol't lent, m'he fet un remastesys de xubuntu jaunty amb l'ssh, lynks, i altres punyetes que no venen amb els CD-Live's.
hi ha alguna combinació de tecles que permeti entrar directament en mode consola abans que s'engeguin les X?
en algunes distribucions et surt la opció al "Boot:" (ex: al knoppix, "Boot: knoppix 2" entra directament a la terminal), però al meu menú no hi es.

Gràcies d'avantmà.


Bones, 

Quan està instal·lat li pots passar la opció **single**. Suposo que des de'l LiveCD, també.

Salut,

---

