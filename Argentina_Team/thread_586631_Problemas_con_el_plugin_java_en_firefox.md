---
title: "Problemas con el plugin java en firefox"
date: 2007-10-22
forum: Argentina Team
---

### Post by atari130xe on 2007-10-22
Hola Foro, instalé Ubuntu 7.10 y la verdad q estoy muy conforme, por un par de razones: 1) logré tener aceleración 3D con mi vieja tarjeta Nvidia TnT2 M64 (no lo puedo creer todavía :) ), 2) la configuración en gral es mucho mas intuitiva y un par de cosita más. Ahora me surgió un problema: al instalar el applet java le dí en las opciones del "administrador de plugins de ubuntu en firefox" a la primera opción (GNU classpath) y metí la pata porque varios sitios que requieren JVM no funcionan, le hice la prueba de instalacíon de java y sale que es una version antigua que instale la 1.6 y aparece como 1.4 vendor: GNU Classpath, o sea bajé manualmente la version 1.6 del sitio de Java y lo instalé (cuando tipeo: java -version en la consola me sale 1.6 instalada correctamente). como podria solucionar ese inconveniente siendo que re instalé 3 veces la version 1.6 pero aparentemente en el navegador sigue apareciendo la 1.4 GNU Classpath. Alguien tiene alguna sugerencia? gracias!

---

### Post by scrooge_74 on 2007-10-22
Eliminaste la versión 1.4?

Seguiste las indicaciones para copiar el archivo en el path de plugins de Firefox?

---

### Post by atari130xe on 2007-10-22
en realidad no se como eliminar esa version (GNU Classpath) y sí, segui tal cual las instrucciones de Sun para instalar java. (el enlace simbólico para mozilla, etc.) si supiera como desinstalar GNU classpath seria bueno.

---

### Post by scrooge_74 on 2007-10-22
No tengo instalado un ubuntu a mano para revisar, pero lo más probable es que tienes un paquete de java instalado y debe aparecer en las listas de programas instalados en synaptic. Des-instala el paquete y reinicia el navegador.  

En teoría sólo debiera quedar instalado la versión de Sun que instalaste manualmente.

De paso hay un paquete en el repositorio que instala la versión de Sun

---

### Post by atari130xe on 2007-10-25
Gracias desinstale con synaptic todos los paquetes y reinstale a mano JRE 1.6.3 y ahora logre hacerlo funcionar, gracias!

---

### Post by ariel on 2007-10-25
para la proxima:  Applications >  Add/Remove > busca "Ubuntu Restricted Extras" (asegurate que Show = All Available Applicatins).

Te instala: Sun JRE 6 y todos los codecs etc para totem/gstreamer, de un saque.

---

