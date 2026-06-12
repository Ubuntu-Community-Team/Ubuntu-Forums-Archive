---
title: "Ubuntu no me reconoce el cdrom SATA"
date: 2007-09-29
forum: Argentina Team
---

### Post by Mataca on 2007-09-29
Chicos/as luego de mucho investigar no puedo montar la lectora de DVD SATA de mi nueva pc.
Como no la tengo muy clara en ingles no tengo idea que dicen en launchpad [_**[COLOR="Navy"]acá[/COLOR]**_]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295") parece que hay un bug con las lectoras SATA en el kernel.
La verdad no se bien que onda, la lectora en Win anda joya y es mas instalé Ubuntu desde la lectora... que se yo me vuelve loco.
Les posteo las config que encontre y diganme si hay alguna idea, gracias!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4abd2825-401f-444e-9c29-6eb20e6fd3a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=9f79232a-1acb-4a03-9b9a-6afafe0e971e /home           ext3    defaults        0       2
# /dev/sda3
UUID=AA68A18068A14C3F /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=a97af05f-1043-4d09-802b-f86fb9f8c4b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda6 /home ext3 rw 0 0
/dev/sda3 /windows ntfs rw,nls=utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by Mataca on 2007-10-01
A ver si alguien me me puede ayudar. =)

Chicos algo nuevo surgio, ahora aparece el cdrom en lugares/equipo. pero miren lo raro
utilice ```
sudo mount - a
``` y no sale ningún error

Pero cuando lo quiero usar, no sucede nada =( directamente no lo monta. Pero yo lo veo!
Ahora bien, lo quise montar desde el menu grafico y solo me dice: mount: special device /dev/scd0 does not exist


O sea, aparece graficamente pero no me lo lee... dios! ayuda plis que sin lectora no me sirve un SO

---

### Post by faktorqm on 2007-10-02
mataca! ahi en launchpad dice que pruebes esto y que arranca:

```
sudo hdparm -w /dev/scd0
```

pero que lo tenes que hacer cada vez que arrancas. o sea, todo mal. lo que lei ahi dice que el kernel quiere reiniciar el dispositivo y no termina nunca, entonces deshabilita el dma y afuera.

despues otro con otro chipset disinto al del anterior dice que no le funciono ese comando. ojo! que hay uno que dice que deshabilitando los modulos del kernel se soluciona y NO ES ASI.

Al final de todo, hay un chabon que actualiza el firmware de la lectora, y le va bien eso, asi que de ultima, postea que lectora tenes asi lo vemos. salu2!

EDITO:

aca esta lo del firmware, si tenes la misma lectora, ganamos tiempo.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295/comments/97](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/75295/comments/97)

proba tambien, de borrar del sistema estos dos paquetes que tienen conflictos con el montaje/desmontaje de la lectora:

"evms" y "evms-ncurses"

si los eliminaste, y sigue, postea tambien, primero en launchpad asi haces bulto, y despues aca en el foro la salida de dmesg y demas menesteres para saber que es lo que esta pasando. no dudes en preguntar si no sabes algo. salu2!!

---

### Post by Mataca on 2007-10-02
pff facktorqm como siempre, un amigo al servicio de todos =)

Hoy cuando llego a casa la trato de instlar, si hay que montarla cada vez q inicio, la verdad no me molestaria. al menos tengo lectora!

Chas gracias

---

### Post by Mataca on 2007-10-02
mataca@wika:~$ sudo hdparm -w /dev/scd0
/dev/scd0: No such file or directory

nunca se instalaron dichas librerias hayyy dios! no funciona

---

### Post by faktorqm on 2007-10-03
claro eso es lo que yo decia, el scd0 no existe......
estas segurisisimo que se llama asi? segun el fstab que posteaste si....

che y borraste los 2 paquetes esos a ver que onda?

te tiro otra: pone el live cd de instalacion, y cuando termine y te muestre el escritorio, es obvio que te tomo la lectora, entonces agarras y apretas CTRL + ALT + F1 para ver una consola y ahi fijate el fstab como esta montado, (creo que deberia estar como root, no se) alguien experimentado? 
curiosidad de paso: fijate si con el fstab del live cd estan puestos los uuid. capaz no usa uuid y capaz es ese el problema.

esta media media la cosa. postea todas las salidas (usa los tags de code por favor) de los siguientes comandos:

```
dmesg | grep ata
```

```
lspci | grep SATA
``` (respeta mayus y minus)

```
lsmod | grep sata
```

```
cat /etc/fstab
```

```
cat /etc/mtab
```

cuando booteas desde el live, y cuando booteas normal. asi vemos las diferencias y lo que te falta. salu2 chabon!!

EDITO: T fijaste q firmware tiene tu lectora? salu2!

---

### Post by Mataca on 2007-10-17
Revivo este tread para contarles lo siguiente:
A pesar de todas las ayudas (estoy muy agradecido especialmente con Faktorqm) no pude montar en ningun momento la lectora SATA en Ubuntu 7.04

El problema es un bug en el kernel, entonces postee en launchpad (como se debe) el bug que en realidad ya estaba posteado, sólo me sumé a la causa.

Hace 3 días maso instalé la 7.10 RC obviamente con el kernel nuevo. Y para mi grata sorpresa, arreglaron el bug y tengo lectora de dvd seeeeeeeee !!!!! :)

Quería contar esto, para que cada uno de ustedes cuando encuentre un bug, lo reporte. El deber ser pasa por cada uno de nosotros, pero si encuentran un bug, por mas tonto que parezca, reportenlo! y si no saben avisen que alguno de nosotros se va a copar.

Me animaría a decir que es una responsabilidad nuestra, a cambio de un SO de lujo. Pero como no lo es desde mi pequeña pc les pido que colaboren =)

Por que realmente el launchpad funciona, 

Sorry si me puse muy cursi

---

### Post by faktorqm on 2007-10-18
me alegro de que lo hayan resuelto y tengas lectora! salu2!!

---

