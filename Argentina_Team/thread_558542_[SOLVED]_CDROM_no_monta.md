---
title: "[SOLVED] CDROM no monta"
date: 2007-09-24
forum: Argentina Team
---

### Post by electronpositivo on 2007-09-24
Buenas!

Tengo una red en la cual un ordenador actua de server ldap para usuarios y nfs para los homes.

El problema es que si logueo en un cliente con un usuario de ldap y le pongo un CD me dice que no tiene privilegios...

¿Qué debo modificar para poder montar con cualquier usuario?

Graciasss

---

### Post by clasificado on 2007-09-24
Buenas Noches!

Desde que uso Ubuntu, se me viene a la idea de que no existe, para nada, un botón para "dejar que todos hagan todo", sino que las cosas se hacen meticulosamente.

en el caso de los usuarios y el acceso a los dispositivos, **agregá al usuario en cuestion al grupo CDROM.** Dicho de otra forma, todos los usuarios dentro del grupo CDROM pueden acceder a ese dispositivo. Como ese, hay una pila de grupos que le dan permisos a cada uno de los dispositivos. en mi Xubuntu, los grupos de mi usuario son los siguientes:

"adm dialout cdrom floppy audio dip video plugdev svn lpadmin scanner admin network"

La explicación es que los dispositivos (/dev/*) tienen un grupo asignado, que le da un aire de "rol", de esta forma, los hda y hdb estan anidados al grupo CDROM, los hdc y las particiones, al grupo DISK, entonces con la asignacion de los usuarios a los grupos ya podes controlar el acceso de los usuarios a los dispositivos.

Como todo en Linux, vos elegis finalmente como es que tu sistema queda, Te recomiendo usar el modelo que ubuntu te presenta y no le cambies los grupos a los /dev/*, que si bien es una posibilidad, hay mejores

Clasificado

---

### Post by electronpositivo on 2007-09-26
Gracias por tu respuesta, pero el problema lo tengo en que los usuarios están en un directorio LDAP que está en otro equipo.

¿De qué forma puedo agregar un usuario LDAP a un grupo local? O mejor, ¿puedo hacer esto en el servidor y que lo reconozca en cualquier cliente?

Espero ser iluminado! :)

---

### Post by electronpositivo on 2007-10-03
Replanteo la pregunta.

_Tengo esto:_

Una red con un servidor LDAP y varios clientes que autentican contra este servidor.

_Me sucede esto:_

Al iniciar en cualquier cliente con un usuario del directorio LDAP, no puedo montar cd (aparece mensaje que indica "No tiene privilegios para montar...")

No puedo iniciar audio (aparece el icono del altavoz con una x roja).

En cambio, si inicio con cualquier usuario local, puedo hacer ambas cosas. Por lo tanto... he pensado que si logro agregar usuarios ldap a grupos locales no tendré estos problemas. ¿Es esto cierto?

_La Pregunta_

Y de ahí, mi pregunta. ¿Se puede agregar un usuario LDAP a grupos locales de los clientes? ¿Alguna idea distinta?

---

### Post by electronpositivo on 2008-02-26
¡¡¡Lo tengo!!! 

Simplemente he añadido manualmente los usuarios en el /etc/group local a los siguientes grupos:

adm
dialout
fax
cdrom
floppy
tape
audio
dip
plugdev
scanner

Que son los grupos que por defecto tiene un usuario local. Y parece que ya lo tengo.

Espero le sirva a alguien. :)

---

### Post by User21 on 2008-02-26
Perfecto! :D

Si resolviste el problema, debes marcar este hilo como resuelto (SOLVED). Puedes hacerlo en el menú Thread Tools, gracias!

---

