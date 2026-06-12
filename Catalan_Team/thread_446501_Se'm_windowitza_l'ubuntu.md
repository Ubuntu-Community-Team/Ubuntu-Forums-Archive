---
title: "Se'm windowitza l'ubuntu"
date: 2007-05-17
forum: Catalan Team
---

### Post by quisoc on 2007-05-17
Sí sí, ja sembla windows... 
Tinc un disc dur extern, usb. Al cap d'unes hores de tindre'l conectat, passa, per art de màgia, a ser de només lectura. L'extrec, el torno a conectar, i segueix com de només lectura.
Alguna idea de que pot passar?
Uitlitzo kubuntu 7.04

---

### Post by CarlesOriol on 2007-05-17
El teu disc deu tenir errors.

Quan això passa el nucli desmunta el disc i el torna a muntar en mode lectura per seguretat.

Desmunta'l amb sudo umount /dev/(nomdeldispositiu) 

i després el comproves amb sudo fsck -p /dev/(nomdeldispositiu) 

...i per cert... el windows no t'avisa i segueix treballant fins que la destrossa no l'arregla ni déu.

---

### Post by patrickfromspain on 2007-05-17
jo dic el mateix que CarlesOriol.. o el sistema Fat esta fotut o sera el propi disc dur. Jo tinc aqui un Western Digital extern de 120 gigues en fat32 i va perfecte.

salut!

---

### Post by quisoc on 2007-05-17
Hola,
     he fet el fsck -p però em deia opció incorrecta. N'he provat d'altres, m'ha trobat errors, sembla que alguns els ha corregit, però fent un sudo fsck, segueix dient-me això:

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action

Li posi l'opció que li posi, sempre em torna a sortir.

---

### Post by jpcman on 2007-06-14
quisoc, company.... ara que pots tenir les dades en NTFS i pots llegir/escriure... per què vols tenir-ho en FAT32??  ;-)

---

