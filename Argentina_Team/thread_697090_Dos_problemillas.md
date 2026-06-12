---
title: "Dos problemillas"
date: 2008-02-14
forum: Argentina Team
---

### Post by nemodot on 2008-02-14
Cada vez que el synaptic me trae una nueva versión de los Linux-Headers, como hoy, sucede que en el grub se duplican  las entradas de ubuntu, se repiten luego de la última, a nadie le pasa esto?

Puedo borrarlas con el editor del Grub, pero quisiera evitar que se duplicaran cada vez.

Por otro lado, al inicio de Ubuntu, se queda un largo rato haciendo una especie de Check Disk y luego me dice que hay diferencias en el disco y que no arregla esto automaticamente. Con cada inicio de ubuntu se sale de la pantalla de carga de ubuntu y me muestra los procesos que se van cargando, ahi es donde aparece el disk check ese. Como puedo reparar esto?

---

### Post by tzulberti on 2008-02-14
Primer punto: es normal que te aparezca "duplicada" la entrada de ubuntu. En verdad no esta duplicada, cada una hace referencia a una version del kernel distinta y/o tiene distintos parametros al momento de inicio.

Segundo punto: apagastes mal la maquina (boton de reset) o algo similar? En que clase de particion te esta tirando eso?

---

### Post by Ptero-4 on 2008-02-14
Primero: ubuntu te pone dos entradas por kernel. Una es la normal y la otra es la que te tira a la consola de recuperación de ubuntu.

Segundo: tu problema (si lo leí bien) suena más a un disco duro petando, revisalo con el smartmon.

---

### Post by nemodot on 2008-02-14
1) La entrada  de Grub que yo afirmo que es duplicada, lo digo asi, por que la versión de linux que muestra es exactamente la misma, en otras palabras las tres primeras opciones que aparecen estan duplicadas literalmente abajo.

2) El problema del inicio sucede siempre, recien la prendí, cuando estaba cargando con el logo de ubuntu se salió a mostrarme una lista con los procesos que se van cargando y se quedo en:

```
Checking File Systems
fsck 1.40.2 (12-jul-2007)
```

Y luego de un poco más de un minuto, un texto pasa muy rápido y sólo alcanzo a leer algo que se refiere a que hay diferencias entre NoSeQue y su Buckup y que no arreglará esto automaticamente.

Esto ya me pasaba de antes, pero no tardaba tanto como ahora, el texto se mostraba rápido y no se colgaba un rato en "checking file systems"

Luego se termina de cargar ubuntu, pero ese minuto más de demora me irrita mucho ya que ubuntu se inicia (o se solía iniciar) muy rapido en mi pc.

---

### Post by faktorqm on 2008-02-15
Hace una cosa, escribi en una consola 

```
cat /boot/grub/menu.lst
```

y postea la salida aca asi te podemos ayudar mejor. (entre tags de code por favor)

Y con lo del fsck yo lo solucione de una manera muy rara. Despues leyendo e investigando aprendi por que, pero basicamente, tendrias que entrar al bios y fijarte que hora tenes. Salir y arrancar ubuntu y fijarte que hora tenes. A mi me pasaba que por ejemplo, en el ubu tenia las 6 de la tarde y en el bios las 3, entonces habia un conflicto en el sistema de archivos por eso. La solucion es click derecho sobre el reloj, ir a preferencias, y activar la casilla UTC. Asi se me arreglo bien la hora. A modo anecdotario, te cuento que esto sucede cuando usas windows y particularmente ubuntu en la misma pc.

Sino lo que podes hacer (no se si anda) es poner en una consola 

```
fsck -v -f
```

-v es para que te muestre todo lo que pasa y -f para que te haga la comprobacion igual por mas que ya este marcada como buena. salu2!!

---

### Post by Oktubre on 2008-02-15
Buenas,

respecto al primer punto, una es para ingresar via normal, la otra para el modo de recuperacion (solo consola). Podes confirmarlo ingresando a cada una de las opciones.

Saludos,

---

### Post by nemodot on 2008-02-15
Parece ser que algunos no me comprendieron respecto al primer punto, más fácil será mostrarles una captura de mi editor de Grub con las entradas que afirmo están repetidas:

[IMG]http://img171.imageshack.us/img171/7486/sinnombrejk5.png[/IMG]

Sobre los segundo, puse el comando del fsck que me recomendaron, pero cuando me salió esto:

```
¡¡CUIDADO!!  Correr e2fsck en un sistema de ficheros montado
puede causar GRAVES daños al sistema de archivos.

```

me acobardé...

Ah, y respecto al comando cat, salió esto:

```
esteban@esteban-desktop:~$ cat /boot/grub/menu.lst
default 0
timeout 10
color cyan/blue white/blue

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro quiet splash locale=es_ES
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
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
# kopt=root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by faktorqm on 2008-02-18
hace "sudo gedit /boot/grub/menu.lst" borra todo lo que veas y pone todo esto:

```

default 0
timeout 10
color cyan/blue white/blue

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro quiet splash locale=es_ES
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fcf75e4d-2bb7-4d2b-ac27-071340f1a40d ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

```

Despues agarra un live cd de ubuntu, y hace desde una consola "fsck -v -f" sin montar la particion y listo... salu2!

---

