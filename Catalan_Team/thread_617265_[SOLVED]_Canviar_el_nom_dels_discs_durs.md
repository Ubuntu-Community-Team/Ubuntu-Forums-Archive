---
title: "[SOLVED] Canviar el nom dels discs durs"
date: 2007-11-19
forum: Catalan Team
---

### Post by patrickfromspain on 2007-11-19
Hola gent!

Aquest cap de setmana m'he insta&#320;lat Fedora Core 8 per jugar una mica i veure altres mons. El cas es que sembla que ha fet algun disbarat: m'ha posat etiquetes als discs.

Al windows, fer-ho era molt facil: Mi PC, boto dret sobre el disc i alla ho canviava al que volia, i aixi la D: era Dades i la C: Sistema. Bé, doncs despres d'insata&#320;lar Fedora, a l'escriptori hi veig /media/Dades on abans hi deia simplement dades.

Doncs be, he buscat una mica i no se com arreglar-ho.. algun hem sap dir quelcom? 

Per cert, la particio esta en ext2.

salut!

---

### Post by jerec on 2007-11-19
Facil!!, això esta al fitxer /etc/fstab que es on li dius el punt de muntatge del dispositu, sigui un disc dur, usb, cdrom, dvd , etc.

Exemple:
/dev/scd1               /media/dvd      udf,iso9660 user,noauto     0       0

Això el que em fa es que un dvd m'el munta al directori /media/dvd

(compte que no canviis l'arrel que ha d'estar a : /)

---

### Post by patrickfromspain on 2007-11-19
No, hem temo que no. El fstab no esta canviat, hi surt el mateix que abans: 

/dev/sda /media/dades ext3 opcions

De totes formes ja ho he averiguat. Es fa amb les eines e2label y tune2fs -L. El problema esta en que no reiniciava i per aixo no s'actualitzava l'etiqueta. 

gracies per contestar :)

---

