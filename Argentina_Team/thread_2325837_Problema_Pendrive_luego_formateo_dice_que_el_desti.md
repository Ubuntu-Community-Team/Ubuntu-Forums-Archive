---
title: "Problema Pendrive luego formateo dice que el destino es solo lectur"
date: 2016-05-25
forum: Argentina Team
---

### Post by Tomas_Garcia on 2016-05-25
Hola como va? Bueno fue así, había copiado una img iso en un pendrive con el escritor de imágenes de discos. 
Una vez usado prosigo a formatearlo a través de discos. 
Le puse FAT en forma rápida, etc. 
Pero cuando quise copiar un par de archivos saltó la leyenda que el destino es solo de lectura.
Probé formateando de vuelta.
Después busqué en google pero las soluciones que vi que se hacen desde terminal no me sirvieron. 
Debe ser una pavada pero como soy nuevo en linux me gustaria saber como se arregla esto porque esos problemas con Windows no lo tenia así que me da algo de bronca no arreglarlo fácilmente.
Saludos

---

### Post by rojojuan on 2016-05-26
Podés ver aquí:

[http://ubuntuforums.org/archive/index.php/t-1184043.html](http://ubuntuforums.org/archive/index.php/t-1184043.html)

---

### Post by gmunioz on 2016-05-30
Prueba con lo siguiente:
Enchufa el pendrive.
Carga gparted.
Selecciona en gparted el pendrive.
Desmontalo.
Crea una nueva tabla de particiones msdos.
Aplica los cambios.
Crea en el espacio sin particionar una partición fat32.
Aplica los cambios.

---

