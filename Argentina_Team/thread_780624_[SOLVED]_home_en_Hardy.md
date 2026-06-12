---
title: "[SOLVED] /home en Hardy"
date: 2008-05-03
forum: Argentina Team
---

### Post by vk-cdg on 2008-05-03
Yo lo acabo de instalar y me reconoció todo. 
Tengo un problema con mi antigua partición /home, que al momento de la instalación me debo haber olvidade de seleccionar algo (no se que) porque ahora el home de hardy está dentro del / y la partición que antes era /home no me la monta automáticamente. 

Alguien sabe cual fue la macana que me mandé y como solucionarlo?

---

### Post by atatiducken on 2008-05-03
no estoy seguro, que alguien me corrija sino, pero al momento de instalar HH tendrias q haber indicado que el /home viejo para q te lo tome como tal, sin formatearlo obvio, en la parte de particionado manual.
Pero hay maneras de separar el /home del /, busco en internet y posteo si lo oncuentro
saludos

---

### Post by atatiducken on 2008-05-03
no estoy seguro, que alguien me corrija sino, pero al momento de instalar HH tendrias q haber indicado que la particion vieja del /home para q te lo tome como tal, sin formatearlo obvio, en la parte de particionado manual.
Pero hay maneras de separar el /home del /, busco en internet y posteo si lo oncuentro
saludos

---

### Post by hernan blau on 2008-05-03
Efectivamente. Tenés que poner instalación manual y luego, en la partición que corresponde a tu home te ponés encima y debés asignarle /home sin formatear. Luego te la lee perfectamente. Lo hice varias veces. Suerte. HB

---

### Post by Hei Ku on 2008-05-03
para corregirlo ahora, lo mas facil es que te metas con un LiveCD, borres las carpetas dentro de home y despues en el fstab pones para que monte tu home viejo en /home

---

### Post by vk-cdg on 2008-05-03
Hasta ahora lo que hice fue agregar en mi fstab la linea para que levante el /home. Todavía no reinicié porque estoy bajando actualizaciones y aplicaciones para instalar.

No estoy seguro si con eso andará pero lo que hice fue esto:

Mi fstab actual

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=08549639-bc1d-4dd9-a521-92fa96276846 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=893b88c5-5351-4046-9d51-8ab59a79ef23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Mi fstab nuevo

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=08549639-bc1d-4dd9-a521-92fa96276846 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2c518566-d7a3-473a-b521-ee9c60059726 /home               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=893b88c5-5351-4046-9d51-8ab59a79ef23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Hay que hacer si o si el paso del liveCD para borrar el home actual?

---

### Post by margori on 2008-05-03
> **vk-cdg said:**
> Tengo un problema con mi antigua partición /home... 
... Alguien sabe cual fue la macana que me mandé y como solucionarlo?

Seguro te mandaste una macana, pero no es nada para alarmarse. Tiene solución.
1 - Modificas el archivo fstab con
    $ sudo gedit /etc/fstab
 en la linea que tiene la particion home le modificas el punto de montaje a /home. Guardas y cerras.
2 - borras el contenido de la home actual (Cuidado con esto)
    $ sudo rm -rf /home/<carpeta>
   repetilo con la carpeta de cada uno de los usuarios. (Repito cuidado)
3 - Luego montas la nueva home con
    $ sudo mount /home/
4 - Reinicias sesion, y listo.

Un par de detalles. Tenes que tener el mismo nombre de usuario que antes, sino cuando inicies la sesión no va poder buscar la carpeta personal. En caso de que sean diferentes, luego de modificar fstab anda a Sistema -> Administración -> Usuarios y Grupos -> <tu usuario> -> botón Propiedades -> Avanzado -> Carpeta persona y lo modificas segun como se va a llamar la nueva carpeta.
Espero te sirva.

---

### Post by margori on 2008-05-03
> **vk-cdg said:**
> ...
Mi fstab actual

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=08549639-bc1d-4dd9-a521-92fa96276846 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=893b88c5-5351-4046-9d51-8ab59a79ef23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
...

Estas seguro que tenes una partición con la /home? Supuestamente la nueva instalación de hardy tendría que haber creado una entrada montando esa partición en /media/discoX y no la veo en el fstab que posteaste... :(

---

### Post by vk-cdg on 2008-05-04
Si, si, la partición estaba, solo que ese fstab es que el me mostraba hardy. Agregué la linea que está en el otro, reinicié y listo.

Gracias a todos por la mano.

---

