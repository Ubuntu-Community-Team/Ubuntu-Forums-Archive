---
title: "No consigo el ntfs-config!!!!"
date: 2007-07-05
forum: Argentina Team
---

### Post by ideafix on 2007-07-05
Hola gente: les cuento que hoy instale Ubuntu 6.06 slt (dapper drake creo que decia por ahi). En fin, me pase todo el dia tratando de instalar el ntfs-config, y no hay caso. Revise la pag oficial, los foros, en ingles, y nada. Use linea de comandos, use el Synaptic, actualice repositorios.... El problema es que da errores para configurar el ntfs-config porque no esta configurado el ntfs-3g, y este no lo configura porque no esta el fase. (errores de dependencia). Que puedo hacer!!!! Desde ya gracias!

---

### Post by fetova on 2007-07-05
Pues... da en una terminal ```
sudo aptitude install ntfs-3g
```

saludos

---

### Post by sdm_cacto on 2007-07-05
> **ideafix said:**
> Hola gente: les cuento que hoy instale Ubuntu 6.06 slt (dapper drake creo que decia por ahi). En fin, me pase todo el dia tratando de instalar el ntfs-config, y no hay caso. Revise la pag oficial, los foros, en ingles, y nada. Use linea de comandos, use el Synaptic, actualice repositorios.... El problema es que da errores para configurar el ntfs-config porque no esta configurado el ntfs-3g, y este no lo configura porque no esta el fase. (errores de dependencia). Que puedo hacer!!!! Desde ya gracias!

No estas haciendo nada mal, ese paquete se encuentra en los repos de ubuntu Feisty, te vas a tener q actualizar o buscar una forma manual de acceder a tu disco NTFS. busca en google o en [Ubuntuguide]("http://www.ubuntuguide.org")

---

### Post by ideafix on 2007-07-05
> No estas haciendo nada mal, ese paquete se encuentra en los repos de ubuntu Feisty, te vas a tener q actualizar o buscar una forma manual de acceder a tu disco NTFS. busca en google o en Ubuntuguide

OK, ya entendi. Muchas Gracias!

> Pues... da en una terminal
Code:

sudo aptitude install ntfs-3g

saludos

Esto es lo que me sale en la terminal:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se encontró ninguna versión candidata para ntfs-3g
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho

Osea, no lo instalo, no? Si quiero montar el disco manualmente, necesito esto si o si no?. Ah, perdon, no era fase, era fuse el error. Mas precisamente no configura el fuse-utils. Que mas puedo hacer?
Gracias por la ayuda

---

### Post by guillermolisi on 2007-07-05
Te da ese mensaje porque, como ya han dicho antes, el paquete no esta disponible para esa version de Ubuntu.

En tu lugar, me fijaria que dependencias y requerimiento de versiones presenta el paquete, tomando la info de la pagina del producto ([http://www.ntfs-3g.org](http://www.ntfs-3g.org)) y si da para instalarlo sin problemas, recien ahi lo bajaria y lo instalaria a mano (sobre el margen izquierdo esta el link para Installation).

En este thread [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) hay una explicacion (en Ingles) de como proceder, inclusive para la 6.06 (parece que hay que agregar unos repos para el apt/aptitude).

---

### Post by sdm_cacto on 2007-07-05
> **ideafix said:**
> OK, ya entendi. Muchas Gracias!



Esto es lo que me sale en la terminal:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se encontró ninguna versión candidata para ntfs-3g
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho

Osea, no lo instalo, no? Si quiero montar el disco manualmente, necesito esto si o si no?. Ah, perdon, no era fase, era fuse el error. Mas precisamente no configura el fuse-utils. Que mas puedo hacer?
Gracias por la ayuda

aca esta la info.. en ingles    [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

---

### Post by ideafix on 2007-07-06
Gracias a todos por las respuestas. Les cuento que ya solucione el tema. Probe la forma mas simple (que debo reconocer no la habia probado del principio):

1:  sudo -u root passwd (para poder acceder como root)
2: habilite la pagina de inicio para ingresar como root
3: cree un directorio en mnt/ llamado "win"
4: mount /dev/hda1 /mnt/win

y listo, Ya puedo navegar la particion. Les comento que igual su ayuda me esta sirviendo para aprender un monton de cosas. Ahora estoy viendo como hacer para montar automaticamente cuando inicio, o como habilitar escritura.

---

