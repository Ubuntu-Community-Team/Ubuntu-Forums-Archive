---
title: "Se me tilda Xubuntu en notebook LG F1"
date: 2007-11-23
forum: Argentina Team
---

### Post by anpa on 2007-11-23
Como estan todos :) Tengo xubuntu 7.10 en mi notebook LG F1 y anda bien, hasta que llega un momento que es completamente aleatorio en donde se tilda (se congela todo) y no la puedo reiniciar de ninguna manera (no puedo ir a consola, ni reiniciar el modo grafico), al querer mudarme a linux, necesito solucionarlo y no estar pendiente de esto. Con versiones anteriores a esta tb tengo el mismo problema
Si me pueden decir como puedo saber que es lo que hace que se trabe o si le ha pasado a alguien con esta maquina o configuracion de hardware de la misma, le agradeceria que me dijeran como solucionaron el problema.
A continuación les dejo las caracteristicas

Centrino duo T2250 de 1.73 GHz
1GB de RAM DDR2 a 667MHz en dual channel
disco SATA Fujitsu MHV2080BH
CHIPSet Calistoga-G i945GM
tarjeta grafica mobile intel GMA 945 (integrada)

Gracias desde ya a todos.

---

### Post by sajnox on 2007-11-23
Ok,

Las preguntas clasicas, con windows pasa lo mismo??

Hiciste un chequeo de memoria?? en los repositorios tenes varios programas 

```
miguel@miguel-desktop:~$ sudo apt-cache search memtest
memtest86+ - thorough real-mode memory tester
hwtools - collection of tools for low-level hardware management
memtester - A utility for testing the memory subsystem
sysutils - Miscellaneous small system utilities - dummy package

```

---

### Post by facundocorradini on 2007-11-23
Tenés un Centrino Duo y usas Xubuntu?... Te debe gustar mucho XFCE, no?...


Bueh, el problema que decís parece una ram pinchada. Corré alguna herramienta para chequear la ram...

saludos

---

### Post by anpa on 2007-11-23
con win anda todo OK.
El mem ya se lo habia pasado y todo OK, ahora pruebo lo otro que me decis :)

---

### Post by anpa on 2007-11-23
como estas facundocorradini, si me gusta XFCE y mas q nada me gusta que corra todo en RAM, por el tema de la vel de procesamiento. 
Ahora estoy pasando el memtest de nuevo por si las moscas :) pero no se como usar el hwtools. Si me pueden dar una mano estaria bueno.
saludos y gracias

---

### Post by anpa on 2007-11-23
como estas facundocorradini, si me gusta XFCE y mas q nada me gusta que corra todo en RAM, por el tema de la vel de procesamiento.
Ahora estoy pasando el memtest de nuevo por si las moscas pero no se como usar el hwtools. Si me pueden dar una mano estaria bueno.
saludos y graci

---

### Post by anpa on 2007-11-24
Comprobe la mem y esta bien, hice el memtest86+ hastao 4 pasos y lo pare :) cada paso con todas las cantidades de test que tiene. Otra sugerencia para probar?
por cierto ayer instale de nuevo xubuntu y me acorde que cdo lo instalo de nuevo el 7.10 las letras de LOGIN y las de los menus dentro de la session de usuario (desde el reloj hasta los menus el aplicaciones y sus submenues) se ven enormes y no puedo usar el entorno grafico para moverme. el de LOGIN no me preocupa, pero el de dentro de la sesion quiero saber como arreglarlo (no encuentro nada en internet) alguna sugerencia?

---

