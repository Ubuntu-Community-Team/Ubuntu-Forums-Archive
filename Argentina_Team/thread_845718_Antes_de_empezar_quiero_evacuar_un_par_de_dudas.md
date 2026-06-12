---
title: "Antes de empezar quiero evacuar un par de dudas"
date: 2008-06-30
forum: Argentina Team
---

### Post by granjero on 2008-06-30
buenas, mi nombre es juan, soy de bs as...

les cuento, mi pc es una amd duron de 850mhz con 256 de ram. no se que mother tengo. tambien tengo en la pc una placa de video nvidia mx6400 y una placa de sonido crestive 5.1

el otro dia me baje el ubuntu de escritorio y lo corri desde el cd para ver que onda y me gusto y tengo ganas de instalarlo sin borrar el windows 2000 todavia...

empiezo con las preguntas:

1- ¿como se instalan drivers de los componentes de hardware? ya sea placa de video y de audio. Porque yo tengo hecho un cableado en casa desde la pc hasta la tele y tengo configurada la placa con "dual monitor" o algo asi, o sea tengo el lado derecho del monitor extendido a la tele configurada la segunda pantalla en 640*480 para ver pelis desde la pc.
cuando corri el ubuntu desde el cd no me reconocio esa configuracion y queria saber si era posible...

2- no me quedo del todo claro si ya esta solucionado el tema de los formatos de disco rigido. tengo 2 discos rigidos. 1 de 80gb partido en 2 y otro de 20gb que uso como destino de descargas. todas la particiones etsan formateadas en NTFS. deberia pasarlas a FAT32? ¿o ya no hay drama con eso?

3- ¿que onda ubuntu y los juegos?

muchas gracias de antemano!

salud!


\\:D/\\:D/\\:D/

---

### Post by tzulberti on 2008-06-30
Vamos por partes como dijo Jack

1) Salvo para la placa de video todos los "drivers" se instalan automaticamente. Es decir, cuadno vos pones el cd y ves el escritorio de ubuntu asi te va a quedar la pc cuando lo instales. Sin embargo, el driver para la placa de video nvidia que se instala por default no trae acelearcion OpenGL, por lo que no vas poder ir lejos en el tema de juegos. Por lo tanto te recomiendo instalar los drivers de Nvidia que se puede hacer haciendo un par de clics: System -> Administration -> Restricted Drivers

2) No creo que haya problemas en el tema con NTFS pero tampoco soy un gran usuario de Windows, asique estaria mejor que alguien te responda.

3) Hay varios juegos libres que la rompen, y si aun sos adicto a los juegos de Windows, podes usar el Wine para correrlos desde Windows.

---

### Post by anka on 2008-07-01
Por cuestiones laborales (para probar programas) y de estudio debo mantener una particion con win nativo, asi que puedo ampliarte la respuesta del compañero:

2) No hay dramas en cuanto a particiones NTFS, hasta 7.04 creo que podias leer pero no escribir de forma predeterminada, necesitabas instalar algo. A partir de 7.10 ya se puede hacer de una, no hay dramas.

Suerte!

---

### Post by valucha on 2008-07-01
> **granjero said:**
> 
1- ¿como se instalan drivers de los componentes de hardware? ya sea placa de video y de audio. Porque yo tengo hecho un cableado en casa desde la pc hasta la tele y tengo configurada la placa con "dual monitor" o algo asi, o sea tengo el lado derecho del monitor extendido a la tele configurada la segunda pantalla en 640*480 para ver pelis desde la pc.
cuando corri el ubuntu desde el cd no me reconocio esa configuracion y queria saber si era posible...



[COLOR="DarkOrchid"]Como te dijeron antes, los drivers se instalan todo por defecto. Si tenés la suerte de que las marcas de tus componentes hayan liberado los drivers, todo funciona perfectamente. Pero, por ejemplo, sé que los componentes Nvidia con el driver que te instala Ubuntu por defecto podés hacer todo,pero no tenés la aceleración gráfica. Es decir, no es que no vas a ver nada o no va a funcionar, simplemente va a faltar instalar el drivar que da Nvidia (se instala fácil como dijo Tzulberti) y listo.

Para tener dual monitor,o como tenés vos con la tele, existen millones de tutoriales en internet: [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) , [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174) , [http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html](http://useopensource.blogspot.com/2007/06/gui-to-configure-dual-monitors-nvidia.html), etc, Así que no te preocupes, además según tengo entendido, Nvidia tiene un panel de control en el que podrías configurarlo gráficamente sin problemas.[/COLOR]






> **granjero said:**
> 

2- no me quedo del todo claro si ya esta solucionado el tema de los formatos de disco rigido. tengo 2 discos rigidos. 1 de 80gb partido en 2 y otro de 20gb que uso como destino de descargas. todas la particiones etsan formateadas en NTFS. deberia pasarlas a FAT32? ¿o ya no hay drama con eso?

[COLOR="DarkOrchid"]Yo tengo 3 prticiones, una con Windows en NTFS, y dos de linux en EXT3, una para los "programas" ("/"), y otra para mis archivos y mi configuración ("/home").
En linux podés montar, leer y escribir perfectamente en la partición de Windos.
En Windows tenés que instalar el Ext2fsb para poder hacerlo andar y leer las particiones de Linux.

Imaginate que yo comparto "Mis documentos" en Windows, con mi "Home" en Linux, es decir que es la misma partición y la misma carpeta, y funciona todo bien tanto en Linux como en Windows, y puedo formatiar sin problema las otra sparticiones sin perder ningúin dato mio.[/COLOR]




> **granjero said:**
> 
3- ¿que onda ubuntu y los juegos?

muchas gracias de antemano!

salud!


\\:D/\\:D/\\:D/

[COLOR="DarkOrchid"]Esta no te puedo decir mas que 2 cosas:
1. Mi primo de 7 años está encantadísimo con Linux por todos los juegos que le instalé y que le enseñé como instalar desde [www.ubuntugames.com](www.ubuntugames.com). Es decir, si no conocés ningún juego y no tenés preferencia y solo te gusta jugar, vas a quedar encantado (creeme, mi tio se sorprendió por juegos FPS nativos de linux aun conociendo los de Windows)

2.Si tenés preferencia por juegos en particular, lo más recomendable es que ya que te va sa quedar con Windows los jueges allí. Aunque, repitiendo lo que dije hace poco en otro post, un amigo con Linux lo configuró de tal forma de que los juegos andan mucho mejor en Linux que en Windows, aún así emulandolos.

Es decir,si tenés ganas de ponerte y hacerlo andar, es posible que puedas correr todos tus juegos en Linux, pero tenés que saber bastante y tener ganas de hacerlo.



Espero que te sirva, Saludos y suerte:)
[/COLOR]

---

### Post by fgl82 on 2008-07-01
[COLOR=DarkOrchid][COLOR=Black]Yo quiero agregar que si realmente te interesa jugar a tus juegos de windows, lo más sano es que lo conserves con un dual boot. Hasta ahora, por más que le puse empeño, Wine me decepcionó bastante.[/COLOR][/COLOR] No sé, fijate, pero por algo existe cedega y ni con ese corren TODOS... 

Ahora, si es como dice Valucha, te interesa jugar así por jugar sin tener antiguos favoritos, con los juegos libres vas a andar bastante bien. No esperes, eso si, mucha profundidad en los juegos. Nada de historias épicas ni tramas complejas. Pensá más bien en FPSs on line, estrategia con solo un par de equipos, emuladores, clones de juegos comerciales... esas cosas... Por lo menos es lo que encontré yo.

---

### Post by granjero on 2008-07-01
muchas gracias a todos por responder!  :KS:KS  todavia no instale y creo que hasta el domingo o lunes de la semana que viene no lo haga pero siguen surgiendo dudas...

el dual boot surge como opcion durante la instalacion?

o sea, booteo con el cd y me da un par de opciones, ahora no las recuerdo todas pero ninguna es instalar con dual boot o similar.

hay que poner instalar y despues me preguntara que deseo hacer???

si no tendre que leer donde esta el dual boot!
gracias gente vuelvo a trabajar!

salud!

---

### Post by fgl82 on 2008-07-01
El dual boot surge de la siguiente manera. Ponele que vos tenés instalado windows. Bueno, para que te funcione el dual boot, simplemente tenés que instalar el Linux en una nueva partición. Es decir, en el momentoen que Linux te pregunte dónde lo querés instalar, tenés que seleccionar una partición de tu disco rígido en la cual NO ESTÉ INSTALADO WINDOWS.

Si bien Ubuntu te permite particionar durante la instalación, a mí me trajo problemas de esa manera, y creo que no hice nada mal. En mi opinión lo mejor que podés hacer es reparticionar tu rígido (si es que no lo tenés ya particionado) DESDE WINDOWS, con un programa del estilo del PARTITION MAGIC.

Cualquier cosa, seguí preguntando! :)

¡Saludos!

---

### Post by granjero on 2008-07-01
yo tengo un disco rigido de 80gb partido en dos

una de 12gb en ntfs donde esta el w2k y esta es en la que quiero instar ubuntu. le quedan 7,5gb libres. 

en la otra particion de 68gb estan mis documentos. y tabien hay un segundo disco rigido de 20gb que es el destino de todas las decargas...

parto el disco donde esta la instalacion de windows?


salud y gracias!

:guitar:

---

### Post by ChameleonDave on 2008-07-01
No creo que sea una buena idea usar NTFS.  Yo prefiero usar el sistema Ext3, instalando en Windows los drivers necesarios para que Window lo lea.

---

### Post by Hei Ku on 2008-07-02
NTFS no se puede hacer el kernel. Y tampoco es recomendable usarlo para el /home (el equivalente a Mis documentos).

---

### Post by valucha on 2008-07-02
[COLOR="DarkOrchid"]Chicos, me parece que granjero no quiere dejarlo con ntfs, lo quiere partir, y al partirlo puede ambiarle el formato...

Hacelo y poné ext3 :)

Yo también lo que haría es poner la "home" en el disco donde tenés todos tus documetnos, así al reinstalar cualquier cosa no perdés nada de nada...[/COLOR]

---

### Post by fgl82 on 2008-07-02
edito la pregunta, no me den bola, ya me acorde

---

### Post by granjero on 2008-07-02
ok, entonces lo que deberia hacer es hacer una particion en el disco C: ¿de que tamaño? en el disco donde la pensaba instalar quedan algo asi como 7,5gb pero no puedo hacer una particion de ese tamaño ya que ahi windows va a dejar de andar? ¿cual es tamaño minimo que recomiendan?

una vez que tenga la particion lista, ejecuto el cd de ubuntu y pongo instalar, y la instalacion me va a pedir que formatee la particion nueva en el formato ext3?

otra pregunta¿ como puse por alla arriba tambien tengo un segundo disco de 20gb en la maquina, pèro esta como esclavo. puedo poner ahi el ubuntu y tener un dual boot igualmente? o me conviene que este en el mismo disco donde esta el otro SO?

sepan disculpar mis preguntas pero estoy tan harto de windows que me voy a hacer un tiempo para estudiar un poco de linux pero para los temblorosos primeros  pasos quiero una manito amiga que me ayude!!!!!

me asusta un poco lo del dual boot, durante la instalacion va a salir la opcion del dual boot?

gracias de nuevo!!!!

](*,)   ](*,)   \\:D/

---

### Post by valucha on 2008-07-03
> **granjero said:**
> ok, entonces lo que deberia hacer es hacer una particion en el disco C: ¿de que tamaño? en el disco donde la pensaba instalar quedan algo asi como 7,5gb pero no puedo hacer una particion de ese tamaño ya que ahi windows va a dejar de andar? ¿cual es tamaño minimo que recomiendan?

una vez que tenga la particion lista, ejecuto el cd de ubuntu y pongo instalar, y la instalacion me va a pedir que formatee la particion nueva en el formato ext3?

otra pregunta¿ como puse por alla arriba tambien tengo un segundo disco de 20gb en la maquina, pèro esta como esclavo. puedo poner ahi el ubuntu y tener un dual boot igualmente? o me conviene que este en el mismo disco donde esta el otro SO?

sepan disculpar mis preguntas pero estoy tan harto de windows que me voy a hacer un tiempo para estudiar un poco de linux pero para los temblorosos primeros  pasos quiero una manito amiga que me ayude!!!!!

me asusta un poco lo del dual boot, durante la instalacion va a salir la opcion del dual boot?

gracias de nuevo!!!!

](*,)   ](*,)   \\:D/
[COLOR="DarkOrchid"]
Tranquilo che!!!...
Mirá, en los minimos requerimientos acá: [https://help.ubuntu.com/community0/Installation/SystemRequirements](https://help.ubuntu.com/community0/Installation/SystemRequirements) dice que necesitarías 8gb para que ande todo bien. Osea, lo minimo minimo minimo son 4 gb, pero te recomiendan 8gb.
Entonces tal vez te convendría hacerlo con el otro disco...


LO del dual boot es una pabada... Tenés instalación gráfica y ahi te guía, pensá que hay gente que sin saber nada,se anima y lo hace y lo hace bien.

Igualmente,creo que leyendo este blog [http://tuxpepino.wordpress.com/2008/04/25/instalar-ubuntu/](http://tuxpepino.wordpress.com/2008/04/25/instalar-ubuntu/) te vas a sacar toditas las dudas.



[/COLOR]

---

### Post by granjero on 2008-07-09
bueno actualizando....

al final me termine comprando una compu nueva.... jejejeje:-({|=:-({|=

ahora les estoy escibiendo desde el ubuntu 8.04 cargado desde el cd... me les cuento mi problema...

antes de instalar ubuntu queria organizar bien la pc y me parece que me salio el tiro por la culata...

lo que hice fue lo siguiente, tengo un disco de 320gb le instale windows en una particion ntfs de 20gb que windows llamo c: 

una vez instalado windows hice una nueva partición de 20 gb a la cual no le di formato

y otra mas del espacio restante...

corri el instalador de ubuntu queriendo que se instale en la particion de 20gb que deje vacia... pero no supe como hacer para estar seguro que estaba instalando en esa particion...

aca en el live sesion  pude darle formato a la particion vacia. le di el formato ext3. pero aun asi no se como hacer para que me instale el SO en esa particion....


quiero saber bien tambien que son los iconos que se llaman:(hablo del archivo que subi) 


"soporte de 21gb"

"sistema de archivos"

los otros son mis cosas....

muchas gracias

salud!

---

### Post by fgl82 on 2008-07-10
El tema de instalar ubuntu en una particion determinada lo tenes que ver cuando corrés el instalador en sí. Ahí te va a dar la opción de elegir en qué partición instalarlo.

Los íconos que mencionas son:

1) Sistema de Archivos: son los directorios de la particion de Ubuntu, como si fuera el "C:\" de Windows. En tu caso, no hay una "particion de Ubuntu" dado que estás con el Live, pero el resultado es el mismo, vas av er directorios propios de linux (/bin, /home, etc).
2) El otro es la particion de 20 GB que armaste

¡Saludos!

---

