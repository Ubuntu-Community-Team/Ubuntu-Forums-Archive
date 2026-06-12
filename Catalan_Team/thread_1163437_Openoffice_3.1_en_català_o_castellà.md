---
title: "Openoffice 3.1 en català? o castellà?"
date: 2009-05-18
forum: Catalan Team
---

### Post by gondle on 2009-05-18
Hola,   He aconseguit instal·lar l'Openoffice.org 3.1 mitjançant fonts de programari. El problema és que se m'instal·la en anglès. Supose que la raó serà que no està disponible encara en català. Però he vist que sí ho està en castellà. M'agradaria saber si és possible instal·lar l'Openoffice en castellà si tinc l'Ubuntu 8.10 en català. Ja sé que és possible canviar l'idioma principal a castellà; però si ho faig de la manera que jo sé, m'instal·larà a partir d'aleshores tots els programes en castellà i jo només vull aplicar-ho a l'Openoffice.  PD: Aquesta pregunta podria haver-la fet més general i estaria bé que algú em tragués de dubtes. Com puc instal·lar un programa en castellà des dels repositoris d'Ubuntu sense haver de canviar tot l'idioma predeterminat de tots els altres programes? Espere haver-me explicat bé.

---

### Post by kimet on 2009-05-18
Al openoffice has d'instalar els paquets d'idiomes apart, busca'ls al synaptic.
 salut.

---

### Post by oriolsbd on 2009-05-19
En Gondle té raó. En instal·lar l'OpenOffice 3.1 a partir dels repositoris de Launchpad (suposo que ho has fet així, oi?) es desinstal·len directament els paquets d'idioma, que són per a la versió 3.0. De moment, jo ho he deixat en anglès, perquè amb OpenOffice 3.1 s'ha millorat moltíssim la compatibilitat amb el format "docx", i realment necessito poder obrir aquest tipus de fitxers de forma fiable.

Salut!

---

### Post by kimet on 2009-05-19
Vaja, no hi havia caigut...

Prova a instal.lar-los desde aquí:

[http://packages.debian.org/sid/localization/](http://packages.debian.org/sid/localization/)

Salut.

---

### Post by gondle on 2009-05-19
Moltes gràcies kimet y oriolsbd. He pogut canviar l'idioma a català des del lloc que ha dit kimet. De totes maneres, com diu oriolsbd he instal·lat Openoffice 3.1 des dels repositoris de Launchpad. M'agradaria saber com anar canviant d'idioma a l'openoffice. Dieu que es fa instal·lant els paquets al synaptic. Però com els trobe en català? Quina terminació he de buscar entre tots els arxius que m'apareixen? És possible que encara no estiga al Launchpad? (Tot i que m'estranya perquè està inclús el basc)  Oriosbd, has provat a canviar l'idioma del teu Openoffice, com ho faries des dels repositoris?  PD: Si intente instal·lar l'ajuda en castellà de l'Openoffice des dels repositoris, m'obliga a desinstal·lar tot l'Openoffice, això és un poc estrany,no?  Ah, i moltes gràcies de nou!

---

### Post by kimet on 2009-05-19
Hola.

> Però com els trobe en català? 

-Posant al buscador de synaptic "openoffice" et sortiràn tots els paquets relacionats. 

> És possible que encara no estiga al Launchpad?
Si, és possible. 

> Si intente instal·lar l'ajuda en castellà de l'Openoffice des dels repositoris, m'obliga a desinstal·lar tot l'Openoffice, això és un poc estrany,no?
 No estaràs intentant instal.lar un paquet per a una versió diferent? En aquest cas synaptic et canviarà la versió del programa que tens instal.lada per la del paquet que vols instal.lar.(tens varis repositoris amb versions diferents dels mateixos programes)):P

---

### Post by oriolsbd on 2009-05-19
Hola, Gondle.

Per resumir una mica, els repositoris estan de la següent manera:
- Als repositoris estàndar d'Ubuntu hi ha l'OpenOffice 3.0, amb tots els paquets d'idioma, d'ajuda, etc.
- Als repositoris del Launchpad (que tant tu com jo ens hem configurat de manera "manual") hi ha l'OpenOffice 3.1, però sense els seus paquets d'idioma.

Quan intentes instal·lar el paquet d'idioma de l'OpenOffice, realment t'està agafant els dels repositoris estàndar (OpenOffice 3.0). Per això detecta que són "incompatibles" amb els que tens instal·lats del Launchpad (OpenOffice 3.1) i et diu que vol desinstal·lar l'OpenOffice (3.1) per posar els paquets d'idioma del 3.0.

A partir d'aquestes dades, si només tirem de repositoris, tens dues opcions: tenir OpenOffice 3.0 en català o tenir OpenOffice 3.1 en anglès.

Ara bé, tenint en compte el missatge del Kimet (per cert, MOLTES GRÀCIES, KIMET :-) , perquè jo no sabia com fer-ho), podem tenir OpenOffice 3.1 en català (jo ja ho he fet, i va bé). Per a fer-ho, ves a l'enllaç que ens ha passat. Allà, fes clic sobre el paquet "openoffice.org-l10n-ca", que veuràs que ja és per a la versió 3.1. Aniràs a la pàgina de descripció del paquet. Al final de tot, veuràs que et pots baixar el paquet (és un fitxer .deb). El deses a qualsevol directori del teu ordinador, hi vas des d'un terminal i executes:
```
sudo dpkg -i openoffice.org-l10n-ca_3.1.0-2_all.deb
```
Obres l'OpenOffice 3.1, i ja el tens en català. :-)

Salut!

---

### Post by gondle on 2009-05-19
Moltes gràcies kimet i oriolsbd. Això era el que volia saber. M'ha quedat tot claríssim. Porte set mesos intentant entendre-ho, però fins ara no m'havia quedat clar del tot el tema dels repositoris de Launchpad sobre l'Openoffice (sobretot l'explicació d'oriolsbd). Una abraçada, estic molt agraït, tema solucionat.

---

### Post by okekarito on 2009-05-21
Hola,

us voldria donar les gràcies perquè fa uns dies vaig actualitzar al 3.1 i em tenia fregit. Primer em va fer algunes desgràcies de configuració amb el teclat (no sé perquè, en teoria no hauria d'haver passat res, però ...) i després no hi havia manera de tenir-lo en català.

En fi, gràcies per la solució.

---

