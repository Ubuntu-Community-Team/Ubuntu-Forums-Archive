---
title: "How to: Instalar Ubuntu en memory stick"
date: 2007-03-20
forum: Argentina Team
---

### Post by DuckMan on 2007-03-20
Traduccion: duckman
Fuente original: [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2)

Disfruten! :D

Este "how to" te mostrara como instalar Ubuntu en un memory stick. EL siguiente tutorial esta basado en esa distribución de Linux, pero deberia funcionar con cualquier otra.

Poder correr Ubuntu en un memory stick es muy practico y aprovecha los beneficios de la tecnología "live cd" (siendo capas de correr Linux en cualquier pc) y con la gran ventaja de ser mas transportable que un CD.

**1. Requerimientos**

Para poder seguir este tutorial, deberás poseer:

    * un LiveCD de Ubuntu
    * Un memory stick de al menos **1 Gb**
    * Un sistema Linux corriendo en una pc de escritorio

Una vez que obtienes todo esto, es hora de preparar el USB

**2. Preparando el disco USB**

2.1. Encontrando el dispositivo

En primer lugar, enchufa tu USB y encuentra a que dispositivo esta asociado. Para encontrar el dispositivo ejecuta el siguiente comando:

```
$ sudo fdisk -l
```

En mi sistema, el dispositivo aparece en /dev/sdb, Voy a usar /dev/sdb como referencia en este tutorial, por favor reemplazarlo acordemente según tus necesidades (sea sda, sdc ...).
Una vez encontrado, vamos a crear las particiones:

**[COLOR="Red"]Usar el dispositivo equivocado puede destruir tu sistema, chequea dos veces por favor.[/COLOR]**

2.2. Creando las particiones

Desmonta todas tus particiones:

```
$sudo umount /dev/sdb1
```

y ejecuta fdisk, la herramienta para editar particiones de Linux:

```
sudo fdisk /dev/sdb
```

Vamos a borrar la partición actual del dispositivo y crear 2 nuevas: una FAT de 750 mb que soportara todos los archivos del liveCD, y el resto en la otra partición.

Una vez ejecutado fdisk, apreta "d *x*" donde *x* es el numero de partición (podes tipear d solamente si solo tienes 1), luego:

    * n para crear una partición
    * p para hacerla primaria
    * 1 para que sea la primera partición
    * Acepta la opción por defecto o apreta 1 para empezar desde el principio del cilindro
    * +750M para hacerla de 750 mb
    * a para hacerla booteable
    * 1 para elegir la partición 1
    * t para cambiar el tipo de partición
    * 6 para setearla en FAT16

Ahora que tenemos nuestra 1ra partición, creemos la 2da:

    * n para crear la partición
    * p para hacerla primaria
    * 2 para que sea la segunda partición
    * Acepta la opción por defecto apretando enter
    * Acepta la opción por defecto para hacerla lo mas grande posible
    * Finalmente, w para aplicar los cambios

Las particiones fueron creadas, vamos a formatearlas

**2.3. Formateando las particiones**

La primera partición va a ser formateada en FAT16 y vamos a etiquetarla como "liveusb".

```
$ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1
```

La segunda va a ser de tipo ext2 con un tamaño de bloque de 4096 bytes y de etiqueta "casper-rw". No elijas otro nombre aqui porque si no no funcionara!.

```
$ sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
```

Hasta ahora, nuestro usb es capas de soportar el liveCD. Ahora vamos a copiar los archivos al memory stick.

**3. Instalando Ubuntu en el memory stick**
3.1. Montando la imagen del LiveCD

En primer lugar, tenemos que montar nuestra ISO (imagen de cd). Dependiendo de si tienes la imagen ISO o el cd, hay 2 maneras de hacerlo.

3.1.1. Montando desde un CD

Los que usen distribuciones amigables como Ubuntu, solo inserten el cd y se montara. Si no es tu caso:

```
$ sudo mount /media/cdrom
```

Debería montarse.

3.1.2. Montando desde una imagen ISO

Tenemos que crear un directorio temporal, usemos /tmp/ubuntu-livecd y luego montaremos la imagen (Usare una imagen de "Feisty fawn", la ultima version de Ubuntu a la fecha de hoy).

```
$ mkdir /tmp/ubuntu-livecd
$ sudo mount -o loop /path/to/feisty-desktop-i386.iso /tmp/ubuntu-livecd
```

Una vez que este lista, es tiempo de montar las nuevas particiones creadas en el usb:

3.2. Montando las particiones USB

Deberías tener acceso a las particiones simplemente enchufando el USB, las particiones aparecen en: /media/liveusb y /media/casper-rw.Si no es el caso, tendrías que montarlas manualmente:

```
$ mkdir /tmp/liveusb
$ sudo mount /dev/sdb1 /tmp/liveusb
```

Todas las particiones que necesitamos están montadas ahora, copiemos los archivos.

3.3. Copiando los archivos al USB

Recorre hasta el directorio del CD (en mi caso: /tmp/ubuntu-livecd ,pero podría ser /media/cdrom , y copia al USB, en el directorio raíz de la 1er partición los siguientes archivos:

    * las carpetas: 'casper', 'disctree', 'dists', 'install', 'pics', 'pool', 'preseed', '.disk'
    * El contenido de la carpeta 'isolinux'
    * y los archivos 'md5sum.txt', 'README.diskdefines', 'ubuntu.ico'
    * Como tambien estos archivos: 'casper/vmlinuz', 'casper/initrd.gz' y 'install/mt86plus'

```
$ cd /tmp/ubutu-livecd
$ sudo cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz install/mt86plus /media/liveusb/
```

Deberian aparecer errores de enlaces simbólicos que no pudieron crearse, ignoralos.

Vamos a la primer partición del USB y renombramos isolinux.cfg a syslinux.cfg:

```
$ cd /tmp/liveusb
$ sudo mv isolinux.cfg syslinux.cfg
```

Cambia /tmp/liveusb acorde a tu caso

Edita syslinux.cfg para que se vea asi:

DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

Uff!, finalmente tenemos nuestro USB casi usable. El ultimo paso que queda: hacerlo booteable.

3.4. Haciendo el USB booteable

Para hacerlo, tenemos que instalar syslinux:

```
$ sudo apt-get install syslinux
```

Desmontar /dev/sdb1 y hacerlo booteable:
```

$ cd
$ sudo umount /tmp/liveusb
$ sudo syslinux -f /dev/sdb1
```

Aqui ya estaremos orgullosos, renicia el sistema, setea tu BIOS para que bootee desde un usb y listo!

**4. Problemas comunes**

Si tienes problemas con tu memory stick, debe ser porque tu MBR esta dañado. Para arreglarlo, puedes usar lilo.

```
$ lilo -M /dev/sdb
```

Arreglaria el MBR en el dispositivo /dev/sdb

---

### Post by Nemesis Teufel on 2007-03-21
Sehr gut duckman!

Muy bueno, muchas gracias!

algunas duditas:
1. La memoria RAM tambien se actvaria? o sea.. la utilizaria tmb?
2. Si 1 es correcto: Cuando ejecute el llavero como livecd.. los programas que "instale" ocuparian el espacio de la RAM o se crearian momentaneamente en el llavero?
3: Puedo particionar el llavero para poner 1 gb para live cd de ubuntu y el otro gb para info?

---

### Post by DuckMan on 2007-03-21
lamentablemente hablamos de un "liveusb" si quisieras instalarlo, tendrias q tener 2 gb al menos..

y si, lo q te reste es para info, si creas una 3ra con el resto!

---

