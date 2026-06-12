---
title: "gparted i particions"
date: 2011-07-24
forum: Catalan Team
---

### Post by knuss on 2011-07-24
Hola a tothom.

Per diversos motius vaig borrar l'ubuntu per fer una instal.lació de zero. En el mateix portatil tinc el w7
. Alhora de tornar a instal.lar i fer les particions tinc la meitat del disc dur per al ubuntu , quan faig la particio
per a muntar la / (15 gb )la fa com a sda4  i com a particio primaria  i  la resta la reservo per al /home i la swap 

Ara be , en el moment que en el proces d'instal.lació faig la particio per al / em bloca la resta de memoria lliure i em diu que esta inusable i no em deixa fer la resta de particions.
Si faig les particions logiques en primer lloc si que les puc fer pero aleshores al moment d'instal.lar les torna a crear duplicant  la swap i el /home.

Sabeu que es el que faig malament ? Ja l 'he borrat tres cops ,,,,


Em sap greu pero he intentat explicarme el millor possible.

Salut !!!

Cesc

---

### Post by wgarcia on 2011-07-25
No sé si entenc del tot bé la disposició de les teves particions, però tingues en compte que sols és possible tenir 4 particions primàries, per tant si vols tenir més particions una d'aquestes particions ha de ser lògica per poder fer més particions dins d'aquesta partició lògica.

Per veure com tens la disposició de particions hi ha un petit programa molt útil que pots baixar de:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Per corre'l des d'una terminal es pot entrar:

sudo bash ~/Baixades/boot_info_script*.sh

suposant que s'ha baixat a la carpeta "Baixades" del teu escriptori, des del directori corrent simplement "sudo bash boot_info_script*.sh"

Et generarà un fitxer amb nom "RESULTS.TXT" que has d'enganxar entre etiquetes de codi (clicant # al menú de l'editor del fòrum), o adjuntar com un fitxer. 

Si inspecciones aquest fitxer "RESULTS.TXT" veuràs que fa un informe de la disposició de les particions.

---

### Post by knuss on 2011-07-25
Hola !! aqui posso el results.txt

tambe poso un parell d'imatges del que em fa el g-parted. Quan faig la particio per a muntar el " / " em bloca la resta d' espai lliure i no se com avançar arribat aqui ,,

moltes gracies per les vostres respostes

el fitxer que genera l'escript  es una passada , m'el poso a preferits ,,,,

gracies de nou

Salut !! Cesc







                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     24,578,048    24,782,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          24,782,848   420,340,399   395,557,552   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE
/dev/sda2        B68AC7E48AC79EED                       ntfs       SYSTEM RESERVED
/dev/sda3        06DCCF13DCCEFC45                       ntfs       Packard Bell

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by wgarcia on 2011-07-26
Em sembla que el problema és que la /dev/sda4 l'has de fer partició lògica, i dins d'aquesta partició et deixarà crear les particions per als punts de muntatge "/", "/home" i  "swap".

---

### Post by akyra on 2011-07-26
El que et diu en wgarcia és correcta i el més pràctic.

En el gparted només has de seleccionar l'espai lliure i fer partició lògica.
Una vegada fet això ja et permetrà fer les demés particions.

Ja diràs.

---

### Post by knuss on 2011-07-26
si però es que sempre l´havia pogut fer i m´empipa no saber perque ara no es deixa ,,,,
 
de totes maneres ho provaré així a veure si es deixa
 
vaig a provar ara,,,
 
 
Gracies de nou ,,,
 
Salut !!!
 
Cesc

---

### Post by knuss on 2011-08-02
Be al final no he tingut mes remei que fer-ho amb una partició logica  i a quedat així,,,



De totes maneres moltes gracies a tothom !!

Salut !!!

Cesc

---

### Post by wgarcia on 2011-08-03
És que no hi ha més remei que la partició lògica si vols tenir més de 4 particions, sols s'admeten 4 particions primàries per restriccions inicials (qui es podia imaginar fa 25 anys que s'acabarien necessitant més de 4 o pel que fa a la memòria RAM més de 640 kbs?)

Penso que ha quedat bé.

---

### Post by knuss on 2011-08-05
doncs una vegada mes us dono les gracies !!


Salut!!!

vaig a intentar tencar el post ....

Cesc

---

