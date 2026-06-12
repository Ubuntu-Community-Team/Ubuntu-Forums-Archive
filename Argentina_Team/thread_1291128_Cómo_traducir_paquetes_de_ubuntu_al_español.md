---
title: "Cómo traducir paquetes de ubuntu al español"
date: 2009-10-14
forum: Argentina Team
---

### Post by faktorqm on 2009-10-14
Hola a todos, voy a transcribir un mail que se mando a una lista de mails que son todos los LoCo's de habla hispana donde se explica como traducir paquetes de ubuntu al castellano, que requisitos son necesarios para ingresar en el spanish translator team (grupo de traductores al español).


El día de hoy durante el Global Bug Jam miembros del Ubuntu Colombian Team (Julian Alarcon y Andres Mujica) darán una introducción/clases de traducción:

    * Configurar su equipo para realizar traducciones (Cuenta en
Launchpad, suscripción a la lista de correo del equipo de traducción
de ubuntu al español, aprobación de licencia de traducciones (BSD).
    * Como hacer traducciones (Familiarizarse con Launchpad, que
traducir, guías de traducción, evitando errores comunes, consejos y
trucos)
    * Evaluar las traducciones prioritarias
    * Usar las traducciones que están siendo realizadas
    * Interactuar en el canal #ubuntu-co y en #ubuntu-classroom-es

Las clases de darán por IRC canal #ubuntu-co-classroom-es en freenode

El log quedo en [http://people.ubuntu.com/~andres.mujica/ugj/Bug-traduccion-es.html](http://people.ubuntu.com/~andres.mujica/ugj/Bug-traduccion-es.html) aunque lo copio aca abajo:

```

Conversation with #ubuntu-classroom-es on sáb 03 oct 2009 16:10:56 COT:
(16:11:51) andresmujica: tyest
(16:12:01) andresmujica: ping darkhole_
(16:12:16) darkhole_: Bueno.. perdon por los problemas tecnicos..
(16:12:19) darkhole_: Comenzamos?
(16:12:30) darkhole_: 1. Introducci?n
(16:12:34) andresmujica left the room (quit: Nick collision from services.).
(16:12:55) ***andresmujica just killed it's ghost
(16:13:11) darkhole_: Para empezar, bienvenidos a esta jornada de Ubuntu Global Jam
(16:13:23) Amaeth1 [n=dfoxpro@186.80.65.181] entered the room.
(16:13:33) ***andresmujica /msg NickServ kill nick_viejo
(16:13:35) lordj left the room (quit: "Page closed").
(16:13:44) ***andresmujica perdon ghost.. no kill .. no interrumpo mas
(16:13:45) darkhole_: De parte del los traductores de Ubuntu al Espa?ol les damos una bienvenida y esperamos aportemos mucho a este proceso..
(16:14:11) darkhole_: Bueno, como empezamos, personalmente "No todo el mundo tiene porque saber Ingles"
(16:14:19) ariasfonseca [n=ariasfon@186.80.65.181] entered the room.
(16:14:20) IngForigua left the room (quit: Read error: 113 (No route to host)).
(16:14:24) czam left the room (quit: Read error: 113 (No route to host)).
(16:14:42) hollman_ is now known as hollman
(16:14:46) darkhole_: El Ingl?s es una barrera muy grande para muchas personas, y mucho m?s hablando de Programas e Inform?tica (que ya de por si es una barrera en estos d?as.)
(16:14:50) czam1 is now known as czam
(16:15:42) IngForigua [n=diego@186.80.65.181] entered the room.
(16:16:32) darkhole_: Por esta raz?n las traducciones de Ubuntu es una parte muy importante de Ubuntu.
(16:16:42) darkhole_: (Valga la redundancia)
(16:17:14) darkhole_: (Por cuestiones tecnicas no usar? acentos, cosa que siempre se debe usar en las traducciones ;) )
(16:17:20) IngForigua: Vuelva a comenzar!!!!
(16:17:46) Amaeth left the room (quit: Read error: 113 (No route to host)).
(16:18:03) Amaeth1 left the room (quit: Client Quit).
(16:18:21) Amaeth [n=dfoxpro@186.80.65.181] entered the room.
(16:18:24) darkhole_: la traduccion de Ubuntu ha empezado desde hace varios a?os y en estos momentos la traduccion a Espa?ol es la mas completa de todas ;)
(16:19:02) darkhole_: En este momento el equipo de Traduccion al Espa?ol es el que menos frases por traducir tiene, gracias a todos los aportes de las personas que han ayudado.
(16:19:12) darkhole_: Sin embargo, a?n faltan muchas cosas para traducir...
(16:19:29) darkhole_: Adem?s, en cada versi?n de ubuntu salen nuevas aplicaciones para traducir... 
(16:19:53) darkhole_: Por esto siempre es bueno contar con un numero de traductores y de traduccion constante...
(16:20:07) darkhole_: Bueno.. pasemos al segundo punto..
(16:20:08) IngForigua left the room (quit: Read error: 104 (Connection reset by peer)).
(16:20:10) darkhole_: 2. Formas de traducir
(16:20:35) darkhole_: Actualmente hay dos formas de traducci?n de las aplicaciones de Ubuntu.
(16:20:40) darkhole_: En Linea (Online)
(16:20:49) darkhole_: O fuera de linea (Offline)
(16:20:54) darkhole_: Cual es la diferencia??
(16:21:16) darkhole_: Bueno, ya es cuesti?n de como nos guste trabajar.. actualmente existen programas que ayudan en las traducciones de algunas aplicaciones
(16:21:50) darkhole_: Para GNOME, KDE o para Windows.
(16:22:02) IngForigua [n=diego@186.80.65.181] entered the room.
(16:22:06) darkhole_: U otras plataformas
(16:22:12) darkhole_: a. Offline
(16:22:42) darkhole_: las traducciones Offline son ?tiles cuando no contamos con conexion a internet, o cuando queremos hacer traducciones masivas (batch)
(16:23:31) tatica1 left the room (quit: Read error: 110 (Connection timed out)).
(16:23:49) darkhole_: Existen varios programa... pero la idea principal es contar con el archivo .PO
(16:24:00) darkhole_: Y abrir este archivo en un editor de traducciones
(16:25:47) czam: osea yo descargo un .PO y despues que hago para traducir?
(16:26:30) darkhole_: Es posible usando Launchpad... sin embargo... personalmente no lo uso mucho
(16:27:04) darkhole_: Es cuestion de gustos, sin embargo, y para empezar, nos embarcaremos en la traducci?n en Linea.
(16:27:16) darkhole_: Si quieren un poco mas de informaci?n de las traducciones Offline, http://es.wikipedia.org/wiki/Gettext
(16:27:25) darkhole_: b. Online
(16:27:58) darkhole_: Ahora, si vamos a lo que nos interesa ;)
(16:28:08) darkhole_: Launchpad es una plataforma por la que actualmente se realiza el reporte de bugs, traduccion, soporte, desarrollo de Ubuntu.
(16:28:15) darkhole_: https://launchpad.net/
(16:29:08) monkey: vas ha explicar que son las traducciones batch?
(16:29:21) IngForigua: darkhole_ cuando yo trabajo offline, donde subo el PO modificado
(16:29:34) darkhole_: Launchpad cuenta con un sistema de traducci?n en linea muy eficiente y sencillo, que ha permitido acercar esta tarea a muchas personas.. y de forma ocacional..
(16:29:53) IngForigua: Y si cuando lo descargue habian items sin traducir que pasa queda doble sugerencia de traduccion
(16:30:06) IngForigua: ???
(16:30:12) IngForigua: no se si me entendio?
(16:30:33) darkhole_: IngForigua: Mm, en Launchpad... para preguntas acerca de esta tem?tica y de otras que por tiempo no veremos hoy existen espacios disponibles..
(16:31:19) IngForigua: :P
(16:31:23) darkhole_: Entonces..
(16:32:27) darkhole_: El sistema de traducciones de Launchpad se llama Rosseta (un poquito de historia: http://es.wikipedia.org/wiki/Piedra_de_Rosetta)
(16:33:14) darkhole_: Para traducir en launchpad, desde la pagina, tenemos unos peque?os requisitos.
(16:33:24) darkhole_: Que nos lleva al tercer punto:
(16:33:26) darkhole_: 3. Prerequisitos iniciales
(16:33:43) darkhole_: para traducir en Launchpad es, logicamente, necesario contar con una cuenta en launchpad.
(16:35:01) darkhole_: Y.. no hay m?s prerequisitos ;)
(16:35:18) darkhole_: Esa es la facilidad de Launchpad y su sistema de traducciones
(16:35:29) darkhole_: (Si tienen preguntas, no duden en hacerlas ;) )
(16:35:37) IngForigua: Pregunta, como hace parte del equipo de traductores
(16:35:58) IngForigua: y como puedo revisar traducciones o debo ser parte del equipo
(16:36:22) darkhole_: Por que es tan sencillo empezar a traducir en Launchpad??? bueno, en realidad en la mayor?a de los casos, cuando uno traduce, lo que hace es SUGERIR traducciones
(16:36:51) darkhole_: IngForigua: Ese es el septimo punto :)
(16:37:20) darkhole_: IngForigua: Ese es el septimo punto :)
(16:37:59) darkhole_: Como funciona Launchpad... (si nos damos cuenta, nunca he dicho traducir en ubuntu)...
(16:38:01) czam: cuando uno ve las traducciones y hay varias sugerencias, hace alguna diferencia si nosoros elegimos una de esas?
(16:38:13) darkhole_: Launchpad es usado por otros proyectos aparte de Ubuntu
(16:38:21) czam: influye nuestra eleccion en la seleccion de la sugerencia final?
(16:38:56) ariasfonseca left the room (quit: Read error: 104 (Connection reset by peer)).
(16:39:03) viperhoot left the room (quit: "Saliendo").
(16:39:35) darkhole_: czam, si solo sugieres traducciones, estas no quedan en el paquete, decidir que traducci?n es la que "queda" es una tarea de los traductores oficiales
(16:41:42) darkhole_: En Launchpad, algunos proyectos tienen las traducciones abiertas, donde no hay sugerencias, y cada vez que alguien traduce esa es la que queda.. pero unos proyectos con traducciones restringidas (como ubuntu) en donde la mayor?a de personas SUGIERE traducciones... y un peque?o grupo las aprueba.
(16:42:00) darkhole_: Este grupo peque?o, es el Ubuntu Spanish Translators Team
(16:42:19) darkhole_: https://launchpad.net/~ubuntu-l10n-es/+members
(16:43:27) darkhole_: Actualmente somos 14 personas a nivel mundial de varias partes... pero estamos recibiendo nueva gente ;) De eso hablaremos en el 7| punto
(16:44:05) darkhole_: Bueno, como tener una cuenta de Launchpad es el unico requisito para traducir Ubuntu, vamos al siguiente.
(16:44:15) darkhole_: 4. Recomendaciones iniciales
(16:44:26) sergioandresmene [i=be9e3ca7@gateway/web/freenode/x-a9bb3333dbe1e4f6] entered the room.
(16:44:36) darkhole_: Para el equipo de traductores de Ubuntu al Espa?ol es mas importante la calidad que la cantidad.
(16:44:59) darkhole_: Por esta raz?n es importante contar con una gu?a de traducci?n.
(16:45:50) darkhole_: En este v?nculo encuentran bastantes referencias/ guias que sirven para realizar traducciones de calidad.
(16:45:51) darkhole_: https://wiki.ubuntu.com/UbuntuSpanishTranslators#Documentos%20de%20referencia
(16:46:18) darkhole_: El principal y primero que debemos leer, es este: https://wiki.ubuntu.com/UbuntuSpanishTranslators/Estilo
(16:47:00) ariasfonseca [n=ariasfon@186.80.65.181] entered the room.
(16:48:17) darkhole_: Bueno, esa seria la primera recomendaci?n, leer las guias
(16:48:31) darkhole_: La segunda recomendacion, traducir al Espa?ol
(16:48:37) darkhole_: ?? Como as????
(16:48:53) darkhole_: Loq ue sucede es que actualmente existen varias variaciones del Espa?ol
(16:48:57) darkhole_: Espa?ol-Colombia
(16:49:01) darkhole_: Espa?ol-Espa?a
(16:49:07) darkhole_: Espa?ol-Argentina, etc..
(16:49:15) IngForigua: Buen punto darkhole_
(16:49:46) darkhole_: En una decisi?n de colaboraci?n de los miembros de Ubuntu en paises de habla hispana se decidio SOLO traducir la plantilla "Espa?ol"
(16:50:02) darkhole_: La gen?rica.. As? mismo realizar traducciones sin regionalismos.
(16:51:15) IngForigua: Entonces el equipo de traduccion se ponen deacuerdo en la sintaxis
(16:51:31) IngForigua: porque no falta el que diga regionalismos
(16:51:43) darkhole_: Aja..
(16:51:57) IngForigua: Y ademas el equipo de traduccion me imagino que no todos don de una zonma
(16:52:03) darkhole_: La lista de discusi?n muchas veces parece solo de Flames, jeje...
(16:52:14) sergioandresmene: jaja
(16:52:33) IngForigua: (berian ser todos rolos)
(16:52:44) darkhole_: Pero, en pro de una buena calidad y de neutralidad siempre es bueno estas discusiones, que estan abiertas a todas las personas que esten inscritas en la lista de traduccion, sin necesidad de se miembros oficiales.
(16:53:48) darkhole_: Eso con respecto al idioma a traducir.
(16:54:00) darkhole_: Una tercera recomendaci?n.
(16:54:52) IngForigua: Y las traducciones que se hacen en LP, las puede usar cierto proyecto
(16:54:52) darkhole_: Activar la correccion ortogr?fica en ubuntu
(16:55:20) darkhole_: Para traducir en launchpad, se debe aprobar la licencia de traducci?n, que es BSD.
(16:56:25) darkhole_: Esta licencia permite que puedan ser usadas por cualquier proyecto.
(16:56:52) darkhole_: La correcci?n ortogr?fica es una herramienta muy muy MUY util.
(16:57:12) darkhole_: Muchas veces cometemos errores muy simples.. pero que hacen que las traducciones no puedan ser aprobadas
(16:57:34) czam: osea si yo tengo mi proyecto de software libre en ingles, puedo integrarme a launchpad para que me ayuden con la traduccion?
(16:58:48) andresmujica: ping darkhole_
(16:59:10) ariasfonseca: pong darkhole_
(16:59:15) darkhole_: 4? recomendaci?n, usar herramientas de traducci?n.
(16:59:16) darkhole_: https://addons.mozilla.org/en-US/firefox/addon/5641
(16:59:16) darkhole_: https://addons.mozilla.org/en-US/firefox/addon/5641
(16:59:18) darkhole_: http://addons.mozilla.org/en-US/firefox/addon/5641
(16:59:20) darkhole_: https://addons.mozilla.org/en-US/firefox/addon/5641
(16:59:22) darkhole_: ?
(16:59:22) Petrux left the room (quit: Read error: 104 (Connection reset by peer)).
(16:59:28) darkhole_: https://addons.mozilla.org/en-US/firefox/addon/5641
(16:59:31) darkhole_: Perdon, por los problemas tecnicos
(16:59:44) darkhole_: La direcci?n es una extension para Firefox
(16:59:56) darkhole_: Si quieren instalenla y reinicien Firefox
(17:00:29) darkhole_: Les permite seleccionar cualquier palabra y aparecer? un recuadro peque?o, puede utilizar varios motores detraducci?n, pero les recomiendo el de babilon o el de Google
(17:01:38) darkhole_: Aparte de esta herramienta..
(17:01:48) darkhole_: Siempre es bueno consultar http://www.wordreference.com/es/index.htm
(17:01:51) sergioandresmene left the room (quit: "Page closed").
(17:02:11) sergiomeneses [i=be9e3ca7@gateway/web/freenode/x-5608626a496c0348] entered the room.
(17:02:25) darkhole_: Wordreference sirve muchisimo para consultar.. Es como un wikipedia solo para traducciones.
(17:03:19) darkhole_: Y la 5? recomendacion, de las que me acuerde, :)
(17:03:23) darkhole_: No traducir todo!!..
(17:04:11) darkhole_: Algunas palabras son reservadas. Por ejemplo, en traducciones de KDE las palabras que entre < y > NO se traducen
(17:04:11) IngForigua: Como asi?
(17:04:24) darkhole_: Por ejemplo <Menu>
(17:04:40) darkhole_: <Icon> </Icon>
(17:04:48) darkhole_: Ese tipo de palabras no se traducen...
(17:04:59) darkhole_: Es importante no traducir por traducir.. sino revisar el contexto... 
(17:05:18) darkhole_: Es bueno saber al menos de que se trata el pauqte que estan traduciendo. Si es de audio, de programaci?n, etc.
(17:05:40) darkhole_: Bueno, vamos al punto bueno :)
(17:05:41) darkhole_: 5. Traduciendo en Launchpad
(17:05:50) darkhole_: Ahora.. traducir Ubuntu en Launchpad.
(17:06:16) darkhole_: Las traducciones de Ubuntu estan divididas por versiones y por paquetes.
(17:07:02) IngForigua: Una pregunta en LP solo estan los paquetes que soporta canonical, no?
(17:07:04) darkhole_: Si uno quiere traducir Ubuntu debe primero seleccionar la version.
(17:07:21) darkhole_: Es preferible traducir la ?ltima versi?n. En este caso seria karmic
(17:07:34) sergiomeneses left the room (quit: "Page closed").
(17:07:55) artopal [n=rafo@f053230008.adsl.alicedsl.de] entered the room.
(17:08:39) darkhole_: Y despues uno puede seleccionar un paquete
(17:08:39) darkhole_: En esta pagina podemos ver las traduccione de karmic:
(17:08:39) darkhole_: https://translations.edge.launchpad.net/ubuntu/
(17:08:39) darkhole_: Pero abajo encontramos los v?nculos a otras versiones anteriores
(17:08:39) darkhole_: Si vemos, hay un monton de paquetes a traducir
(17:08:39) darkhole_: Perdon... idiomas
(17:08:40) darkhole_: idiomas a traducir
(17:09:14) darkhole_: la interfaz de Launchpad permite organizar por numero de traducciones completadas. Simplemente hagamos clic en Status
(17:09:34) darkhole_: Se organizar? seg?n los idiomas m?s traducidos
(17:09:41) darkhole_: Y de primero esta Espa?ol :)
(17:10:10) monkey left the room (quit: Ping timeout: 180 seconds).
(17:10:14) darkhole_: Ahora hagamos clic en Espa?ol, llegaremos a esta pagina: https://translations.launchpad.net/ubuntu/karmic/+lang/es
(17:10:27) darkhole_: Ahora si veremos las traducciones por paquete.
(17:10:40) czam: si no se traduce completamente a un idioma, entonces que pasa, igual se publica la version con ese idioma cono lo que se tradujo?
(17:10:54) darkhole_: En Launchpad existe un orden, por el cual los paquetes que estan en la primera pagina son los prioritarios para traducir, por la importancia que estos tienen.
(17:11:24) darkhole_: Como vemos, al principio esta el programa de instalaci?n de Ubuntu (ubiquity)
(17:13:53) darkhole_: En Template Name esta el nombre del paquete.
(17:14:36) darkhole_: en Length esta el numero de frases en el paquete (muy distinto al tama?o real de las frases, alguans veces, una frase puede ser muy grande o muy peque?a)
(17:14:46) darkhole_: En Status est? el estado del paquete
(17:15:05) darkhole_: Que significan los colores???
(17:15:11) darkhole_: Verde: Traducciones ya realizadas
(17:15:16) darkhole_: y aprobadas.
(17:15:44) darkhole_: Azul: Con cambios (cuando la traducci?n ya se realiz? pero es distinta a la que estaba en la anterior version de Ubuntu)
(17:16:14) darkhole_: Morado: Frases nuevas que ya estan traducidas, pero que no existian en la anterior version.
(17:16:22) darkhole_: Y, el querido Rojo: Frases sin traducir
(17:16:42) darkhole_: Si nos damos cuenta la mayor?a de programas ya est?n traducidos
(17:17:05) darkhole_: La columna Untranslated es el numero de frases sin traducir
(17:17:35) darkhole_: Need review: Es el numero de traaducciones que, aunque ya han sido traducidas, tienen nuevas sugerencias de traducci?n.
(17:17:59) darkhole_: Changed: Es el numero de los cambios realizados.
(17:18:05) darkhole_: Last Edited: la ?ltima vez que alguien realiz? una traducci?n
(17:18:22) darkhole_: By: Indica quien fue la ULTIMA persona que realizo la traducci?n.
(17:18:40) darkhole_: Descansemos un poquito.. tienen alguna pregunta hasta ahora..?
(17:19:05) SergioMeneses [n=sergio@190.158.60.167] entered the room.
(17:20:03) IngForigua: No por ahora no
(17:20:11) darkhole_: Bueno, entonces, sigamos..
(17:20:14) IngForigua: o depronto si
(17:20:49) IngForigua: Si alguna sugerencia queda mal, y se fue en la version del paquete que se puede hacer
(17:22:06) darkhole_: Mm, informar a la lista/reportar un error que explique cual es la traducci?n As? podremos traducirla rapido y esperar a que se empaquetada.
(17:22:16) darkhole_: Ahora, vamos a buscar frases para traducir... Si nos damos cuenta esta como dificil
(17:22:29) IngForigua: Darkhole_ no se si es ot
(17:22:30) darkhole_: Pero, si avanzamos un poco con el vinculo de Next.
(17:22:55) darkhole_: https://translations.edge.launchpad.net/ubuntu/karmic/+lang/es/+index?start=1000&batch=50
(17:23:26) darkhole_: Existe un paquete, tuxmath
(17:23:42) darkhole_: Hay 10 para traducir!!!
(17:23:45) darkhole_: hagamosle..
(17:25:12) SergioMeneses: pregunta por una licencia... le damos ok?
(17:25:26) darkhole_: Si seleccionamos el numero 10 de tuxmath, veremos que nos lleva a una pagina en la que solo estan las frases sin traducir
(17:25:52) darkhole_: https://translations.launchpad.net/ubuntu/karmic/+source/tuxmath/+pots/tuxmath/es/+translate?show=untranslated
(17:27:09) darkhole_: Ahh, si, para traducir es necesario aprobar la licencia BSD.
(17:27:09) SergioMeneses: ok... una vez ubicado un texto q hacemos?
(17:27:49) darkhole_: 49. to split it. Destroy fractions that can not be further simplified in a single shot!
(17:27:52) darkhole_: Buena frase..
(17:28:23) darkhole_: En el cuadro de New Translation: COloquemos la traducci?n que creamos.
(17:28:29) SergioMeneses: ya traduje uno... =)
(17:28:40) darkhole_: En este momento estar?mos haciendo sugerencias, y estas sugerencias no ser?n aprobadas
(17:28:54) SergioMeneses: asi darkhole_ https://translations.launchpad.net/ubuntu/karmic/+source/tuxmath/+pots/tuxmath/es/39/+translate
(17:30:11) darkhole_: Gracias SergioMeneses
(17:30:29) SergioMeneses: darkhole_, asi esta bien???
(17:30:46) darkhole_: Para ver solo una frase de traducci?n, a la izquierda de las frases hay un icono de Lupa, al hacer clic en el solo veremos la traduccion.
(17:33:20) darkhole_: No se preocupen si tienen errores en las traducciones o no estan seguros, grabenlas... tal vez alguien sepa como traducir partes de la frase..
(17:33:30) darkhole_: As? alguien podr? sugerir toda la traducci?n.
(17:34:35) darkhole_: Puede que parezca que algunas frases ya estan traducidas pero no loe stan.. Solo son sugerencias
(17:34:50) darkhole_: Es facil saber si no estan traducidas si leemos: (no translation yet) 
(17:35:39) trinium [n=TriniuM@201.230.185.221] entered the room.
(17:36:27) trinium left the room (quit: "Saliendo").
(17:36:43) SergioMeneses: darkhole_, y hasta cuando se corriguen traducciones??
(17:37:14) darkhole_: En Suggestions: estan las sugerencias de todos
(17:37:19) darkhole_: Ahora, aprrovemos algunas :)
(17:39:36) darkhole_: Si les gusto lo del karma...
(17:40:01) darkhole_: Si un traductor oficial aprueba su sugerencia sin hacer cambios, el karma principalmente ser? de quien hace la sugerencia, y muy poco para el que lo aprueba
(13:51:52) darkhole: Buenas tardes..
(13:52:06) darkhole: En unos minutos comenzaremos la segunda parte del taller de traducci?n.
(13:54:14) darkhole ha salido de la sala ("Saliendo").
(13:55:42) darkhole [n=darkhole@190.27.55.241] ha entrado en la sala.
(13:56:36) Amaeth ha salido de la sala (quit: "Leaving.").
(13:58:01) SergioMeneses [n=sergio@190.240.60.64] ha entrado en la sala.
(13:58:27) darkhole: Buenas SergioMeneses 
(13:58:37) SergioMeneses: q mas don darkhole 
(13:58:39) SergioMeneses: como vamos?
(13:58:55) darkhole: Bien bien..
(13:59:03) darkhole: Se ven las tildes? á
(13:59:35) SergioMeneses: si
(13:59:42) SergioMeneses: ?
(13:59:45) SergioMeneses: ud la ve?
(13:59:58) darkhole: Sip ;)
(14:01:24) czam: si
(14:01:45) darkhole: Bueno..
(14:02:43) darkhole: Si es el caso, empezaré con lo que falto ayer..
(14:03:01) darkhole: COmo ya vimos, realizar traducciones es muy sencillo.
(14:03:15) darkhole: Y además la colaboración de toda la comunidad es importante.
(14:03:32) darkhole: Ej. Ayer TuxMath tenia 10 traducciones sin realizar, sin embargo hoy ya solo que da una ;)
(14:03:43) darkhole: https://translations.launchpad.net/ubuntu/karmic/+source/tuxmath/+pots/tuxmath/es/+translate?show=untranslated
(14:04:24) darkhole: Ya habiendo traducido algo, solo queda esperar que sea aprovada la traducción.
(14:04:54) darkhole: Se puede tener una idea de cuando le son aprobadas a uno las traducciones desde la página del karma de cada uno.
(14:05:13) darkhole: https://launchpad.net/people/+me/+karma
(14:06:14) SergioMeneses: jaja yo aparezco como traductor =)
(14:06:20) darkhole: Además, es posible ver todas las traducciones realizadas por uno desde este vínculo:
(14:06:20) darkhole: https://translations.edge.launchpad.net/people/+me/+activity
(14:08:18) darkhole: Si seleccionamos cualquiera de los paquetes que aparecen listados, podremos ver con detalle cuales son las traducciones que han sido aprobadas (en negrita), cuales son las que aún están por revisión (en color negro sencillo) o las traducciones que se consideraron que no eran apropiadas y que se tradujeron con otra sugerencia (en gris)
(14:08:29) darkhole: Aja :)
(14:09:17) darkhole: Es el crédito que uno recibe. Cuando salga karmic Koala y veas los créditos de los traductores, si ayudaste a realizar la traducción aparecerá tu nombre ysus direcciones en Launchpad
(14:09:56) darkhole: Con esto terminamos el 5° punto, traduciendo Ubuntu en Launchpad
(14:10:07) darkhole: Ahora, vamos para el 6° punto.
(14:10:12) darkhole: 6. Consejos y trucos
(14:10:33) SergioMeneses: darkhole, una pregunta antes
(14:10:49) darkhole: Como vimos, el traducir es muy sencillo, pero, para poder participar y colaborar con mayor calidad y eficiencia siempre hay uos peqeños trucos..
(14:10:57) SergioMeneses: d donde ve ud el listado d paquetes en negrita por ejemplo?
(14:11:02) Andphe [n=Andphe@186.81.5.42] ha entrado en la sala.
(14:11:38) darkhole: SergioMeneses: Mm, son frases que estan en negrita, no paquetes.. 
(14:11:58) SergioMeneses: aaa ok
(14:12:01) SergioMeneses: thank's
(14:12:15) darkhole: En https://translations.edge.launchpad.net/people/+me/+activity estan los pauqtes, si seleccionamos cualquiera de ellos, veremos algunas frases en negro, en negrita y en gris
(14:13:13) darkhole: En la interfaz web de traducción de un paquete cualquiera. Por ejemplo: https://translations.launchpad.net/ubuntu/karmic/+source/xubuntu-docs/+pots/basic-commands/es/+translate
(14:13:29) darkhole: Veremos que hay un máximo de frases por página, en este caso es de 10.
(14:13:40) SergioMeneses: darkhole, por ejemplo esta https://translations.edge.launchpad.net/ubuntu/jaunty/+source/installation-guide/+pots/gpl/es/+filter?person=sergiomeneses
(14:13:48) SergioMeneses: esta en negrita la primera
(14:14:48) darkhole: Exacto, en este caso esa traducción ha sido aprobada
(14:14:58) darkhole: Pero, las que estan en gris no...
(14:15:05) SergioMeneses: ok
(14:15:28) darkhole: Si deseamos traducir más frases sin estar perdiendo tiempo seleccionando en todo momento Save & Continue
(14:16:05) darkhole: Podemos agregar unos cuantos datos adicionales al final de la direccion
(14:16:37) darkhole: ?start=0&batch=50
(14:16:44) darkhole: Quedando de esta forma
(14:16:53) darkhole: https://translations.launchpad.net/ubuntu/karmic/+source/xubuntu-docs/+pots/basic-commands/es/+translate?start=10&batch=50
(14:17:04) darkhole: Esto nos mostrará una lista más larga de traducción.
(14:17:25) darkhole: Esto mismo tambien aplica en la lista de paquetes.
(14:17:41) darkhole: https://translations.launchpad.net/ubuntu/karmic/+lang/es/+index
(14:18:08) darkhole: El numero de paquetes es de 50, pero podemos aumentarlo a 300, que nos permite ver mejor que paquetes estan sin traducir
(14:18:38) darkhole: https://translations.launchpad.net/ubuntu/karmic/+lang/es/+index?start=0&batch=300
(14:18:53) darkhole: Así podemos ver más paquetes por pagina y rapidamente ver los que estan sin traducir.
(14:19:32) darkhole: Otro consejo es.... Primero traducir los paquetes que estan en la primera página, debido a que Launchpad organiza los pauqtes segun su importancia.
(14:19:59) darkhole: Aunque, como vemos en este caso todos los pauqtes estan sin traducir, otra pequeña ayuda a laa hora de ver que falta es empezar de atras para adelante..
(14:20:31) darkhole: Normalmente las personas a la hora de traducir no miran los ultimos paquetes.
(14:20:45) darkhole: https://translations.launchpad.net/ubuntu/karmic/+lang/es/+index?start=1500&batch=300
(14:21:05) darkhole: Aquí ya vemos que hay varios paquetes sin traducir
(14:22:01) darkhole: Bueno, ahora, siguiendo por el lado de los consejos..
(14:22:10) darkhole: Siempre es bueno fijarse en las pequeñas cosas... 
(14:22:30) darkhole: Si existe un punto al final de una traducción este se debe dejar.
(14:23:04) darkhole: Es necesario realizar este tipo de cosas, debido a que muchas veces, por un punto que faltó, por una tilde que no se colocó o por otra razón trivial, las traducciones no son aprovadas
(14:23:13) darkhole: *aprobadas
(14:23:35) czam: Pueden invalidar una traducción por una tilde?
(14:23:58) darkhole: Mas que invalidar, es no aprobarla. Y si, perfectamente. COmo mencioné ha ocurrido muchisimas veces.
(14:24:28) darkhole: Me ha tocado corregir una tilde, o el punto final de la frase que no estaba, y en este caso el crédito va para la persona que realiza la sugerencia correcta.
(14:25:10) darkhole: Otro útil consejo es ser neutral con las traducciones no usar regionalismos y señirse mucho a lo que ha sido aprobado por la RAE
(14:26:05) darkhole: Siempre que duden, consulten el diccionario: http://www.rae.es/rae.html
(14:26:45) darkhole: Algo muy importante, y ara terminar la parte de consejos.. siempre es bueno establecer el contexto de la traducción.
(14:27:20) darkhole: Muchos de estos consejos estan en la documentación de los traductores.
(14:28:12) darkhole: Bueno, ahroa, para terminar, vamos con el 7° y último punto, como convertirse en traductor oficial.
(14:28:28) darkhole: En la sección del wiki: https://wiki.ubuntu.com/UbuntuSpanishTranslators#C%C3%B3mo%20participar
(14:28:40) darkhole: Vemos cuales son los apsos necesarios para ser un miembro oficial.
(14:29:24) darkhole: Al ser miembro del equipo de traductores, las traducciones que realicemos no pasarán por revisión, sino que serán aplicadas de forma instantánea.. 
(14:29:39) darkhole: Además, tendremos la oportunidad de aprobar traducciones realizadas por otras personas.
(14:29:54) darkhole: Si vemos los requisitos, no son muchos. 
(14:29:59) darkhole: * Tener cuenta en Launchpad
(14:30:06) darkhole: * Haber traducido en el ultimo mes
(14:31:09) darkhole: * Realizar traducciones numerosas (o es necesario haber realizado muchisimas traducciones, pero si es importante haber realizado un poco más de 100 traducciones APROBADAS)
(14:31:40) darkhole: * Realizar traducciones de buena calidad (si han sido aprobadas, significa que son consideradas de buena calidad)
(14:32:05) darkhole: * Y presentarse en l alista de correo de los traductores.
(14:32:40) darkhole: La membresía tiene una duración de un año, y si se quiere renovar se debe enviar un correo a la lista con esta petición.
(14:32:54) darkhole: Como vemos, hay varias formas de perder la membresía
(14:33:34) darkhole: Bueno, eso sería todo.
(14:33:40) darkhole: No se si tengan alguna pregunta.
(14:33:52) darkhole: .....
(14:34:20) czam: Cual es el plugin para mozilla?
(14:34:32) darkhole: Mm, QTL
(14:34:35) SergioMeneses: vale... osea q toca traducir muy seguido para lograr ser aprovado??'
(14:34:38) darkhole: https://addons.mozilla.org/en-US/firefox/addon/5641
(14:35:08) darkhole: Es muy útil, aunque hay otras herramientas, pero de forma personal, es el menos intrusivo y completo que conozco, a menos que tengan alguna otra sugerencia ;)
(14:35:47) darkhole: Mm, traducir en el ultimo mestraducir, hacerlo bien y hacerlo de forma regular
(14:35:52) darkhole: Eses es el secreto.
(14:36:17) darkhole: Y la mayoría de las ocaciones por las cuales las solicitudes son rechazadas es por la 2° razón, la calidad de las traducciones
(14:37:06) darkhole: Como les mencioné, el equipo considera más importante la calidad que la cantidad.
(14:36:34) SergioMeneses: perfecto
(14:36:36) SergioMeneses: =)
(14:37:06) darkhole: Como les mencioné, el equipo considera más importante la calidad que la cantidad.
(14:37:58) darkhole: Bueno, si no hay más preguntas, es un placer haber colaborado en esta sesión del Ubuntu Global Jam, espero que ya hayan realizado algunas traducciones en el día de hoy, yo personalmente voy a traducir bastante este día... Y ojalá pueda aprobar muchas de sus traducciones
(14:38:16) czam: Que bueno saber esto, yo me postule hace como 2 semanas atras, pero creo que todavia me falta, fue algo muy apresurado.
(14:38:22) darkhole: Muchas gracias.. Y espero haber aportado en algo..

```

A mi me re sirvio aprender como se hacia, por que nadie me habia explicado antes y yo no ahbia preguntado. La cosa es que me puse en la lista de los traductores y empece a traducir paquetes en launchpad. es sumamente facil cuando tenes semejante explicacion.

Desde ya muchas gracias a los ubunteros colombianos que se pusieron a explicar esto por IRC. 

Si tienen preguntas, pregunten :) Salu2!!!

---

