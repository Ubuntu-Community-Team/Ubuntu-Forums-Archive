---
title: "Imposible ver DivX"
date: 2007-09-20
forum: Argentina Team
---

### Post by pablo0469 on 2007-09-20
Hola, gente, hace mas de 3 meses tengo al feisty cohabitando con winxp, y lo unico que me frena a no hacerlo unico habitante de mi dr es que me ha resultado imposible ver videos DivX con ubuntu. He seguido no menos de 100 tutoriales, tengo instalado cuanto codec haya dando vueltas y nada... pero tambien he leido por ahi que Totem y MPlayer suelen no levantar bien ciertos codecs, y recomiendan instalar Amarok como reproductor predeterminado de medios, ¿puede ser que la cosa venga por ahi?
Necesito si o si poder ver este formato, puesto que en la pagina afin a mi profesion, los articulos vienen acompañados con videos de este tipo. Muchas gracias de antemano.

---

### Post by sajnox on 2007-09-20
Hola,

Por lo que decis el resto de los formatos los ves bien, probaste con Amarok?? que paso??, otra opcion es bajar los codecs con automatix (si bien dicen que no es el mejor, creo que te puede dar una mano).

Otra pregunta, mencionas una pagina, los videos necesitas verlos directamente desde ahi, probaste bajarlos con wget??

Saludos,

---

### Post by pablo0469 on 2007-09-20
Gracias por la respuesta tan rapida. Tengo instalados todos los codecs, por automatix, synaptic y algunos por terminal (esas extensiones que por ahi no te cubren los anteriores). Probe con wget y tampoco pude. Siempre me salta la leyenda "missing plugins video-divx" Pero veo que si sugeris que instale otro reproductor de medios, quiza la mano venga por ahi, no? Pruebo con Amarok y despues te cuento. De nuevo, gracias, y ojala pueda solucionar esto asi plancho de una buena vez mi dr con el ubuntu, jejeje!!!

---

### Post by spg76 on 2007-09-20
¿Tenes instalado "w32codecs"?
Podés instalarlos desde los repositorios de Medibuntu [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)
Con eso deberías poder verlos sin problemas.
Espero que te sirva.

---

### Post by Montsegur87 on 2007-09-20
Si estas apurado , usa VLC.

---

### Post by MatoGroso on 2007-09-20
Hola! Yo me descargué el VLC + un paquete de codecs que estan dentro de "agregar y quitar" y los DIVX se veian bien.
Lo que si tengo problemas con algunos subtitulos que estan desplazados en tiempo que no los veo bien...

---

### Post by FlyerDie on 2007-09-20
> **MatoGroso said:**
> Hola! Yo me descargué el VLC + un paquete de codecs que estan dentro de "agregar y quitar" y los DIVX se veian bien.
Lo que si tengo problemas con algunos subtitulos que estan desplazados en tiempo que no los veo bien...

Pero si los ves desincronizados ya no es problema del reproductor ;)

O en windows los ves en sincro con la peli esos mismos subs??:confused:

---

### Post by daz! on 2007-09-20
Navegando por [hachemuda]("http://www.hachemuda.com/category/ubuntu/page/2") encontré esta solución para ver videos DivX _on line_. 

Tal vez te sea útil, no aclaraste si los videos son online. 

Cita textual:
[I]Si usas Gnome, tienes que tener instalado el paquete totem-mozilla. Puedes instalarlo ejecutando &#8220;sudo apt-get install totem-mozilla&#8221; en un terminal.

Si al intentar ver el video te sale en negro y debajo un botoncito de Play que no hace nada aunque pulses sobre él (como en la imagen) , haz click derecho sobre el área del video y selecciona Abrir en Reproductor de Películas. Se te abrirá el Totem y te hará el buffering del video y empezará a reproducirlo en streaming.[/I]

Saludos y comentá si encontraste la solución.

---

### Post by pablo0469 on 2007-09-20
Esta es la 1º vez que escribo algo en un foro, y realmente me asombra y me alegra semejante camaraderia. Los felicito a todos. Este fin de semana, con un poco de tiempo, reviso todo de nuevo siguiendo todos estos consejos, aunque por todo lo que he leido, justamente este es un punto medio problematico para Linux en gral., los w32codecs leen bien los AVI puros, pero no los comprimidos (DivX). Repito, tengo todos los codecs instalados (deberia revisar el totem-mozilla) los videos que pretendo ver, son on-line. Estoy seguro que con vuestra mayor experiencia, voy a poder solucionar este tema, por el momento para verlos me arreglare con el win2 (aunque cada vez me cuesta mas entrar a el, es absolutamente cierto que linux es harto adictivo, y si sigo asi me voy a terminar divorciando, jejeje!!!)

---

### Post by pablo0469 on 2007-09-20
Me faltaba instalar el plugin totem-mozilla, ya esta, ahora los puedo ver sin problemas. No pude con mi genio, e intente solucionarlo ya mismo... creo que la vida media del win2 en mi pc es cada vez menor...
De nuevo, muchas gracias a todos.

---

### Post by MatoGroso on 2007-09-20
> **FlyerDie said:**
> Pero si los ves desincronizados ya no es problema del reproductor ;)

O en windows los ves en sincro con la peli esos mismos subs??:confused:

En win los veo bien, en sincro. En Ubuntu si el frame de la peli ya pasó, no me muestra el sub. 
Igualmente creo que deberiamos abrir otro thread para esto...

---

### Post by por100pre1 on 2007-09-20
> **spg76 said:**
> ¿Tenes instalado "w32codecs"?
Podés instalarlos desde los repositorios de Medibuntu [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)
Con eso deberías poder verlos sin problemas.
Espero que te sirva.

Medibuntu ahora tiene la siguiente dirección:

[http://www.medibuntu.org](http://www.medibuntu.org)

El otro enlace aún funciona, pero eso pudiera cambiar en el futuro. ;)

---

### Post by lega on 2007-09-21
> **MatoGroso said:**
> En win los veo bien, en sincro. En Ubuntu si el frame de la peli ya pasó, no me muestra el sub. 
Igualmente creo que deberiamos abrir otro thread para esto...

En el vlc si los subs estas seguro que estan en sincro tenes que ir a Preferencias > Entradas / Codecs > Otros Codecs > Subtitulos

y pones como codificacion de texto ISO-8859-1 yo lo solucioné así

saludos

---

