---
title: "Ubuntu Server no me detecta CDROM"
date: 2007-07-29
forum: Argentina Team
---

### Post by aceki on 2007-07-29
Gente consulta migre mi servidor de windows server a ubuntu server, ahora bien se instalo precioso todo lindo, pero cuando por ejemplo le doy un "apt-get install XFCE4" me pide el CDROM de ubuntu server que este en /cdrom, lo cual no esta, quise montar el cdrom pero en /dev no hay ningun CDROM, alguien me puede decir como la puedo montar, y dejarla desde inicio, el servidor tiene 3 discos scsi y la lectora es una IDE, cosa que me parece raro, Buenos muchas gracias!!

---

### Post by guillermolisi on 2007-07-29
> **aceki said:**
> Gente consulta migre mi servidor de windows server a ubuntu server, ahora bien se instalo precioso todo lindo, pero cuando por ejemplo le doy un "apt-get install XFCE4" me pide el CDROM de ubuntu server que este en /cdrom, lo cual no esta, quise montar el cdrom pero en /dev no hay ningun CDROM, alguien me puede decir como la puedo montar, y dejarla desde inicio, el servidor tiene 3 discos scsi y la lectora es una IDE, cosa que me parece raro, Buenos muchas gracias!!

Es que por defecto en /etc/apt/sources.list hay una entrada que hace referencia a los paquetes que estan en el CD de Ubuntu y, para que luego de la instalacion no te lo pida cada vez que actualizas paquetes via Internet, se comenta.

Te paso un ejemplo a modo ilustrativo:

```

#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty
 main restricted

```

---

### Post by aceki on 2007-07-29
Barbaro, por lo menos ya baja los paquetes de internet, pero no puedo montar el cdrom eso es lo que mas me falta

---

### Post by Hei Ku on 2007-07-29
lo que puede suceder es que como es un IDE, el cdrom te aparezca como hda1 o algo similar. Si tenes todos los discos SCSI o SATA y un device hda, ese debe ser el cdrom.

---

### Post by aceki on 2007-07-30
Y como me doy cuenta de si hay un HDA en /dev?

---

### Post by aceki on 2007-07-30
La cosa es la siguiente en /dev no tengo hda ni ningun hd*, tambien quise montar un disco que tengo con windows de donde quiero sacar unas cosas que tengo, y tampoco me lo monta

---

### Post by faktorqm on 2007-07-30
por favor escribi esto en una consola y postealo a ver que sale:

```
cat /etc/fstab
```

```
cat /etc/mtab
```

El disco con windows, el tipo de particion es ntfs? o fat32?

Lo último, podrias postear exactamente que escribís cuando intentas montar algo, y que te devuelve la consola? Espero que si. salu2!!

---

### Post by aceki on 2007-07-30
con cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6a336a92-8bae-4eab-8e0c-bad2b4fbea7b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2f05d6ee-51eb-4a31-b0ac-54d2d1fb31e7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2       /media/windows  vfat #aca puse lo que vi por ahi para montar el disco.

con cat /etc/mtab:

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0

---

### Post by faktorqm on 2007-07-31
En el archivo fstab, en la linea que dice:

/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

deberia decir:

/dev/hda1 /media/cdrom0 udf,iso9660 user,noauto 0 0

(NOTAR EL UNO DESPUES DEL HDA, SI NO PROBAR EL 2, DEPENDE...
EN MI FSTAB APARECE COMO [SIZE="4"]HDD[/SIZE], PROBALO CAPAZ TE ANDA)

En el mismo archivo linea: 

/dev/sda2 /media/windows vfat #aca puse lo que vi por ahi para montar el disco.

es evidente que esta mal. Te copio aca lo que deberia decir:

/dev/sda2 /media/windows   vfat    iocharset=utf8,umask=000  0    0

Yo lo tengo asi en mi compu. Si queres ver particiones NTFS, vas a tener que usar NTFS-3G. si no tenes la menor idea de que es hacé:

```
sudo apt-get install ntfs-3g
```

y luego, en tu fstab pones:

/dev/sda2 /media/windows  ntfs-3g  defaults,locale=en_US.utf8    0    0

Asegurate de que /media/windows exista, y tengas permisos sobre esa carpeta. Salu2!!

---

### Post by aceki on 2007-07-31
La verdad no entiendo ya, hise lo que me dijiste y no, me canso, voy a volver a windows que andaba muy bien en el servidor, gracias de todos modos.

---

### Post by Hei Ku on 2007-07-31
con un cdrom puesto en la compactera, proba lo siguiente:

sudo mount /dev/hda1 /media/cdrom -t iso9660 -noloop

y postea si te sale algun error.

---

### Post by aceki on 2007-07-31
No no anda, haber como dije antes que ndie vio, en el directorio /dev no hay ningun HDA, por ende, si le doy sudo mount /dev/hda1 /media/cdrom -t iso9660 -noloop me tira que hda1 no existe, a mi pobre entender en linux tiene que haber un archivo que se llame hda uno para poder montarce o no?

---

### Post by faktorqm on 2007-07-31
Si la verdad es rarisimo, digo, es como que es re simple que te tome el cd rom. la verdad no se que decirte, no tengo experiencia en hardware no detectado bajo linux, de hecho si existe alguien que entienda como se hace por favor que me explike XDD

Ahora una pregunta, como instalaste ubuntu? desde el cd? salu2!

---

### Post by aceki on 2007-07-31
La verdad, agarre y tire la imagen que tenia con mi querido windows server 2003 y listo, chau problema, la verdad que linux esta a años todabia de ser util para mi, no tengo tiempo de estar renegando con un disco rigido, algo tan simple, en cambio con windows hay bastantes utilidades para leer Ext3, y no requiero perder tiempo como lo hise con ubuntu.

---

### Post by faktorqm on 2007-07-31
ok, suerte con eso entonces. si podes, capaz tenes algun disco sin usar, conectalo, e instalate ubuntu, asi cuando tenes tiempo te fijas todo bien, y si no te anda no te afecta en lo que necesitas hacer.

p.d.: cuando se te cuelgue el win te vas a acordar de este post ;)

---

### Post by aceki on 2007-07-31
Mira ya deje un disco con ubuntu, pero de ahi a que se me cuelgue win, medio raro, el servidor es un 24x7 y tiene un windows server 2003 y desde hace ya 1 años nunca se cayo, ni un drama, si lo tenes bien configurado anda joya, pero uno siempre desea probar cosas pero bueno, linux no es para mi. Gracias por tu consejo

---

### Post by aceki on 2007-08-02
Bueno le cuento como solucione el tema:

Primero en el server me baje el  NTFS-3G (para ver particiones nfts), luego en el /etc/fstab puse:

/dev/sdb1    /media/windows  ntfs-3g defaults,ro,locale=en_US.utg8 0 0

la verdad que anda de 10, espero q con esto les ayude a la gente que SUFRIO como yo!!!! gracias a todos!!!

---

### Post by faktorqm on 2007-08-02
/dev/sdb1 /media/windows ntfs-3g defaults,ro,locale=en_US.utg8 0 0

Hola, en el final, no va una "F" en vez de una "G"? Capaz lo posteaste mal, o capaz lo tenes mal en el fstab. Te anda igual por que seguro si no reconoce un flag debe tener uno por defecto. salu2!

---

### Post by aceki on 2007-08-03
No con la F anda bien, ni un drama es mas lo copie de una ayuda que andaba por ahi

---

