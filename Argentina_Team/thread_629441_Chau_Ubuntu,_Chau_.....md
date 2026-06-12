---
title: "Chau Ubuntu, Chau ...."
date: 2007-12-02
forum: Argentina Team
---

### Post by leonardo83 on 2007-12-02
Que tal gente, la verdad que estoy a cerca de 10 cm. de eliminar ubuntu de mi ordenador, y quedarme tranquilo con mi Window$ , ya se ya se, me van a tildar de que no transpiro la camiseta y varias cosas mas pero 
a saber:
Si se puede solucionar esto la verdad me volcaria a decirle chau a win gradualmente, pero como hasta ahora cosecho experiencias algo negativas, veamos como es el panorama...
No puedo leer los live cd, esto pasa hace rato y tengo posts sobre el mismo, igualmente mi jefe trabaja para ubuntu y me prometio una solucion para esta semana.
El otro dia APENAS acabe de instalar ubuntu 7.4, vaya a saber porque, en un momento de estupidez, en la terminal escribi
```
compiz --replace
```, esto es porque estaba viendo como era lo de instalar beryl y bla bla, no me habia bajado nadas pero aun no se porque tipee eso!! cuestiion que a partir de ese momento mi escritorio MURIO.Es decir que entro con mi pass y user y carga bla bla pero la pantalla esta toda en negro, apreto ALT + f2 y escribo de nuevo "compiz --replace" y por aprox 3 segundos se ve mi escritorio, y despues vuelve la pantalla negra.
Luego de maldecir un rato, entre por el modo texto al inicio y agrugue un usuario nuevo, con este entro y veo todo bien, pero si coloco cd's se abre la ventana con susu contenidos pero no se montan automaticamente en el escritorio como con mi otra sesion. Ademas de que estoy peleando hace rato para ver como corno instalo los drivers de mi placa riva tnt2, y que no se bien como instalar archivos como por ejemplo xpdf que me grabe en un cd, no lo puedo elegir en los repositorios y ademas ni idea como instalar un tar.gz desde terminal.
Como ven en este momento estoy bastante sacado!! :mad:
Si leyeron hasta aca se agradece, espero puedan al menos decirme como deshabilitar esa macana que hice con compiz, o lo los tar. o ayuda similar.
Ah, me olvidaba, en win me aparece el disco duro donde tengo ubuntu, y la opcion formatear, mi idea es borrar todo al diablo como paera tener el rigido vacio de nuevo para instalar ubuntu de cero, pero no se si se puede esa manera, en todo caso si es asi, como elimino el grub ? aplico fdisk mbr ???
Saludos!!
Chau, me voy a tomar un [COLOR="YellowGreen"]armonil[/COLOR] ......

---

### Post by Hei Ku on 2007-12-02
vamos por partes.

Supongo que tenes ubuntu. En ese caso, para sacar el compiz lo que tenes que hacer es:

desde alt+F2
metacity --replace

En cuanto a instalar programas desde tar.gz, tenes que descomprimirlos y despues en general tienen un archivo readme o install donde explican como compilarlo. La forma mas comun es:

./configure
make
sudo make install

Para esto tenes que tener instalados los archivos para compilar:

sudo apt-get install build-essential

En cuanto a los drivers de tu placa, no se, pero me parece que es de las dificiles y a lo sumo vas a poder tener buena resolucion, pero no aceleracion 3d.

---

### Post by tzulberti on 2007-12-02
Yo no entiendo la parte del xpdf. Las dudas que tengo son:
1) Cuando lo buscas en el synaptic no te aparece?
Rta: Anda a Settings -> Filters, y tilda todas las opciones.
Una vez hecho eso hace un Reload ( un update desde el apt) y listo.

2) En el cd grabastes el .deb del xpdf y no sabes como agregarlo a los repositorios?
Rta: Basicamente no lo vas a poder agregar, lo que tenes que hacer para instalarlo: es usar el comando "sudo dpkg -i nombreDelArchivo.deb" (no estoy seguro de si primero lo tenes que pasar al rigido)

3) Si te bajastes un .tar.gz hace lo que dice: Hei Ku

---

### Post by Thalskarth on 2007-12-02
> **leonardo83 said:**
> mi idea es borrar todo al diablo como paera tener el rigido vacio de nuevo para instalar ubuntu de cero, pero no se si se puede esa manera, en todo caso si es asi, como elimino el grub ? aplico fdisk mbr ???

[COLOR="RoyalBlue"]De Ubuntu se poco ya que soy principiante... pero en este caso, si queres hacerlo podes borrar todo el disco y empezar de cero otra vez.

Para quitar el Grub del arranque, lo más facil es que bootees con un diskette de arranque (de Win98, ME, etc). y entonces, desde el promt pones:

```
A:\> fdisk /MBR
```

y listo. luego al arrancar ya arranca el windows de una (al menos con WinXP funciona de 10. COn Vista nunca lo probe, ya que no tengo ni tendre el Vista)[/COLOR]

---

### Post by User21 on 2007-12-03
Jejeje, es un desertor corajudo, o uno arrepentido ? Si hubieras querido irte, te hubieses ido sin preguntar! JAJAJA, me parece que te gustó el Ubuntu, pillín! y no lo querés dejar, sabés que lo vas a extrañar ! xD

Tomémoslo con un poquito de humor: cuántos posts hay que digan que abandonan Ubuntu? :D 

:lolflag:

---

### Post by Hei Ku on 2007-12-03
> **User21 said:**
> Jejeje, es un desertor corajudo, o uno arrepentido ? Si hubieras querido irte, te hubieses ido sin preguntar! JAJAJA, me parece que te gustó el Ubuntu, pillín! y no lo querés dejar, sabés que lo vas a extrañar ! xD

Tomémoslo con un poquito de humor: cuántos posts hay que digan que abandonan Ubuntu? :D 

:lolflag:

Y cada post hay que tomarlo seriamente, porque nos muestran los lados flacos de Ubuntu. Por una u otra cosa, un usuario se sintio tan frustrado, enojado, etc que se tomo el tiempo de escribir un largo post sobre eso. Y si, muchas veces es como el suicida que amenaza con saltar para llamar la atencion, pero por cada usuario que escribe que va a sacar ubuntu, hay un monton que no lo hacen, y que ni siquiera nos enteramos por qué.

Ahora, lo que sí me gustaría saber es si las respuestas que dimos sirvieron.

---

### Post by User21 on 2007-12-03
Alguna vez, mi viejo me hizo poner una fila de ladrillos, de lo que en un futuro sería mi pieza. Lo maldije, me enojé, zapateé, y me sentía re frustrado... Sin duda, mis primeros ladrillos daban asco! Estaban todos chuecos, y la mezcla desbordaba por los lados. Al volver mi padre, derrumbó nuevamente toda la fila que yo había puesto con tanto esmero. Me sentí aun más humillado, y hasta pensé tirarle un ladrillazo en el lomo! xD

Con mucha paciencia, me dijo cómo había que hacerlo, para luego, nuevamente irse, y dejarme allí, entre ladrillos, mezcla y herramientas. 

Volví a intentarlo, esta vez con un poco más de éxito. Algo más realizado, le encontré la vuelta, y pude hacerlo con mayor agilidad. Construí un ínfimo porcentaje de esa pared, pero encima de MIS LADRILLOS se apoyan todos los demas, y así, sucesivamente...

Querés desinstalar Ubuntu? Estás en todo tu derecho, como dueño de tu libertad, de tu elección. Querés renunciar por que no te sale hacerlo funcionar? ESO NO me suena razonable. Si yo no hubiese puestos esos ladrillos, seguro mi papá lo hubiese continuado... pero el sabor de haberlo hecho uno mismo (con la ayuda de mi viejo), es sin duda la mejor recompensa.

Pensá que a miles de usuarios les funciona y lo han adoptado como sistema único. No te des por vencido, si de los primeros intentos se trata. 

TE CANSASTE del todo? Entonces quizás sos vos quien le fallaste al Ubuntu / Linux. Quizás no estas a la altura de usarlo, quizás no sea para vos... Pero, de verdad crees que esa es la respuesta ?..

y para finalizar.. la droga no es la respuesta tampoco, afloja con el armonil...

Por favor, no tomes todo esto personal: mi viejo también me daba consejos, y me daba una broncaaaaa! :D

---

### Post by leonardo83 on 2007-12-04
> **User21 said:**
> Alguna vez, mi viejo me hizo poner una fila de ladrillos, de lo que en un futuro sería mi pieza. Lo maldije, me enojé, zapateé, y me sentía re frustrado... Sin duda, mis primeros ladrillos daban asco! Estaban todos chuecos, y la mezcla desbordaba por los lados. Al volver mi padre, derrumbó nuevamente toda la fila que yo había puesto con tanto esmero. Me sentí aun más humillado, y hasta pensé tirarle un ladrillazo en el lomo! xD

Con mucha paciencia, me dijo cómo había que hacerlo, para luego, nuevamente irse, y dejarme allí, entre ladrillos, mezcla y herramientas. 

Volví a intentarlo, esta vez con un poco más de éxito. Algo más realizado, le encontré la vuelta, y pude hacerlo con mayor agilidad. Construí un ínfimo porcentaje de esa pared, pero encima de MIS LADRILLOS se apoyan todos los demas, y así, sucesivamente...

Querés desinstalar Ubuntu? Estás en todo tu derecho, como dueño de tu libertad, de tu elección. Querés renunciar por que no te sale hacerlo funcionar? ESO NO me suena razonable. Si yo no hubiese puestos esos ladrillos, seguro mi papá lo hubiese continuado... pero el sabor de haberlo hecho uno mismo (con la ayuda de mi viejo), es sin duda la mejor recompensa.

Pensá que a miles de usuarios les funciona y lo han adoptado como sistema único. No te des por vencido, si de los primeros intentos se trata. 

TE CANSASTE del todo? Entonces quizás sos vos quien le fallaste al Ubuntu / Linux. Quizás no estas a la altura de usarlo, quizás no sea para vos... Pero, de verdad crees que esa es la respuesta ?..

y para finalizar.. la droga no es la respuesta tampoco, afloja con el armonil...

Por favor, no tomes todo esto personal: mi viejo también me daba consejos, y me daba una broncaaaaa! :D

1) los consejos que me dieron si me sirvieron, se agradece
2) SI considere abandonar ubuntu y por varias razones, no tengo banda ancha, conectarse con el modem interno por lo que lei es un bardo, cargar archivos en un cd y leerlos no me los acepta (no se porque), los efectos 3d casi en un 89% voy a tener que resignarme de usarlos alguna vez, etc etc etc
3)no entiendo la comparativa entre hacer una pieza y mi ubuntu....ah para.!...no no...:)
4)que problema de drogas? el armonil es como un m&m, y ademas la cerveza te da horas de diversion sana !! :lolflag: 
5)no me acuerdo quein me dijo lo de probar lo de metacity, pero funciono!!! gracias por eso, ahora puedo ver mi escritorio d enuevo siiiiiiiiiiiii!!
El problema es que no se porque no se me ve en equipo las lectoras ni el rigido de win que aparecia antes, y cuando pongo un cd aparece una ventana con el contenido pero no se monta la unidad automaticamente como lo hacia antes....no se porque.
A ubuntu le voy adar5 unos meses mas, igual no tengo ningun apuro, pasa que ahora l afacu captura toda mi atencion ja ja
Saludos!!

[I]SEE YOU IN THE MOSH

[/I]

---

### Post by BiTFx on 2007-12-06
Hola **leonardo83**, te cuento, hace casi 1 mes que instalé Ubuntu, y bue, en mi propia experiencia, la cosa no es tan facil como te la pintan, a veces no encontrás la ayuda donde te recomiendan que la busques, tenés los que te dan la ayuda desde la linea de comandos (que para los nuevos es muy aterradora a veces), y están los otros que escriben un poco mas y te dan la forma de hacerlo desde la parte visual (clásico como nuestro Win), aunque ese no es motivo para echarse pa' tras.
 
Reinstalé Ubuntu 3 veces, esta semana voy por la cuarta, hasta acá hice de todo, probé, borré, instalé, metí la pata, y me enojé mucho.
 
Entré al irc, al canal #ubuntu-ar (o #ar-ubuntu) varias veces y el unico que me dio ayuda fue una sola persona, que para colmo el otro día me dijo -"Creo que es así, porque Yo no uso ubuntu...". Pero aclaro que sabía bastante esta persona(mstreetlinux creo ke era el nick) y me dio una mano bárbara. 
 
Pero me calentaba ver siempre a los mismos conectados y que no me pasaran un tronco de bola, ni siquiera saludaran. Ahí yo terminaba peor!!! me molestaba no sentir ese apoyo que profesa la comunidad, pero ke se le va a hacer, **el sistema es libre, toda una comunidad ayuda, pero al final el que mete la mano en tu pc sos Vos, y esa es la idea QUE APRENDAS**, a mi me pasa, me siento frustado, despues de haber instalado 500 veces en mi pc desde el win 98 hasta el XP, pensaba, -"Uhhh, instalo 1 vez el Linux, lo uso 1 semana, lo doy vuelta, lo hago de goma y me olvido (como buen usuario de win)..." MINGA!!!! Activando el Compiz Fusion me la mandé y arruiné la parte gráfica, probé varias soluciones y nada, reinstalé.
 
Lo bueno de esa primer experiencia fue que en los intentos de arreglar la metida de pata me encontraba con cosas que aprendía, y que ahora me sirven.
 
Después quise hacer una conexion compartida a internet, se demoraba 10 minutos en arrancar despues de queres hacerlo, 2º reinstalada, y así, bueno no te voy a contar por todo lo que pasé, ya que sería aburrido, pero la idea es que no te des por vencido, que reinstales Ubuntu, que pruebes otra versión, aunque algunos te digan que no es necesario reinstalar, que lo podes arreglar así nomás, yo me tranquilizo reinstalando (gracias a la cultura win, aclaro) y empezando desde 0 otra vez, y tratando de no meter la pata de nuevo con los errores anteriores.
 
Llevo 1 semana si tocar Ubuntu, me puse a ver unos videotutoriales (los puse en otro post), leo algo, pregunto aquí, como para tomar el cuarto aire para empezar de nuevo (aunque a esta altura la parte gráfica está como quiero, no pude compartir internet aún, pero esa es la meta, aunque le buscaré la vuelta antes de reinstalar así ya tengo un problema menos, ;)), ayer reinstale mi win, así que ni me aparece Ubuntu al arranque, tengo la particiones escondidas esperando que en estos dias les vuelva a dar vida...
 
**Desde mi experiencia**: 
 
Probá TODO lo que sea necesario, no tengas miedo de meter la pata, creo que Ubuntu va a llenar tus espectativas, solo que debes "descularlo" (encontrarle la vuelta), y darle su tiempo y el tuyo. Probá las aplicaciones que trae por defecto y después meté otras así vas comparando y eligiendo, nos va a costar un poquito cambiar nuestra mentalidad windows.
 
No abandones este foro, es de gran ayuda, hace unos días que no entro y en verdad se extraña, y todo lo que he logrado lo he encontrado por acá.
 
No te desanimes, **la práctica hace al maestro**.

---

### Post by sajnox on 2007-12-07
Interesante lo que se armo, en mi opinion la facilidad de Ubuntu hoy por hoy depende del hard que tengas, en mi caso detecto TODO y sin mas vueltas tuve la maquina andando, me dio un poco de problemas la placa de video AYI y sus drivers, pero lo solucione. Esto en cuanto a la configuracion.

Respecto al software hay cosas que estan MUY bien y otras no tanto. Es cuestion de gustos, necesidades y costumbres.

Dale un tiempo, cuando tengas ganas "Juga!!", para mi lo mas importante es saber que hay opciones que windows no es lo unico, en lo que es la maquina de mi casa solo uso Linux y la verdad que me siento mas seguro y cubro todas las cosas que hacia antes. Demosle tiempo, paciencia y ganas.

Saludos a todos

(Ya casi que los extrañaba)

---

### Post by LisaSimpson on 2007-12-07
Hola a todos, es mi primera participación y espero que me acepten como forera asidua...
Yo les puedo contar que tardé un año en convencer al resto de los usuarios de la compu de casa para instalar un linux... cualquiera fuera... pero un Linux... por favor...

Les llevé live cd de todas las distribuciones que se les ocurran... y no podía convencerlos... hasta que el window$ se descompuso por un virus... el pasado miércoles 14 y entonces... ¡¡¡magia!!! aceptaron mi propuesta.

Por suerte, en la máquina de casa el live cd del ubuntu funcionó de maravillas, detectó todo... hasta el modem interno (yo tenía mis reservas acerca de él)... ahora será cuestión de ir adaptándolo a la medida de cada uno de los usuarios....

Con esta experiencia espectacular nos compramos otra máquina, más nueva, que decía que venía preparada para linux... etc... y qué pasó... me está dando un dolor de cabeza... ya aprenderé a instalarla... lo más cómico es que es la máquina que yo uso, y es en la que todavía no pude instalar el ubuntu... ¡¡¡¡buaaaaa!!!! qué puedo decirle a mi familia que ahora es ubunturera cuando yo sigo cabalgando en xp.... mi discuro sobre linux suena a guitarreada... :guitar:

Pero no desfalleceré... es como dice alguien más arriba... con cada nuevo problema aprendo muchísimo... jajaja
Aunque no vienen mal algunas ayudas...
jeje

PS: no soy muy ducha en este sistema, sé de do$, window$, y o$warp (qué nostalgia... jaja) pero de linux poco... nunca lo había instalado. La instalación de casa fue tan simple, tan piola, tan buena... y esta otra, es tan tediosa... buaaaaa de nuevo... esto me pasa por comprar una máquina nueva... buaaaaaaa
:KS

---

### Post by facundocorradini on 2007-12-07
Hola "lisasimpson"

Cualquier problema que tengas no dudes en preguntar (topic aparte, claro está)

---

### Post by BiTFx on 2007-12-07
> **LisaSimpson said:**
> 
Hola a todos, es mi primera participación y espero que me acepten como forera asidua...

 
Hola **LisaSimpson**!!!, bienvenida al foro, tal vez no soy el más indicado en dar la bienvenida por ser nuevo también ;) pero ya vas a ver como en muy pocas posteadas y leidas te vas a sentir parte de esta comunidad.
 
> **LisaSimpson said:**
> 
Con esta experiencia espectacular nos compramos otra máquina, más nueva, que decía que venía preparada para linux... etc... y qué pasó... me está dando un dolor de cabeza... ya aprenderé a instalarla... lo más cómico es que es la máquina que yo uso, y es en la que todavía no pude instalar el ubuntu... ¡¡¡¡buaaaaa!!!! qué puedo decirle a mi familia que ahora es ubunturera cuando yo sigo cabalgando en xp.... **mi discuro sobre linux suena a guitarreada...** :guitar:

 
:grin: No veía la hora de terminar la mañana para ir a casa, y este comentario me hizo reir bastante. Llegó la hora de irme y me voy con una sonrisa, **gracias por el buen humor y bienvenida de nuevo!!!**

---

### Post by LisaSimpson on 2007-12-07
Me alegro que te hayas reído con mi comentario...
por lo menos te alegré el fin de semana...

Y gracias por la oferta de ayuda...
si tengo algún problema irresoluble en forma real (con amigos más cercanos) no duden que preguntaré aquí en el foro...
Después les cuento... quiero invertir el fin de semana para instalar mi querido Ubuntu... mientras el resto de la family mira pelis o disfruta de su vida "real"... :popcorn:

Yo soy cabeza dura... a mí no me ganará este hardware... jejejej ](*,)

---

### Post by leo_rockway on 2007-12-07
> **BiTFx said:**
> 
Entré al irc, al canal #ubuntu-ar (o #ar-ubuntu) varias veces y el unico que me dio ayuda fue una sola persona, que para colmo el otro día me dijo -"Creo que es así, porque Yo no uso ubuntu...". Pero aclaro que sabía bastante esta persona(mstreetlinux creo ke era el nick) y me dio una mano bárbara. 
 
Pero me calentaba ver siempre a los mismos conectados y que no me pasaran un tronco de bola, ni siquiera saludaran. Ahí yo terminaba peor!!! me molestaba no sentir ese apoyo que profesa la comunidad, pero ke se le va a hacer

Yo soy uno de los que generalmente esta en #ubuntu-ar

No es que no te saludemos de mala onda, es que no estamos sentados 24/07 adelante del x-chat/konversation/bitchx/irssi esperando tus preguntas. Muchas veces las personas entran, tiran una pregunta y 5 minutos despues se van porque no obtuvieron ninguna respuesta; 50 minutos despues alguien sale con "que lastima que se fue, yo podria haberlo ayudado".

A mi tambien me paso de necesitar una respuesta urgente, pero pensa que la gente que esta en IRC esta haciendo otras cosas de su vida (esta trabajando, esta estudiando, etc).

Asi que no desesperes que si no te ayudamos o saludamos no es de mala onda.

---

### Post by BiTFx on 2007-12-07
[**OFF-TOPIC**]
 
> **leo_rockway said:**
> Yo soy uno de los que generalmente esta en #ubuntu-ar
 
No es que no te saludemos de mala onda, es que no estamos sentados 24/07 adelante del x-chat/konversation/bitchx/irssi esperando tus preguntas. Muchas veces las personas entran, tiran una pregunta y 5 minutos despues se van porque no obtuvieron ninguna respuesta; 50 minutos despues alguien sale con "que lastima que se fue, yo podria haberlo ayudado".
 
A mi tambien me paso de necesitar una respuesta urgente, pero pensa que la gente que esta en IRC esta haciendo otras cosas de su vida (esta trabajando, esta estudiando, etc).
 
Asi que no desesperes que si no te ayudamos o saludamos no es de mala onda.
 
Hola **leo_rockway**, está todo bien, ese tema lo mencioné porque contaba mi experiencia y desaires con Ubuntu, pero sin animos de generar alguna discusión, enojar u ofender a nadie.
 
Recibí ayuda en el irc, lo aclaré, y se que los que están ahí tienen su vida "real" como cualquiera que se llame persona, y también se que lo que hacen, lo hacen de onda, porque es una cuestión personal la de ayudar y GRATIS, así que agradezco en lo que me ayudaron, pero aclaro, no quiero desviar el tema principal del post.
 
Agradezco tu aclaración y pido disculpas si en el comentario fui tal vez injusto (o eso transmite), **reconozco que entré al irc a hacer las preguntas y al cabo de un rato me salía**, no me quedaba a esperar (tal vez por la ansiedad de solucionar mi problema), pero esa fue mi primera impresión, y es la opinión que tengo al respecto dentro de ese contexto (frustración, impotencia por no solucionar el problema de mi Ubuntu).
 
Saludos a todos, perdón por desviarme del hilo del post.

---

