---
title: "Ubuntu 8.04 y discos NTFS"
date: 2008-04-30
forum: Argentina Team
---

### Post by smrdelj on 2008-04-30
Hola buenas noches, nuevamente yo y mis dudas de novato :$

He notado que en Ubuntu 8.04 los discos NTFS se montan al querer leer informacion contenido en ellos.

Hay alguna forma mas inteligente de manejar esto que la q viene configurada por defecto? porq la verdad q eso de tener los iconos de los discos NTFS en el escritorio me ***. No pueden estar montados per defecto y q se pueda explorar en ellos? Sin ningun icono de más en el escritorio...no sé, la verdad q ***...¿Cómo lo manejan uds? ¿Qué se puede hacer o qué recomiendan?

Muchas gracias, saludos. Agradezco su paciencia.

---

### Post by sajnox on 2008-04-30
Si se pueden montar por defecto.

Para que te podamos indicar como, postea lo que te devuelve por estos comandos

```
sudo fdisk -l
```

```
cat /etc/fstab
```

Saludos

---

### Post by smrdelj on 2008-05-01
Hola q tal. Gracias por tu ayuda. Te expongo los resultados de lo q me pediste:

La ejecucion del "**sudo fdisk -l**" me arrojó lo siguiente: ```

Disco /dev/sda: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x039c039c

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5804    46620598+   7  HPFS/NTFS
/dev/sda2            5805        8482    21511035    f  W95 Ext'd (LBA)
/dev/sda3            8483        9886    11277630   83  Linux
/dev/sda4            9887       10011     1004062+  82  Linux swap / Solaris
/dev/sda5            5805        8482    21511003+   7  HPFS/NTFS

```

En tanto el "**cat /etc/fstab**" me reveló lo siguiente: ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1d2689c8-6ab9-4909-83ea-fa37029bebee /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=7e75af6d-e42a-46a4-b05c-0da3f3799707 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Si te sirve tambien saberlo (aunque pueda deducirse de mi fdisk), tengo un disco de 80 Gb partido en 4: Dos NTFS ("C:" y "D:". Windows XP está en "C:"), el ext3 (Donde tengo Ubuntu 8.04) y el swap.

Muchas gracias, espero tu respuesta. Saludos y suerte.

---

### Post by ajonat on 2008-05-01
Yo te recomendaría que no montes nada por defecto. Si queres tener la misma funcionalidad que hasta ahora, es decir, que se montan cuando son accedidos, pero que no se muestre ningun icono en el escritorio directamente hace esto:
$ gconf-editor
Ahi dentro anda a apps > nautilus > desktop y deshabilita la opcion que dice volumes_visible.
De esta manera igual vas a poder acceder a los discos (y se van a montan cuando los accedas) pero no te pone ningun icono en el escritorio.

Saludos!

---

### Post by faktorqm on 2008-05-01
Yo te recomiendo lo mismo que ajonat. Montar particiones ntfs cuando arrancas es lo peor que podes hacer desde el punto de vista de la performance. 
Para que te des una idea, yo borre todo y puse todas las particiones ext3 salvo la de windows ntfs, y le puse a windows el driver para que "vea" particiones ext3. 
Y ahora si monto todas las particiones en el inicio sin problemas :D

---

### Post by smrdelj on 2008-05-01
Barbaro muchachos, para mi es casi lo mismo. Lo q mas me interesaba era q al montar las particiones no me aparecieran los iconos en el escritorio. 

Saludoss

---

