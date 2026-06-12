---
title: "Pendrive usb2.0 amb comportament 1.0"
date: 2009-06-29
forum: Catalan Team
---

### Post by mestrefona on 2009-06-29
Hola!

He mirat de trobar si algú més tenia aquest problema i no ho he sabut trobar. 

La petita història (per donar pistes):

Tinc un pendrive nou (fa mig mes) que anava força bé, fins que va decidir no sé com, que una de les carpetes no es pogués escriure ni borrar, ni tal sols des de root. 
El pendrive el faig servir indistintament amb linux i windows i agafa infeccions periòdiques de virus perquè hi ha gent bruta que no neteja els ordinadors de la feina. Jo sempre desinfecto però pot acabar quedant algun arxiu perniciós (són de propaganda de webs sobretot).
Tornem a la carpeta... mirant la mida, la tenia variable (sempre diverses GB quan el pendrive és només de 8). No hi havia manera...
I m'he decidit a formatejar i fer cau i net.
He fet el ```
sudo mkfs.vfat /dev/sdb
``` i no m'ha deixat, deia que provés amb -I
així ho he fet (```
sudo mkfs.vfat /dev/sdb -I
```), però llavors no podia canviar-li el nom al pendrive...
Ho he provat amb el gparted.
Donava error:
[CODE]GParted 0.3.8

Libparted 1.8.9

[HTML]GParted 0.3.8

Libparted 1.8.9

   Suprimeix de /dev/sdb1 (desconegut, 7.53 GiB) de /dev/sdb  00:00:01    ( SUCCESS )             calibra /dev/sdb1  00:00:00    ( SUCCESS )             camÃ*: /dev/sdb1
inici: 63
final: 15791894
mida: 15791832 (7.53 GiB)          suprimeix la particiÃ³  00:00:01    ( SUCCESS )       
========================================

   Crea una ParticiÃ³ primÃ ria #1 (fat32, 7.53 GiB) en /dev/sdb  00:00:01    ( ERROR )             crea una particiÃ³ buida  00:00:00    ( SUCCESS )             camÃ*: /dev/sdb1
inici: 63
final: 15791894
mida: 15791832 (7.53 GiB)          defineix el tipus de particiÃ³ en /dev/sdb1  00:00:01    ( SUCCESS )             nou tipus de particiÃ³: fat32          crea un nou sistema de fitxers de tipus fat32  00:00:00    ( ERROR )             mkdosfs -F32 -v -n "UNIVERSITAT" /dev/sdb1             mkdosfs 2.11 (12 Mar 2005)
       mkdosfs: unable to open /dev/sdb1
             
========================================
[/HTML]

Total, que m'he ratllat i l'he portat a formatejar a can finestra.
Tot ha anat bé, fins que he provat de copiar-hi unes carpetes. Llavors m'he adonat de la seva fantabulosa nova velocitat d'usb1.0 (me'l van vendre, i fins avui ha funcionat com a usb 2.0!!!).

En tot moment els ports usb que he utilitzat eren 2.0. He provat de copiar les mateixes carpetes en un disc dur extern usb2.0 i ha anat a la velocitat adequada (unes 10 vegades més ràpid).

Algú té la solució? Té solució?

Moltes gràcies!

---

