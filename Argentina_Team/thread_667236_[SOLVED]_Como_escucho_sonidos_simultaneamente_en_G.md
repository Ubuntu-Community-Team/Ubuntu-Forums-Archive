---
title: "[SOLVED] Como escucho sonidos simultaneamente en Gutsy?"
date: 2008-01-14
forum: Argentina Team
---

### Post by atari130xe on 2008-01-14
Gente, me gustaria saber como puedo escuchar múltiples sonidos a la vez (aMSN, XMMS y otros eventos), Googleé un poco y encontré respuestas pero ninguna funcionó. Alguna sugerencia?, En Sistema --->preferencias ---> Sonido, elejí ESD pero nada me sale:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: No se pudo establecer una conexión con el servidor de sonido"

También y agregándolo al tema, no encuentro la manera de "escuchar" el sonido de cierre de Ubuntu, por alguna razón, (me pasó en otras instalaciones en otras PC) no funciona ese sonido (Si en cambio el sonido de inicio), será un Bug? o soy el único al que le pasa eso? :) (conste que entré a sonidos---> salida de la sesión y al reproducir suena perfectamente, pero al apagar la PC ni ahi.

---

### Post by Mafber on 2008-01-14
Hola Atari130xe!! te cuento que también tengo el problema de que no se escucha el sonido de cierre.
En cuanto a lo que decís de escuchar dos sonidos a la vez, no se que puede ser :(  Lo que si te digo es que se puede, de hecho uso 2 reproductores (en algunos momentos) y paginas con sonidos y se "escucha" todo junto.

---

### Post by atari130xe on 2008-01-14
Me dejás mas tranquilo :) el tema es que ya encontré tantas "sugerencias" sobre la posibilidad de escuchar varios sonidos simultaneamente que empecé a "sonar" la instalación, porque en un par de juegos (mania drive) el sonido empezo a entrecortarse. Llegué a instalar el flamante "PulseAudio" (el nuevo servidor de sonido) pero.. sin éxito, (can´t connect the server) ufa! :confused: así que si alguien me puede dar una mano genial!

---

### Post by valucha on 2008-01-15
[COLOR="DarkOrchid"]Aqui otra que tampoco escucha el sondio de cierre... pero sí varios a la vez...
MI placa de sonido es integrada a la mother Realtek ALC850.
Saludo.[/COLOR]

---

### Post by atari130xe on 2008-01-15
Deberia desinstalar todo el sistema de sonido? (después de todo lo que intenté es claro que algo quedó mal porque algunas cosas suenan entrecortadas y otras como el sonido de inicio desaparecieron, como deberia hacerlo?

Aclaro que la placa de sonido la cambié hace unos días: Mi PC es "prehistórica" (1999) por ende solo quise actualizarla un poco para tirar un tiempo más hasta armarme una nueva. 

Antes: Audio integrado AC97
ahora: Placa Genius Live 5.1 (según investigué es full compatible con Linux)

Antes: 256MB de Ram PC133
Ahora: 448MB PC133 (si raro el combo pero funca mucho mejor).

Antes: CD/DVD ROM/RW Lite ON (una porquería tiré $200 mangos al tacho por unos meses, -problemas para la apertura de la bandeja y leía los discos cuando se le cantaba) -quedó fuera de la garantía por eso la reemplacé por una nueva- Me salió mala.
Ahora: CD/DVD ROM/RW DL Sony AD7190A me gusta como funca, ya veremos con el tiempo, tuve una Samsung desde el 2001 hasta la Lite ON y me salió muy buena.

Antes: 2 puerto USB1.0 integrados 
Ahora: placa expansora con 4 puertos USB2.0 y uno USB1.0 (se sumaron a los que tenía)

Y gueno es mi humilde "mejora".

---

### Post by atari130xe on 2008-01-16
Con respeto a esto, Ubuntu configura por defecto (al instalarlo) la reproduccion de múltiples sonidos a la vez? al menos hablo de Gutsy, porque me desconcierta buscar por todas partes y seguir con un sonido por vez.

---

### Post by Mauro22 on 2008-01-16
Probaste actualizar el ESD?

Buscalo con synaptic por 'esound'

creo que hay un common y un par mas


:popcorn:

---

### Post by atari130xe on 2008-01-17
Gracias, hice la actualizacion, ahora puedo escuchar el sonido de inicio y de cierre de Ubuntu, algo es algo :lolflag: pero la mezcla de sonidos sigue sin funcionar, solo puedo escuchar una cosa por vez...

---

### Post by atari130xe on 2008-01-17
ahora tengo multiples sonidos, eureka! pero tengo que desinstalar mania drive por ejemplo porque clickea el sonido y es una pena, asi que a reinstalar eso, y estoy peleando con el aMSN para que pueda escuchar el sonido de lso eventos, asi que SOLVED grax! :)

Supongo que como tengo dial up y no le di duro y parejo a las actualizaciones ahi esta el tema, es que son CIENTO NOVENTA Y CUATRO y con dial up me llevaria todo junto como 4 dias jeje asi que de a poco lo haré.

---

### Post by xboo2 on 2008-01-30
Fijate si te es posible descargar los paquetes de actualización desde un ciber o alguien que tenga banda ancha. Primero conectate en tu casa con el dial up y te genera un archivo de peticiones del los paquetes que te faltan. Luego te llevas eso a un lugar donde baje rápido y te lo llevás en un pen drive o cd. Creo que vas a ahorrar tiempo y plata. Además es mas copado el aprovechar esa herramienta que hicieron para quienes están en tu misma situación.:)

---

### Post by atari130xe on 2008-01-31
Gracias, así lo hice, llevé mi pen drive al laburo donde tengo conexion a 512k, bajé los paquetes y en synaptic, agregar archivos y listo, actualizado! :)

---

