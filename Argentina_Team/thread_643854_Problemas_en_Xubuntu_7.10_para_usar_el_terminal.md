---
title: "Problemas en Xubuntu 7.10 para usar el terminal"
date: 2007-12-18
forum: Argentina Team
---

### Post by krebscycle on 2007-12-18
Tengo problemas para usar las terminales, cada vez que presiono Ctrl+Alt+F1 (o F2, F3, etc) aparece de manera recursiva el siguiente mensaje:

**sr0: CDROM (ioctl) error, command: Test Unit Ready: 00 00 00 00 00 00**

Esto me impide ingresar cualquier comando en la terminal. De momento solo puedo usar la interfaz gráfica del terminal para ingresar comandos. Como información adicional dmesg, entrega el siguiente resultado:

[B][I]dmesg | tail
[ 1011.156000] sr: ASC=0x2 <<vendor>> ASCQ=0xa7
[ 1013.156000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

[ 1013.156000] sr: Sense Key : Data Protect [deferred] [descriptor]
[ 1013.156000] sr: ASC=0x2 <<vendor>> ASCQ=0xa7
[ 1015.156000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

[ 1015.156000] sr: Sense Key : Data Protect [deferred] [descriptor]
[ 1015.156000] sr: ASC=0x2 <<vendor>> ASCQ=0xa7
[ 1017.156000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

[ 1017.156000] sr: Sense Key : Data Protect [deferred] [desc[/I][/B]riptor]
[ 1017.156000] sr: ASC=0x2 <<vendor>> ASCQ=0xa7

He investigado las posibles soluciones, pero hasta el momento no he encontrado nada. De antemano agradezco a quienes puedan arrojar luces sobre este problema.

---

### Post by faktorqm on 2007-12-19
posts con posibles soluciones:

[http://ubuntuforums.org/showthread.php?t=485597](http://ubuntuforums.org/showthread.php?t=485597)

[http://ubuntuforums.org/showthread.php?t=438711](http://ubuntuforums.org/showthread.php?t=438711)

[http://www.webservertalk.com/message2249261.html](http://www.webservertalk.com/message2249261.html)

posts informativos:

[http://ubuntuforums.org/showthread.php?t=97717](http://ubuntuforums.org/showthread.php?t=97717)

[http://www.devlib.org/forums/opensuse-ata3-00-t5087.html?](http://www.devlib.org/forums/opensuse-ata3-00-t5087.html?)

[http://groups.google.com/group/es.comp.os.linux.misc/browse_thread/thread/ce8e457d0792a8b0](http://groups.google.com/group/es.comp.os.linux.misc/browse_thread/thread/ce8e457d0792a8b0)

google no muerde.... salu2!

---

### Post by krebscycle on 2007-12-19
Tengo una unidad CDROM (la cual corresponde a sr0), y otra unidad CDW/DVD, la que funciona sin problemas.

No osbtante lo anterior, la unidad CDROM (sr0) lee los CDs sin inconvenientes. Por lo demás, éste fallo sólo se presenta cuando la unidad está vacia. Cuando la unidad tiene un CD adentro el mensaje deja de presentarse en cualquiera de los terminales (Ctrl+Alt+F1 o F2, F3, etc), sólo entonces los puedo utilizar directamente (es decir, sin tener que recurrir a la interfaz gráfica), sin embargo, al sacar el CD de la unidad el problema vuelve a presentarse.

Otras personas han reportado en internet éste problema pero en ningún caso han obtenido soluciones.

---

### Post by faktorqm on 2007-12-21
por favor, postea la salida de este comando:

```
cat /etc/fstab
```

Sirve para ver las cosas que estas cargando al inicio, las unidades y puntos de montaje, etc. No olvides hacerlo entre tags de code :D salu2!

---

### Post by krebscycle on 2007-12-21
Esta es la salida:

```
[B]$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc              /proc   proc       defaults           0              0
# /dev/sda2
UUID=79739e56-e534-41c8-9f4e-df4c3f8764c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C41CF5C71CF5B510 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8344a997-816a-4085-a8ce-595ccb2ea4dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0[/B]
```

Como información adicional, en mi disco duro de 40 GB tengo una partición para WinXP (25 GB), otra para Xubuntu (14 GB) y finalmente una para la memoria swap (1 GB).

Saludos.

---

### Post by faktorqm on 2007-12-23
hola, bueno, en mi caso la grabadora esta asi:

```
/dev/hdd	/media/cdrom0	auto	defaults,auto	0	0
```

asi que a vos te deberia quedar algo asi:

```
/dev/scd0       /media/cdrom0   auto defaults,auto 0       0
/dev/scd1       /media/cdrom1   auto defaults,auto 0       0
```

PRIMERO KE NADA BAKAPEAS EL ARCHIVO CON:

```
sudo cp /etc/fstab /etc/fstab_bkp_navidad
```

jajaja ponele el nobre que quieras. espero que t haya servido. salu2!

---

### Post by krebscycle on 2008-01-02
Gracias, pero el problema persiste, no surtieron efectos al editar el archivo fstab.

¿Alguna otra idea?.

Saludos

---

