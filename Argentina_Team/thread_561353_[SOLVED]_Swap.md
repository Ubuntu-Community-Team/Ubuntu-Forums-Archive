---
title: "[SOLVED] Swap"
date: 2007-09-27
forum: Argentina Team
---

### Post by Vero1 on 2007-09-27
Hola,

Quisiera saber por qué Swap se deshabilita en cada reboot.

gracias

---

### Post by asmoore82 on 2007-09-27
if you wanted to disable Swap you would need to **comment out**
its entry in ``/etc/fstab'' comments are marked with a ``#''
so you would have to change like **this** ...

```

**~$** cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4fa903bd-fdb4-4c31-97de-92382088c774 /               ext3    defaults,noatime,errors=remount-ro 0       1
# UUID=C2A8259FA82592C9 
/dev/sda1       /media/windows        ntfs    defaults,noauto,user,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=cd9d18d9-043d-4755-98d2-becb79822a25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

tmpfs           /tmp            tmpfs   defaults        0       0
**[B]~$** gksudo gedit /etc/fstab[/B]
**~$** cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4fa903bd-fdb4-4c31-97de-92382088c774 /               ext3    defaults,noatime,errors=remount-ro 0       1
# UUID=C2A8259FA82592C9 
/dev/sda1       /media/windows        ntfs    defaults,noauto,user,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
**#**UUID=cd9d18d9-043d-4755-98d2-becb79822a25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

tmpfs           /tmp            tmpfs   defaults        0       0

```

---

### Post by Vero1 on 2007-09-27
Hi, asmore82,

Thanks for your answer but I don't want disable swap.

I need to know why appears disabled after every boot.

regards

---

### Post by asmoore82 on 2007-09-27
it is diabled after reboot or just empty?
the kernel won't start using swapspace until the physical
RAM is in danger of filling up ...
you can change the kernel's tendancy to use swap by changing
the ``swapiness'' value in ``/etc/sysctl.conf''

[https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e](https://help.ubuntu.com/community/SwapFaq#head-b179a5c0d7df0ab7d0ea1d58caaa47c7a5f8ab0e)

---

### Post by Vero1 on 2007-09-28
It is disabled after reboot.

In fstab says:

UUID=472efe3a-916c-4b21-9375-cff5b1007fd7 none            swap    sw              0       0

Have I to change something here?

spawiness does not exits.

thanks

---

### Post by asmoore82 on 2007-09-29
> **Vero1 said:**
> It is disabled after reboot.

how do you know? what is the specific symptom?

---

### Post by Vero1 on 2007-09-29
As I had many trouble with my partitions, I run gparted every time to see if all are working.

---

### Post by asmoore82 on 2007-09-29
run this command to see what swap exists;
if similar output shows up after a reboot, everything is fine.

```
**~$** cat /proc/swaps 
Filename                                Type            Size    Used    Priority
/dev/sda3                               partition       1052248 33888   -1
```

---

### Post by Vero1 on 2007-09-29
I've got this answer:

cut: se debe indicar una lista de bytes, caracteres o campos
Pruebe `cut --help' para más información.

Sorry, the answer is

Filename                                Type            Size    Used    Priority

anything else

thanks

---

### Post by User21 on 2007-09-29
Where am I?
Is this UBUNTU-AR?..
WTF ?

---

### Post by Vero1 on 2007-09-29
Yes, you are in Ubunt-ar:)

But I speak a little english, so...

I hope you will keeping help me:)

---

### Post by Vero1 on 2007-09-29
> **Vero1 said:**
> Yes, you are in Ubunt-ar:)

But I speak a little english, so...

I hope you will keeping help me:)

sorry you are another person:(

---

### Post by LaHire on 2007-09-29
> **Vero1 said:**
> I've got this answer:

cut: se debe indicar una lista de bytes, caracteres o campos
Pruebe `cut --help' para más información.

Hola! :)
Vero, creo que te equivocaste con el comando

es "cat", no "cut" :P


Por si las moscas, probé, asi que debe hacer eso :)
[quote=Mi Consola]
kane@Nostromo:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/hdc5                               partition       1510068 34580   -1
kane@Nostromo:~$ cut /proc/swaps
cut: se debe indicar una lista de bytes, caracteres o campos
Pruebe `cut --help' para más información.
kane@Nostromo:~$
[/quote]

Capaz que sea eso nomás...

ahora, q raro que se desabilite sola en cada reboot...
igual podés trabajar bien? (porq de ser así en teoría trabajarías bien hasta que se llene la memoria ram...)

---

### Post by Vero1 on 2007-09-29
Hola LaHire:)

Pues yo copié lo que me dijo el amigo: cat /proc/swaps ...

En cuanto a trabajar bien, pues no hago mas que tonterías por ahora y mi Ram es de 512...

De todas formas me gustaría poder arreglar este asunto del swap.

saludos

En realidad me equivoqué porque no dejé un espacio despues de cat...

Pero igual, no figura nada en swap.

---

### Post by LaHire on 2007-09-29
> **Vero1 said:**
> Hola LaHire:)

Pues yo copié lo que me dijo el amigo: cat /proc/swaps ...

En cuanto a trabajar bien, pues no hago mas que tonterías por ahora y mi Ram es de 512...

De todas formas me gustaría poder arreglar este asunto del swap.

saludos

Ah :P

no te aparece ninguna partición...


Fijate lo siguiente

capaz que no se inicie al principio porq no está en la fstab
(el fstab es la tabla de particiones que tienen que montarce al principio.)

poné en consola

> sudo gedit /etc/fstab 

y fijate si por algún lugar dice "swap"

(estás en el IRC?, así te ayudamos en vivo y en directo :P)

---

### Post by Vero1 on 2007-09-29
Hola LaHire:)

No es que no me aparezca ninguna partición. Aparecen todas, inclusive el Swap. Lo que pasa es que en cada boot se deshabilita.

Sí estuve en el IRC y me estaba ayudando erUSUL, tuve que salir. Recien vuelvo y volveré al IRC.

Gracias y nos vemos.

---

### Post by Vero1 on 2007-09-30
Sólo para decir que ya se solucionó.

saludos:)

---

### Post by leo_rockway on 2007-10-02
este post me sirvio cuando destrui mi swap al intentar hibernar.

el metodo que use yo fue
mkswap /dev/x
donde x es la particion en donde queria crear la swap.
despues agregue el uuid a fstab y listo. para cargar la swap en esa sesion use swapon /dev/x

---

### Post by Vero1 on 2007-10-02
Hola,

mi solución fue formatear todas las particiones y reinstalar porque hace tiempo que me daban problemas las particiones.

Así creé swap nuevamente y sin problemas.

saludos

---

### Post by leo_rockway on 2007-10-02
jaja, yo deberia hacer eso, mis particiones son un desastre (vinieron asi de fabrica y al momento de instalar no le preste atencion). la verdad que seria lo mas facil para arreglar mis particiones, pero me gusta mi instalacion tal cual esta y no me da para formatear.

---

### Post by Vero1 on 2007-10-02
Sabés qujé pasa? En realidad no formateé por Swap exclusivamente. El motivo principal fue que tenía una partición de 32 Gib que no estaba donde correspondía y me era imposible agregarla a /.

saludos:)

---

### Post by leo_rockway on 2007-10-02
yo tengo una particion de 90gb en ntfs de un xp que no uso. asi q tarde o temprano voy a tener que formatearla a ext3 y convertirla en /home

estoy pateando la tarea lo mas que puedo xq soy un vago, jaja

---

### Post by Vero1 on 2007-10-02
Bueno, no es hacer la gran cosa y no lleva tanto tiempo.
Pero por ejemplo ahora estoy en Win porque en Ubuntu no consigo conectar a Internet, haga lo que haga.

Ahora voy a sacar un nuevo thread sobre este problema.

saludos

---

