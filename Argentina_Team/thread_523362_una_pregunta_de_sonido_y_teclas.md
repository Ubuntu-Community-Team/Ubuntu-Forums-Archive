---
title: "una pregunta de sonido y teclas"
date: 2007-08-11
forum: Argentina Team
---

### Post by Mauro22 on 2007-08-11
Hola!,

una preguntita,

Desde que instale el keytouch, para poder usar mi teclado multimedia no he podido usar el control de volumen.

Les explico:

Si uso los botones + - y mute, aparece una barra de acuerdo  a la funcion. La cosa es que estos botones controlan el 'Maestro' y el que necesito es que controle el 'PCM'.

Me fije en el keytouch y no pude hacer nada.

Me fije en sistema->preferencias->sonidos, y elegi PCM como controlador, tampoco tuve exito



Alguien sabe como cambiar Maestro x PCM

Salu2

---

### Post by Hei Ku on 2007-08-11
El volumen que podes controlar es el del canal maestro, salvo que lo accedas por DCOP (si tenes KDE, eso anda seguro, si tenes Gnome, no estoy tan seguro)
Lo que podes hacer, es seleccionar como canal maestro el PCM. En KMix, con click derecho sobre el icono de la barra podes seleccionarlo. De vuelta, si usas Gnome no estoy seguro de como es, pero tiene que haber una opcion similar, y si no a traves del gconf tiene que estar.

---

### Post by Mauro22 on 2007-08-11
Tengo Gnome


Me fije en el gconf-editor, y el predeterminado es PCM, pero aun asi baja el Maestro

Salu2

---

### Post by Hei Ku on 2007-08-12
fijate en el alsa-mixer, cual es el canal seleccionado de maestro. Si coinciden, entonces podrias probar con el DCOP. Eso te permite mandar comandos directo a un programa. Creo que funciona en Gnome.

proba de poner en la consola: DCOP <nombre del programa que controla el volumen>
Eso te deberia tirar la lista de comandos disponibles.
Con el KMix era algo tipo: DCOP KMix decreasevolume <numero del canal maestro> <porcentaje a bajar del volumen>


Una curiosidad, por qué es que quieres bajar el volumen del PCM y no del canal principal?

---

### Post by Mauro22 on 2007-08-12
Desde la consola puedo manejar el PCM con:

amixer set PCM 10%+
amixer set PCM 10%-
amixer set PCM mute
amixer set PCM unmute

Ahora, voy a poner esos comandos, en el keytouch. Pero igual, tengo 3 teclas, y 4 funciones. Si pudiera cambiar maestro x pcm, iria joya


Es medio raro, pero aunque baje el maestro no pasa nada, con lo unico que si tiene efectos es bajando el PCM, es rarisimo.

---

### Post by Hei Ku on 2007-08-12
el problema es la seleccion del canal maestro, me parece. En algunos casos tenes que seleccionar como canal "maestro", el PCM. Fijate si lo podes hacer desde el alsa-mixer, por consola.
Yo tenia problemas con el tema del volumen hasta que me instale el keytouch, pero recuerdo haber visto threads donde reportaban justamente este problema, que cambiando el volumen al canal maestro no pasaba nada, y entonces tenias que seleccionar otro como  maestro.

---

