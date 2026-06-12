---
title: "Disc Dur Extern aparentment buit"
date: 2010-11-03
forum: Catalan Team
---

### Post by Sergi17 on 2010-11-03
Hola, bona tarda a tots. Tinc un problema amb l'ubuntu, que espero pogueu ajudar-me a solucionar.

Tinc un disc Dur extern, per usb, de 500gb, on hi guardo coses importants ( per això faig servir un extern, per si hi hagués qualsevol problema per "manazas" virus o fallades )

Des d'ahir, el disc dur, és munta, però apareix buit, hi han carpetes, però en comptes de haver-hi la informació que hi ha d'haver, és mostren totes buides menys una.

Com podeu veure a la captura de pantalla, no he diu que hi han 250 i pico gb buits, però i els altres 250? on és tota la informació que hi manca?

[http://img703.imageshack.us/img703/2084/captura.png](http://img703.imageshack.us/img703/2084/captura.png)

Recientment he fet un seguit de canvis al ordinador, extrets d'aquets missatge :
[http://ubuntulife.wordpress.com/2010/11/02/mi-netbook-escritorio-de-noviembre/](http://ubuntulife.wordpress.com/2010/11/02/mi-netbook-escritorio-de-noviembre/)


Salut, i gràcies de bestreta . La informació que no trobo és summament important.

Segons el que puc veure, en la data de modificació de les carpetes, és alguna cosa que va passar ahir a la mateixa hora al mateix segon.

Si obro el disc dur a travès del terminal, m'indica les carpetes com buides. No només és un error del nautilus

---

### Post by wgarcia on 2010-11-03
Mira a les carpetes ocultes .Trash* (amb un punt endavant) que tens al disc, que no hi hagin aquests 253 gigues en aquestes carpetes. Ho pots fer posant al Nautilus (el navegador de carpetes) que ensenyi les carpetes buides, o des de la terminal com deies, fent primer
ls -a 
i després entrant a aquestes carpetes per mirar.

---

### Post by Sergi17 on 2010-11-03
Gràcies per respondre, m'he obidat de mencionar que això ja ho havia comprovat, i el .trash del disc dur extern també esta buit, però m'inquieta, que el .trash del escriptori, osigi el general em marca que hi han 116 arxius, però al obrir-lo no l'obre, es queda penjat

---

### Post by wgarcia on 2010-11-03
Mira els permisos, no sigui que hagi quedat com a sols lectura i que el teu usuari no sigui el propietari.

---

### Post by Sergi17 on 2010-11-03
> **wgarcia said:**
> Mira els permisos, no sigui que hagi quedat com a sols lectura i que el teu usuari no sigui el propietari.

Gràcies per respondre, he provat en un altre sistema, aquest amb windows , i segeix trobant les carpetes buides. Pot ser que hagui suprimit els fitxers? a la paperera em surten 132 arxius que al apretar sobre la paperera, no se m'obre, es queda pensant,i em surt el trash buit, però evidentment hi han arxius. :S

---

### Post by Martima on 2010-11-03
Hola Sergi. Des de la meva humil condició de pràcticament galàctic ignorant, intento aportar alguna cosa per si t'ha de servir d'ajuda.

Jo també vaig comprar un disc dur de 500Gb amb USB. Ara fa poc. I vaig fer una còpia de seguretat per a poder reinstal·lar l'UBNTU des de CD.

El cas és que en algun moment determinat em va gravar alguns arxius dels que apareix el nom però em diu que ocupen 0Mb. Són arxius que se m'han danyat i que he acabat perdent. No són gaires, per sort ni gaire importants al capdevall.

Amb la còpia i enganxa des de l'ordinador a la memòria USB se'm va fer malbé unes coses que en diu "particions".

He aconseguit "arreglar-ho" millorar-ho una mica, conectant la memòria a un ordinador que té el windows (espero no soni a aberració en aquest fòrum). És com si de la botiga, la memòria vingués esperant un ordinador amb windows i alguna cosa fa que no rutlli bé (per incompatibilitat??).

Prova de conectar-lo a un ordinador amb windows i mira si te les visualitza bé les carpetes. Ja que hi ets, fes una prova de la unitat, a veure que no tingui cap error.

Els arxius hi deuen ser, però se't poden haver fet malbé i no ho llegeix com toca (????)  és una teoria de collita pròpia. No em facis cas si en saps més que jo, que és molt provable. Però no hi perds res per fer la prova amb un ordinador amb windows.

Que la força t'acompanyi...

---

### Post by oriolsbd on 2010-11-04
Cal anar amb compte, perquè les dades segurament hi són, però depèn de què facis pot ser que es perdi alguna cosa.

No sé si ja ho has fet, però suposo que el millor és primer fer una comprovació física dels errors. Des d'Ubuntu, pots utilitzar el "ntfsfix", que  comprova (i arregla en cas d'errors) alguns errors molt bàsics:
[http://www.gnulinux.cat/2009/12/comprovacio-i-correccio-derrors-en-particions-ntfs/](http://www.gnulinux.cat/2009/12/comprovacio-i-correccio-derrors-en-particions-ntfs/)

Si després de passar el "ntfsfix" segueixes sense veure els fitxers, pots mirar de fer una comprovació des del chkdsk de Windows. Primer, jo miraria de fer només una comprovació (sense arreglar errors). Ara no recordo amb quin paràmetre s'havia de passar el chkdsk perquè no arregli res. Després, depenent de què et digui, fes-ho amb la opció /f (durarà pocs minuts) i després amb la /r (durarà força més, perquè comprova tots els sectors del disc dur.

Salut!

---

### Post by Sergi17 on 2010-11-07
Gràcies per respondre, aquesta nit torno a casa, i m´ho estudio bé (:

---

### Post by Sergi17 on 2010-11-07
> **oriolsbd said:**
> Cal anar amb compte, perquè les dades segurament hi són, però depèn de què facis pot ser que es perdi alguna cosa.

No sé si ja ho has fet, però suposo que el millor és primer fer una comprovació física dels errors. Des d'Ubuntu, pots utilitzar el "ntfsfix", que  comprova (i arregla en cas d'errors) alguns errors molt bàsics:
[http://www.gnulinux.cat/2009/12/comprovacio-i-correccio-derrors-en-particions-ntfs/](http://www.gnulinux.cat/2009/12/comprovacio-i-correccio-derrors-en-particions-ntfs/)

Si després de passar el "ntfsfix" segueixes sense veure els fitxers, pots mirar de fer una comprovació des del chkdsk de Windows. Primer, jo miraria de fer només una comprovació (sense arreglar errors). Ara no recordo amb quin paràmetre s'havia de passar el chkdsk perquè no arregli res. Després, depenent de què et digui, fes-ho amb la opció /f (durarà pocs minuts) i després amb la /r (durarà força més, perquè comprova tots els sectors del disc dur.

Salut!

Gràcies per la resposta, per començar, el disc dur és fat32, així que he fet servir el fsck, no vull equivocar-me i perdre tota la info, al apretar el

sudo /dev/sbd1 fsck

em dona la seguent info:

> fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
/.Trash-1000
 Start does point to root directory. Deleting dir. 
/coses series
 Start does point to root directory. Deleting dir. 
/aaaa
 Start does point to root directory. Deleting dir. 
/aaaa
 Start does point to root directory. Deleting dir. 
/aaaaa
 Start does point to root directory. Deleting dir. 
/aaaaa
.... Totes les carpetes, que marca com buides....


Reclaimed 5866435 unused clusters (192231342080 bytes).
Free cluster summary wrong (8310856 vs. really 14177291)
1) Correct
2) Don't correct


Ara que faic, segons el que puc entendre,a això eliminarà els directoris que diu ?! :S

graciess

---

### Post by Sergi17 on 2010-11-09
Odio el repost, intentaré aportar informació nova, he fet diferents proves amb altres SO però em dona el mateix resultat.

Siusplau, quansevol informació és ben rebuda (:

---

