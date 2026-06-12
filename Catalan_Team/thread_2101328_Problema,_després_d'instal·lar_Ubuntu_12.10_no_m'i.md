---
title: "Problema, després d'instal·lar Ubuntu 12.10 no m'inicia W7."
date: 2013-01-04
forum: Catalan Team
---

### Post by TRYCAS73 on 2013-01-04
Hola a tots.
 
                         La partició de W7 la tinc al disc &#8220;sdb&#8221; i la de  Ubuntu amb XP al &#8220;sda&#8221;. Al GRUB surt Ubuntu i Windows7, Xp no (es igual  no passa res), a mi les dues que m'interessen son Ubuntu i W7, ja que  la de W7 tenim configurat el correu de Telefònica i els certificats  digitals per accedir a pagines que ho requereixen, potser es pugui  passar tot aixo a Ubuntu, però la meva dona es mou millor a W7 i jo ara  començo a fer les meves primeres passes amb Linux.

> **wgarcia said:**
> Respecte al problema que no es vegi el W7, si no  has fet servir tot el disc per instal·lar l'Ubuntu, el W7 hauria de  tenir una partició encara al disc. 

Per veure si és així, es pot obrir una terminal (ALT-F2 i entra "terminal" sense les cometes) i un cop oberta la terminal entra:

```
sudo fdisk -l
```i prem INTRO. 

Aquí es podran veure les particions que hi ha al disc i si encara hi és la partició de W7.



    Com el company **wgarcia** m'ha explicat he executat la instrucció esmentada al terminal i el resultat es aquest:
 

 jlgt73@jlgt73-System-Product-Name:~$ sudo fdisk -l 
 [sudo] password for jlgt73:
  
 Disk /dev/sda: 250.1 GB, 250059350016 bytes 
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x51dc51dc 
  
 Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema 
 /dev/sda1   *          63   209712509   104856223+   7  HPFS/NTFS/exFAT 
 /dev/sda2       209712571   488396799   139342114+   f  W95 Estesa (LBA) 
 /dev/sda5       209712573   259712572    25000000   83  Linux 
 /dev/sda6       259713024   262713343     1500160   82  Intercanvi Linux / Solaris 
 /dev/sda7       262715392   488396799   112840704   83  Linux 
  
 Disk /dev/sdb: 251.0 GB, 251000193024 bytes 
 255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x395e395d 
  
 Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema 
 /dev/sdb1   *          63   490207409   245103673+   7  HPFS/NTFS/exFAT 
 

 Gracies per la seva ajuda.

---

### Post by wgarcia on 2013-01-04
Sembla que sí que hi són les particions de W7, segons el resultat que enganxes de fdisk. Són les dues primeres particions del disc al qual el sistema l'assigna el dispositiu /dev/sda. Per tant sembla que sols es tracti d'actualitzar el programa d'arrencada "grub" perquè vegi la instal·lació de W7 i mostri l'opció d'iniciar en aquest sistema operatiu. Per fer això, un cop iniciat l'escriptori de Linux, des d'una terminal també es pot fer:

```
sudo update-grub
```

Guarda una còpia de la sortida d'aquesta comanda per si no funcionés finalment aquest procediment. 

A veure si això ho arregla.

---

### Post by TRYCAS73 on 2013-01-04
> **wgarcia said:**
> Sembla que sí que hi són les particions de W7, segons el resultat que enganxes de fdisk. Són les dues primeres particions del disc al qual el sistema l'assigna el dispositiu /dev/sda. Per tant sembla que sols es tracti d'actualitzar el programa d'arrencada "grub" perquè vegi la instal·lació de W7 i mostri l'opció d'iniciar en aquest sistema operatiu. Per fer això, un cop iniciat l'escriptori de Linux, des d'una terminal també es pot fer:

```
sudo update-grub
```Guarda una còpia de la sortida d'aquesta comanda per si no funcionés finalment aquest procediment. 

A veure si això ho arregla.

                                  Hola wgarcia.
 

    Vols dir que he de fer una copia del GRUB abans de introduir aquesta instrucció al terminal? Com la puc fer?

---

### Post by TRYCAS73 on 2013-01-04
Quan inicio el GRUB hi ha la opció d'editar l'accés a W7 i hi han unes línies d'instruccions, però no se si estan be:
 

 ### BEGIN /etc/grub.d/30_os-prober ### 
 menuentry 'Windows 7 (loader) (a /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-01CDE918A325E8F0' { 
 	insmod part_msdos 
 	insmod ntfs 
 	set root='hd0,msdos1' 
 	if [ x$feature_platform_search_hint = xy ]; then 
 	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  01CDE918A325E8F0 
 	else 
 	  search --no-floppy --fs-uuid --set=root 01CDE918A325E8F0 
 	fi 
 	chainloader +1 
 } 
 ### END /etc/grub.d/30_os-prober ###

---

### Post by wgarcia on 2013-01-05
> Vols dir que he de fer una copia del GRUB abans de introduir aquesta instrucció al terminal? Com la puc fer? 

No, volia dir simplement que copiïs els que es veu al terminal quan entres la instrucció "sudo update-grub", potser permeti entendre després si no funciona l'arrencada del W7.

Però potser no he entès bé el problema. Segons el que dius a l'últim missatge sembla que sí que es veu una opció per arrencar W7 al grub, però quan cliques no ho fa? Dóna algun error?

---

### Post by TRYCAS73 on 2013-01-05
> **wgarcia said:**
> No, volia dir simplement que copiïs els que es veu al terminal quan entres la instrucció "sudo update-grub", potser permeti entendre després si no funciona l'arrencada del W7.

Però potser no he entès bé el problema. Segons el que dius a l'últim missatge sembla que sí que es veu una opció per arrencar W7 al grub, però quan cliques no ho fa? Dóna algun error?


Si, fa l'intent, s'esborra la pantalla i torna a sortir el GRUB.

---

### Post by wgarcia on 2013-01-06
Bé, doncs no costa res provar allò de "sudo update-grub" i tornar a provar. El més probable és que no funcioni, per la qual cosa s'haurà de restaurar l'arrencada del W7, però això sols es pot fer des d'un disc o partició de recuperació d'aquest sistema operatiu. 

Això deixarà sense funcionar l'arrencada de linux, però no esborrarà la partició on està instal·lat (W7 no "veu" aquesta partició i per tant no li fa res). Però sí que instal·larà l'arrencada de sols W7 i no el grub, òbviament.

Per restaurar l'arrencada de Linux, que no hauria de tornar a afectar l'arrencada de W7, s'ha d'iniciar el sistema amb un CD o USB d'arrencada d'Ubuntu, entrar en el sistema "autònom" (live). S'explica per exemple a aquesta pàgina:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by TRYCAS73 on 2013-01-07
> **wgarcia said:**
> Bé, doncs no costa res provar allò de "sudo update-grub" i tornar a provar. El més probable és que no funcioni, per la qual cosa s'haurà de restaurar l'arrencada del W7, però això sols es pot fer des d'un disc o partició de recuperació d'aquest sistema operatiu. 

Això deixarà sense funcionar l'arrencada de linux, però no esborrarà la partició on està instal·lat (W7 no "veu" aquesta partició i per tant no li fa res). Però sí que instal·larà l'arrencada de sols W7 i no el grub, òbviament.

Per restaurar l'arrencada de Linux, que no hauria de tornar a afectar l'arrencada de W7, s'ha d'iniciar el sistema amb un CD o USB d'arrencada d'Ubuntu, entrar en el sistema "autònom" (live). S'explica per exemple a aquesta pàgina:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

                                  Moltes gracies **wgarcia**, aixi ho faré.

---

### Post by wgarcia on 2013-01-07
D'acord, ja diràs si s'ha arreglat.

---

