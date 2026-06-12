---
title: "despres de reinstal·lar el xp i instal·lar el 7 el grub ha desaparegut"
date: 2010-08-28
forum: Catalan Team
---

### Post by pserra on 2010-08-28
Hola...
un altre cop jo.... aquesta me la he buscat jo....
tenia el meu portàtil acer one amb el 9.04 i el xp.
Resulta que per motius de feina el xp 'senzill' que portava  estava limitat i he instal·lat el xp professional. Per la dona a la 'C' he posat el windos 7...(tot i que la interfície es més practica la Remix) i la part de l'ubuntu no la he tocat...

EL CAS ES QUE EL GRUB HA DESAPAREGUT I NOMÉS ENGEGO EL WINDOS QUE 'REPARO'...
abans de tocar rés al fdisk tenia:
sudo fdisk -l

Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37c0b349

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1        1045     8388608   12  Diagnòstics Compaq
/dev/sda2            1045        4293    26093890+   7  HPFS/NTFS
/dev/sda3   *        5076       19457   115523415    f  W95 Estesa (LBA)
/dev/sda4            4294        5075     6281415    7  HPFS/NTFS
/dev/sda5           17546       19086    12378082+  83  Linux
/dev/sda6           19087       19457     2980026   82  Intercanvi Linux / Solaris
/dev/sda7            5076       17545   100165212    b  W95 FAT32


ara(no he tocat particions, l'unic que el xp 'pelat' l'he deixat al sda1, passo de les còpies)
i tinc:(live CD)
 sudo fdisk -l

Disc /dev/sda: 160.0 GB, 160041885696 bytes
62 heads, 62 sectors/track, 1018 cylinders
Units = cilindres of 3844 * 512 = 1968128 bytes
Disk identifier: 0x000dc7b9

device Boot   Start              End    Blocs       Id  Sistem
/dev/sda1               1        1045     8388608   12  HPFS/NTFS **formatat i amb el xp**
partition 1 does not end on cylinder boundary.
/dev/sda2  *          1045        4293    26093890+   7  HPFS/NTFS
/dev/sda3             4294        5075     6281415    7  HPFS/NTFS
/dev/sda4             5076       19457   115523415    f  W95 Ext'd (LBA)
/dev/sda5             5076       17545    100165212   7  HPFS/NTFS
/dev/sda6             19087       19457     2980026   82  Linux  swap/ Solaris


també per internet he trobar un cas semblant, i ho solucionen amb aquestes comandes (el meu cas entenc que ha de ser el sda5), però al fer el  mount --bind /dev /mnt/dev  em genera error
> sudo su
mount /dev/sdb5 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
chroot /mnt
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda
Ctrl+D para salir de chroot.
umount /mnt/sys
umount /mnt/proc
umount /mnt/dev
umount /mnt
reboot

com ho puc solucionar? TAMBÉ HE PROVAT AMB EL SUPER GRUB I RÉS...
GRACIES PER ENDAVANT

---

### Post by kukat on 2010-08-29
Has provat amb el SuperGrub Disk, o amb el SUperGrub**2** Disk??? 
:D
[http://www.pctux.com.ar/2010/02/recuperar-el-arranque-de-ubuntu-gnulinux-9-10-grub-2-con-super-grub2-disk.html](http://www.pctux.com.ar/2010/02/recuperar-el-arranque-de-ubuntu-gnulinux-9-10-grub-2-con-super-grub2-disk.html)

---

### Post by CarlesOriol on 2010-08-30
El grub no s'ha d'insta&#320;lar a la partició bootable? No n'estic segur, peró em sembla que hauries de fer-ho a la sda3 o 2 (no acabo d'entendre la llista de particions) en comptes de la 5.

---

### Post by wgarcia on 2010-08-30
> **pserra said:**
> mount --bind /dev /mnt/dev em genera error


Aquest és el procediment correcte per reinstal·lar el grub al MBR del disc un cop l'ha esborrat el windows. Quin error et genera?

---

### Post by pserra on 2010-08-30
> **kukat said:**
> Has provat amb el SuperGrub Disk, o amb el SUperGrub**2** Disk??? 
:D
[http://www.pctux.com.ar/2010/02/recuperar-el-arranque-de-ubuntu-gnulinux-9-10-grub-2-con-super-grub2-disk.html](http://www.pctux.com.ar/2010/02/recuperar-el-arranque-de-ubuntu-gnulinux-9-10-grub-2-con-super-grub2-disk.html)
Merci per l'ajuda kukat, això es el primer que vaig probar però vaig estar mirant totes les possibilitats i no va haver manera...

---

### Post by pserra on 2010-08-30
> **CarlesOriol said:**
> El grub no s'ha d'insta&#320;lar a la partició bootable? No n'estic segur, peró em sembla que hauries de fer-ho a la sda3 o 2 (no acabo d'entendre la llista de particions) en comptes de la 5.

LA VERITAT NO HO TINC MASSA CLAR, VOLIA ADJUNTAR LA IMATGE DE GPARTED, PERO AMB EL LIVE NO EM RECONEIX EL DISC DUR NI PENDRIVES NI INTERNET EM FUNCIONA...
PERÒ RESUMINT EL ESQUEMA DE GPARTED:
    dev/sda1    ntfs      és on tinc el xp
    dev/sda2    ntfs      es on tinc el windos 7    ----boot
    dev/sda3    ntfs      particio SMALL (només de dades)
    dev/sda4    extended -dintre hi ha:
    dev/sda5    fat 32  particio de dades
    unallocated (11.8 GB) penso que es on tinc el REMIX
    dev/sda6     linux swap (2.84 GB)

JA SE QUE TINC LES PARTCICIONS UNA MICA ENREVESSADES...
EL QUE A VISTA DEL GPARTED EM LIA ES QUE LA PARTICIO ON TINC EL REMIX "NO EL TE LOCALITZAT"
que m'aconselleu de fer?

Merci

---

### Post by pserra on 2010-08-30
> **wgarcia said:**
> Aquest és el procediment correcte per reinstal·lar el grub al MBR del disc un cop l'ha esborrat el windows. Quin error et genera?
el problema em sembla que potser em ve perque no em reconeix on tinc la particio de LINUX...no se com reactivar-ho...
per el que veig el fdisk-l...  el sda5 m'ha canviat(primer missatge) i tinc una particio 'desapareguda'...

---

### Post by wgarcia on 2010-08-30
Perquè no fas servir "gparted" des del LIVE CD per veure realment com tens les particions al disc "sda" (al teu missatge  hi ha alguna menció a "sdb" que deu ser un error)

---

### Post by pserra on 2010-08-30
> **wgarcia said:**
> Perquè no fas servir "gparted" des del LIVE CD per veure realment com tens les particions al disc "sda" (al teu missatge  hi ha alguna menció a "sdb" que deu ser un error)

al final, aquesta vegada al arrencar des de el live em reconeix els discs i pen drives. adjunto imatge:
[IMG]http://a.imageshack.us/img718/4331/screenshotmzj.png[/IMG]

SEMBLA QUE NO ES VISUALITZA GAIRE BÉ,(ES LA PRIMERA IMATGE QUE PENJO)
posant aquest enllaç al navegador es veu millor:
                            [http://a.imageshack.us/img237/834/screenshotka.png](http://a.imageshack.us/img237/834/screenshotka.png)

---

### Post by wgarcia on 2010-08-31
Em sembla que el que t'ha fet el particionador que has utilitzat des de Windows és ficar una partició primària que tenies a dins d'una partició lògica. És per això que ara surt com "unallocated". 

Coses que passen amb els particionadors de windows que no respecten la taula de particions adequadament. 

Aquí hi ha un post que explica (en anglès) com arreglar-ho, tot i que sembla força complicat:

[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

---

### Post by pserra on 2010-08-31
> **wgarcia said:**
> Em sembla que el que t'ha fet el particionador que has utilitzat des de Windows és ficar una partició primària que tenies a dins d'una partició lògica. És per això que ara surt com "unallocated". 

Coses que passen amb els particionadors de windows que no respecten la taula de particions adequadament. 

Aquí hi ha un post que explica (en anglès) com arreglar-ho, tot i que sembla força complicat:

[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)


Hola wgarcia,
he mira't  per sobre els enllaços i la veritat, sembla complicat...
el que no entenc es el que dius:
"que has utilitzat des de Windows és ficar una partició primària que tenies a dins d'una partició lògica"

la particio al seu dia la vaig crear així... penso que la particio amb etiqueta COMPARTIT hauria d'haver anat fora del sda4, però el vaig crear així i ha anat bé (recordo que vaig intentar moure-ho, però no em deixava el gparted).
MIRANT EL GPARTED, L'UNIC QUE TROBO DE DIFERENT ES QUE EM SURT EL UNALLOCATED QUE ABANS NO EM SORTIA...
Hi pot haver alguna manera més simple de solucionar-ho??
Merci

---

### Post by wgarcia on 2010-08-31
Em sembla que la taula de particions ha quedat afectada per la instal·lació o reparació que has fet del windows XP, com dius en el teu post inicial.

---

### Post by pserra on 2010-08-31
Merci,
al final he optat per el més fàcil (per a mí), com ha estat reinstal·lar ubuntu... amb 30 minuts ho he fet... el problema el tinc que em reconeix el windows 7, però no la partició on tinc el xp....

algú si ha trobat??


Merci

---

### Post by wgarcia on 2010-09-01
Potser hagis d'entrar manualment les línies necessàries als fitxers de configuració del grub per arrencar el windows xp, hi ha un error en les versions recents de "update-grub" que ignoren algunes de les particions amb altres sistemes operatius. Per exemple al meu portàtil a mi no em reconeixia una partició on hi ha utilitats de DELL. Per arreglar-ho vaig editar el fitxer "40_custom" a /etc/grub.d, posant el següent:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Dell Utility (on /dev/sda1)" {
	insmod vfat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3030-3030
	chainloader +1
}

El que hi ha entre cometes a continuació de "menuentry" ho pots canviar (posant per exemple "XP a /dev/sda3" o el que vulguis. Canvia la línia "set root" posant a (hd0, ...) el número del /dev/sda... on tinguis XP, i a --set el "uuid" de la partició on tinguis XP. A "insmod" posa "ntfs", i finalment fes "update-grub" des de la línia de comandes.

---

### Post by pserra on 2010-09-02
> **wgarcia said:**
> Potser hagis d'entrar manualment les línies necessàries als fitxers de configuració del grub per arrencar el windows xp, hi ha un error en les versions recents de "update-grub" que ignoren algunes de les particions amb altres sistemes operatius. Per exemple al meu portàtil a mi no em reconeixia una partició on hi ha utilitats de DELL. Per arreglar-ho vaig editar el fitxer "40_custom" a /etc/grub.d, posant el següent:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Dell Utility (on /dev/sda1)" {
	insmod vfat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3030-3030
	chainloader +1
}

El que hi ha entre cometes a continuació de "menuentry" ho pots canviar (posant per exemple "XP a /dev/sda3" o el que vulguis. Canvia la línia "set root" posant a (hd0, ...) el número del /dev/sda... on tinguis XP, i a --set el "uuid" de la partició on tinguis XP. A "insmod" posa "ntfs", i finalment fes "update-grub" des de la línia de comandes.
Hola wgarcia,
gràcies per el teu interès,
aquesta partició no em surt al arxiu /etc/grub.d, la vaig crear posant el seu UUID i al arrencar em surt error: FALTA NTLDR, per solucionar-ho el més fàcil es posar el cd de recuperació del windows  xp, però temo tornar a 'xafar' el que tinc al grub...
vaig estar mirant també amb el SUPER GRUB si podia arreglar-ho i em surt el mateix  error.....
després de forçar l'arrencada de la partició en qüestió amb el SUPER GRUB, no se perquè el grub el vaig  perdre... a veure si aquest vespre quan torni a posar-m'hi ho puc solventar però no se com....
Merci

---

### Post by wgarcia on 2010-09-02
En quina partició tens el  XP?

Quan dius "posant en /etc/grub.d" suposo que et refereixes a alguna cosa que vas posar en algun fitxer d'aquesta carpeta. En quin fitxer i què vas posar exactament?

I efectivament, si recuperes amb l'arxiu de reparació de Windows XP possiblement t'esborrarà el grub.

---

### Post by pserra on 2010-09-02
> **wgarcia said:**
> En quina partició tens el  XP?

Quan dius "posant en /etc/grub.d" suposo que et refereixes a alguna cosa que vas posar en algun fitxer d'aquesta carpeta. En quin fitxer i què vas posar exactament?

I efectivament, si recuperes amb l'arxiu de reparació de Windows XP possiblement t'esborrarà el grub.

el xp el tinc a sda1, i lo del  /boot/grub/grub.cfg   ha estat que he editat l'entrada que no existia de xp, posant 
l' adreça(UUID) correcte, sembla que esta ben editada, ja que em fa saltar em mateix error que si provo d'entrar des de el Super Grub....

---

### Post by wgarcia on 2010-09-02
Què et surt quan fas

sudo blkid

I què has entrat exactament al /etc/grub/grub.cfg? Posa les línies que hagis entrat sisplau. 

El mètode recomant per agregar entrades d'altres sistemes operatius és editar el fitxer que menciono a #14.

---

### Post by pserra on 2010-09-02
> **wgarcia said:**
> Què et surt quan fas

sudo blkid

I què has entrat exactament al /etc/grub/grub.cfg? Posa les línies que hagis entrat sisplau. 

El mètode recomant per agregar entrades d'altres sistemes operatius és editar el fitxer que menciono a #14.

aqui passo:
> pere@pere-laptop:~$ sudo blkid
[sudo] password for pere: 
/dev/sda1: UUID="9C4CDED74CDEAB72" LABEL="XP" TYPE="ntfs" 
/dev/sda2: UUID="50CE6529CE650894" TYPE="ntfs" 
/dev/sda3: UUID="6660D66D000BF257" LABEL="SMALL" TYPE="ntfs" 
/dev/sda5: LABEL="COMPARTIT" UUID="59992001-fb02-424e-84b2-ad4fac032afc" TYPE="ext4" 
/dev/sda6: UUID="502a905c-2122-48e4-bd8b-1700a6f263a5" TYPE="swap" 
/dev/sda7: UUID="310badb7-fc6e-4072-b91e-f2c39613982c" TYPE="ext4" 
/dev/sda8: UUID="79b5ccd7-0b34-4c3e-a607-5d9911a7f157" TYPE="ext4" 
pere@pere-laptop:~$ 
 i la part de  arrencades de l'arxiu: /boot/grub/grub.cfg

> ### BEGIN /etc/grub.d/30_os-prober ###
**menuentry "Windows 7 (loader) (on /dev/sda2)**" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 50ce6529ce650894
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/10_linux ###
**menuentry "Ubuntu, Linux 2.6.31-22-generic"** {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 310badb7-fc6e-4072-b91e-f2c39613982c
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=310badb7-fc6e-4072-b91e-f2c39613982c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### BEGIN /etc/grub.d/30_os-prober ###
[B]menuentry "Windows  XP des de sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9C4CDED74CDEAB72
	chainloader +1
}[/B]
### END /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 310badb7-fc6e-4072-b91e-f2c39613982c
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=310badb7-fc6e-4072-b91e-f2c39613982c ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 310badb7-fc6e-4072-b91e-f2c39613982c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=310badb7-fc6e-4072-b91e-f2c39613982c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 310badb7-fc6e-4072-b91e-f2c39613982c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=310badb7-fc6e-4072-b91e-f2c39613982c ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


---

### Post by wgarcia on 2010-09-02
D'acord, sembla que està tot correcte. I ara rellegint els teus missatges anteriors veig que la partició de Windows XP sí que la veu, però et diu:

Falta NTLDR

Això és un problema del Windows, són els arxius d'arrencada. És possible que un altre cop tinguis instal·lat el grub a la partició on està windows XP i no al MBR del disc (en un altre fil et comentava l'ús del programet "testdisk" per veure on està intal·lat el grub). 

Per tant se m'acut que la solució és : 1) reparar el windows xp com deies, 2) si després no et surt el grub, reinstal·lar el grub amb el Live CD o el supergrub.

---

### Post by pserra on 2010-09-02
> **wgarcia said:**
> D'acord, sembla que està tot correcte. I ara rellegint els teus missatges anteriors veig que la partició de Windows XP sí que la veu, però et diu:

Falta NTLDR

Això és un problema del Windows, són els arxius d'arrencada. És possible que un altre cop tinguis instal·lat el grub a la partició on està windows XP i no al MBR del disc (en un altre fil et comentava l'ús del programet "testdisk" per veure on està intal·lat el grub). 

Per tant se m'acut que la solució és : 1) reparar el windows xp com deies, 2) si després no et surt el grub, reinstal·lar el grub amb el Live CD o el supergrub.
Aquesta nit ho provaré wgarcia... em sembla que haurà de funcionar... 
Merci

---

### Post by pserra on 2010-09-07
> **pserra said:**
> Aquesta nit ho provaré wgarcia... em sembla que haurà de funcionar... 
Merci

Perfecte,
reinstal·lant i fent un recheck del grub... tot ha quedat solucionat....Merci una altre vegada.

---

