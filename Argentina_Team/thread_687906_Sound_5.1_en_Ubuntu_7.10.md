---
title: "Sound 5.1 en Ubuntu 7.10"
date: 2008-02-04
forum: Argentina Team
---

### Post by matlnx on 2008-02-04
Buenas noches, me gustaría hacerles una consulta. Tengo mi PC con salida 7.1 on board, y un Home 5.1 conectado a la misma.

El tema es que mi PC tiene tres Sistemas Operativos (XP, VISTA y Ubuntu 7.10) pero cuando uso la pc con los dos Windows el home a mitad de volumen suena muy fuerte.
El tema es que con Ubuntu, tengo que subir TODO el volumen de home, mas todo el volumen del ubuntu y se escucha leve.

Alguno tiene idea de donde se configura para que se escuche igual de fuerte? o medianamente fuerte??? y sacarle provecho al 5.1 con una peli o un juego??

Desde ya muchas gracias
Atte.
MatLnx

---

### Post by Hei Ku on 2008-02-04
probaste de usar el alsa-mixer? de ahi podes configurar bien todo el volumen.

---

### Post by lank23 on 2008-02-04
Run the volume control "gnome-volume-control", click on edit then preferences and check the needed speakers, this will allow you to adjust the volume of each channel.

"Google translation"

Ejecutar el control de volumen "gnome-volume-control", luego haga clic en editar preferencias y comprobar la necesaria oradores, esta le permitirá ajustar el volumen de cada canal.


lank23

---

### Post by matlnx on 2008-02-04
Primero que nada gracias por responder. Les comento que instale el alsamixergui y cuando lo ejecuto me aparece un error que dice:

alsamixer: function snd_ctl_open failed for default: invalid argument

Vi que en internet hay muchos errores parecidos que que en lugar de argumento invalido dice no such device, por lo que aparentemente en mi caso ve el Dispositivo pero hay una configuracion default que no le esta gustando.

Muchas gracias por cualquier ayuda que puedan brindar.
Sds
MatLnx

---

### Post by niko_3100 on 2008-02-04
En una consola escribi alsamixer ahi te levanta una pequeñita gui de consola para configurar.

---

