---
title: "Eliminar partició  anterior  ubuntu"
date: 2009-06-25
forum: Catalan Team
---

### Post by pserra on 2009-06-25
Hola,
després de fer una imprudència (mea culpa) amb l'ubuntu, se'm va inutilitzar i se'm va ocórrer (potser una altre imprudència) de tornar-lo a instal_lar però se'm va crear a un altre directori.
I com es pot fer, sense que se'm resenteixi la actual partició de eliminar l'anterior instal·lació i cedir-li l'espai a l'actual?
pels foros he trobat informació, però tinc molts dubtes i por de
tornar-la a liar....

MERCI COMPANYS

A continuació poso sortida terminal particions:



pere@pere-portatil:~$ sudo fdisk -l

Disc /dev/sda: 320.0 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fca1fd5

Dispositiu Arrenc. Inici Final Blocs Id Sistema
/dev/sda1 * 1 13462 108133483+ 7 HPFS/NTFS
/dev/sda2 37632 38913 10292224 7 HPFS/NTFS
/dev/sda3 36059 37631 12635122+ 5 Estesa
/dev/sda4 13463 36058 181502370 7 HPFS/NTFS
/dev/sda5 36059 36362 2441817 83 Linux
/dev/sda6 36363 36384 176683+ 82 Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc

Disc /dev/sdb: 8065 MB, 8065646592 octets
25 heads, 25 sectors/track, 25205 cylinders
Units = cilindres of 625 * 512 = 320000 bytes
Disk identifier: 0x04030201

Dispositiu Arrenc. Inici Final Blocs Id Sistema
/dev/sdb1 4 25206 7875564 b W95 FAT32

---

### Post by sianeu on 2009-06-25
Quant et demani com vols les particions, marques MANUAL. En el partidor cliques a la partició sda5 (linux) i pulsa EDITAR:
El tamany el deixes tal cual.
Al sistema de fitxers escolleixes ext3 o ext4 (al gust).
Al punt de muntatge escolleixes "/".

Cliques a següent i la resta es com el primer cop. Abans d'aplicar els canvis t'en farà un resum i t'en demanarà conformitat.

Salut

---

### Post by pserra on 2009-06-25
Hola Sianeu,
que vols dir, tornar a instal·lar ubuntu?? no seria (penso jo,més fàcil donar-li més espai a la particio on tinc ara el ubuntu??
ja el tinc bastant (adaptat...)
adjunto pantalla Gparted.Volia eliminar les particions unallocalled i l'espai donar-li a la particio ubuntu, però amb el boto dret no em surt cap opció....

MERCI

---

### Post by akyra on 2009-06-26
Hola pserra,

A on tens la teva partició /home? És la partició realment important a on es guarden totes les configuracions que tenim a l'ubuntu en arxius ".el_que_sigui".

Crec que seria bó que a on tenies instal·lat el ubuntu Ç(paritició "/"" el reinstalesis a sobre o formatesis la partició i el tornesis a instal·lar de nou.

Com a dit en seianeu, hauries de dir-li cada punt de muntage quin és: el "/", el "/home" el "swap" i les que tens de windows.

No crec que tinguis gaire més problema a recuperar-lo com estava abans.

Espero haver-te ajudat.

Adeu

---

### Post by pserra on 2009-06-26
Hola companys,
ja escric des de la nova particio creada segons consells d'akyra, però ara, com elimino la particio anterior creada a sd5 sense malmetre rés??
quan tingui actualitzat el sistema passaré pantalla gparted.

---

### Post by jhnotario on 2009-06-26
Hola pserra.
Et recomano que instal·lis Gparted, que es un gestor de particions com el Partition Magic de Windows.

```
sudo apt-get install gparted
```

o bé desde Synaptic. Quan el tinguis instal·lat, podras fer tot el que necesitis amb las particions. Només has de tenir en compte desmuntar els volums que necesitis modificar, ja que si no et surtira com bloquejat.

---

### Post by akyra on 2009-06-26
Hola pserra,

M'alegro que comenci a funcionar.

Que hi tens en la sda5?

Per eliminar la /dev/sda5, haurias d'iniciar el gparted seleccionar-la i eliminar-la. Et quedarà un espai sense assignar. Després la podries afegir a la sda3.


Si instal·las el gparted, com diu en jhnotario, ho podries fer.
Per desmuntar una unitat, des de la linea de comandes fes umount /dev/sda5.

Ja diràs com vas.

Salutacions.

---

### Post by pserra on 2009-06-26
Merci Akyra per el teu ajut,
actualment ho tinc  tal com adjunto el gparted,
demà ja miraré d'aplicar el teu darrer missatge. ara m'acabo de tornar a connectar i ho deixaré per dema.
Meri per tot.

---

### Post by pserra on 2009-06-26
em deixzava adjuncio gparted

---

### Post by pserra on 2009-06-26
Hola,
deixo sortida fdisk
una pregunta, al arrencar no em carrega les particions NTFS, la manera més fàcil quina és de fer que al engegar m'ho carregui tot?

255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fca1fd5

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       13462   108133483+   7  HPFS/NTFS
/dev/sda2           37632       38913    10292224    7  HPFS/NTFS
/dev/sda3           36059       37631    12635122+   5  Estesa
/dev/sda4           13463       36058   181502370    7  HPFS/NTFS
/dev/sda5           36059       36362     2441817   83  Linux
/dev/sda6           36363       36384      176683+  82  Intercanvi Linux / Solaris
/dev/sda7           36385       37631    10016496   83  Linux

Les entrades a la taula de particions no estan en l'ordre del disc

Disc /dev/sdb: 8065 MB, 8065646592 octets
25 heads, 25 sectors/track, 25205 cylinders
Units = cilindres of 625 * 512 = 320000 bytes
Disk identifier: 0x04030201

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdb1               4       25206     7875564    b  W95 FAT32
pere@pere-portatil:~$

---

### Post by sianeu on 2009-06-27
El millor es editar el fstab, hi han molts fils que en parlen. Però si no t'en surts mira això 

[http://ubuntuforums.org/showthread.php?t=1151704]("http://ubuntuforums.org/showthread.php?t=1151704")


Salut

P.D: Per al pròxim cop, hauries d'obrir un altre fil per a un tema nou. Obre'l si has de seguir preguntant sobre les particions al inici.

---

### Post by pserra on 2009-06-27
Merci Sianeu per l'enllaç, ho he solventat sense modificar fstab i ha anat perfecte, molt fàcil.
Encara tinc pendent eliminar l'antiga particio de ubuntu la que em va quedar saturada, sense prendre mal.... com ho puc fer??

MERCI SIANEU

---

### Post by sianeu on 2009-06-27
Suposo que et referixes a sda5. Unir-la a sda7 (l'actual "/") es una moguda, per que tens pel mitg la swap (sda6), i tot plegat son poc més de dues gigas. Jo simplement eliminaria el que hi ha (o pots formatar amb gparted) i la faria servir com a partició de dades per ubuntu (programes, manuals, copies de seguretat........). Ja que no tens el /home a un altre particiò, al menys tindries les dades d'ubuntu separades de les del finestres.

Si de totes maneres vols fer-ho el gparted ho fa, pero no m'atraveixo a guiar-te per que no ho he fet mai. Però al no ser particions contigües hi ha més risc d'error. Al instal·lar de nou hauries d'haver eliminat sda5 i sda6 i tornat a crear la swap i la "/". Quan hagis de tornar a instal·lar, elimina les tres (sda5, sda6, i sda7) i reorganitza l'espai amb dues ("/" i swap) o tres ("/" "/home" i swap) particions.

Salut

---

### Post by pserra on 2009-06-27
Merci pel consell Sianeu, 
tens raó tot plegat no val la pena, 
provaré de formatejar-ho i per alguna cosa el faré servir....
Merci per la teva AJUDA  i consells que van molt bé...

---

