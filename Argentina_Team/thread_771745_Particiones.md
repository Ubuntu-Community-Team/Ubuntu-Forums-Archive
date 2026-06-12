---
title: "Particiones"
date: 2008-04-27
forum: Argentina Team
---

### Post by ramiro_md on 2008-04-27
Hola amigos del foro, realmente no se si este es el foro adecuado para hacer esta consulta, pero se que es en el unico donde me van a dar una respuesta.
Resulta que al instalar ubuntu en mi computadora, a la hora de hacer las particiones (en mi disco de 160gb) hice las siguientes:
1)/: de 10 gb donde esta el sistema ubuntu instalado
2) la swap
y una tercera, (/home) de datos...el tema es que en esta particion (/home) tenia 20 gb ociosos, es decir que no los utilizaba para nada, puesto que los datos los guardaba en la particion "D".Entonces no tuve mejor idea que eliminar la particion "/home" con el Partition Magic. Al hace resto el partition magic me decia que tenia 20 gb sin asignar en la particion "D"...y a la hora de reasignar ese espacio, con la opcion "redistribuir espacio disponible"...me salta un error antes de que incie la redistribucion...No se si me podrian dar una mano con este problemita que yo solo me busque xD
Desde ya muchas. Espero que alguien me ayude.

---

### Post by ramiro_md on 2008-04-27
aca dejo una captura de pantalla..para que se guien un poco...

este es exactamente el error q me tira

"access violation at address 004b8016 in module pmagicnt.exe"

---

### Post by ramiro_md on 2008-04-27
lo deje adjunto en este thread

---

### Post by clasificado on 2008-04-28
Podrias hacer esa misma pregunta en el [foro de soporte de partition magic]("http://www.techsupportforum.com/"), que seguro van a tener mas idea. Por la clase de error, parece un bug del mismo. Podrias buscarte una versión más actualizada.

También podrias usar una herramienta open source para llevar a cabo esa tarea: Le toca el turno al [Live CD de GParted]("http://gparted.sourceforge.net/livecd.php")

ahora, exactamente exactamente que quiere decir, no tengo idea


clasificado

---

### Post by ramiro_md on 2008-04-28
Gracias clasificado, también intente con el gparted pero no lo se manejar. Me podrías decir como unir ese espacio no asignado a la partición "D" ?

---

### Post by uidb4056 on 2008-04-28
> **ramiro_md said:**
> Hola amigos del foro, realmente no se si este es el foro adecuado para hacer esta consulta, pero se que es en el unico donde me van a dar una respuesta.
Resulta que al instalar ubuntu en mi computadora, a la hora de hacer las particiones (en mi disco de 160gb) hice las siguientes:
1)/: de 10 gb donde esta el sistema ubuntu instalado
2) la swap
y una tercera, (/home) de datos...el tema es que en esta particion (/home) tenia 20 gb ociosos, es decir que no los utilizaba para nada, puesto que los datos los guardaba en la particion "D".Entonces no tuve mejor idea que eliminar la particion "/home" con el Partition Magic. Al hace resto el partition magic me decia que tenia 20 gb sin asignar en la particion "D"...y a la hora de reasignar ese espacio, con la opcion "redistribuir espacio disponible"...me salta un error antes de que incie la redistribucion...No se si me podrian dar una mano con este problemita que yo solo me busque xD
Desde ya muchas. Espero que alguien me ayude.

El espacio libre sin particionar solo se puede añadir a particiones contiguas, debes mover las particiones de linux hasta dejar el espacio sin particionar detras de la particion NTFS, entonces puedes aumentar el tamaño de la particion usando el espacio libre contiguo.

---

### Post by ramiro_md on 2008-04-28
muchas gracias x la info..pero..como muevo particiones con partitonmagic?? el gparted desde linux me permite hacerlo ??

---

### Post by valucha on 2008-04-29
[COLOR="DarkOrchid"]Si, pero tarda años luz...

Si tenés paciencia hacelo sino agregale ese espacio a la partición de 10 gigas de linux y ya ^^, total tenes 100 g en los datos y 5 utilizados xD [/COLOR]

---

### Post by ramiro_md on 2008-04-29
Bueno, muchas gracias, se los voy voy a poner a linux...:(...de ultima mas adelante formateo...gracias muchachos

---

