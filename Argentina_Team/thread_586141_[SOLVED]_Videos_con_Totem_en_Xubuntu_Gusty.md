---
title: "[SOLVED] Videos con Totem en Xubuntu Gusty"
date: 2007-10-22
forum: Argentina Team
---

### Post by santiagoward2000 on 2007-10-22
Hola gente,
Recién actualicé a Gusty, y estoy teniendo un problema con Totem. No puedo reproducir videos (por lo menos .mov y .mpg, no probé con otros formatos).
Cuando trato de abrir un .mpg, me dice:
> Totem could not play 'file:///home/santi/Videos/MOV00020.MPG'.
There is no plugin to handle this movie.

y con los .mov:
> Totem could not play 'file:///home/santi/Videos/P1000016.MOV'.
Video codec 'JPEG' is not handled. You might need to install additional plugins to be able to play some types of movies

En Feisty, yo había instalado estos codecs:
[LIST]
[*]libxvidcore4
[*]gstreamer0.10-plugins-base
[*]gstreamer0.10-plugins-good
[*]gstreamer0.10-plugins-ugly
[*]gstreamer0.10-plugins-ugly-multiverse
[*]gstreamer0.10-plugins-bad
[*]gstreamer0.10-plugins-bad-multiverse
[*]gstreamer0.10-ffmpeg
[*]gstreamer0.10-gl
[*]gstreamer0.10-pitfdll
[*]libquicktime0
[/LIST]

y el w32codecs de Medibuntu.
No sé si tenga algo que ver, pero el ahora el paquete libquicktime0 se llama libquicktime1.
Ahora no instalé el w32codecs, porque no hay repositorio de Medibuntu para Gusty.
Me falta algo? Alguien sabe?
Gracias

---

### Post by leo_rockway on 2007-10-22
yo creo que w32codecs deberia solucionar tu problema.

fijate aca para agregar medibuntu que si tiene repo para gutsy:
[http://www.ubunteate.es/blog/medibuntu-en-gutsy-gibbon/](http://www.ubunteate.es/blog/medibuntu-en-gutsy-gibbon/)

---

### Post by santiagoward2000 on 2007-10-22
Hola leo,
Te cuento que instalé el w32codecs como me dijiste, pero me sigue dando el mismo error... :(

---

### Post by santiagoward2000 on 2007-10-22
Bueno, estuve probando con otros tipos de videos que encontré en mi disco, y puedo reproducir .ogg (obvio), .wmv y .asf sin problemas, pero parece que no tengo los codecs para .mov, .mpg y .mpeg. En realidad no probé otros formatos como .avi porque no tengo ninguno a mano. ¿Alguien sabe qué paquetes traen estos codecs?

---

### Post by valucha on 2007-10-22
[COLOR="DarkOrchid"]Andá al synaptic y bajá todo lo que sea gstreamer alguno va a funcionar ^^[/COLOR]

---

### Post by santiagoward2000 on 2007-10-22
> **valucha said:**
> [COLOR="DarkOrchid"]Andá al synaptic y bajá todo lo que sea gstreamer alguno va a funcionar ^^[/COLOR]

Bueno... y si no? Acabo de instalar TODOS los gstreamer, menos los -doc y -dev, y sigue sin andar.

---

### Post by santiagoward2000 on 2007-10-23
Bueno gente! LO ARREGLE!!! :guitar:
Me acabo de avivar que Xubuntu 7.10 viene con Totem para Xine instalado, y yo estaba usando los codecs para gstreamer #-o (voy a enterrarme en algún lado). JEJE
Entonces traté de instalar los codecs para Xine, pero me decía:
> Either the application requires special hardware features or the vendor decided to not support your computer type.
Asíque instalé Totem para Gstreamer, y ahora andan todos los videos!!
Igual gracias a todos por ayudar!

---

### Post by leo_rockway on 2007-10-23
bueno, por suerte se arreglo!

---

