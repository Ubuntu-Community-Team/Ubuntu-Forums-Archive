---
title: "Aquest ordinador no duu cap sistema operatiu que s'hagi detectat. Què voleu fer?"
date: 2014-05-25
forum: Catalan Team
---

### Post by jinglada on 2014-05-25
Intento instal·lar l'Ubuntu en un Acer amb Windows i em dóna el següent missatge:

"Aquest ordinador no duu cap sistema operatiu que s'hagi detectat. Què voleu fer?"

Ho he provat amb el 13.10 i amb el 14.04 i el missatge és el mateix.

Llavors proposa: "Esborra el disc i instal·la el sistema operatiu Ubuntu". Ho desmarco i ...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253444&d=1401053355[/IMG]

... marco "Alguna altra cosa" i a la taula de particions es veu que hi ha espai ocupat.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253443&d=1401053346[/IMG]

Reinicio i entro a Windows i a l'Administració de discs es veu on és cada cosa:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=253446&d=1401053958[/IMG]

Què aconselleu?

---

### Post by jinglada on 2014-05-26
Em sembla que he trobat la solució a: [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by jinglada on 2014-05-28
> **jinglada said:**
> Em sembla que he trobat la solució a: [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Ha fallat. Vaig seguir tots els passos fins el vuité i em va donar el següent missatge:

> S'ha produït un error mentre es reparava.
Escriviu en un full de paper l’URL següent: [http://paste.ubuntu.com/7524765/](http://paste.ubuntu.com/7524765/)
En el cas de que continue tenint problemes a l'arranc, indica esta URL a: [email]boot.repair@gmail.com[/email]

Ara pots reiniciar l'ordinador.

Per favor no oblide fer que la BIOS inicie al disc sda (750GB) ! Si us plau, desactive  SecureBoot en la BIOS.

Els arxius d'inici de  [El sistema operatiu que s'està usant - Ubuntu 14.04 LTS] estan lluny de l'inici del disk. La seua BIOS no pot detectar-los. Potser que vulga tornar-ho a intentar després de crear una partició /boot (EXT4, >200MB, començament del disc). Açò es pot fer amb eines com gParted. Ara selecciona esta partició via l'opció [Separa la partició /boot:] o la [Repara l'arranc]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

Aquest ordenador no permet desactivar SecureBoot. En reiniciar entrava directament a windows.

Vaig enviar el missatge i em van respondre això:
> 
Hello,

We, volunteers at Boot-Repair project, have received your request.
Please note that solving a boot problem can be long, and unfortunately
we do not have time any more to answer all requests, so we offer this
help service only to our contributors.

In order to assist you, please indicate:
1) how you have contributed to the Boot-Repair project. If you haven't
contributed yet, you can find on our homepage several ways to
contribute, such as translating or doing a small Paypal donation to
[email]boot.repair@gmail.com[/email] . Thanks for your support.
2) if not done yet, a detailed description of your problem before
using Boot-Repair
3) the BootInfo (URL or text file) that appeared after you used the
"Recommended Repair" of Boot-Repair
4) a detailed description of your problem after using Boot-Repair's
Recommended Repair.

Best regards,
The Boot-Repair Team
[https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)

Vaig canviar UEFI per Legacy perquè ho vaig llegir en dos comentaris de la mateixa pàgina. Vaig tornar a iniciar amb l'USB live i vaig reinstal·lar amb l'opció d'esborrar previament la instal·lació anterior. 

[ATTACH=CONFIG]253551[/ATTACH]

I finalment s'inicia entrant directament a l'Uuntu 14.04 i ha quedat així:
joan@joan-Aspire-E1-572:~$ sudo fdisk -l
[sudo] password for joan:   

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4eca580f

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002504

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sdc1              63   976768064   488384001   83  Linux
joan@joan-Aspire-E1-572:~$ 

[ATTACH=CONFIG]253550[/ATTACH]

PS: em sembla que no hi ha windows, oi? (Tinc l'USB de recovery)

---

### Post by wgarcia on 2014-05-29
Jo vaig instal·lar un Ubuntu 14.04 fa poc en un ordinador que em sembla que té les mateixes especificacions que el teu. Vaig estar trastejant tot un matí, i el màxim que vaig aconseguir va ser: 1) Tenir Secure Boot habilitat. 2) Córrer el Boot repair, que arregla el grub, i permet arrencar l'Ubuntu. 3) El windows es veu al boot, però quan intentes arrencar surt el següent missatge:

```

/EndEntire
file path:/ACPI(a0341d0,0)/PCI(2,1f)/UnknwnMessaging(12)/HD(2,200800,82000,a8d996409dcfe211,a8,59)/File(\EFI|Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.

```

L'única manera de tornar a poder arrencar el Windows va ser fer servir l'USB de recuperació que vam crear, però això torna a trencar el GRUB i no permet arrencar l'Ubuntu.

Posant l'arrencada al "Legacy" a la configuració permet arrencar l'Ubuntu però el Windows com dius no es veu.

Vaig provar altres coses, que suggereixen l'enllaç que vas posar al principi, com dins de Windows cancel·lar "Fastboot", o també dins de Windows a una línia d'ordres com administrador entrar 

```
bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi
```

però tot ha quedat igual. L'Ubuntu arrenca però el Windows dóna l'error que he posat a dalt.

No he pogut tornar a l 'ordinador, que no és meu, he trobat mentrestant un article interessant que no he provat a veure si ho arregla:

[http://unix.stackexchange.com/questions/49165/can-grub2-share-the-efi-system-partition-with-windows](http://unix.stackexchange.com/questions/49165/can-grub2-share-the-efi-system-partition-with-windows)

La primera part de l'article crec que no és rellevant perquè l'instal·lador de l'Ubuntu ja ho fa. El que pot servir és el que comenta al final sobre com canviar les línies de la configuració del grub que arrenquen el windows.

---

### Post by jinglada on 2014-05-29
Gràcies wgarcia.

He provat de tornar a posar UEFI i al reiniciar m'ha dirt que el HDD estava bloquejat i que poses el recovery de Windows. He tornat a posar Legacy.

Què et sembla, doncs que podria provar de l'enllaç que em dones?

Tinc això:

joan@joan-Aspire-E1-572:/boot/efi$ ls
EFI
joan@joan-Aspire-E1-572:/boot/efi$ cd EFI
joan@joan-Aspire-E1-572:/boot/efi/EFI$ ls
ubuntu
joan@joan-Aspire-E1-572:/boot/efi/EFI$ cd ubuntu
joan@joan-Aspire-E1-572:/boot/efi/EFI/ubuntu$ ls
grub.cfg  grubx64.efi  MokManager.efi  shimx64.efi

joan@joan-Aspire-E1-572:/boot/efi/EFI/ubuntu$ sudo dpkg -l grub-common
[sudo] password for joan: 
Desitjat=desconegUt/Insta&#320;la/supRimeix/Purga/retín(H)
| Estat=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Estat,Err: majúsc.=dolent)
||/ Nom            Versió       Arquitectura Descripció
+++-==============-============-============-=================================
ii  grub-common    2.02~beta2-9 amd64        GRand Unified Bootloader (common 

cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

joan@joan-Aspire-E1-572:/boot/grub$ ls
fonts  grub.cfg  grubenv  locale  unicode.pf2  x86_64-efi

---

### Post by wgarcia on 2014-05-30
Jo el que provaria, tot i que no sé si funcionarà, és:

1) Recuperar Windows amb el disc de recuperació, assegurar-me que es fan els punts 4. i 8. de l'enllaç que posaves:

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

2) Reiniciar amb un USB autònom (live) i córrer el Boot Repair , "recommended". Hauràs d'instal·lar el boot repair la sessió d'Ubuntu que es corre des del Live USB perquè no està instal·lat. Assegura't que a "advanced" el grub està instal·lat a /boot/efi, i mira si ha una pestanya que diu "fer còpia de l'arrenc efi" o alguna cosa així.

3) Iniciar l'ordinador i mirar com es veu el grub, provar si arrenca Ubuntu i si arrenca Windows. Ubuntu hauria d'arrencar, Windows crec que no. Provar ara arrencar l'ordinador, prémer F12, i mirar si surt una opció per arrencar Windows. Provar si arrenca des d'aquí. Si arrenca fins i tot ho podries deixar així, l'Ubuntu l'arrenques des del grub i el Windows des d'aquest menú. Si el Windows tampoc arrenca des d'aquí, o ho vols arreglar del tot es pot provar el punt 4).

4) Entrar a Ubuntu i córrer

```
grub-probe --target=hints_string /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
```

suposa que et dóna:

```
--hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1 1ce5-7f28
```

Ara obres el boot-repair, vas a "advanced", i esculls "editar configuració grub". Has de buscar una línia semblant al que poso i insertar el que t'ha donat el grub-probe on ho poso:

```

menuentry "Microsoft Windows x86_64 UEFI-GPT" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root <inserta sortida de grub-probe aquí>
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

```

o sigui quedaria

```

menuentry "Microsoft Windows x86_64 UEFI-GPT" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root grub-probe --target=hints_string /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

```

Per últim córrer "reinstal·lar grub" des del boot-repair

I creuar els dits a veure si ara arrenquen Ubuntu i Windows.

---

### Post by jinglada on 2014-05-30
Gràcies wgarcia!
Dissabte o diumenge, si tobo una estona de calma, ho provaré i ja diré el resultat.

---

### Post by jinglada on 2014-05-31
> **jinglada said:**
> Gràcies wgarcia!
Dissabte o diumenge, si trobo una estona de calma, ho provaré i ja diré el resultat.

Passos que he fet:

1 No em permet arrancar des d'USB en Boot Mode "Legacy", per tant restitueixo "UEFI". (Secure Boot queda "Enabled" ja que no permet canviar-lo).
2 No em permet restaurar windows respectant el que hi ha particionat.
3 Provo el punt 4. i em respon: grub-probe: error: no s'ha pogut aconseguir el camí canònic de «/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi».

-----------------------------------------------

Quan arranco l'ordinador no mostra cap menú del grub sinó que entra directament en l'Ubuntu 14.04
Abans en el directori /boot/efi/ només hi havia el directori EFI i ara hi ha creat el directori Temp, en el que hi ha posat els següents fitxers:

joan@joan-Aspire-E1-572:/boot/efi/Temp$ ls -l
total 24
-rwxr-xr-x 1 root root  130 jun  1 00:03 bcdinfo.txt
-rwxr-xr-x 1 root root    4 jun  1 00:03 bootfailure.txt
-rwxr-xr-x 1 root root 3375 jun  1 00:03 disklayout.txt
-rwxr-xr-x 1 root root 8084 jun  1 00:03 SrtTrail.log
-rwxr-xr-x 1 root root 2602 jun  1 00:03 SrtTrail.txt
 
En el disklayout.txt hi ha:

joan@joan-Aspire-E1-572:/boot/efi/Temp$ cat disklayout.txt

Microsoft DiskPart versi&#65533;n 6.3.9600

Copyright (C) 1999-2013 Microsoft Corporation.
En el equipo: MININT-QFMUVIS

  N&#65533;m Disco  Estado      Tama&#65533;o   Disp     Din  Gpt
  ---------- ----------  -------  -------  ---  ---
  Disco 0    En l&#65533;nea        698 GB      0 B        *
  Disco 1    En l&#65533;nea         28 GB      0 B         

El disco 0 es ahora el disco seleccionado.

ST750LM022 HN-M750MBB
Id. de disco: {866607CD-B86C-411D-88C1-181B2B90BC39}
Tipo        : SATA
Estado : En l&#65533;nea
Ruta        : 0
Destino     : 0
Id. de LUN  : 0
Ruta de la ubicaci&#65533;n: PCIROOT(0)#PCI(1F02)#ATA(C00T00L00)
Estado de solo lectura actual: No
Solo lectura       : No
Disco de arranque  : No
Disco de archivo de paginaci&#65533;n  : No
Disco de archivo de hibernaci&#65533;n  : No
Disco de volcado  : No
Disco en cl&#65533;ster: No

  N&#65533;m Volumen Ltr  Etiqueta     Fs     Tipo        Tama&#65533;o   Estado     Info
  ----------- ---  -----------  -----  ----------  -------  ---------  --------
  Volumen 0                     FAT32  Partici&#65533;n    512 MB  Correcto   Oculto  

  N&#65533;m Volumen Ltr  Etiqueta     Fs     Tipo        Tama&#65533;o   Estado     Info
  ----------- ---  -----------  -----  ----------  -------  ---------  --------
  Volumen 0                     FAT32  Partici&#65533;n    512 MB  Correcto   Oculto  
  Volumen 1     C               FAT32  Extra&#65533;ble     28 GB  Correcto           

El volumen 1 es el volumen seleccionado.

  N&#65533;m Disco  Estado      Tama&#65533;o   Disp     Din  Gpt
  ---------- ----------  -------  -------  ---  ---
* Disco 1    En l&#65533;nea         28 GB      0 B         

Solo lectura              : No
Oculto                    : No
Letra de unidad no predet.: No
Instant&#65533;nea               : No
Desconectado              : No
Cifrado con BitLocker     : No
Instalable            : No

Capacidad del volumen               :   28 GB
Espacio disponible en el volumen    :   13 GB

El disco 0 es ahora el disco seleccionado.

ST750LM022 HN-M750MBB
Id. de disco: {866607CD-B86C-411D-88C1-181B2B90BC39}
Tipo        : SATA
Estado : En l&#65533;nea
Ruta        : 0
Destino     : 0
Id. de LUN  : 0
Ruta de la ubicaci&#65533;n: PCIROOT(0)#PCI(1F02)#ATA(C00T00L00)
Estado de solo lectura actual: No
Solo lectura       : No
Disco de arranque  : No
Disco de archivo de paginaci&#65533;n  : No
Disco de archivo de hibernaci&#65533;n  : No
Disco de volcado  : No
Disco en cl&#65533;ster: No

  N&#65533;m Volumen Ltr  Etiqueta     Fs     Tipo        Tama&#65533;o   Estado     Info
  ----------- ---  -----------  -----  ----------  -------  ---------  --------
  Volumen 0                     FAT32  Partici&#65533;n    512 MB  Correcto   Oculto  

  N&#65533;m Partici&#65533;n  Tipo              Tama&#65533;o   Desplazamiento
  -------------  ----------------  -------  ---------------
  Partici&#65533;n 1    Sistema            512 MB  1024 KB
  Partici&#65533;n 2    Desconocido        694 GB   513 MB
  Partici&#65533;n 3    Desconocido       3975 MB   694 GB

La partici&#65533;n 1 es ahora la partici&#65533;n seleccionada.

Partici&#65533;n 1
Tipo          : c12a7328-f81f-11d2-ba4b-00a0c93ec93b
Oculta        : S&#65533;
Necesaria     : No
Atrib.        : 0000000000000000
Desplaz. bytes: 1048576

  N&#65533;m Volumen Ltr  Etiqueta     Fs     Tipo        Tama&#65533;o   Estado     Info
  ----------- ---  -----------  -----  ----------  -------  ---------  --------
* Volumen 0                     FAT32  Partici&#65533;n    512 MB  Correcto   Oculto

---

### Post by wgarcia on 2014-06-01
Suposo que de moment no tens dades a la instal·lació d'Ubuntu, oi? El que vull dir és que no hi ha perill de perdre coses. Per tant jo començaria per recuperar Windows amb el suport de recuperació que tinguis. És a dir intentar la seqüència que comentava en el meu comentari anterior, començant pel punt 1.

---

### Post by jinglada on 2014-06-01
Gràcies wgarcia!

> **wgarcia said:**
> Jo el que provaria, tot i que no sé si funcionarà, és:

1) Recuperar Windows amb el disc de recuperació, assegurar-me que es fan els punts 4. i 8. de l'enllaç que posaves:

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Tenia:
1. Back up Windows
2. Create a bootable Ubuntu USB drive

He fet:
Restore de Windows
3. Shrink your Windows partition
4. Turn off fast boot

No puc fer:
5. Turn off secure boot (No ho permet) He posat Boot Mode a "Legacy" perquè ho he llegit a [http://www.taringa.net/comunidades/ubuntuparataringeros/6557897/Acer-aspire-v5-con-windows-8-impide-instalacion-de-ubuntu.html](http://www.taringa.net/comunidades/ubuntuparataringeros/6557897/Acer-aspire-v5-con-windows-8-impide-instalacion-de-ubuntu.html)

He entès que no havia de fer:
6. Install Ubuntu

He fet:
7. Boot Repair (L'arranc ha sigut reparat amb èxit.)

> 
2) Reiniciar amb un USB autònom (live) i córrer el Boot Repair , "recommended". Hauràs d'instal·lar el boot repair la sessió d'Ubuntu que es corre des del Live USB perquè no està instal·lat. Assegura't que a "advanced" el grub està instal·lat a /boot/efi, i mira si ha una pestanya que diu "fer còpia de l'arrenc efi" o alguna cosa així.

A "advanced" hi ha:
Opcions principals:
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253653](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253653)
Altres opcions:
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253652](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253652)

A les altres pestanyes no hi ha res.

Suposo que havia d'haver instal·lat l'Ubuntu del pas 6., oi?

I després seguir amb això:
> 
3) Iniciar l'ordinador i mirar com es veu el grub, provar si arrenca Ubuntu i si arrenca Windows. Ubuntu hauria d'arrencar, Windows crec que no. Provar ara arrencar l'ordinador, prémer F12, i mirar si surt una opció per arrencar Windows. Provar si arrenca des d'aquí. Si arrenca fins i tot ho podries deixar així, l'Ubuntu l'arrenques des del grub i el Windows des d'aquest menú. Si el Windows tampoc arrenca des d'aquí, o ho vols arreglar del tot es pot provar el punt 4).

4) Entrar a Ubuntu i córrer

```
grub-probe --target=hints_string /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
```

suposa que et dóna:

```
--hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1 1ce5-7f28
```

Ara obres el boot-repair, vas a "advanced", i esculls "editar configuració grub". Has de buscar una línia semblant al que poso i insertar el que t'ha donat el grub-probe on ho poso:

```

menuentry "Microsoft Windows x86_64 UEFI-GPT" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root <inserta sortida de grub-probe aquí>
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

```

o sigui quedaria

[CODE]
menuentry "Microsoft Windows x86_64 UEFI-GPT" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root grub-probe --target=hints_string /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
    chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

Per últim córrer "reinstal·lar grub" des del boot-repair

I creuar els dits a veure si ara arrenquen Ubuntu i Windows.

---

### Post by wgarcia on 2014-06-02
Jo crec que has de mantenir el Secure Boot habilitat, és a dir no passar a "Legacy". Aquestes versions de Windows 8.1 no poden arrencar en Legacy, i l'Ubuntu, des de la versió 12.04.2 o 12.04.3 no recordo quina, pot arrencar perfectament sota Secure Boot perquè la imatge ja ve amb una signatura que els de Canonical han registrat perquè el Secure Boot no es queixi.

---

### Post by jinglada on 2014-06-02
> **wgarcia said:**
> Jo crec que has de mantenir el Secure Boot habilitat, és a dir no passar a "Legacy". Aquestes versions de Windows 8.1 no poden arrencar en Legacy, i l'Ubuntu, des de la versió 12.04.2 o 12.04.3 no recordo quina, pot arrencar perfectament sota Secure Boot perquè la imatge ja ve amb una signatura que els de Canonical han registrat perquè el Secure Boot no es queixi.

D'acord. Windows s'inicia bé però surt un missatge a l'escriptori que diu: "Secure Boot no està configurat correctament".

El que he de fer ara és això?:

Posar Boot Mode a "UEFI" amb Secure Boot habilitat.
6. Install Ubuntu
7. Boot Repair (Faig la còpia de seguretat de les taules de partició, sectors d'arrancada i registre de l'advanced?)
8. Fix the boot loader

I seguir amb el punt 3. del teu missatge de fa 3 dies.

D'acord?
Ah!, gràcies novament, wgarcia!

---

### Post by wgarcia on 2014-06-02
Sí, posar tot a arrencada UEFI, però jo crec que no has de tornar a instal·lar Ubuntu perquè ja està instal·lat. Has d'iniciar l'Ubuntu amb una memòria USB o CD autònom (Life), instal·lar el boot-repair , i córrer la Reparació recomanada. I després seguir els passos que suggeria.

---

### Post by jinglada on 2014-06-02
Gràcies per la paciència, wgarcia!

> **wgarcia said:**
> Jo crec que no has de tornar a instal·lar Ubuntu perquè ja està instal·lat. Has d'iniciar l'Ubuntu amb una memòria USB o CD autònom (Life), instal·lar el boot-repair , i córrer la Reparació recomanada. I després seguir els passos que suggeria.

Vols dir que hi ha l'Ubuntu? Després de fer el restore del windows ha quedat així:
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253446](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253446)

Ja vaig fer això que dius: "... d'iniciar l'Ubuntu amb una memòria USB o CD autònom (Life), instal·lar el boot-repair , i córrer la Reparació recomanada.

> 
3) Iniciar l'ordinador i mirar com es veu el grub, provar si arrenca Ubuntu i si arrenca Windows. Ubuntu hauria d'arrencar, Windows crec que no. Provar ara arrencar l'ordinador, prémer F12, i mirar si surt una opció per arrencar Windows. Provar si arrenca des d'aquí. Si arrenca fins i tot ho podries deixar així, l'Ubuntu l'arrenques des del grub i el Windows des d'aquest menú. Si el Windows tampoc arrenca des d'aquí, o ho vols arreglar del tot es pot provar el punt 4). 

A l'arrancar l'ordinador entra directament a Windows. Si premo F12 surt això:
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253676](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253676)

---

### Post by wgarcia on 2014-06-03
Dius que has fet el pas 2) d'arrencar amb l'USB Ubuntu i fer el boot-repair. No et dóna cap error? Et diu alguna cosa sobre si veu la partició EFI? 

És estrany perquè després de córrer el boot-repair ja hauria d'iniciar-se el grub quan reinicies l'ordinador, mostrant tant Ubuntu com Windows.

---

### Post by jinglada on 2014-06-03
Hola wgarcia.

> **wgarcia said:**
> Dius que has fet el pas 2) d'arrencar amb l'USB Ubuntu i fer el boot-repair. No et dóna cap error? Et diu alguna cosa sobre si veu la partició EFI? 

És estrany perquè després de córrer el boot-repair ja hauria d'iniciar-se el grub quan reinicies l'ordinador, mostrant tant Ubuntu com Windows.

Vaig fer fotos de tots els missatges en seqüència:

"EFI detectat. Per favor, comprove les opcions"  ----> No vaig comprovar les opcions, perquè no sabia quines.
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253694](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253694)

"Per favor, faça una còpia de seguretat de les seues dades abans de fer esta operació" ----------> No vaig fer cap còpia perquè és nou.
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253695](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253695)

"Reparació de l'arranc de l'equip"
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253697](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253697)

"La reparació del sistema d'arxius necessita desmuntar les particions. Per favor, tanque tots els seus programes. Després tanca esta finestra." -----> Vaig tancar el navegador i la finestra.
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253698](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253698)

"L'arranc ha sigut reparat amb èxit"
[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253699](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253699)

---

### Post by wgarcia on 2014-06-03
M'he estudiat tota la seqüència des del teu primer missatge, i concordo amb tu que ara no es veu l'Ubuntu. Per tant tornem enrere. 

Una cosa que vas fer a la instal·lació d'Ubuntu anterior va ser deshabilitar el Secure Boot, crec que no s'ha de fer, com deia en un altre missatge, els Ubuntu actuals poden funcionar sota Secure Boot (i la nova UEFI que substitueix les antigues BIOS). Si deshabilites el Secure Boot l'Ubuntu s'instal·larà bé però el Windows 8.1 no podrà arrencar.

Per tant mantingues habilitat UEFI i Secure Boot (crec que si habilites un s'habilita l'altre per defecte). 

Torna a instal·lar l'Ubuntu, tal quals vas fe el primer cop. Un cop acabi prova des del Grub si ara arrenquen l'Ubuntu i el Windows. El Windows és molt probable que no arrenqui: corre el boot-repair. Torna a provar si arrenca l'Ubuntu i el Windows. Si el Windows continua sense arrencar comentem quin missatge o símptoma dóna.

---

### Post by jinglada on 2014-06-04
> **wgarcia said:**
> M'he estudiat tota la seqüència des del teu primer missatge, i concordo amb tu que ara no es veu l'Ubuntu. Per tant tornem enrere. 

Una cosa que vas fer a la instal·lació d'Ubuntu anterior va ser deshabilitar el Secure Boot, crec que no s'ha de fer, com deia en un altre missatge, els Ubuntu actuals poden funcionar sota Secure Boot (i la nova UEFI que substitueix les antigues BIOS). Si deshabilites el Secure Boot l'Ubuntu s'instal·larà bé però el Windows 8.1 no podrà arrencar.

Per tant mantingues habilitat UEFI i Secure Boot (crec que si habilites un s'habilita l'altre per defecte). 

Torna a instal·lar l'Ubuntu, tal quals vas fe el primer cop. Un cop acabi prova des del Grub si ara arrenquen l'Ubuntu i el Windows. El Windows és molt probable que no arrenqui: corre el boot-repair. Torna a provar si arrenca l'Ubuntu i el Windows. Si el Windows continua sense arrencar comentem quin missatge o símptoma dóna.

No va anar exactament com dius, wgarcia. En el missatge #3 ([http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679](http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679)), dic: 

1) "Vaig seguir tots els passos fins el vuité ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)) ... Aquest ordenador no permet desactivar SecureBoot. En reiniciar entrava directament a windows."

2) "Vaig canviar UEFI per Legacy ... Vaig tornar a iniciar amb l'USB live i vaig reinstal·lar amb l'opció d'esborrar prèviament la instal·lació anterior... I finalment s'inicia entrant directament a l'Ubuntu 14.04

--------------------------------------

Resumint:
1) Amb UEFI, Secure Boot habilitat, instal·lo l'Ubuntu i quan reinicio entra directament a Windows.
2) Anb Legacy, instal·lo l'Ubuntu i quan reinicio entra directament a Ubuntu.

Entenc que el que em proposes és repetir el que ja vaig fer de bon començament, no?

---

### Post by wgarcia on 2014-06-04
> **jinglada said:**
> 
1) Amb UEFI, Secure Boot habilitat, instal·lo l'Ubuntu i quan reinicio entra directament a Windows.
2) Anb Legacy, instal·lo l'Ubuntu i quan reinicio entra directament a Ubuntu.

Entenc que el que em proposes és repetir el que ja vaig fer de bon començament, no?

Si entenc bé el que no has fet és:

1) Amb UEFI, Secure Boot habilitat, instal·lo l'Ubuntu i quan reinicio entra directament a Windows.

I aquí, reiniciar amb l'USB, i allí  instal·lar el boot-repair i fer la reparació recomanada. És a dir, no passar directament el punt 2).

---

### Post by jinglada on 2014-06-05
> **wgarcia said:**
> Si entenc bé el que no has fet és:

1) Amb UEFI, Secure Boot habilitat, instal·lo l'Ubuntu i quan reinicio entra directament a Windows.

I aquí, reiniciar amb l'USB, i allí  instal·lar el boot-repair i fer la reparació recomanada. És a dir, no passar directament el punt 2).

Perdona, wgarcia, les meves dificultats comunicatives.

El que vaig fer en primer lloc va ser seguir** tots els passos fins el vuité** ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html), **excepte el cinquè**, ja que **aquest ordenador no permet desactivar SecureBoot en Boot Mode UEFI** i així en Boot Mode UEFI i SecureBoot habilitat vaig seguir fins el 8è, o sigui que vaig fer:

6. Install Ubuntu
7. Boot Repair, que va fallar, aquesta 1a vegada, amb el següent missatge:

------------------------------------------------------------------------
S'ha produït un error mentre es reparava.
Escriviu en un full de paper l&#8217;URL següent: **[http://paste.ubuntu.com/7524765/](http://paste.ubuntu.com/7524765/)**
En el cas de que continue tenint problemes a l'arranc, indica esta URL a: [email]boot.repair@gmail.com[/email]
Ara pots reiniciar l'ordinador.
Per favor no oblide fer que la BIOS inicie al disc sda (750GB) ! Si us plau, desactive SecureBoot en la BIOS.
Els arxius d'inici de [El sistema operatiu que s'està usant - Ubuntu 14.04 LTS] estan lluny de l'inici del disk. La seua BIOS no pot detectar-los. Potser que vulga tornar-ho a intentar després de crear una partició /boot (EXT4, >200MB, començament del disc). Açò es pot fer amb eines com gParted. Ara selecciona esta partició via l'opció [Separa la partició /boot:] o la [Repara l'arranc]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
--------------------------------------------------------------------------

8. Fix the boot loader. 

Després, en reiniciar entrava a windows directament.

=========================================

Si et sembla bé ho torno a fer altra vegada, evidentment sense el punt 5è?

---

### Post by wgarcia on 2014-06-05
A veure, anem a recapitular una mica. 

Segon tinc entès ara la situació és la següent:
1) Has instal·lat l'Ubuntu mantenint el Secure Boot habilitat
2) Has iniciat i surt el Grub però no es pot iniciar Windows
3) Has executat el Boot Repair - recommended repair, però no ho ha arreglat
4) Has recuperat Windows, i ara arrenca Windows directament
5) Has iniciat UBUNTU des d'USB, has executat boot-repair, però en reiniciar continua arrencant windows

A més l'Ubuntu ara no es veu per enlloc. 

És així la seqüència?

---

### Post by jinglada on 2014-06-05
> **wgarcia said:**
> A veure, anem a recapitular una mica. 

Segon tinc entès ara la situació és la següent:
1) Has instal·lat l'Ubuntu mantenint el Secure Boot habilitat                             =========> SI
2) Has iniciat i surt el Grub però no es pot iniciar Windows                              =========> No recordo si vaig reiniciar després d'instal·lar l'Ubuntu.
3) Has executat el Boot Repair - recommended repair, però no ho ha arreglat    =========> SI, vaig reiniciar i sortia directament l'Ubuntu.
4) Has recuperat Windows, i ara arrenca Windows directament                        =========> SI
5) Has iniciat UBUNTU des d'USB, has executat boot-repair, però en reiniciar continua arrencant windows =========> SI

A més l'Ubuntu ara no es veu per enlloc. =========> SI

És així la seqüència?

---

### Post by wgarcia on 2014-06-05
D'acord, però el que em desconcerta és el que dius en el teu missatge #3:
[http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679](http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679)

Específicament el següent:
> Vaig canviar UEFI per Legacy perquè ho vaig llegir en dos comentaris de la mateixa pàgina. Vaig tornar a iniciar amb l'USB live i vaig reinstal·lar amb l'opció d'esborrar previament la instal·lació anterior. 

I finalment s'inicia entrant directament a l'Uuntu 14.04 i ha quedat així:

Perquè si realment vas fer això, pot explicar el que hagi desaparegut la instal·lació de l'Ubuntu. Realment vas fer el que dius en aquest missatge #3? Perquè no surt en la seqüència que vam repassar ara.

---

### Post by jinglada on 2014-06-06
> **wgarcia said:**
> D'acord, però el que em desconcerta és el que dius en el teu missatge #3:
[http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679](http://ubuntuforums.org/showthread.php?t=2226157&p=13035679#post13035679)

Específicament el següent:

```

Vaig canviar UEFI per Legacy perquè ho vaig llegir en dos comentaris de la mateixa pàgina. Vaig tornar a iniciar amb l'USB live i vaig reinstal·lar amb l'opció d'esborrar previament la instal·lació anterior. 

I finalment s'inicia entrant directament a l'Uuntu 14.04 i ha quedat així:
```


Perquè si realment vas fer això, pot explicar el que hagi desaparegut la instal·lació de l'Ubuntu. Realment vas fer el que dius en aquest missatge #3? Perquè no surt en la seqüència que vam repassar ara.

**Perquè això és el que vaig fer a continuació de la seqüència que tu em vas posar.**

De tota manera, si et sembla més efectiu, puc començar de nou: 

1- poso el Boot Mode a UEFI, 
2- faig el restore de Windows, 
3- redueixo la partició de Windows
4- poso en off el fast boot de Windows
5- instal·lo Ubuntu
6- reinicio i et dic com queda

Què et sembla?

---

### Post by wgarcia on 2014-06-06
Sí, crec que millor intentar-lo un altre cop i aquests serien els passos.

---

### Post by jinglada on 2014-06-06
> **wgarcia said:**
> Sí, crec que millor intentar-lo un altre cop i aquests serien els passos.

Fet. A l'iniciar no surt el Grub i entra directament a Windows i el disc ha quedat així:

[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253789](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253789)


Edito: Prement F12 surt això:

[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253791](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253791)

i clicant l'Ubuntu surt el Grub així:

[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253793](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253793)

---

### Post by wgarcia on 2014-06-07
L'Ubuntu arrenca?

---

### Post by jinglada on 2014-06-07
> **wgarcia said:**
> L'Ubuntu arrenca?

Siiiiiii !!!

joan@joan-Aspire-E1-572:~$ ls /boot
abi-3.13.0-24-generic     efi                           memtest86+.bin                System.map-3.13.0-29-generic
abi-3.13.0-29-generic     grub                          memtest86+.elf                vmlinuz-3.13.0-24-generic
config-3.13.0-24-generic  initrd.img-3.13.0-24-generic  memtest86+_multiboot.bin      vmlinuz-3.13.0-29-generic
config-3.13.0-29-generic  initrd.img-3.13.0-29-generic  System.map-3.13.0-24-generic  vmlinuz-3.13.0-29-generic.efi.signed

joan@joan-Aspire-E1-572:/boot/efi/EFI$ cd /boot/grub
joan@joan-Aspire-E1-572:/boot/grub$ ls
fonts  grub.cfg  grubenv  locale  unicode.pf2  x86_64-efi
joan@joan-Aspire-E1-572:/boot/grub$ cd /boot/efi/EFI
joan@joan-Aspire-E1-572:/boot/efi/EFI$ ls
Boot  Microsoft  OEM  ubuntu

joan@joan-Aspire-E1-572:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdc4d3b68

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

---

### Post by wgarcia on 2014-06-07
Doncs segons ho entenc ara tens un sistema que arrenca directament a Windows, però si fas F12 des del menú que surt pots arrencar l'Ubuntu. 

Ho entenc bé?

---

### Post by jinglada on 2014-06-07
> **wgarcia said:**
> Doncs segons ho entenc ara tens un sistema que arrenca directament a Windows, però si fas F12 des del menú que surt pots arrencar l'Ubuntu. 

Ho entenc bé?

Si i gràcies a tu, wgarcia. Em pensava que no me'n sortiria aquesta vegada. Uff !!!

Exacte, arrenca directament a Windows, però si premo F12, des del menú que surt, puc arrencar l'Ubuntu des del punt 2 i el windows des dels punts 1 i 3.

[http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253791](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253791)

Quan premo el punt 2. Ubuntu, surt el Grub ([http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253793](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253793)), des del qual puc entrar a l'Ubuntu, a les opcions avançades de l'Ubuntu ([http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253797](http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253797)), al Windows i al System Setup.

Pregunta:

Per intentar arranjar el problema d'haver de prèmer F12, és ara que hauria de fer els següents passos:

7. Boot Repair
8. Fix the boot loader

???

---

### Post by wgarcia on 2014-06-09
Exacte, tot i que qui sap si no acaba embolicant-se tot un altre cop i tornem a la situació anterior... Al Grub et surt una opció per arrencar Windows? Suposo que no, oi?

---

### Post by jinglada on 2014-06-09
> **wgarcia said:**
> Exacte, tot i que qui sap si no acaba embolicant-se tot un altre cop i tornem a la situació anterior... Al Grub et surt una opció per arrencar Windows? Suposo que no, oi?

De moment potser és millor que no toqui res més, oi? I sí, ja t'ho dic en el missatge anterior: *Quan premo el punt 2. Ubuntu, surt el Grub, des del qual puc entrar a l'Ubuntu, a les opcions avançades de l'Ubuntu, **[COLOR="#FF0000"] al Windows[/COLOR]** i al System Setup.*

[IMG]http://ubuntuforums.org/album.php?albumid=2586&attachmentid=253793[/IMG]

---

### Post by wgarcia on 2014-06-09
D'acord, i l'últim punt, l'entrada al Windows es pot fer des d'aqui, oi?, no sols des del menú del F12...

---

### Post by jinglada on 2014-06-09
> **wgarcia said:**
> D'acord, i l'últim punt, l'entrada al Windows es pot fer des d'aqui, oi?, no sols des del menú del F12...

Exacte. I moltes gràcies per tot l'ajut, wgarcia.

---

### Post by wgarcia on 2014-06-09
Perfecte, ara s'haurà d'estar atent a veure què passa quan arribi una actualització del nucli de Linux d'Ubuntu i/o una actualització de Windows. Suposo que aquesta última no afectarà l'arrenc per F12, però no sé què passarà quan l'Ubuntu vulgui actualitzar el grub i configuri un nucli més nou.

---

