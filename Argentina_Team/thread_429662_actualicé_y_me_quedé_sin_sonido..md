---
title: "actualicé y me quedé sin sonido."
date: 2007-05-01
forum: Argentina Team
---

### Post by valucha on 2007-05-01
[COLOR="DarkOrchid"]Otroo problema más con el sonido.
El tema es que feisty me daba más dolores de cabeza que otra cosa, por lo que decidí volver a edgy.
Instalé, funcionaba todo perfecto, y actualicé y desde ese momento tengo el siguiente comportamiento con los sonidos:
1) cuando prendo la compu y me pide la clave hace el sonido normalmente.
2) cuando pasa a la splash screen ya no hace el sonido de inicio como siempre.
3) los sonidos del gaim no los reproduce.
4) la música, los videos, sí...

Decidí investigar y descubri que:
a) en "preferencias del sonido", cuando testeo todo en la 1er solapa el último me salta con este error.[/COLOR]
[IMG]http://img251.imageshack.us/img251/5813/problemasonidorv9.png[/IMG]
[COLOR="DarkOrchid"]b) teniendo el alsamixer (el cual ya lo reinstalé por si acaso) y tratando de ejecutarlo en la terminal me dice "no mixer elems found".

Y también busqué dentr del foro y en internet y no encontré nada parecido ;S...

Bueno, espero que puedan ayudarme y les agradezco por adelantado.
[/COLOR]

---

### Post by valucha on 2007-05-01
[COLOR="DarkOrchid"]Ya encontré una posible solución.
Lo posteo en caso de que alguien tenga el mismo problema.

instalé nuevamente el alsa pero como me dice acá: [http://wiki.ubuntu-cl.org/MU_Audio](http://wiki.ubuntu-cl.org/MU_Audio)

ejecuté:  gstreamer-properties
y donde dice "entrada" puse "test sound" y ahora se escucha. 
No se escucha tan bien como antes... tiene como "interfernecias" o "ruidos", pero se escucha.


Perdonen las molestias y cierrenlo si quieren.[/COLOR]

---

### Post by nico-ar on 2007-06-29
me paso exactamente lo mismo.. tenia 6.10 y me pase a 7.04 actualizando.. antes andaba ahora no.. por lo q veo alsa no anda pero oss si.. voy a probar con eso q pusiste a ver si anda ya me esoy volviendo looocoo

---

### Post by nico-ar on 2007-06-29
no me andubo.. me sigue tirando el error como el que esta en e1º post-..
probe borrar todo y instalar los alsa 1.0.14  y sigue igual.. ya nose q mas hacer

~$ lspci | grep -i audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)

---

