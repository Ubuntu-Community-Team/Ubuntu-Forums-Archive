---
title: "Configurar el torrent"
date: 2007-10-16
forum: Argentina Team
---

### Post by cerebrobaires20 on 2007-10-16
Hola gente del foro,les cuento que soy un new ubuntu-user,pero me encanta,tengo winDO$ instalado en mi maquina,en el mismo disco,pero ya ni lo uso(que buenooooooooo):guitar:bueno,paso a la pregunta,hace unos dias,me instale los paquetes para el cliente de torrent bittornado,pero al configurarlo me pedia que le indique los puertos,cosa que no tengo la mas palida idea,es que me tiro un num muy alto,y probe un monton y nada,asi que si me pueden ayudar se los aradeceria muchiiiiiiooooooooooo,un abrazo gente,y sigan asiiiiiiii!!!!!!!!!!!1:popcorn:

---

### Post by tzulberti on 2007-10-16
Dos puntos:
-> No uses letras tan grandes que dificultan la leida
-> El bittornado tiene tanto un cliente con interface como uno de linea de comando. Cual de los dos estas usando?

Saludos,
TZ

---

### Post by undiaperfecto on 2007-10-16
Yo te aconsejo, despues de haber usado azureus, utorrent via wine, bittornado, qtorrent y algunos mas. Usar el mas sencillo y graficamente mas lindo de todos, Transmission
sin tantas complicaciones de configuracions y livianisimo.

---

### Post by faktorqm on 2007-10-16
si queres saber que es un puerto y demas buscalo por internet.

Una vez que lo sepas, te bajas el firestarter (sudo apt-get install firestarter) y ahi vas a poder abrir el que vos quieras. si ademas usas un firewall en el router tambien vas a tener que abrirlo ahi.

Una vez que tengas toda la red configurada, para mi el transmission la rompe, y es el que uso desde el vamos en ubuntu (sudo apt-get install transmission).
La unica macana es que en los repos hay una version viejisima, plagada de bugs, y la de la pagina no es facil de hacerla andar por que hay que compilar y demas. si vas a bajar archivos "chicos", usalo sin ningun problema. yo estaba bajando el otro dia 26,4 gb y tuve tooooodos los problemas. es mas, todavia no los solucione :S

Please escribi "normalmente", te vamos a leer y a responder igual. salu2!!

---

### Post by cerebrobaires20 on 2007-10-16
te cuento que no estoy usando el bittornado porque cuando lo abro me aparece una ventana que me dice que archivo es el que quiero abrir,y no entiendo de que se trata,entonces trate de darle pa delante con el azureus,pero por lo visto es mas dificil,y alguien tiro una respuesta que decia que averigue de los puertos,lo hice,me dijeron que puertos tengo que usar,pero no pude,y tengo instalado el firestarter,creo que es por eso,por que a cada rato me bloquea conexiones....ahhhhh,y no me bardeen tanto por las letras,no fue mi intencon...jajajaja,grax a todos por las respuestas,y voy a ver si me va mejor con el transmission

---

### Post by tzulberti on 2007-10-16
> **cerebrobaires20 said:**
> te cuento que no estoy usando el bittornado porque cuando lo abro me aparece una ventana que me dice que archivo es el que quiero abrir,

Si hicistes doble clic sobre el archivo, y te abrio el bittornado, entonces te esta preguntando en donde es que queres guardar lo que te estas bajando. Sino, lo que te esta pidiendo ahi el el archivo de torrent con el que queres bajar. Despues de eso te pregunta en donde es que queres guardar los datos.

---

### Post by Mataca on 2007-10-16
Posteate un screenshot de última. Y así vemos exactamente que sucede!

---

### Post by cerebrobaires20 on 2007-10-17
bueno,es bueno lo que me dicen,mejor subo un screenshoot y lo ven,eso pasa cuando abro mi bittornado,ahhhh,les cuento,ahora tengo otro fuc... problema,no puedo reproducir mis canciones con juk,que segun lo que se es para eso,me pueden ayudar tambien con eso,y disculpen que sea tan molesto,pero ese es el precio del saber muchachos,un abrazoooooooo!!!!

---

### Post by cerebrobaires20 on 2007-10-17
ahhhh,perdon,yo hablano y no subi nada,jajaja,que colgado

---

### Post by Hernán-Amaya on 2007-10-18
por lo del torrent no te puedo ayudar, pero por el tema del JuK abri otro thread y detalla el error o los errores que te tira. fijate que puede ser que no tengas los codecs para escuchar mp3 o cosas por el estilo

---

### Post by faktorqm on 2007-10-18
hola kpo! no te cuelgues! :P:P
aca te hago un mini how to de como abrir un puerto en firestarter.
abri el firestarter, (yo lo hago con "sudo firestarter" desde un terminal), anda a la ficha "NORMATIVA", y arriba hay un boton grande que dice "AÑADIR REGLAS".

en la ventanita que te aparece, le das a NOMBRE, y te tira una lista con los servicios. ahi le pones "BIT TORRENT", y abajo en la casilla de puertos, por lo menos a mi me aparece "6881-6889", eso quiere decir que te va a abrir del puerto 6881 al 6889. pero si queres lo podes setear vos eso, yo por ejemplo en mi casa el que va es el 9009. podes elegir uno entre 1000 y 65000, solo para esa aplicacion. NO uses ninguno menor a 1000. ok?

despues le pones: "cuando el origen es..." ahi le pones CUALQUIERA.

si queres ponele un comentario, sino es lo mismo, y le das al boton AÑADIR.

entonces abajo te va a aparecer, permitir servicio: bit torrent, puerto blabla, para: everyone. 

despues vas al coso que dice EDICION, y le das a "NORMATIVA PARA TRAFICO SALIENTE", y te fijas que tiene que estar en "PERMISIVO POR OMISION, TRAFICO EN LISTA NEGRA".

y listo con el firestater. si usas el transmission, es tipo el azureus, lo abris, vas al boton preferencias, le pones la carpeta, el puerto (EL MISMO QUE ELEGISTE PARA EL FIRESTARTER), y despues le das ok.

Vas al boton añadir, le pones el torrent que queres vos, y te fijas que pasa. si no anda, nos consultas, si te anda josha, nos agradeces XDXD

espero que te haya servido. salu2!!

---

### Post by Hei Ku on 2007-10-19
acordate de aplicar las reglas. Por defecto no te las aplica automaticamente.

---

### Post by faktorqm on 2007-10-22
gracias hei ku!! ^_^

---

