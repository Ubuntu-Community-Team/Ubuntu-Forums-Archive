---
title: "Problemas con mi camara digital"
date: 2007-04-19
forum: Argentina Team
---

### Post by letalx on 2007-04-19
Hello, como estan, he tratado de bajar mis fotos en mi reciente Ubuntu 6.10 y no he podido hacerlo.
El SO me detecta perfectamente la camará pero al momento de importar las fotos me aparece este error:
***[COLOR="Red"]Se ha producido un error en la biblioteca de entrada-salida ('No se pudo reclamar el dispositivo USB'): No se pudo reclamar la interfaz 0 (Operación no permitida). Debe asegurarse de tener acceso de lectura/escritura al dispositivo y que ningún otro programa o módulo del núcleo (como sdc2xx, stv680, spca50x) esté utilizándolo.[/COLOR]***
Me he fijado en el dmesg y detecta bien la camara ala arrancar el Sist., lo unico no se genera ningun dispositivo sda para soportarla, no se que estoy haciendo mal, si alguin me puede dar una mano se los agradeceria.

Saludos  Me.-

:guitar:

---

### Post by bapoumba on 2007-05-14
I'm very sorry I did not see that post before now. I'm moving it to one of the spanish speaking LoCo sub-forums.

---

### Post by Al_maverick on 2007-05-14
A ver si te podemos dar una mano.

Que modelo de camara tenes? El unico problema es que no la podes acceder como dispositivo de almacenamiento?

Probaste de conectar y reconectarla mientras esta la PC prendida y fijarte que dice en el dmsg? Ah, no te va a generar un dispositivo sda (esos son para discos SATA) si no un usb, si por lo que decis tu camara es usb.

---

### Post by screening on 2007-05-14
El mismo problema tuve yo, y leyendo en este mismo foro encontré que es gphoto y libgphoto, en la ultima actualización se modificaron ciertos archivos y da ese problema.

Creo que una de las soluciones es hacer un backport a la version anterior (yo no pude y lo solucioné comprandome una lectora de tarjetas usb xD)

Acá podes ver mas:
[http://ubuntuforums.org/showthread.php?t=319492](http://ubuntuforums.org/showthread.php?t=319492)

---

### Post by lugonesjoaquin on 2007-05-14
¿Y en la version 7.04 no se soluciona?

---

### Post by screening on 2007-05-15
tengo la version 7.04, el problema es la version de gphoto2-2.3 y libgphoto2-2.3
en cualquier version de ubuntu que actualices gphoto y libgphoto a esas versiones... deja de andar tu camara digital...

---

