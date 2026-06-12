---
title: "Como habilto la salida de TV en mi placa Nvidia?"
date: 2007-07-16
forum: Argentina Team
---

### Post by Thalskarth on 2007-07-16
Hola, buenas...

Ayer termine de insalar Ubuntu 7.04... y ya le habilite los drivers restringidos de Nvidia. Mi placa es una Nvidia Geforce FX 5200...eso anda todo de maravilla...

Mi problema es que no me anda la TV-Out y el televisor no recibe ninguna señal... como hago para activar la salida de TV (es una S-Video)? Y una vez activado, si es posible, como hago para configurarla? ya que me gustaria que fuera con el estilo de "clonacion" (el mismo desktop en el monitor y en el TV)...

Desde ya, muchas gracias

---

### Post by jajajavi on 2007-07-16
Yo tengo la [FX 5500 con dos monitores en modo TwinView]("http://ubuntuforums.org/showthread.php?t=345063&highlight=fx+5500") y lo hice toqueteando el /etc/X11/xorg.conf y reiniciando las x hasta que quedaba más o menos como quería (antes que todo backupear el xorg.conf), fijate en [http://www.linuca.org/body.phtml?nIdNoticia=186](http://www.linuca.org/body.phtml?nIdNoticia=186) o en la [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-4349/README.txt"]Installation Guide de Nvidia]("). Aunque creo que con **nvidia-settings** (está en el synaptic) lo tenés más fácil. Cualquier cosa chiflá!

---

### Post by jajajavi on 2007-07-16
```
gksudo nvidia-settings
```
y lo configurás igual que en windows

---

### Post by undiaperfecto on 2007-07-17
que fierrazo la 5500, yo me la compre hace poco y la verdad se re porta.aunque todavia no la use para conectar al tv, no consigo en ningun lugar un cable mas o menos largo.

---

### Post by faktorqm on 2007-07-17
Hola, yo lo hice desde el xorg.conf, y despues descubri el nvidia-settings y tb lo toke de ahi, pero el xorg.conf me kedo asi (en la seccion screen me agrego esto:

Option		"TVStandard" "PAL-NC"
Option		"TVOutFormat" "AUTOSELECT"

En el readme de nvidia dice ke pal-nc es la norma que usa argentina de pal-n. cualquiera hubiera puesto pal-n solo, pero en el readme dice que para argentina es pal-nc asi que les hago caso.
El tvoutformat no se para que es, pero tb te recomiendan ponerlo en autoselect. salu2!

---

### Post by Thalskarth on 2007-07-17
Gracias por su ayuda... probe con el nvidia-settings, pero solo tiene las opciones de que "ambas muestren un exritorio estirado, mitad en una pantalla mitad en la otra" o que muestre dos desktops diferentes e independientes...

no se puede hacer que ambas muestren exactamente el mismo desktop??

---

### Post by faktorqm on 2007-07-18
Hola, en modo clonacion! por lo general, en linea nvidia tenes 3 modos, uno, el monitor, el otro clonacion (que son el tv y el mon al mismo tiempo), el otro tv solo. las ati tienen uno mejor que te manda la salida de los programas de video (tipo guidous media, etc) al tv pero el escritorio al monitor, tonces vos podes seguir jugando al starcraft mientras otro mira una peli en el tv. no recomiendo ati x q en linux no anda, o al menos no lo hace como una nvidia.
resumiendo, en el readme del driver de nvidia, te dice bien lo que yo te puse arriba del modo de tv y demas cosas, yo tengo una gforce 4mx y particularmente, para ke el nvidia settings me haga los cambios tengo que enchufar el tv, y despues prender la pc, o reiniciar en el caso que ya la tenga prendida, sino no anda. (en guidous tengo que hacer lo mismo).
Espero que t haya servido. salu2!

---

### Post by User21 on 2007-07-18
> **undiaperfecto said:**
> que fierrazo la 5500, yo me la compre hace poco y la verdad se re porta.aunque todavia no la use para conectar al tv, no consigo en ningun lugar un cable mas o menos largo.

Yo me hice uno con un cable coaxil, una ficha S-video y otra RCA o S-Video, segun lo tenga tu TV. El mio tiene como 7 mts!!! xD

Lo vi en [http://www.pasarlascanutas.com/video/conectores_senales_cables.htm](http://www.pasarlascanutas.com/video/conectores_senales_cables.htm) , en alguno de los tutoriales... En las tiendas no conseguis mas largo ke 3 mts..! 

Funciona de lujo.

---

### Post by jpmorelli on 2007-07-19
> **User21 said:**
> 

Lo vi en [http://www.pasarlascanutas.com/video/conectores_senales_cables.htm](http://www.pasarlascanutas.com/video/conectores_senales_cables.htm) , en alguno de los tutoriales... En las tiendas no conseguis mas largo ke 3 mts..! 

Funciona de lujo.

Excelente Link User21, gracias !

---

### Post by Thalskarth on 2007-07-19
> **faktorqm said:**
> Hola, en modo clonacion! por lo general, en linea nvidia tenes 3 modos, uno, el monitor, el otro clonacion (que son el tv y el mon al mismo tiempo), el otro tv solo. las ati tienen uno mejor que te manda la salida de los programas de video (tipo guidous media, etc) al tv pero el escritorio al monitor, tonces vos podes seguir jugando al starcraft mientras otro mira una peli en el tv. no recomiendo ati x q en linux no anda, o al menos no lo hace como una nvidia.


Perdona que sea denso... pero entonces si pongo lo que vos me decis... ya se habilita el TV-OUT y en modo clonacion??? o como activo el clonacion???

perdon pero la verdad no se bien como se hace esto... soy nuevito en linux (mi 1er semana)...

---

### Post by rojojuan on 2007-07-20
Tengo una placa gforce 64 mmx con tv out. En mi caso lo solucioné así:

Aplicaciones - Añadir y Quitar - Sonido y video - NVTV Tv oUT-

Te queda instalado en Aplicaciones - Sonido y Video - 

Para usarlo lo arrancás y le colocás los parámetros necesarios. Hay algo con lo que muchos se vuelven locos y es que en Argentina el sistema es plan n, pero en mi caso el TV es brasilero y no funcionaba. En el seteo elegí pal m y todo de maravillas.

Ese programa, como verás, tiene muchas opciones.

Si tenés dudas y conozco las repuestas, puedo aportarlas.

Suerte.

---

### Post by Thalskarth on 2007-07-22
> **rojojuan said:**
> Tengo una placa gforce 64 mmx con tv out. En mi caso lo solucioné así:

Aplicaciones - Añadir y Quitar - Sonido y video - NVTV Tv oUT-

Te queda instalado en Aplicaciones - Sonido y Video - 

Para usarlo lo arrancás y le colocás los parámetros necesarios. Hay algo con lo que muchos se vuelven locos y es que en Argentina el sistema es plan n, pero en mi caso el TV es brasilero y no funcionaba. En el seteo elegí pal m y todo de maravillas.

Ese programa, como verás, tiene muchas opciones.

Si tenés dudas y conozco las repuestas, puedo aportarlas.

Suerte.

Lo probé... pero al queres iniciar el NVTV OUT... no pasa nada... le doy click al lanzador y nunca ocurre nada..

Volviendo a lo de modificar el Xorg.conf, como lo hago... y donde pongo lo de la vista clonacion? como se llama esa opcion??

---

### Post by faktorqm on 2007-07-23
Hola, perdona que no respondi antes, es que tuve ocupado.
Enchufa el tv con la pc apagada, y prende el tv y despues prende la pc.

Anda a aplicaciones -> Herramientas del sistema -> NVIDIA X Server settings.

Te aparece una ventana, dividida en dos partes. En la parte de la izquierda, clickeas donde dice
"X server display configuration". y a la derecha te aparecen 3 contenedores, uno que dice "Layout", 
otro que dice "Display" y otro mas que dice "X Screen".

En el contenedor que dice "Display" tenes un botón que se llama "configure...". Clickealo y te aparece una ventana que dice:

"How should this display device be configured?"

Y te dice 3 opciones: 

- disabled
- separate x screen 
- TwinView (requires X restart)

Ahi tenes que elegir Twinview y ese es el modo clonacion. Despues te reinicia el server X y teoricamente te deberia clonar. Sino te anda avisá. salu2!

---

### Post by rojojuan on 2007-07-23
> **faktorqm said:**
> Hola, perdona que no respondi antes, es que tuve ocupado.
Enchufa el tv con la pc apagada, y prende el tv y despues prende la pc.
m
Anda a aplicaciones -> Herramientas del sistema -> NVIDIA X Server settings.

Te aparece una ventana, dividida en dos partes. En la parte de la izquierda, clickeas donde dice
"X server display configuration". y a la derecha te aparecen 3 contenedores, uno que dice "Layout", 
otro que dice "Display" y otro mas que dice "X Screen".

En el contenedor que dice "Display" tenes un botón que se llama "configure...". Clickealo y te aparece una ventana que dice:

"How should this display device be configured?"

Y te dice 3 opciones: 

- disabled
- separate x screen 
- TwinView (requires X restart)

Ahi tenes que elegir Twinview y ese es el modo clonacion. Despues te reinicia el server X y teoricamente te deberia clonar. Sino te anda avisá. salu2!


En mi caso NVTV-Out me da salida como si fuera Twinview. Lo aporto por si sirve para aclarar más.
Saludos

---

### Post by faktorqm on 2007-07-23
si, gracias, yo ni enterado, el dia que se me caiga el conf ese me quedo sin clonar jajajaj salu2!!

---

### Post by rojojuan on 2007-07-24
Tal vez no tenés instalados los drivers correctos. Qué procesador tenés? Por que en Nvidia hay diferencias en los drivers según el procesador.

---

### Post by Thalskarth on 2007-07-26
> **faktorqm said:**
> Hola, perdona que no respondi antes, es que tuve ocupado.
Enchufa el tv con la pc apagada, y prende el tv y despues prende la pc.

Anda a aplicaciones -> Herramientas del sistema -> NVIDIA X Server settings.

Te aparece una ventana, dividida en dos partes. En la parte de la izquierda, clickeas donde dice
"X server display configuration". y a la derecha te aparecen 3 contenedores, uno que dice "Layout", 
otro que dice "Display" y otro mas que dice "X Screen".

En el contenedor que dice "Display" tenes un botón que se llama "configure...". Clickealo y te aparece una ventana que dice:

"How should this display device be configured?"

Y te dice 3 opciones: 

- disabled
- separate x screen 
- TwinView (requires X restart)

Ahi tenes que elegir Twinview y ese es el modo clonacion. Despues te reinicia el server X y teoricamente te deberia clonar. Sino te anda avisá. salu2!

muchas gracias... ahora si entendi y pude habilitarlo sin dramas... al principio me pasaba que me extendia el escritirio a las dos pantallas... despues encontre que hay un pequeño menucito abajo de todo para decir si queres extendido o clon absoluto...

Muchas gracias por su ayuda y consejos!!!

---

### Post by Skavenger on 2007-12-26
antes que nada, disculpen por revivir esto, pero tengo un problema =/

la salida de video funciona perfectamente, veo las pantallas clonadas, todo como tenia en windows, el unico problema es que si reproduzco un video en el tele sale cortado :S, si la veo en fullscreen tbn se ve cortado...

en windows uso bsplayer y cuando veo una pelicula en fullscreen automaticamente se acomoda a la resolucion del televisor, hay algo que pueda hacer para que en ubuntu pase lo mismo? o alguna manera de ver la pelicula entera sin que aparezca cortada u.u

probe con vlc, talvez con otro reproductor se solucione, pero no conozco otro tan completo...

gracias!

---

### Post by User21 on 2007-12-26
Yo tengo un problema similar, con una mx4000, en donde, en modo Twinview, el monitor tiene 1280 x 1024, y el tv tiene 1024 x 768. Al reproducir una pelicula en pantalla completa, en el TV, parte del video queda fuera de la pantalla (la diferencia entre 1280 x 1024 y 1024 x 768!!!). De modo, que para visualizar correctamente, debo hacerlo desde una ventana de video de 1024 x 768, ya que el TV no soporta una resolucion mayor ni forzandolo manualmente! Tampoco hay forma de solucionarlo desde las propiedades de nvidia-settings. Por otro lado, el video SE ME VISUALIZA PERFECTAMENTE con mplayer!..

Aprovecho para dejaros [este video]("http://www.youtube.com/watch?v=DUSn-jBA3CE") de como deberian funcionar las cosas con Compiz Fusion :P Si, lo hemos visto mil veces, pero este video es re copado! :P

---

