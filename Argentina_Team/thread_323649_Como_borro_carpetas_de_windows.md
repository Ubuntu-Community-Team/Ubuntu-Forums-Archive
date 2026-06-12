---
title: "Como borro carpetas de windows??"
date: 2006-12-22
forum: Argentina Team
---

### Post by Mafber on 2006-12-22
Hola, tengo un problema con window y necesito borrar una carpetas desde linux. Son unas carpetas que estan en Achivos de programa. ya probé con sudo remove, sudo  rmdir y siempre me dice que no tengo acceso. como puedeo hacer paraborrarlas? es una particion ntfs.

---

### Post by spg76 on 2006-12-22
Una pregunta. ¿Tenes instalado el soporte para Escritura en NTFS?
Si no es así, ahí está tu problema. Para resolverlo simplemente tenes que instalarlo.
Podes leer un como hacerlo [acá]("http://ubuntuforums.org/showthread.php?t=312107").
Saludos.

---

### Post by felipelerena on 2006-12-22
¿en que sistema de archivos tenes formateado el windows? lo montaste vos o se monto solo con la instalacion? es el mismo disco que ubuntu o es otro?

---

### Post by Mafber on 2006-12-22
Hola. 
spg76: cada ves que pongo el driver me desaparece la unidad. hice lo quedecia la guia pero lo que no estoy seguro es lo del "punto de montaje". Al final les paso el fstab para que vean si estoy metiendo la pata. ](*,) 
felipelerena: windows esta en ntfs y supongo que ubuntu lo montó cuando lo instalé.

En el fstab decia
# /dev/sda1
UUID=90D4640DD463F3BE /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
y ahora 
# /dev/sda1
UUID=90D4640DD463F3BE /media/sda1     ntfs-3g     defaults,locale=es_ES.utf8   0    0

---

