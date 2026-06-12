---
title: "Error muntar disc"
date: 2011-03-05
forum: Catalan Team
---

### Post by venusfenix on 2011-03-05
Buenas,

fa un temps que porto amb aquest error, i es que vaig intentar cambiar el nom d'un dels disc durs, de sdb1 a Fitxers, desde llavors, quan arrenca el sistema, i intentar muntar el disc dur Fitxers, en dona error, en canvi el disc sdb1 el munta sense problemes.
voldria saber com desfer aquest error.

gracies,

---

### Post by wgarcia on 2011-03-05
Quan dius que l'has canviat el nom al disc sdb1, exactament què vas fer?

Una altra cosa que pot ser útil és enganxar el resultat de donar la instrucció:


sudo fdisk -l

a una terminal, perquè mostrarà tots els discos que veu el teu sistema.

---

### Post by venusfenix on 2011-03-06
buenas Wgarcia,

aqui tens el resultat:


Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e9b4b0f

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       18799   151002936   83  Linux
/dev/sda2           18800       19457     5285354+   5  Estesa
/dev/sda5           18800       19457     5285353+  82  Intercanvi Linux / Solaris

Disc /dev/sdb: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1e9b4b0e

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1   *           1       18820   151171618+   7  HPFS/NTFS
/dev/sdb2           18821       19457     5116702+  82  Intercanvi Linux / Solaris

---

### Post by wgarcia on 2011-03-07
Segons el que mostra "fdisk -l" tens linux al disc sda i suposo que windows al disc sdb, tot i que hi ha una partició swap de linux al disc sdb. 

Una altra cosa que pot ser útil es veure el contingut del fitxer "fstab" que és on es munten els discos a l'arrencada:

cat /etc/fstab

t'ho mostrarà.

---

### Post by venusfenix on 2011-03-07
buenas,

no, son 2 discs durs independents, no tinc windows en aquest ordinador.
sdb1 es un disc dur amb informacion, un "mis documentos"

paso el contigut de Fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                   proc         defaults                                               0  0  
/dev/sda1                                  /                       ext3         relatime,errors=remount-ro                             0  1  
/dev/sdb1                                  /media/Fitxers Sistema  ntfs-3g      defaults,owner,users,user,locale=ca_ES.UTF-8@valencia  0  0  
/dev/sda1                                  /media/sda1             ext3         defaults                                               0  0  
/dev/sdb1                                  /media/sdb1             ntfs         defaults                                               0  0  
/dev/sda5                                  none                    swap         sw                                                     0  0  
/dev/scd0                                  /media/cdrom0           udf,iso9660  user,noauto,exec,utf8                                  0  0  
/dev/sdb2                                  /media/sdb2             swap         defaults                                               0  0  
/dev/sda5                                  /media/sda5             swap         defaults                                               0  0  
/dev/sdb2                                  /media/sdb2             swap         defaults                                               0  0  

UUID=d3fe6c4d-6870-43a8-b86d-3fd22311c0c5  none                    swap         sw

---

### Post by venusfenix on 2011-03-07
sense saber res, veig que estic montant 2 vegades sda1, sdb1 (amb dos noms diferents?) i sdb2 (swap), i per postres, l'ultima linea em sembla que es sbd5 de segones.

---

### Post by wgarcia on 2011-03-07
Doncs ja en saps molt, perquè sembla que és exactament el problema que no et deixa muntar el disc. Per tant es tracta d'esborrar les línies duplicades. Això ho pots fer obrint una terminal i entrant:

gksudo gedit /etc/fstab

Ara a l'editor que s'obre has d'esborrar les dues línies, jo esborraria les segones versions dels punts de muntatge que tens entrades, i llavors hauria de quedar així:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
/dev/sda1 / ext3 relatime,errors=remount-ro 0 1
/dev/sdb1 /media/Fitxers Sistema ntfs-3g defaults,owner,users,user,locale=ca_ES.UTF-8@valencia 0 0
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb2 /media/sdb2 swap defaults 0 0
/dev/sda5 /media/sda5 swap defaults 0 0
/dev/sdb2 /media/sdb2 swap defaults 0 0

UUID=d3fe6c4d-6870-43a8-b86d-3fd22311c0c5 none swap sw 

```

Compte de simplement esborrar aquestes dues línies i no fer cap altre canvi, perquè aquest fitxer és clau perquè el teu sistema comenci correctament i si queda danyat no s'iniciarà. Es pot arreglar en aquest cas, però ja es tracta d'un procediment més complicat.

---

### Post by venusfenix on 2011-03-07
buenas,

donat que l'error nomes el tinc, i pel que sembla amb la linea de /dev/sdb1 /media/Fitxers, em sembla que probaré posan un # en aquesta linea.

keep on line.

---

### Post by venusfenix on 2011-03-07
dit i fet, problema resolt!!

per cert, com es faria un equivalent de scandisk i defrag en ubuntu?
es l'unica cosa que faltaria fer ara i llestos!

merci!!

---

### Post by wgarcia on 2011-03-08
A linux no fa falta defragmentar, el sistema de fitxers (ext3 o més recentment ext4) no es fragmenta, no ho sé tècnicament però em sembla que està relacionat amb el sistema de "journal" que utilitza, que a més és molt més ràpid que altres sistemes de fitxers. 

Per verificar errors al disc ja ho fa automàticament després d'unes quantes arrencades (ara mateix de memòria no recordo quantes), però si vols fer-la abans que ho faci automàticament es pot fer amb la instrucció des d'una terminal:

fsck /dev/sda

per exemple, i si vols forçar que ho faci a la següent arrencada:

sudo touch /forcefsck

---

