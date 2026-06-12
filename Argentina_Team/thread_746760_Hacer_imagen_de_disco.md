---
title: "Hacer imagen de disco"
date: 2008-04-05
forum: Argentina Team
---

### Post by Mauro22 on 2008-04-05
Hola!!


Estaba viendo la posibilidad de copiar mi particion en formato de imagen para guardarla en un dvd y asi evitar volver a instalar y configurar todo.

Y encontré esto:

>  dd if=/dev/hda1 | gzip -9c - > /otrodisco/particionhda1.img.gz

Estando /dev/hda1 desmontado y /otrodisco montado.

El resultado de esto seria un archivo comprimido .img.gz con una copia exacta de /dev/hda1


Y para escribir esa imagen en una particion:

>  gzip -dc /otrodisco/backup.img.gz | dd of=/dev/hda1

Montado el origen y desmontado el destino.



No se si eso es todo, pero mañana lo probaré. Esta bueno para limpiar todo el disco de particiones y dejar todo mas ordenado y despues cargar esta imagen.


:guitar:

---

### Post by guisheca on 2008-04-06
Muy interesante, yo conozco el comando dd y lo potente que es, pero no se bien como usarlo, espero a ver que resultados te da, me sería de mucha ayuda.

---

### Post by clasificado on 2008-04-07
Valiente lo tuyo!

¡Yo con dd hacia copias bit a bit de mis diskettes! ¡Que épocas!

Por lo de la utilización para un backup, tiene el inconveniente que te "congela" la versión del linux a lo que tenias en ese momento.

Si dentro de un año querés reinstalar, vas a tener una version de ubuntu dos veces vieja, y por ahi convenga reinstalar todo. Por lo que el propósito del backup se va a la basura.

Podrias separar los datos de /home en otra particion y backupear solo eso

---

