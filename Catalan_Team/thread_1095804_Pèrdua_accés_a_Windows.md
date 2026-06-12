---
title: "Pèrdua accés a Windows"
date: 2009-03-14
forum: Catalan Team
---

### Post by jinglada on 2009-03-14
Després d'instal·lar l'Ubuntu he perdut l'accés al w-vista.

Aquesta és la situació actual:
joan@joan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=26a92486-3c94-4cbf-b0fe-7cdaf335b0ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


joan@joan-laptop:~$ sudo fdisk -l
[sudo] password for joan: 

Disc /dev/sda: 320.0 GB, 320072933376 octets
255 heads, 63 sectors/track, 38913 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf571c4dc

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        1567    12586896    7  HPFS/NTFS
/dev/sda2            1568        6193    37158345    7  HPFS/NTFS
/dev/sda3            6194       38913   262823400    5  Estesa
/dev/sda5            6194       11292    40957686   83  Linux
/dev/sda6           37583       38913    10691226   82  Intercanvi Linux / Solaris
/dev/sda7           11293       37582   211174393+  83  Linux

---

### Post by tanreb20 on 2009-03-14
I el grub et surt la opció per entrar a windows?

cat /boot/grub/menu.lst ---> Enganxa aixo aqui.

---

### Post by PatrickVogeli on 2009-03-15
Prova amb aixo

sudo mkdir /media/windows
sudo mount /dev/sda2 /media/windows
 
Si funciona, ho pets fer permanent afegint aquesta linia a l'fstab:

/dev/sda2 /media/windows ntfs user,auto,noexec,umask=0 0 0

salut

---

### Post by jinglada on 2009-03-15
> **tanreb20 said:**
> I el grub et surt la opció per entrar a windows?

cat /boot/grub/menu.lst ---> Enganxa aixo aqui.

joan@joan-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=77942702-4f80-4d16-88a7-91a5b0d1ff22

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		77942702-4f80-4d16-88a7-91a5b0d1ff22
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		77942702-4f80-4d16-88a7-91a5b0d1ff22
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		77942702-4f80-4d16-88a7-91a5b0d1ff22
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		77942702-4f80-4d16-88a7-91a5b0d1ff22
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=77942702-4f80-4d16-88a7-91a5b0d1ff22 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		77942702-4f80-4d16-88a7-91a5b0d1ff22
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by PatrickVogeli on 2009-03-15
has de comprovar quina opcio del windows funciona al grub, la primera o la segona. Segurament, sera la segona la que t'entri al windows i, per tant, la primera entrada la pots borrar del menu.lst.

---

### Post by jinglada on 2009-03-15
> **PatrickVogeli said:**
> has de comprovar quina opcio del windows funciona al grub, la primera o la segona. Segurament, sera la segona la que t'entri al windows i, per tant, la primera entrada la pots borrar del menu.lst.

Ara si! És la segona. La primera em porta al programa de recuperació de Packard Bell i a l'entorn de recuperació de Windows. En lloc de treure-la del menu.lst potser la podria posar en segon lloc i així quedaria accessible si mai cal fer-la servir?!


Què faig amb el que em deies en el primer missatge? 

> sudo mkdir /media/windows
sudo mount /dev/sda2 /media/windows

Si funciona, ho pets fer permanent afegint aquesta linia a l'fstab:

/dev/sda2 /media/windows ntfs user,auto,noexec,umask=0 0 0

Com puc saber si funciona, si he de reiniciar per entrar a Windows?
Ho poso en el fstab?

Gràcies

---

### Post by PatrickVogeli on 2009-03-15
aixo de l'fstab es per entrar a la particio del windows des d'ubuntu, per accedir a les dades i tot aixo.

Sobre la particio de recovery... si, ho pots deixar hi simplementa canviar el titol i posar-li Recovery Packard Bell o qualsevol cosa.

salut

---

### Post by jinglada on 2009-03-15
> **PatrickVogeli said:**
> aixo de l'fstab es per entrar a la particio del windows des d'ubuntu, per accedir a les dades i tot aixo.

Ah. doncs si que funciona el muntatge de windows a media però com que de moment no hi tinc res...

Marcaria el fil [SOLVED] però no m'apareix l'opció "Mark this thread as solved" a "Thread tools".

---

### Post by carevolta on 2009-03-18
Bon dia, no sé si aporte cap informació nova, però per casualitat ahir vaig instal·lar Ubuntu en un Acer amb Windows Vista d'un amic i em vaig trobar en la mateixa situació. Després de l'ensurt inicial i de buscar per internet, certifique que la solució és la correcta i que la segona opció de Windows Vista/Longhorn (loader) permet entrar al SO. Ara ja és qüestio de gustos retocar menu.lst.

---

