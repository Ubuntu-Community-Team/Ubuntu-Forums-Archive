---
title: "Problemas con grub"
date: 2006-11-19
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-11-19
Siguiendo los pasos de este [how-to]("http://cmaverick.wordpress.com/2006/08/12/grub-estilo-suse-en-ubuntu/")

tuve el problema que cuando iniciaba la imagen, pero cuando seleccionaba ubuntu, cargaba la barra pero acto seguido se ponia la pantalla en negra como que no encuentra donde iniciar.

Vean una foto de mi disco(aunque me de verguenza) y como es que tendria que hacer ya que me parece que hago algo mal :s

[IMG]http://i117.photobucket.com/albums/o77/nemesisteufel/Untitled.jpg[/IMG]

en mi disco como master tengo instalado winpx con ntfs  y en el slave tengo edgy y un espacio en ntfs para hacer backup.

espero que me puedan ayudar.

---

### Post by beuno on 2006-11-19
¿No bootea directamente?

En tal caso te pediria que entres con un Live CD y postees tu menu.list del grub (/boot/grub/)

---

### Post by cocotapioca on 2006-11-20
Para estos casos es bueno tener a mano un Super Grub Disk... 
En el comando "sudo grub-install /dev/hda" cambiaste hda x lo q te corresponde?
Como dice beuno, lo mejor es q postees tu menu.lst

---

### Post by kalel on 2006-11-20
leete esto

[http://www.3d-arg.com/forum/linux/13663-super-disco-grub.html](http://www.3d-arg.com/forum/linux/13663-super-disco-grub.html)

---

### Post by QUASAR_FREAK on 2006-11-20
Como me leechean el grub patcheado jaja

fijate kuando estes en grub apreta escape, y deberias ir a modo texto de grub, ahi parate sobre la linea de inicio de ubuntu y apreta la "e", asi editas la entrada de ubuntu, fijate la primera linea deberia decir root=algo, ese algo deberia ser el id de tu disco, si no lo sabes ponele el dispositivo, en tu kaso seria root=/dev/hdb1)

despues de todo eso apreta enter y luego "b" para bootear usando esas modificaciones, si inicia ponelo para siempre en /boot/grub/menu.lst y fijate de hacer backups siempre ke modifiques archivos de sistema.

Suerte!

---

### Post by Nemesis Teufel on 2006-11-20
sigo sin poder arrancar, ahora me voy a comprar un diskette para probar el super grub disk.

aca esta el menu.list (espero que sea esto)

grub> find /boot/grub/stage1
 (hd1,0)

y con lo que dijo QUASAR_FREAK hice los pasos que me dijiste y paso esto cuando apretaba B para bootear

grub edit > root (hd1,0)
error 11: unrecognized device string
Press a key to continue..

lo que me resulta raro es que deberia decir /dev/hdb1 al menos, ya que lo cambie antes.

Por otro lado, en el boot del safe mode del kernel dice esto:
Kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash locale=es_ES

y va bien, va a la linea de codigo fuera del gnome(no se como se llama) y dice el disco donde arranca.

estoy mal parido :(
hay si no alguna forma de volver todo como antes?, aunque duda mucho..

---

### Post by beuno on 2006-11-20
¿Estas con edgy o con dapper?

---

### Post by Nemesis Teufel on 2006-11-20
> ¿Estas con edgy o con dapper?

edgy, ya cambio mi info.

---

### Post by beuno on 2006-11-20
> **Nemesis Teufel said:**
> edgy, ya cambio mi info.

Ahi esta el problemaaaaaaaaaaaaaaaaaa.
Edgy no esa mas esa forma de identificar las particiones, tiene un ID unico para que puedas cambiar la particion de lugar todas las veces que quieras.
El tutorial que vos seguiste, es para Dapper y usa la forma vieja de identificar.

Las entradas del grub en Edgy son algo asi:

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=7adaf9c3-dd4d-44fa-ba3d-ddef34283ba8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```


Postea aca tu /boot/grub/menu.lst y te digo como seguimos.

---

### Post by beuno on 2006-11-20
Pensandolo bien, tambien mantiene la compatibilidad para atras.
Igual quiero tu menu.lst

---

### Post by Nemesis Teufel on 2006-11-20
si.. asi se ve mi grub :-)

> Postea aca tu /boot/grub/menu.lst y te digo como seguimos.

te referis a esto?
grub> find /boot/grub/menu.lst
 (hd1,0)


> compatibilidad para atras
ahh me haces acordas a mis clases de teleinformatica y el magnifico profesor que tenia!

cuando no este mas con live cd paso foto

---

### Post by beuno on 2006-11-21
Tiene que tener mucho mas texto que eso tu menu.lst...
sino ahi tenes el principio del problema

---

### Post by Nemesis Teufel on 2006-11-21
y el comando: find /boot/grub/menu.lst  es el correcto? o hay algun otro?

---

### Post by QUASAR_FREAK on 2006-11-21
En edgy aun se puede usar root=/dev/dispositivo en lugar del id pero perdes la compatibilidad de mover el disco de un lado a otro.

Para ver el contenido de tu menu.lst usa
grub> cat (hd0,1)/boot/grub/menu.lst

---

### Post by Nemesis Teufel on 2006-11-21
> En edgy aun se puede usar root=/dev/dispositivo en lugar del id pero perdes la compatibilidad de mover el disco de un lado a otro.
no pienso andar moviendo el disco, lo dejo ahi quietito :-D 

> Para ver el contenido de tu menu.lst usa
grub> cat (hd0,1)/boot/grub/menu.ls

aca va

```

grub> cat (hd1,0)/boot/grub/menu.lst
gfxmenu /boot/grub/message.ubugrey
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default             0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout             10

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
# title             Windows 95/98/NT/2000
# root              (hd0,0)
# makeactive
# chainloader       +1#
# title             Linux
# root              (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=a7a7d9bb-ca77-48ef-b0a2-47f7de6946e4 ro
# kopt_2_6=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet splash locale=es_ES

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

## ## End Default Options ##

title               Ubuntu, kernel 2.6.17-10-generic
root                (hd1,0)
kernel              /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet spl
ash locale=es_ES
initrd              /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title               Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root                (hd1,0)
kernel              /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd              /boot/initrd.img-2.6.17-10-generic
boot
title               Ubuntu, memtest86+
root                (hd1,0)
kernel              /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title               Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title               Microsoft Windows XP Professional
root                (hd0,0)
savedefault
makeactive
chainloader     +1



```

Un poco largo fue.

---

### Post by ariel on 2006-11-21
> **beuno said:**
> Pensandolo bien, tambien mantiene la compatibilidad para atras.
Igual quiero tu menu.lst


@Beuno: efectivamente, si removes los unique-ids de los discos, no pasa nada, el uso de los ids es opcional, esta documentado y lo pude comprobar en la practica tb. :)

@nemesis: yo tuve problemas similares despues de borrar o crear nuevas particiones en mi disco, y tambien pasa si por error windows o algo te borra el mbr del disco.

Yo use varias veces el procedimiento que sigue. (Use AT YOUR OWN RISK :)), no se si aplica en tu caso pero te puede dar una idea.

 > GRUB Restore after GParted or Windows breaks it:
   1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
   2. Open a Terminal. Go SuperUser (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.
   3. Type "grub" which makes a GRUB prompt appear.
   4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". 
      Use whatever your computer spits out for the following lines.
   5. Type "root (hd0,3)".
   6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. 
      If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
      Nota: yo tuve que usar: "setup (hd0)"
   7. Type "quit".
   8. Restart the system. Remove the bootable CD.

---

### Post by Nemesis Teufel on 2006-11-22
nada ariel, probe con las de formas en setup, tanto el (hd1,0) que me da como con el (hd0) que te funciono a vos, mismos resultados.

Pregunta: para que sirve el "sudo -i"?

---

### Post by QUASAR_FREAK on 2006-11-22
es para simular el login de root, onda temporalmente te setea dentro de esa terminal el home como root el path del root y demas =)

Si bien esta en ingles por defecto podes instalar los manuales en español y poner

man sudo

---

### Post by Nemesis Teufel on 2006-11-22
gracias quasar =)

---

### Post by Nemesis Teufel on 2006-11-25
Enconté la solución!!

formatear..

y si, no me quedaba otra y me pudri de windows.

Igual no tenia nada importante aunque me jodo yo solo por andar toqueteando dodne no debo.
De todos modos voy a hacerlo otra vez y espero que salga!!

---

### Post by beuno on 2006-11-26
No se si eso lo llamaria "solucion", pero me alegro que lo hayas resuelto.

---

