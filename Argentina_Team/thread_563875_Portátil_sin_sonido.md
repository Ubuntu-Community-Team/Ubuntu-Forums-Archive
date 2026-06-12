---
title: "Portátil sin sonido"
date: 2007-09-30
forum: Argentina Team
---

### Post by zerio on 2007-09-30
Hola a todos. Veréis, tengo un portátil packard bell con ubuntu feisty. Desde el principio me dio problemas, el sonido no iba, pero lo conseguí arreglar añadiendo la línea "options snd-hda-intel model=3stack" al archivo alsa-base. Pero los auriculares seguían sin funcinar por muchas cosas que probé, así que espero que alguien tenga alguna idea porque yo ya no sé dónde buscar.
Pero es que el problema se ha agravado desde que actualicé el kernel a la versión 2.6.20-16, ahora el sonido a vuelto a no funcionar, y ni que decir tiene que los auriculares siguen igual; pero es que además no puedo reproducir vídeos, cuando abro alguno el programa se queda pensando un rato y no hace nada (si lo abro con el totem) o directamente se cierra (con el vlc).
Lo peor es que con el windows instalado sí funciona todo, pero casi prefiero estar así que volver a utilizar windows.
Por dar algunos datos del ordenador que pueden ser útiles, mi tarjeta gráfica es una ati radeon xpress 200M y la tarjeta de sonido es una realtek alc861 vd
Ah, otra cosa, si le doy dos veces al icono del altavoz que aparece al lado de la hora arriba y a la derecha de la pantalla me da un error que dice que "No se han encontrado complementos y/o dispositivos control de volumen de GStreamer."
Espero que me podáis ayudar, porque empiezo a estar bastante desesperado. Gracias de antemano.

---

### Post by leo_rockway on 2007-10-02
yo tuve un problema parecido al actualizar a 2.6.22-10. la solucion fue recompilar alsa. fijate si eso te funciona a vos tb.

---

### Post by hernan blau on 2007-10-02
Estoy en la misma situación que Zerio. Si alguien se entera de una solución, por favor, avise. Gracias

---

### Post by leo_rockway on 2007-10-02
hernan, probaste recompilar alsa como recomende?

---

### Post by zerio on 2007-10-05
Leo yo he probado lo que dices y no funciona

---

### Post by leo_rockway on 2007-10-05
te fijaste si alguien documento un fallo en launchpad?

---

### Post by zerio on 2007-10-06
Pues he mirado y he visto un problema que se parece un poco al mío, aunque todavía no está resuelto.

---

### Post by marianom on 2007-10-06
Poneles presión: adjunta con los mayores detalles posibles tu problema al mismo bug.

---

### Post by faktorqm on 2007-10-08
hola:

[http://www.ubuntu-ve.org/?q=node/1134](http://www.ubuntu-ve.org/?q=node/1134)

[http://www.ubuntu-es.org/index.php?q=node/27376](http://www.ubuntu-es.org/index.php?q=node/27376)

[http://dbkernel.blogspot.com/2007/05/ubuntu-704-parte-2.html](http://dbkernel.blogspot.com/2007/05/ubuntu-704-parte-2.html)

[http://foros.ubuntu-cl.org/viewtopic.php?t=1077](http://foros.ubuntu-cl.org/viewtopic.php?t=1077)

por favor pongan de bookmark esta pagina: [http://www.google.com/](http://www.google.com/) 
posteen como lo solucionaron si lo lograron. salu2!!

---

### Post by zerio on 2007-10-08
Pues bueno, ya he empezado a probar algunas de las páginas que dice faktorqm aunque de momento sin resultado.
Aunque hay otra cosa que me gustaría comentar y se me había olvidado.
Resulta que desde que actualicé el kernel, si le doy a Sistema, Preferencias y por último a Sonido, no me aparece ningún dispositivo, mientras que antes me salía Realtek alc861-vd. Supongo que es porque no me reconoce o no tengo instalada la tarjeta, pero antes me la reconocía y ya he intentado reinstalar los drivers y creo que lo hice bien. Puede deberse a otra cosa??

---

### Post by faktorqm on 2007-10-08
yo creo que ahi esta la respuesta a todo el problema. cada vez que actualices el kernel, vas a tener que compilar alsa. (yo lo tengo que hacer con el diver de nvidia, asi que imaginate :S) lo que si no me acuerdo es como se hace, supongo que en los links de arriba en alguna parte debe decir como recompilar alsa, sino, lo vemos. salu2!

---

### Post by leo_rockway on 2007-10-08
la compilacion de alsa es solo descargar lo necesario de alsa-project.org y despues todo sale con tar zxvf ./configure make sudo make install

a mi nunca me tiro problema de dependecias por lo que imagino que lo unico necesario seria build-essential (pero no puedo asegurarlo)

---

### Post by zerio on 2007-10-10
Bueno, pues siguiendo la página [http://www.ubuntu-ve.org/?q=node/1134](http://www.ubuntu-ve.org/?q=node/1134) he conseguido que me detecte la tarjeta y el sonido ya va (muhcas gracias, Faktorqm); es sólo descargarse una cosa e instalarla. De todas maneras, tengo la certeza de que si enchufo los auriculares seguirá sin funcionar (no tengo ningunos a mano para probar), que es el problema que tenía en un principio, antes de actualizar el kernel.
Además, cuando intento abrir alsamixer me sale:
alsamixer: function snd_ctl_open failed for default: No such device
y evidentemente no se abre

---

### Post by faktorqm on 2007-10-11
de nada! ke bueno ke avanzaste con el problema. con el tema de los auriculares (si vas a buscar algo hacelo por "jack sensing") hasta lo que yo no se no hay solucion, es decir, enchufas el auricular pero seguis escuchando en los parlantes. asi que eso todo mal :S me alegro que te haya servido. salu2!

---

