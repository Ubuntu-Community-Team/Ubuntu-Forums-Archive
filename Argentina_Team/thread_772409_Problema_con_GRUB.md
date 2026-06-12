---
title: "Problema con GRUB"
date: 2008-04-28
forum: Argentina Team
---

### Post by faktorqm on 2008-04-28
Hola gente, esta vez me toca preguntar a mi :(

Les cuento, me consegui finalmente un hdd ide para instalar ubuntu en el trabajo, de 20gb, wd. Puse el HH desktop cd y todo perfecto, reinicio y el grub me tiraba el error 17.

Fui a la documentacion de GRUB ([http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)) a ver que estaba pasando y dice:

```

17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

```

Esto significa: 

```

17: No se puede montar la particion seleccionada
Este error es devuelto si la particion requerida existe, pero el tipo de sistema de archivos no es reconocido por GRUB.

```

Al parecer tenia un problema con la tabla de particiones, ya que mire en el Acronis Disk Director y ¡me decia que era fat32 la particion!! increible no? yo supongo que ustedes no dudaran de mi y me creeran que hice el particionado manual formateando todo en ext3, haciendo una para /, otra para /home y otra para swap.

Ahora bien, borre todas las particiones, para asegurarme de que nada malo vuelva a ocurrir y con el disco limpio arranque de vuelta la instalacion. Esta vez me decia que estaba vacio el disco, particione todo de vuelta, e instale. Cuando arranca me tira Error 15. De vuelta a la documentacion de grub:

```

15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.
```

Esto es:

```

15 : Archivo no encontrado
Este error es devuelto si el nombre de archivo especificado no puede ser encontrado, pero todo lo demas (como la información del disco o la particion) esta OK.

```

Asi que me fui hasta el buscador del foro, y en mil lugares explicaban como restablecer el grub, y en todos decia lo mismo, asi que paso a explicar lo que hice y cual era el error que me tiraba en todos los casos. Esto es bueno destacarlo por que significa que siempre pasa lo mismo, lo cual no es poco.

Arranque la compu con el live cd.
Abri un terminal, puse "grub" y me tiro al mini bash del grub.
puse ```
root (hd0,0)
```
luego ```
setup (hd0)
```
y siempre me devuelve:

```

Cheking if "/boot/grub/stage1" exists... no
Cheking if "/grub/stage1" exists... no
Cheking if "/lib/grub/i386-pc/stage1" exists... no

Error 15: File not found

```

Entonces pense que algo andaba mal y me fui hasta lo del amigo que armo el super grub disk. Le di instalar automaticamente, magicamente, manualmente, etcetc y siempre tira el mismo error.

La compu esta conformada por:
mother: ECS NF61S
video: gforce 5100
memoria: ddr II de 256mb a 666mhz
disco: wd ide 20gb 7200

Particiones:

particion 1, primaria, ext3, montada en /, 4.5gb
particion 2, primaria, ext3, montada en /home, 14 gb
particion 3, primaria, swap, no montada :P, 1.5gb

el disco aparece como /dev/sda1, es el unico en el sistema, y tengo una lectora de cd que aparece como /dev/sdd.

A partir de aca, no se mas que hacer. Preguntas que me surgen:
- será el disco? antes tenia un 98 y andaba perfecto.
- será la mother que no tranza con el kernel? tiene un solo ide para enchufar la lectora y el disco, el resto sata. el bios me lo reconoce bien.
- será que deberia reinstalar con otro cd a ver que pasa? desde ya cuando me baje la iso le tire el md5sum y me dio igual que el que publican, y le saque una iso al cd que grabe y tb me dio bien (si, soy un enfermito, y ke?)

Desde ya muchas gracias por haberse molestado en leer este largo post. Salu2!!

---

### Post by Mauro22 on 2008-04-28
Hola!!, algo que no me quedo claro,

'grub' lo corriste con el usuario comun que da el livecd o pusiste sudo su para ser root ???



:guitar:

---

### Post by Hei Ku on 2008-04-28
En que orden tenes conectado el disco y la lectora de cd?
Es decir, tenes el disco como master en la primer interfaz ide y el cd como master en la segunda, o al reves?
Con eso te puede cambiar el orden de hd0 a hd1, o hd0,1, etc.

---

### Post by oktubrer on 2008-04-28
> **Hei Ku said:**
> En que orden tenes conectado el disco y la lectora de cd?
Es decir, tenes el disco como master en la primer interfaz ide y el cd como master en la segunda, o al reves?
Con eso te puede cambiar el orden de hd0 a hd1, o hd0,1, etc.

También fijate el estado de los jumpers del disco, quizás está mal seteado.

---

### Post by faktorqm on 2008-04-28
Hola, gracias x responder. 

Hice todo con root, partamos de la base que ningun usuario puede escribir sobre /boot. Me llamo la atencion por ejemplo cuando arranque con el live cd de ubuntu que no me mostraba el /boot/grub, es decir, el directorio grub no existia... pense que estaba oculto o algo de eso pero naranja fanta. Es mas, me fui al Synaptic para ver si el paquete estaba instalado, pero no sabia si estaba viendo el synaptic del live cd o el de la instalacion, como conclui que era el del live cd, tambien conclui que no tenia manera de ver si realmente estaba instalado, mal instalado o que habia pasado con la instalacion del disco.

El disco está master, el jumper esta perfecto, la lectora slave, el jumper esta perfecto, y el canal ide es único, los otros son todos SATA. Hay un disco sata de 160gb con windows xp pero para instalar todo lo desenchufe directamente y cuando terminara el proceso lo enchufaba y montaba feliz. (Es más contento para mi saber que los datos de mis compañeros estan aislados de faktorqm particionando un disco a las 7 am jijijij)

Probe con dmesg | tail a ver si me decia algo y me tiraba errores de cosas que no entendi. Cualquier cosa posteo. Puede ser que el disco cuando tenia 98 andaba y ahora no? No empiecen a bardear, va en serio la pregunta. Capaz el error surgio luego de instalar w98, y kedo asi durante años y cuando lo agarre yo justo le pegue "en la llaga". De todas maneras desconfio de ese disco, o sea, es de 20gb, es wd, es viejo y es de mi laburo, o sea que en mayor o menor medida estuvo bajo el rigor de gente que sabe muy poco de computacion/informatica/electronica, y no contento con eso me tira error, asi que no se. 

Voy a probar con otro disco, intentando ver si anda en otra pc, de ultima lo intercambia y si se termina de romper.... ehhmmmm... eehhmmm.... ok!

Salu2 y gracias! ;D

---

### Post by Hei Ku on 2008-04-28
un disco de 20GB? No sera algun problema con la interfaz PATA? Fijate el modelo del disco y busquemos a partir de ahi.

---

### Post by faktorqm on 2008-04-29
Hola, no se cual fue el problema al final, no lo pude solucionar. En una arranque la compu y no me reconocia la lectora y el disco, luego reinicie y anduvo, asi que decidi que era el disco, lo probamos en otra compu y arranco. termine probando como 3 discos, sin que ninguno ande. :( (de paso me sirvio para marcarlos jaja)
Hasta que agarre un Quantum Fireball de 4.3gb y arranco todo. Ya tengo HH instalado. Esperemos que dure, por que si se me cae ese, chau ubu en el trabajo :( Gracias a todos por responder :D:D:D:D Salu2!

---

