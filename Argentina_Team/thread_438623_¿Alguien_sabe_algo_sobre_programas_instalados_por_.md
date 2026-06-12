---
title: "¿Alguien sabe algo sobre programas instalados por usuario?"
date: 2007-05-09
forum: Argentina Team
---

### Post by clasificado on 2007-05-09
¡Buenas Noches!

Vengo esta vez a preguntarles que opinan sobre **instalar programas sin permisos de superuser**

La idea corta seria: Darle a los usuarios que usan la machine (por ej: la mia) la posibilidad de instalarse los programas que quieran (Messengers, de consola, browsers, nose. lo que sea que quieran) pero sin necesitar permisos de superuser, por ende: **que todo se instale dentro del entorno del usuario (y en carpetas del usuario).**

*Pero me está costando mucho encontrar informacion de otra gente que haya querido hacer lo mismo*

**Linux es un sistema multiusuario. **Linux maneja el sistema de permisos, de puertos, procesos, todo separado por usuarios. 

Por lo que en teoria cualquier bin que me baje y dandole un chmod +x bin, ya ejecuta en el espacio del usuario, hasta ahi vamos bien para un programa simple. Pero **algo complejo, necesita un instalador.**

Los instaladores son el metodo "moderno" de distribuir un programa. Windows tiene sus MSI. **Debian (por extension, ubuntu) tiene los DEB, **Red Hat sus RPM, pero ¿funcionan a nivel de usuario?

*Windows lo intentó*, Algunos programas vienen con la opcion de instalarlo por usuario. Pero no pienso hacer comentarios sobre este sistema. Red Hat, no usé. Asi que tampoco voy a opinar. Y **los Ubuntu, solo permiten iniciar el Adept (o el Synaptic) con contraseña de superuser**, asi que tampoco me sirve.

Entonces planteo la cuestión... ¿Hay algun sistema que permita la instalación de programas en linux pero englobados en el entorno del usuario? ¿o alguien oyó que se pueda dar una vuelta de tuerca a los existentes para que funcionen de esta forma?

Clasificado

---

### Post by marianom on 2007-05-10
No se con paquetes .deb -supongo que el prefijo de instalación debe ser algo en debian/rules o debian/substvars pero realmente no estoy seguro- (tenemos una colaboradora de Debian en el canal #ubuntu-ar, podrías loguearte y preguntarle) pero cuando compilas desde el fuente, generalmente tenes una opción que es --prefix con la cual indicas en que lugar se va a instalar un paquete. 
Obviamente esta opción no es válida para todos, en muchos casos los paquetes tienen que tocar archivos protegidos lo cual es imposible sin el sudo (aunque calculo que un programa que tiene que hacer eso, no es del tipo de programa que queres que instalen usuario solos).

---

### Post by gepatino on 2007-05-10
En el caso de los debs, o al menos los oficiales, lo veo un poco complejo por el tema de las dependencias. 
Si un usuario quiere instalar el programa1, que necesitas las librerias1 y librerias2, estas dos... donde se instalan? en el home del usuario o en el sistema?
Si se instalan en el home del usuario, habria que modificar los binarios de programa1 para que apunten a estas librerias y no a /lib/loquesea

Con los fuentes no hay problema, los compilas con --prefix (como dijo marianom) y todo funciona sin problemas, porque estas enlazando a las librerias en ese momento. En la mayoria de los casos podes indicar que algunas librerias las busque en otros directorios que no sean lo del sistema asi que podes hacer una instalacion completa en un directorio arbitrario.

---

### Post by lavaramano on 2007-05-11
lo mas sencillo y "seguro" que podes hacer es darle permisos de ejecucion de los proggies para instalar a ese usuario.
digamos, modificas la linea para que quede allllllllgo asi.
por ej:
usuario ALL =(ALL) NOPASSWD: /usr/bin/dpkg,/usr/bin/aptitude,/usr/bin/apt-get,/usr/bin/apt-cache,/usr/bin/apt-key,/usr/sbin/dpkg-reconfigure

o algo por el estilo, **man sudo** es tu amigo
digamos que con eso, ya el usuario podria instalar .debs, podria bajar desde los repositorios con apt-get y aptitude, tb puede buscar paquetes con aptitude y apt-cache (search *paquete*), y por las dudas el dpkg-reconfigure, ah y me olvidaba tb esta el apt-key para firmar digitalmente (?) a los repositorios cuando agregas uno.

saludos

---

