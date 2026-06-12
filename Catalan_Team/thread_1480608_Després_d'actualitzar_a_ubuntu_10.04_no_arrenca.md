---
title: "Després d'actualitzar a ubuntu 10.04 no arrenca"
date: 2010-05-11
forum: Catalan Team
---

### Post by jmfubu on 2010-05-11
Hola,

Vaig fer una actualització de 9.10 a 10.04 i ara em trobo que Ubuntu no arrenca. Ni amb Kernel 26.32 ni 26.31 Durant l'actualització vaig ordenar que no actualitzés el grub per evitar problemes. Com ho puc solucionar?

Tinc instal·lat i funcionant Windows XP.

Gràcies.

---

### Post by wgarcia on 2010-05-12
Hauries d'explicar una mica millor exactament què passa. Mostra el grub? Queda la pantalla en negre i no fa res quan intentes començar l'Ubuntu des del grub?

---

### Post by jmfubu on 2010-05-13
Com es desprén del missatge surt el Grub amb 2 ubuntu amb kernels diferents i les corresponents versions recovery. També hi ha dues opcions per a Windows XP que funcionen.

El problema és que si cap opció d'Ubuntu respon.

Gràcies.

---

### Post by wgarcia on 2010-05-13
Peró què passa exactament, sembla començar i queda una pantalla negra?

---

### Post by jmfubu on 2010-05-13
Si cliques en el grub qualsevol de les línies d'Ubuntu surt el següent missatge:

error:unknown command "recordfail"
Press any key to continue

Recordo que en el procés d'actualització a 10.04 vaig triar l'opció de no actualitzar el grub.

---

### Post by SiscoGarcia on 2010-05-13
> **jmfubu said:**
> Si cliques en el grub qualsevol de les línies d'Ubuntu surt el següent missatge:

error:unknown command "recordfail"
Press any key to continue

Recordo que en el procés d'actualització a 10.04 vaig triar l'opció de no actualitzar el grub.

També et surt aquest missatge amb les «recovery mode»? Has provat a entrar en l'opció d'arreglar paquets trencats?

Per cert, si prems qualsevol tecla com et demana:
```
[I]error:unknown command "recordfail"
Press any key to continue[/I]
```
què passa?

---

### Post by jmfubu on 2010-05-13
Sí amb Recovery mode surt el mateix missatge

No sé com fer això dels paquets trencats

Si clico qualsevol tecla torna al grub

---

### Post by wgarcia on 2010-05-14
Què posa a dalt del tot de la pantalla inicial del Grub? (més que res per assegurar que realment tinguis el grub 0.97 i no hagis instal·lat el grub 2 per alguna raó)

---

### Post by jmfubu on 2010-05-14
Dalt de tot hi posa

Grub version 1,97 beta4

---

### Post by wgarcia on 2010-05-15
Doncs sembla que sí que se t'ha instal·lat el Grub 2, perquè la línia de dalt està mostrant el nou grub, tot i que ja hi ha una actualització a la versió 1.98. 

Llavors el que pots fer és un cop que vegis el menú del grub, prèmer la tecla "e", i podràs editar el menú puntualment per a una arrencada. Esborra la primera línia on hauria de sortir-te "recordfail", i mira si arrenca. 

Si arrenca instal·la totes les actualitzacions que t'oferirà un cop que estiguis al teu escriptori, i mira si el problema desapareix.

---

### Post by jmfubu on 2010-05-15
Gracies.  Estic a l'Ubuntu. Ja he pogut arrencar però  no puc actualitzar. Si ho comprovo em diu que ja està actualitzat. El problema continua i per arrencar cada vegada he de fer el mateix. Se us ocorre alguna altra cosa?

---

### Post by wgarcia on 2010-05-16
M'estranya una mica perquè la versió 1.97 era la que hi havia a Karmic Koala i la versió 1.98 és la que hi ha a Lucid, per això et deia d'actualitzar tot a veure si això ho canviava. Què et surt quan entres :

uname -a

a una terminal de comandes?

---

### Post by jmfubu on 2010-05-16
Doncs em surt això:

Linux NOU 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

(Ara ja tinc paquets per actualitzar. Ho intento i en dic el resultat)

---

### Post by jmfubu on 2010-05-16
> **jmfubu said:**
> Doncs em surt això:

Linux NOU 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

(Ara ja tinc paquets per actualitzar. Ho intento i en dic el resultat)

He actualitzat tots els paquets però no s'ha resolt.

---

### Post by wgarcia on 2010-05-17
Et continua sortint:

Grub version 1,97 beta4

a dalt del menú del Grub?

---

### Post by jmfubu on 2010-05-17
> **wgarcia said:**
> Et continua sortint:

Grub version 1,97 beta4

a dalt del menú del Grub?

Sí.

Grub version 1.97 [un signe una mica estrany] beta4

---

### Post by wgarcia on 2010-05-18
No se t'ha actualitzat el grub a l'última versió ("1.98"). Mira d'obrir Sistema -> Gestor de Paquets Synaptic, i allà marcar 

grub                    0.97-29ubuntu60

per desinstal·lar i 

grub-pc
grub2
grub-common

per instal·lar.

Tot hauria d'anar bé en la substitució del vell grub pel nou, però quan es treballa amb el grub sempre s'ha d'estar preparat, perquè és el mecanisme que dóna entrada al sistema. 

Per això és molt útil tenir preparat un CD Live d'Ubuntu provat que funcioni per arrencar el sistema, per si s'ha d'arreglar alguna cosa del grub arrencant el sistema des del CD, cosa que es pot fer si fa falta. 

Tot i que insisteixo que no crec que sigui necessari en el teu cas reinstal·lant el grub des del propi sistema ja arrencat.

---

### Post by jmfubu on 2010-05-18
> **wgarcia said:**
> No se t'ha actualitzat el grub a l'última versió ("1.98"). Mira d'obrir Sistema -> Gestor de Paquets Synaptic, i allà marcar 

grub                    0.97-29ubuntu60

per desinstal·lar i 

grub-pc
grub2
grub-common

per instal·lar.

Tot hauria d'anar bé en la substitució del vell grub pel nou, però quan es treballa amb el grub sempre s'ha d'estar preparat, perquè és el mecanisme que dóna entrada al sistema. 

Per això és molt útil tenir preparat un CD Live d'Ubuntu provat que funcioni per arrencar el sistema, per si s'ha d'arreglar alguna cosa del grub arrencant el sistema des del CD, cosa que es pot fer si fa falta. 

Tot i que insisteixo que no crec que sigui necessari en el teu cas reinstal·lant el grub des del propi sistema ja arrencat.

No he pogut marcar grub                    0.97-29ubuntu60. No ho tenia instal·lat. Si ho marcava  em desinstal·lava grub pc. Total que he  instal·at (o reinstal·lat) grub pc; grub common i  grub2. Però tot continua igual.

---

### Post by jmfubu on 2010-05-18
Finalment he desintal·lat 
sudo aptitude purge grub2 grub-common grub-pc grub2-splashimages

i he instal·lat
sudo aptitude install grub2 grub2-splashimages os-prober

amb molts dubtes perquè em feia preguntes sobre coses que no entenia.

Ara ja funciona. Això sí:
1. Des que arrenca Ubuntu, triga més d'un minut a sortir l'escriptori.
2. Conitnua sortint la versio 1.97 beta4 del grub.

Gràcies per tot. Si convé algun aclariment només cal que ho diguis.

---

### Post by wgarcia on 2010-05-18
Pots posar el següent a una terminal de comandes?:

sudo aptitude search grub | grep ^i

i posar aquí el resultat?
(Mostra quins paquets que continguin grub al nom estan instal·lats, la línia comença amb "i")

---

### Post by jmfubu on 2010-05-18
> **wgarcia said:**
> Pots posar el següent a una terminal de comandes?:

sudo aptitude search grub | grep ^i

i posar aquí el resultat?
(Mostra quins paquets que continguin grub al nom estan instal·lats, la línia comença amb "i")

i A grub-common                     - GRand Unified Bootloader, version 2 (commo
i A grub-pc                         - GRand Unified Bootloader, version 2 (PC/BI
i   grub2                           - GRand Unified Bootloader, version 2 (dummy
i   grub2-splashimages              - a collection of great GRUB2 splashimages

---

### Post by wgarcia on 2010-05-19
Aquests són els paquets que has de tenir, però m'estranya que es continuï sortint "1.97" quan hauria de sortir "1.98". 

Hi ha un programeta que mostra on està instal·lat el grub. L'has de baixar de:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Posa'l en qualsevol lloc que puguis accedir (per exemple el teu "home") i entra en una terminal de comandes:

 sudo bash ~/boot_info_script*.sh 

Crearà un arxiu que es diu "RESULT.txt". Posa els resultats aquí a veure si es pot veure si el grub està instal·lat al lloc correcte.

---

### Post by jmfubu on 2010-05-19
> **wgarcia said:**
> Aquests són els paquets que has de tenir, però m'estranya que es continuï sortint "1.97" quan hauria de sortir "1.98". 

Hi ha un programeta que mostra on està instal·lat el grub. L'has de baixar de:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Posa'l en qualsevol lloc que puguis accedir (per exemple el teu "home") i entra en una terminal de comandes:

 sudo bash ~/boot_info_script*.sh 

Crearà un arxiu que es diu "RESULT.txt". Posa els resultats aquí a veure si es pot veure si el grub està instal·lat al lloc correcte.
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disc /dev/sda: 40.0 GB, 40020664320 octets
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    74,862,899    74,862,837  83 Linux
/dev/sda2          74,862,900    78,156,224     3,293,325   5 Extended
/dev/sda5          74,862,963    78,156,224     3,293,262  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disc /dev/sdb: 120.0 GB, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disc /dev/sdc: 500.1 GB, 500107862016 octets
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdc2          81,915,435   976,768,064   894,852,630   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2: PTTYPE="dos" 
/dev/sda5        fd41890f-5838-4565-b4a9-c068f9c3f6df   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1470BE4970BE30FA                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F064FA1564F9DDF2                       ntfs       Disc Windows                  
/dev/sdc2        46F8865AF886485F                       ntfs       Disc quart                    
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="7"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    linux    /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1470be4970be30fa
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set f064fa1564f9ddf2
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b0c16c89-a8ae-46a5-b42c-476ad9a9a5ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fd41890f-5838-4565-b4a9-c068f9c3f6df none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.7GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
   6.9GB: boot/initrd.img-2.6.31-20-generic
   1.9GB: boot/initrd.img-2.6.32-22-generic
   2.2GB: boot/vmlinuz-2.6.31-20-generic
   1.9GB: boot/vmlinuz-2.6.32-22-generic
   1.9GB: initrd.img
   6.9GB: initrd.img.old
   1.9GB: vmlinuz
   2.2GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by wgarcia on 2010-05-20
Sembla que tens 3 discos, un de 40, un de 120 i un altre de 500 Gigues. En el disc de 40 tens l'Ubuntu, en el de 120 tens uns Windows XP  i en el de 500 tens instal·lat un altre Windows XP. 

Una cosa estranya és que la primera partició (/dev/sda1) on hi ha el linux, té un sistema d'arxius "fat16". Aquest és un sistema d'arxius molt primitiu que no permet definir ni tan sols permisos. 

Bé, de totes maneres sembla que el teu sistema et funciona ara, però en quant pogués miraria d'esbrinar una mica més com està muntat i si convé reinstal·lar l'Ubuntu de zero al disc de 40 gigues.

---

### Post by jmfubu on 2010-05-20
> **wgarcia said:**
> Sembla que tens 3 discos, un de 40, un de 120 i un altre de 500 Gigues. En el disc de 40 tens l'Ubuntu, en el de 120 tens uns Windows XP  i en el de 500 tens instal·lat un altre Windows XP. 

Una cosa estranya és que la primera partició (/dev/sda1) on hi ha el linux, té un sistema d'arxius "fat16". Aquest és un sistema d'arxius molt primitiu que no permet definir ni tan sols permisos. 

Bé, de totes maneres sembla que el teu sistema et funciona ara, però en quant pogués miraria d'esbrinar una mica més com està muntat i si convé reinstal·lar l'Ubuntu de zero al disc de 40 gigues.

He instal·lat ubuntu 10.04 des de zero al disc de 40 Gb. Tot resolt. Moltes gràcies.
 (La utilitat de discos em diu que aquest disc té algun sector defectuós, però.)

---

