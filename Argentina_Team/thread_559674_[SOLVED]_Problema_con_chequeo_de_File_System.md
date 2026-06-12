---
title: "[SOLVED] Problema con chequeo de File System"
date: 2007-09-25
forum: Argentina Team
---

### Post by Vero1 on 2007-09-25
Hola a todos,

Tengo un problema bastante serio.
Cuando booteo me sale una pantalla negra que dice entre otras cosas:

Si contiene ext2, el superblock está corrupto y pide que corra e2fsck

e2fsck -b 8193(device)

fsck died with exit status 8

File system check failed.

Creo no tener nada en ext2, ya que las particiones son ext3.

Qué debo hacer?

gracias de antemano por la ayuda.

saludos:)

---

### Post by marianom on 2007-09-25
Buscá "badblocks" en este subforo. Ahí tenés casi toda la información que necesitas tener para poder diagnosticar este problema.

---

### Post by Vero1 on 2007-09-25
Muchas gracias.

---

### Post by Vero1 on 2007-09-25
marianom,

te referís a tu pregunta sobre tus discos o hay otro lugar para ver badblocks?

---

### Post by marianom on 2007-09-25
> **Vero1 said:**
> te referís a tu pregunta sobre tus discos o hay otro lugar para ver badblocks?

[Este]("http://ubuntuforums.org/showthread.php?t=533085") es el thread que tiene algo de info.

---

### Post by Vero1 on 2007-09-25
marianom,

he visto tu link.

A mi lo que me sugiere es:
Run fsck manually(without -a -p)

para correr fsck se hace desde el rígido por consola?

ésto es lo que lleva tanto tiempo?

---

### Post by marianom on 2007-09-25
No, el badblocks es lo que lleva tiempo.
El fsck lo tenes que correr con el disco desmontado o sea que desde el LiveCD (con sudo y haciendo fdisk -l antes para saber el nombre de la partición). Creo que así es Ubuntu style. 

Chequea las opciones del fsck para corroborar cuales son de utilidad.

---

### Post by Vero1 on 2007-09-25
Gracias marianom, pero ya está solucionado.

Borré una línea en el fstb que provocaba todo el problema y ya no me sale la pantalla negra con el error.

saludos

---

