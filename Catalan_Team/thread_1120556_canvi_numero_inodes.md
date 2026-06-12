---
title: "canvi numero inodes"
date: 2009-04-09
forum: Catalan Team
---

### Post by guillemsola on 2009-04-09
Hola,

tinc un sistema de copies de seguretat diaries a base de rsync i links simbolics, vaja, que crea una carpeta backup per cada dia de la setmana amb links a tots els fitxers mitjançant el inode i copia realment només els fitxers que han canviat.

Bé això funciona perfecte però fa un parell de dies em va fallar el hub usb on estava el disc extern (hub que he hagut de canviar) i alguna cosa ha passat perquè ara els fitxers de la carpeta de la qual faig el backup diari han canviat d'inode. 

M'explico, aquesta carpeta és com està actualment:

> 
51611216 drwxr-xr-x   2 jaume jaume 4.0K 2008-02-25 20:41 .
50135041 drwxr-xr-x 314 jaume jaume  20K 2009-04-02 19:31 ..
51611218 -rwxr--r--   1 jaume jaume  96K 2004-02-04 09:25 nuevo-10.tif
51611219 -rwxr--r--   1 jaume jaume 122K 2004-02-04 09:25 nuevo-11.tif
51611220 -rwxr--r--   1 jaume jaume 124K 2004-02-04 09:26 nuevo-12.tif
51611221 -rwxr--r--   1 jaume jaume 130K 2004-02-04 09:27 nuevo-13.tif
51611222 -rwxr--r--   1 jaume jaume 171K 2004-02-04 09:28 nuevo-14.tif
51611217 -rwxr--r--   1 jaume jaume 126K 2004-02-04 09:17 nuevo-1.tif
51611223 -rwxr--r--   1 jaume jaume 141K 2004-02-04 09:17 nuevo-2.tif
51611224 -rwxr--r--   1 jaume jaume 159K 2004-02-04 09:18 nuevo-3.tif
51611225 -rwxr--r--   1 jaume jaume 159K 2004-02-04 09:19 nuevo-4.tif
51611226 -rwxr--r--   1 jaume jaume 145K 2004-02-04 09:20 nuevo-5.tif
51611227 -rwxr--r--   1 jaume jaume 1.1M 2004-02-04 09:21 nuevo-6.tif
51611228 -rwxr--r--   1 jaume jaume 1.1M 2004-02-04 09:22 nuevo-7.tif
51611229 -rwxr--r--   1 jaume jaume 112K 2004-02-04 09:23 nuevo-8.tif
51611230 -rwxr--r--   1 jaume jaume 111K 2004-02-04 09:24 nuevo-9.tif


Això és el que trobo llistant la còpia de seguretat de fa 2 dies.

> 
32965036 drwxr-xr-x   2 jaume jaume 4.0K 2008-02-25 20:41 .
26035204 drwxr-xr-x 314 jaume jaume  20K 2009-04-02 19:31 ..
31670421 -rwxr--r--   7 jaume jaume  96K 2004-02-04 09:25 nuevo-10.tif
31670422 -rwxr--r--   7 jaume jaume 122K 2004-02-04 09:25 nuevo-11.tif
31670423 -rwxr--r--   7 jaume jaume 124K 2004-02-04 09:26 nuevo-12.tif
31670424 -rwxr--r--   7 jaume jaume 130K 2004-02-04 09:27 nuevo-13.tif
31670425 -rwxr--r--   7 jaume jaume 171K 2004-02-04 09:28 nuevo-14.tif
31670420 -rwxr--r--   7 jaume jaume 126K 2004-02-04 09:17 nuevo-1.tif
31670426 -rwxr--r--   7 jaume jaume 141K 2004-02-04 09:17 nuevo-2.tif
31670427 -rwxr--r--   7 jaume jaume 159K 2004-02-04 09:18 nuevo-3.tif
31670428 -rwxr--r--   7 jaume jaume 159K 2004-02-04 09:19 nuevo-4.tif
31670429 -rwxr--r--   7 jaume jaume 145K 2004-02-04 09:20 nuevo-5.tif
31670430 -rwxr--r--   7 jaume jaume 1.1M 2004-02-04 09:21 nuevo-6.tif
31670431 -rwxr--r--   7 jaume jaume 1.1M 2004-02-04 09:22 nuevo-7.tif
31670432 -rwxr--r--   7 jaume jaume 112K 2004-02-04 09:23 nuevo-8.tif
31670433 -rwxr--r--   7 jaume jaume 111K 2004-02-04 09:24 nuevo-9.tif


Podeu veure que els inodes no es corresponen, també que els arxius de la copia de fa dos dies tenien 7 links i els actuals només 1.

Per molt que hi dono voltes no entenc que pot portar al disc dur a canviar els inodes de tots els fitxers.

Òbviament l'únic problema que he tingut és que ara li toca fer la còpia de nou i que durant uns dies es duplicarà el contingut però m'agradaria saber que pot haver passat.

salutacions

---

