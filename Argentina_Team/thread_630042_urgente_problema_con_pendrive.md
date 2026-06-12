---
title: "urgente problema con pendrive"
date: 2007-12-02
forum: Argentina Team
---

### Post by fedeavila on 2007-12-02
[FONT="Comic Sans MS"][SIZE="2"]hola de nuevo gente
otra vez pidiendo ayuda esta vez es urgente!

se trata de mi mp4 
tiene 2 gigas de memoria
intentaba formatearlo en el dia de ayer
obviamente no podia...

yo buscaba en el icono q siempre se me aparece solito en mi escri
con el clic secundario q apareciera "formatear" o algo similar...
pero nada... 
entonces no tuve la mejor idea q borrar TODO con la tecla Suprimir del teclado
de los 2 gigas siempre me decia q tenia 285 megas de espacio disponible 
(sisi re loco)

entonces seleccione todo y lo borre a lo "normal"
se borro todo, pero seguia con el mismo espacio disponible!

vi q en la papelera de mi escri (q suponia no tenia nada q ver) 
estaban las cosas q habia borrado en mi mp4 ¿?
no pense, directamente vacie la papelera
entonces me fije y seguia teniendo el mismo espacio disponible en el mp4

empece a buscar y a buscar en google
y me encuentro en una pag q dice q me tenia q instalar el gtparted
hago todo, lo instalo...

conecto al aparato, lo desmonto desde el icono del escri, como decia en la pag web
abro el gtparted, veo el mp4 q aparecia x ahi 
pero no me aparecia disponible la herramienta para formatear...
es mas, no podia hacer nada!

simplemente se me habilitaba el botoncito para obtener info de la unidad
q decia sistemas de archivos "unknown" y en otro lado me decia "vfat"
entonces busque en otra pag y decia q tenia q poner en una terminal:

sudo mkdosfs -I -n nombre_volumen /dev/sda

y lo escribo tal cual esta ahi
y veo q algo hace...

ahora... como un nabo q soy lo deje asi tal cual donde dice "nombre_volumen" 
en vez de ponerle el nombre q era realmente (x-micro)

y ahora parece q lo rompii todoo
cada vez q lo conecto me pone: 

---------------------------------------------------------------------------
No se puede montar el volumen.
No es posible montar el volumen <<nombre_volu>>
Detalles: mount: /dev/sda: can't read superblock
---------------------------------------------------------------------------

y bueno, no solo q mepa q lo rompi para siempre
sino q cuando intento encender el mp4 para escuchar musica
se queda con la pantallita de inicio y se queda ahi como congelada
no hace nada...

por las dudas apague todo xq cada vez q intento hacer las cosas solo
las termino descajetando maal

asi q mañana cuando ire a laburar se q me voy a aburrir en el tren jjja
por este y solo por este motivo les ruego ayuda a la mayor brevedad posiblee

muchas gracias x adelantado :(

___________________________________________________________
pd: con respecto a lo del sonido comento q se arreglo SOLO

no hice nada de nada... 
de un dia para otro se me arreglo
antes el unico prog q se podia escuchar musica era el Rythmbox
ahora me funcionan todos

y con respecto a lo del photoshop tambien
ya me anda la herramienta de la curita 
asi q esta todo bien con eso :D

el unico problema q tengo ahora es este, del mp4
y el de los videos de youtube q no se q onda

me baje el QtTube y me bajo los videos y los guardo en la compu
ahi si se escucha pero directamente desde firefox imposible
y ya puse eso de "esd" "none" "auto" aoss" 
no me funca con ninguno! 
y cuando pongo "esd" directamente no me funca el firefox en su totalidad jajaja

yo ya creo q porque tengo el equipo conectado a la pc

.
.
.

otra pregunta!
hay alguna manera de hacer q la aplicacion Glipper 
se ejecute automaticamente cada vez q se inicia el sistema?

otra... el "emesene" despues de 1 hora de uso se me tilda
o sea, no se cuelga, puedo ver mis contactos en la pantalla principal
pero cuando hago doble clic para abrir una nueva conversacion
no me abre nada!
yo se q son detalles y boludeces, pero no se xq pasa todo eso :S
al igual q la barra de notificaciones, si se me cuelga algo y pongo Forzar salida
(a ese programa q se me colgo) la barra de notificaciones no muestra ningun icono

otra pregunta: en la parte de Sistema/Preferencias
tengo como 5 iconos pertenecientes a JAVA
se pueden ocultar esos iconos de alguna manera?
xq aunq parezca molesto (y para mi lo es) me hace q la barra esa sea demasiado extensa

ultima consulta: como hago para poner tipo el estado del tiempo
o algun calendario en el escritorio q se vea en 3D ??

opinion: el GPicView no funciona para ver imagenes en una red local...

opinion2: el programa ArtManager se cierra cuando intento poner "Descargar archivo" en vez de "Instalar automaticamente"

nada mas! 
yo tengo un bloc de notas q voy poniendo todas mis preguntas
a medida q me van surgiendo o me van sucediendo
y cuando ya llevo una gran cantidad, hago el post

mil disculpas x la cantidad de preguntas...[/SIZE][/FONT]

---

### Post by ariel on 2007-12-03
tu post es un tanto prolongado, no lo pude terminar de leer :)

al parecer briqueaste tu mp4. seguramente tu mp4 tiene alguna combinacion de teclas para que al encenderse, formatee la memoria flash en whatever format que estaba usando. te recomiendo googlear. no creo que haya otra manera de salvarlo (quizas: si te vino con un cd de windows).

Si solo veias una particion de 250megas, puede ser que tu mp4 usa el protocolo MTP en la interfaz usb en lugar de la mas comun "mass storage". Con Mass storage el player se ve como si fuese un disco; con MTP, nope. Algunos mp4 permiten seleccionar MTP/mass storage. De ultima, podes usar en linux music manager que soporte MTP; googlea / chequea rythmbox, amarok, etc.

---

### Post by fedeavila on 2007-12-05
> **ariel said:**
> tu post es un tanto prolongado, no lo pude terminar de leer :)

al parecer briqueaste tu mp4. seguramente tu mp4 tiene alguna combinacion de teclas para que al encenderse, formatee la memoria flash en whatever format que estaba usando. te recomiendo googlear. no creo que haya otra manera de salvarlo (quizas: si te vino con un cd de windows).

Si solo veias una particion de 250megas, puede ser que tu mp4 usa el protocolo MTP en la interfaz usb en lugar de la mas comun "mass storage". Con Mass storage el player se ve como si fuese un disco; con MTP, nope. Algunos mp4 permiten seleccionar MTP/mass storage. De ultima, podes usar en linux music manager que soporte MTP; googlea / chequea rythmbox, amarok, etc.
hey! grax! sos el primero y unico q me ayuda jaja! nada... no entendi casi nada de lo q dijiste pero tengo una mejor idea... voy a intentar formatear con una pc q tiene windows xp a ver q sucede... grax igual man! saludos

---

### Post by faktorqm on 2007-12-06
bueno al igual que Ariel no termine de leer tu post...... sin comentarios. Capaz te venga bien leer esto: [http://www.sindominio.net/ayuda/preguntas-inteligentes.html](http://www.sindominio.net/ayuda/preguntas-inteligentes.html)

escuchame una cosa, te lo digo con toda la onda del mundo, sos muy atolondrado, lo unico que tenias que hacer con tu mp4, era borrar los temas como bien hiciste, y luego te los manda a la papelera del dispositivo, (existe una papelera para cada particion o disco).
Entonces, borraste con suprimir y seguias teniendo lo mismo, en el nautilus, sobre la carpeta que estabas parado, presionas "control + h" y te va a mostrar los archivos ocultos. ahi vas a ver una carpeta que se llama ".Trash-nombredeusuario", por ejemplo la mia se llama ".Trash-faktorqm" entonces vas a ahi y borras todo con suprimir.

A partir de ahi, tenias 2 opciones, o fijarte si seguia igual, o fijarte si ya estaba vacio efectivamente con los 2 gb. si no estaba vacio, primero te tenes que fijar lo que dijo Ariel, la configuracion del mp4, fijate que capaz tiene un modo "normal" o algo parecido. una vez seteado eso, te recomiendo (por las dudas) de formatearlo con windows por una cuestion de compatibilidad. si se te cuelga el software fijate que puede ser por que tambien planchaste todo o parte del programa que usa el micro adentro. la verdad no se muy bien como se manejan esas cosas, si queres te averiguo y te digo.
suerte con eso y comentame a ver que paso. salu2!

---

### Post by fedeavila on 2007-12-06
> **faktorqm said:**
> bueno al igual que Ariel no termine de leer tu post...... sin comentarios. Capaz te venga bien leer esto: [http://www.sindominio.net/ayuda/preguntas-inteligentes.html](http://www.sindominio.net/ayuda/preguntas-inteligentes.html)

escuchame una cosa, te lo digo con toda la onda del mundo, sos muy atolondrado, lo unico que tenias que hacer con tu mp4, era borrar los temas como bien hiciste, y luego te los manda a la papelera del dispositivo, (existe una papelera para cada particion o disco).
Entonces, borraste con suprimir y seguias teniendo lo mismo, en el nautilus, sobre la carpeta que estabas parado, presionas "control + h" y te va a mostrar los archivos ocultos. ahi vas a ver una carpeta que se llama ".Trash-nombredeusuario", por ejemplo la mia se llama ".Trash-faktorqm" entonces vas a ahi y borras todo con suprimir.

A partir de ahi, tenias 2 opciones, o fijarte si seguia igual, o fijarte si ya estaba vacio efectivamente con los 2 gb. si no estaba vacio, primero te tenes que fijar lo que dijo Ariel, la configuracion del mp4, fijate que capaz tiene un modo "normal" o algo parecido. una vez seteado eso, te recomiendo (por las dudas) de formatearlo con windows por una cuestion de compatibilidad. si se te cuelga el software fijate que puede ser por que tambien planchaste todo o parte del programa que usa el micro adentro. la verdad no se muy bien como se manejan esas cosas, si queres te averiguo y te digo.
suerte con eso y comentame a ver que paso. salu2!
gracias por la infooooOO!!!!!!! te comento q ya lo arreglee :D lleve el mp4 a una compu con windows xp y me salto al toke un mensaje q decia q el disco no tenia formato q si keria darle formato puse q sii y yaa lo hicee jejejeje le puse fat16 formato completo y ahora anda joyitaa!! saludos gracias x la infoo despues voy a leer el manual ese con las preguntas!

---

