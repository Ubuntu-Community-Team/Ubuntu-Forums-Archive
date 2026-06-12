---
title: "[SOLVED] Tamaño de subtitulos en Mplayer"
date: 2007-08-28
forum: Argentina Team
---

### Post by leo_rockway on 2007-08-28
Hola a todos. Ando con unas dudas de subtitulos.

Alguien sabe como cambiar el tamaño de los subs en MPlayer?

Es posible hacer que no se dibujen sobre el video sino debajo? (sobre las barras negras en una peli wide)

gracias
Leo

---

### Post by tzulberti on 2007-08-28
Clic botn derecho sobre la peli, Preferences. En la pestaña de Fonts, el tamañano de la letra es el campo textScale (puede ser que tambien sea osd scale, no me acuerdo cual de los dos habia que tocar), y la ubicacion es outline

---

### Post by leo_rockway on 2007-08-28
en realidad yo estaba usando mplayer desde consola (me olvide completamente de la gui jaja) igual tu ayuda me sirvo :-D

gracias.

(igualmente todavia me queda la duda existencial de si se puede modificar desde consola)


EDIT:
de hecho... estuve mirando el mplayer con gui y es buenisimo! (yo antes estaba usando el kmplayer que no tiene ninguna de estas opciones). tzulberti, sos grosso, sabelo.

---

### Post by croto on 2007-08-29
Podes usar esta opcion:

-subfont-text-scale <0-100> 

Creo que no se puede hacer q los subtitulos esten por debajo de la imagen... si encontras alguna forma avisa!

---

### Post by leo_rockway on 2007-08-29
googlee lo q me pasaste de -subfont-text-scale y cai en una pagina con todos los parametros de modificacion del mplayer y encontre la forma de hacer q los subtitulos esten por debajo del imagen.

primero que nada: -subpos 100 (para que los subtitulos esten abajo de todo)

y despues: -vop expand ancho:largo:X:Y:R

esto lo que hace es expandir el video agregandole bandas negras en donde se lo indiquemos (a lo largo o a lo ancho) usando un valor negativo.
X e Y es donde queremos la pelicula con respecto a las bandas.
r es rendering. el default es 0 (desactivado). hay q poner 1 xq si no los subtitulos no desaparecen del todo, se enciman y no se lee nada.

ejemplo: -vop expand=0:-100:0:50:1 agrega una barra de 100 pixeles por debajo de la peli y mueve la peli 50 pixeles en el eje y (para q no nos quede descentrada)

entonces nos quedaria algo asi:

> $ mplayer -sub ElephantDreams.srt ElephantDreams.avi -vop expand=0:-100:0:50:1 -subpos 100

si a alguien le interesa seguir jugando con los comandos del mplayer aca les dejo la pagina q encontre: [http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html](http://tivo-mplayer.sourceforge.net/docs/mplayer-man.html)

---

