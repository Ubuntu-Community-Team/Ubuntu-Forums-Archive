---
title: "[SOLVED] ¿Que causa la Lentitud del Arranque?"
date: 2008-03-08
forum: Argentina Team
---

### Post by pol666 on 2008-03-08
Simplemente eso.

Que es lo que causa que el sistema se valla poniendo cada ves mas lento cuando arranca. Tanto en el Boot como en el Splash. Tarda bastante al mejor estilo de win2.

Compiz? Monta Particiones? Muchos prog para cargar?

---

### Post by marcosba on 2008-03-08
Seguramente, taras plagado de programas instalados por vos

mucho, sudo apt-get install en tu haber

Me paso con mi PC de escritorio, tardaba demaciado, lo instale en otra PC y la diferencia era demaciada.

Yo que vos me fijo y limpio un poco el sistema

---

### Post by pol666 on 2008-03-08
mmm  no tengo tantas cosas instaladas

y de lo que carga al principio es

Compiz
Awn Bar
1 panel
Iconos de Escritorio


hace poco hice un "clean" para liberar espacio

yo pregunto sino tendra algo que ver que monte particiones.
Monta 2, una de Datos y otra de Win.

---

### Post by facundocorradini on 2008-03-08
Tenés una instalación dual con windows???

si es así, el montaje de las particiones de windows es lo que lo retrasa. 


En mi compu, los tiempos de arranque cuando tenía dual boot eran más del doble de los que tengo ahora que me quedé con Ubuntu solo.

---

### Post by pol666 on 2008-03-08
sisi.. 

alguna solucion q no sea desinstalar el win?

---

### Post by toomuchcomputertime on 2008-03-08
No digo el español bueno. Compruebe el número y tipos de programas que usted ha instalado. También, la cantidad de RAM en su computadora, y cuantos programas comienzan en la bota

---

### Post by pol666 on 2008-03-08
decinstale lo q no uso pero igual sigue inciando lento 

lo raro es en la parte del splash

---

### Post by guisheca on 2008-03-08
Mirá, dos cosas que tardan mucho para arrancar son el AWN y el compiz. Es notable, cuando recién instalo algún ubuntu, la diferencia en el arranque cuando ubuntu corre el metacity que cuano corre compiz.
Otra cosa, también puede ser lo del montaje de las particiones NTFS, la solución que yo te daría sería comentar las líneas correspondiente a esas particiones en el fstab. De esa manera el sistema las va a ignorar en el arranque, pero siempre que quieras usarlas las podés montar de forma manual.
El procedimiento es el siguiente:
```

sudo gedit /etc/fstab
```

te pongo como ejemplo mi fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=8a438c8c-a59a-4587-9c34-381a89a57260 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A28CEDFA8CEDC8BD /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=73552402565455F8 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=4685-D1D4  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=cc13f199-f599-4be6-a6f2-46167852b32c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Tendría que poner un # antes de cada línea que tenga formato NTFS (o antes de la línea que se refiera a la partición que quieras que el sistema ignore al inicio).
Quedaría algo así:

```
#UUID=73552402565455F8 /media/hda5     ntfs
```    

Guardas y listo, las próxima ves que inicie ubuntu ni se va a preocupar por esa partición, pero siempre que quieras usarla la podés montar manualmente.
Espero que te haya servido.
Un saludo.

---

### Post by Hei Ku on 2008-03-08
Ubuntu hace una optimizacion de los archivos la primera que se instala, para encontrar y cargar rapido los archivos que necesita primero. A medida que vas actualizando, los archivos cambian de lugar y se pierde la optimizacion.

Busca en los foros por "readahead".

---

### Post by nemodot on 2008-03-08
Te recomiendo que vayas a Servicios (Sistema->Admin->Servicios) y saques aquellos que no les des ninguna utilidad. En mi caso, yo no uso Bluetuth entonces saco ese servicio y la pc tarda un poquitito menos en iniciar y consume menos memoria.

---

### Post by facundocorradini on 2008-03-08
La solución es simple: desinstalar windows. 

No creo que lo extrañes para nada, y la pc va a arrancar en menos de la mitad de tiempo. 


Aunque sino puedes hacerlo, tomarce un cafecito mientras arranca nunca está de más  :p

:lolflag:

---

### Post by pol666 on 2008-03-09
Uh, fue... 
EL dia que me compre una consola de video juegos o una pc mejor, desinstalo guin.  (lo uso dia por medio :mad:)


Igual gracias, saque algunos servicios, desinstale prog, reduje el compiz asi que algo me va a servir :)
 
Gracias y marco el tema como Solved.

---

### Post by niko_3100 on 2008-03-10
Probaste poniendo en el menu.lst del grub  la opcion "nosplash" a ver que onda?

---

