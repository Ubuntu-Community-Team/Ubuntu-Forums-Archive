---
title: "initramfs sin solucion aparente."
date: 2015-07-12
forum: Argentina Team
---

### Post by rafa-yael on 2015-07-12
Hola a todos.
 Antes que nada quisiera comentarles que he buscado por mas de 8 horas por internet, leyendo foros diversos y documentacion en ingles y no he podido encontrar solucion a mi problema No soy muy conocedor de linux pero me defiendo. Actualmente es mi sistema operativo por defecto. Es una instalacion limpia en el disco duro.
 Ayer por la noche estaba trabajando con Ubuntu Studio 14.04 y de repente se me apago el computador. No se si fue un bajon de luz o que paso. Al reiniciarse me aparecio lo que ahora se que es el prompt de initramfs.
 Probe iniciar en modo recovery y regreso al mismo prompt. Escribi "exit" y se congela despues de algunas lineas. Probre con rescatux desde una usb, desde donde estoy escribiendo esto. Probe lo siguiente.
```


 root@debian:/home/user# sudo fdisk -l
 Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9a01000c
    Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1      121602   976759808   83  Linux
 Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000614c0
    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              32       19458   156039169    5  Extended
/dev/sdb5              32       19458   156039168   8e  Linux LVM
 Disk /dev/sdc: 4007 MB, 4007264256 bytes
28 heads, 52 sectors/track, 5375 cylinders
Units = cylinders of 1456 * 512 = 745472 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2        5375     3911680    c  W95 FAT32 (LBA)
 Disk /dev/dm-0: 153.3 GB, 153343754240 bytes
255 heads, 63 sectors/track, 18642 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 Disk /dev/dm-0 doesn't contain a valid partition table
 Disk /dev/dm-1: 6438 MB, 6438256640 bytes
255 heads, 63 sectors/track, 782 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 Disk /dev/dm-1 doesn't contain a valid partition table
root@debian:/home/user# sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
 e2fsck 1.41.12 (17-May-2010)
/dev/sdb1: clean, 381/62248 files, 229399/248832 blocks

``` 
sdb1 es el que tiene la instalacion de linux. He tratado de montar pero me da este error- 
[INDENT]DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

[/INDENT]
y despues ...[INDENT] Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/mapper/ubuntu--studio--vg-root,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so 
[/INDENT]
La particion de sistema si la puede montar. Son 255 megas. Los 153 GB restantes pues muestran el error.
 Con gparted selecciono /deb/sdb y me aparece...

/dev/sdb1 ext2 /media/7b8a7c3b-ce9b-4da6-9cff-99d93d84cb7a
/dev/sdb2 extended
/dev/sdb5 lvm2 VeDNw6-dWlx-sO55-uVQr-871g-dxPX-qYTWBC

 
Seleccine la opcion partition>check reinicio y todo igual.

 
La verdad no se que hacer. Probe muchas mas cosas pero ninguna medio resultado. Espero que me puedan ayudar.

---

### Post by gmunioz on 2015-07-12
Tienes un sistema de particiones LVM.
Este es un tipo de particionado que permite unir varios discos físicos en uno lógico, 
permitiendo que el sistema que está en uso pueda ser aumentado de tamaño. 
La mayoria de servidores Gnu/Linux usan este tipo de particionamiento.
El problema de este tipo de particionamiento es que no se pueden montar las
particiones directamente desde cualquier otra distribución Gnu/Linux.
¿Qué importa esto en este caso? Importa porque tu sistema de archivos
está corrupto y para repararlo debes acceder desde una sesión live y al tener 
parte del sistema instalado sobre un LVM, se complica un poco. 
Inicia con un live-dvd/usb de Ubuntu 14.04.
Terminada la carga abre una terminal.
En la terminal ejecuta:
> $ sudo -i
# apt-get update
# apt-get install lvm2
# modprobe dm-mod
# vgchange -a y
# lvscan
Conforme lo que has posteado, debería informarte algo así como:
> ACTIVE &#8216;/dev/VolGroup00/LogVol00&#8242; [153.50 GB] inherit
Ese es el nombre de la partición que debes reparar, lo haces con
> #fsck /dev/VolGroup00/Log/Vol00


---

### Post by rafa-yael on 2015-07-13
HA!!! Tan sencilla solucion! Gracias!! Asunto resuelto.

---

