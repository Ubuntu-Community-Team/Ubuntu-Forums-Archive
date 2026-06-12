---
title: "Geforce 2 Mx 400 en Hardy - problemas"
date: 2008-04-21
forum: Argentina Team
---

### Post by lega on 2008-04-21
El viernes bajé la versión RC de hardy y me dispuse a hacer una instalación limpia, todo salió bien hasta que el sistema me dijo que debía instalar los drivers restrictivos para habilitar la placa de video, como dice el título una Geforce2 que en gusty funciona de maravillas, lo hice reinicié, con la sorpresa que al entrar al sistema  mi resolución era de 640x480, desinstalé los drivers, instalé Envy NG instalé los drivers, reinicié y no llegué a loguearme, el sistema me decía que iba a iniciar en baja resolución, y me daba la opción de elegir otro monitor o placa de video, no hubo caso, probé bajar los drivers legacy de la página de nvidia y nada.
Así que con la moral por el suelo, y repitiendo a todo el quisiera escucharme que era la primera vez que me pasaba,volví a instalar Gutsy, y a prender una vela a San Tux para que en la versión final esto sea solo un mal recuerdo.

Mi pregunta es, en caso que para la versión final esto no cambie, puedo tocar algo? no se, editar el xorg.conf o algo por el estilo...

Gracias de antemano, saludos

---

### Post by User21 on 2008-04-22
Yo te recomendaria que te bajes el controlador desde el sitio de Nvidia, para probarlo.

---

### Post by faktorqm on 2008-04-22
[http://ubuntuforums.org/showthread.php?t=760539&page=2](http://ubuntuforums.org/showthread.php?t=760539&page=2)

---

### Post by lega on 2008-04-22
User21, fué una de las cosas que hice, bajé los drivers legacy de Nvidia y los instalé, pero no funcionó, voy a probar la solución de faktorqm, el viernes si la versión final no cambia en algo este tema.
Saludos y gracias

---

### Post by lega on 2008-04-25
Gente a ver si alguien puede darme una mano, con este tema, la versión final no solucionó nada tengo el mismo problema, los drivers restringidos me dan una resolucion de 640x480, instalar los driver legacy con ENVY tampoco me lo soluciona, y el link que me pusieron tampoco es la solucion, alguien me podra dar una mano por favor? estoy algo desesperado y desauciado:(

---

### Post by faktorqm on 2008-04-26
Que exagerado!

- Instalate el driver de nvidia con el envy, la version 71.XX.
- Despues, anda a aplicaciones -> accesorios -> terminal y escribis

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Ahi le pones la resolucion que queres Y LAS FRECUENCIAS DE ACTUALIZACION HORIZONTAL Y VERTICAL DE TU MONITOR. No te olvides de poner bien eso. 

- Reinicias
- Anda a aplicaciones -> accesorios -> terminal y escribis

```
glxinfo | grep direct
```

Te tiene que decir "Direct rendering: YES". Si esta eso, postea a partir de aca cual es el problema. Salu2!

---

### Post by lega on 2008-04-26
Hola, no llego ni a poner las frecuencias sudo dpkg-reconfigure -phigh xserver-xorg

me tira esto
 
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080426160731

```

No se si hice bien pero por las dudas hice uan copia del xorg.conf como dice el texto
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20080426160456

```
Volví a probar y me da el mismo mensaje

---

### Post by faktorqm on 2008-04-26
Bueno, hoy en la flisol me di cuenta de que te tira las configuraciones en otro archivo, y no en ese. Lipe te puede ayudar mas creo yo. Yo me instalo HH y te cuento como se hace. Salu2!!

---

### Post by lega on 2008-04-26
Ya lo solucioné :) lo que hice fue desinstalar envy e instalar los  drivers restrictivos directamente desde Hardy, reinicié y obviamente me inicio otra vez en 640x480 previamente habia instalado la aplicación nvidia-settings así que la corrí desde una consola con privilegios de sudo, puse la resolución deseada,la frecuencia del monitor, apliqué y guardé, reinicié por las dudas y anduvo :)
 
tipeé en la consola 

```
glxinfo | grep direct
```

y las mágicas palabritas salieron

```
direct rendering: Yes
```:):)

Lo extraño es que si quiero habilitar los efectos de escritorio desde Sistema > Preferencias > Apariencias > Efectos visuales, luego de un par de parpadeos me salta un cartel que no se pudo habilitar los efectos, sin embargo si habilito lo efectos desde CCSM si andan...no se porqué..pero bueno está solucionado

Gracias por la ayuda, saludos

---

