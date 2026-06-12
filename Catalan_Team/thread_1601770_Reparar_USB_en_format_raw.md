---
title: "Reparar USB en format raw ?"
date: 2010-10-20
forum: Catalan Team
---

### Post by jaumevegas on 2010-10-20
Hola a tots,
vaig crear un disc d'arrancada d'Ubuntu en un USB de 2Gb i com que em pensava que s'havia penjat, el vaig cancel·lar. Ara el disc m'ha passat de 2 Gb a 8 MB i l'Ubuntu no el reconeix i el Windows el reconeix però només amb 8Mb. He provat de formatar-lo però em dóna error. He provat diferents programes del windows per a reparar l'USB però tots amb el mateix resultat : ERROR (HP USB Disk Storage Format Tool, HDD Low Level Format Tool, Administrador de dispositius de Windows, ...).
Amb l'Ubuntu he provat amb ordres del tipus de format, amb programes com el gparted, ...
 
Buscant per internet he deduït que estava en format raw, per això de la reducció de memòria que ha fet. També podria tenir problemes de partició, ...
El nom que té ara l'USB és ChipsBnk Flash Disk (per si us dóna alguna informació).
 
Algú em pot ajudar ?
Moltes gràcies a l'avançada.

---

### Post by epileg on 2010-10-20
Prova a esborrar i després crear una partició fat16 o fat32 de tota la unitat amb Gparted.

Salut,

---

### Post by jaumevegas on 2010-10-20
Hola de nou, tinc problemes ja que amb Ubuntu ja no em munta l'USB i per tant no sé què he de fer per esborrar-lo. Com es pot fer si no es munta ? Amb la utilitat de discs de l'Ubuntu i el gparted em diuen que es troba a /dev/sdd però sense numerar.
Gràcies.

---

### Post by epileg on 2010-10-20
Es que per esborrar una partició, aquesta ha d'estar desmuntada, sinó el sistema no t'ho permetria.
Per fer el que et dic, has d'obrir el gparted i seleccionar l'a unitat,en el teu cas /dev/sdd, després mira quines particions hi han, si n'hi ha alguna, la selecciones i li dius que la esborri, ho pots fer amb el botó dret del ratolí. Un cop fet això has d'aplicar els canvis, tot fent clic al botó verd amb el check. Repeteix el procés si hi ha més d'una partició. Un cop fet això, a l'espai lliure que et quedi crees una nova partició fat16 o fat32 que ocupi tota la unitat, i després tornes a confirmar amb el botó amb el check vard.

Sort!

---

### Post by jaumevegas on 2010-10-20
Hola, amb el gparted em surt /dev/sdc (7.84 MiB)
Partició : no assignat (i un triangle amb un signe d'admiració)
Sistema de fitxers : no assignat (i un quadrat gris)
Mida : 7.84 MiB

Ja no surt res més.
No em deixa suprimir ni res

Amb el botó dret només em deixa fer nou i informació.
Si premo nou em diu :

[SIZE=2]**No partition table found on device /dev/sdc**[/SIZE]
A partition table is required before partitions can be added.
To create a new partition table choose the menu item:
Device --> Create Partition Table.

Ara el tinc connectat directe al PC i no en un hub i per això em diu que ara es troba a /dev/sdc.

A l'hora de crear una taula de particions com que el volum és de 7.84 MiB no em surt el fat ni el fat32. Només msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun i loop.
He provat de fer-ne algun però el resultat és el mateix, es queda igual.
Gràcies.

---

### Post by epileg on 2010-10-20
Vés al menú dispositiu > Crea una taula de particions, que ha de ser msdos.
Després crea la partició. Ja t'apareixeran els tipus de format fat16 i fat32.

Si vols alguna cosa més, ara soc al canal #ubuntu-cat de irc.freenode.net

---

### Post by jaumevegas on 2010-10-21
Hola de nou, he intentat crear la taula de partició i no dóna error.
Llavors per a fer la partició em diu l'error de sempre :

[SIZE=2]**No partition table found on device /dev/sdc**[/SIZE]
A partition table is required before partitions can be added.
To create a new partition table choose the menu item:
Device --> Create Partition Table.

D'aquí no passa, no sé pas com arreglar-ho.
Gràcies.

---

### Post by epileg on 2010-10-21
Doncs no té bona pinta això. Jo he fet proves amb un pen meu, i ho fa sense problemes. Que té alguna pestanya que faci el teu pen de només lectura? Suposo que nop

Prova a insta&#320;lar tesdisk, munta el pen i executa
# sudo testdisk
a veure si et repara la taula de particions.
També post provar l'aplicació gpart.

Sort!
Salut,

---

### Post by jaumevegas on 2010-10-21
Hola, he provat el testdisk i el gpart. No sé massa com funcionen però mirant manuals ho he pogut saber :

El testdisk no em troba cap partició i si en creo una em surt com a partition unknown
Però com he dit abans no entenc aquest programa ni el sé fer funcionar.

El gpart tampoc em troba cap partició.

Potser si que té mala pinta això.

---

### Post by epileg on 2010-10-21
No ho sé, com a últim recurs provaria a fer un
# sudo cfdisk /dev/sdc
A veure si així et permet crear/modificar/suprimir particions.

Sort!
Salut,

---

### Post by jaumevegas on 2010-10-22
Hola, no me'n surto. És igual ho deixem córrer ja que em sembla que no té solució.
Moltes gràcies per tot.

---

