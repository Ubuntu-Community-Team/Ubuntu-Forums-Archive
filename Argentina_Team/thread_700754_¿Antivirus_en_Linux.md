---
title: "¿Antivirus en Linux?"
date: 2008-02-18
forum: Argentina Team
---

### Post by atari130xe on 2008-02-18
Que opinan de esta noticia? 
[http://www.cnnexpansion.com/blogs/e-volution/archive/2008/02/18/linux-blindado---vendran-los-anti-virus-comerciales-para-linux]("http://www.cnnexpansion.com/blogs/e-volution/archive/2008/02/18/linux-blindado---vendran-los-anti-virus-comerciales-para-linux")

---

### Post by Mauro22 on 2008-02-18
Para mi es pura mentira.

Es un SO 100% Transparante. No va a hacer falta estar corriendo un antivirus.

---

### Post by pol666 on 2008-02-18
Trabaja para Microsó esa gente? 

Muy amarillista, hacer virus que ataquen Unix segun tengo entendido es MUY dificil.

---

### Post by atari130xe on 2008-02-18
Me huele a lo mismo, es más hoy estuve por un foro español y la verdad que se nota mucho ese tipo de cosas....

---

### Post by facundocorradini on 2008-02-18
La noticia hace amarillismo de un exploit que se descubríó hace una semana, y que permitía obtener privilegios de administrador a un atacante local <-- léase, sentado en tu PC. 

Esto fué corregido inmediatamente. En ubuntu, a las 22 horas de descubierto el exploit ya teniamos la solución en las actualizaciones.

El resto de la nota, es FUD en su expresión máxima. 


La cuestión de "en linux no hay virus pq no lo usa nadie" es un argumento tonto. La realidad es que gracias a la estructura del sistema, la propagación de malware es imposible. Busquen un poco al respecto y seguro encuentran una laaaaaarga lista de las razones de esto...

---

### Post by atari130xe on 2008-02-18
Suena como a "a rio revuelto ganancia de pescadores", creo el rumor de que tu compu con Linux es tan vulnerable como con Windows y no podrá faltar gente que se prenda en "necesito tal antivirus", que casualidad que ahora que Linux se está haciendo cada vez más popular (Ubuntu de por medio), aparecen de la nada "Virus", Malware (FUDware, Trollware, etc), yo no soy "pro nada" pero la verdad que la historia de ciertas cias de Soft y como se hicieron "masivas" es como MUY evidente... Por la plata "baila el mono"...

---

### Post by clasificado on 2008-02-18
Este es un hermoso punto :D con el cual me siento entre los comentarios de la comunidad y algun punto que el muchacho de la nota destaca

¿Alguien conoce los troyanos de encriptación por PGP?
> 
El cirtuito de contagio es bastante simple: Te llega un archivo por MSN, por correo de alguna forma, de alguien de confianza y uno está convencido de que tiene que ejecutarlo.

Al hacerlo, busca todos los documentos de oficina y los encripta, te manda un correo con una cuenta de banco para que deposites X cantidad de plata y te dan la clave de desencriptado. Al mismo tiempo utiliza al MSN abierto para reenviarse a los contactos.


¿Porqué funciona tan bien en Windows? ¿Que tan diferente es de un virus que trate de formatear?

-) El fallo de seguridad esta basado en la ingenieria social, donde lo que hay que parchear es al usuario.
-) No necesita ni quiere dañar al sistema
-) No necesita permisos de superusuario para cumplir su cometido
-) El daño puede ser MUCHO mas costoso para el usuario en comparacion a un virus que te obligue a reinstalar

Contra eso, un buen sistema herústico para identificar al binario y atraparlo al vuelo seria una gran ayuda.

¿Cual es mi problema? Que funciona sin complicaciones en cualquier sistema binariamente compatible, ya que es la única limitación técnica en la propagación.

clasificado

---

### Post by faktorqm on 2008-02-18
Que payasos, les escribi esto en los comentarios, a ver si me lo publican JAJAJAJA

```

A mi parecer, no están dando toda la información al respecto, lo cual debo pensar en periodistas que poco saben del sistema operativo GNU/Linux, pero aún asi insisten en escribir sobre él...
El "bug" sólo se podía explotar localmente, es decir, que alguien este enfrente del equipo y con esa versión de kernel, podía llegar a aprovecharse.
Ningún sistema existente es invulnerable, los usuarios que creen eso lamentablemente están equivocados también, pero de ahí a decir que se necesita de un antivirus es una completa exageración.
"y la triste realidad no es así", no es así, pero casi ;)

```

Microsoft les tirará un manguito a estos? yo creo que no... pero nunca se sabe... jaja salu2!

---

### Post by atari130xe on 2008-02-19
> **facundocorradini said:**
> La noticia hace amarillismo de un exploit que se descubríó hace una semana, y que permitía obtener privilegios de administrador a un atacante local <-- léase, sentado en tu PC. 

Esto fué corregido inmediatamente. En ubuntu, a las 22 horas de descubierto el exploit ya teniamos la solución en las actualizaciones.

El resto de la nota, es FUD en su expresión máxima. 


La cuestión de "en linux no hay virus pq no lo usa nadie" es un argumento tonto. La realidad es que gracias a la estructura del sistema, la propagación de malware es imposible. Busquen un poco al respecto y seguro encuentran una laaaaaarga lista de las razones de esto...

extractado del sitio [www.vivalinux.com.ar](www.vivalinux.com.ar)
>  Velocidad de respuestas al exploit local contra el Kernel 2.6

Publicado por vivab0rg el 18/02/2008

Después de que la semana pasada se publicaran los detalles de un exploit local contra el Kernel 2.6 producido por la llamada al sistema vmsplice(), el sitio DistroWatch hace un resumen de la rapidez con que las principales distribuciones GNU/Linux respondieron publicando sus correcciones al problema. Todas las 10 primeras distribuciones reaccionaron en menos de 48 horas:

   1. Debian (0+ horas)
   2. Fedora (8+ horas)
   3. Slackware (12+ horas)
   4. Mandriva (19+ horas)
   5. Frugalware (21+ horas)
   6. OpenSUSE (23+ horas)
   7. rPath (26+ horas)
   8. Red Hat Enterprise Linux (27+ horas)
   9. Ubuntu (27+ horas)
  10. CentOS (37+ horas)

Aunque con este exploit un usuario sin privilegios ejecutando un Kernel vulnerable localmente podría obtener un acceso de superusuario, potencialmente afectando a millones de sistemas, el mismo no fué considerado crítico, pero solucionado con una rapidez imposible de encontrar en el mundo del software privativo. :)

---

### Post by pante on 2008-02-20
Decir que fue publicado en CNN y decir que es amarillista es redundante.:)

Saludos

---

### Post by niko_3100 on 2008-02-20
Che mas alla de la noticia avg tiene un antivirus para linux. Aca dejo el link:

[http://free.grisoft.com/doc/5390/us/frt/0](http://free.grisoft.com/doc/5390/us/frt/0)

---

### Post by MeduZa on 2008-02-20
> **atari130xe said:**
> Suena como a "a rio revuelto ganancia de pescadores", creo el rumor de que tu compu con Linux es tan vulnerable como con Windows y no podrá faltar gente que se prenda en "necesito tal antivirus", que casualidad que ahora que Linux se está haciendo cada vez más popular (Ubuntu de por medio), aparecen de la nada "Virus", Malware (FUDware, Trollware, etc), yo no soy "pro nada" pero la verdad que la historia de ciertas cias de Soft y como se hicieron "masivas" es como MUY evidente... Por la plata "baila el mono"...

es tal cual lo que decis vos, la maquinaria linux esta encendida y se la ven venir, de mis amigos ya 5 se pasaron a linux y cada vez mas gente lo hace, y que pasa con toda esa gente que consumia los productos que ellos generaban para el tan echo mal apropocito windows?
Claro aca esta echo bien y no necesita de extras para nada, entonces, se la ven venir y ya empiezan con eso, el tiempo de salida de un parch en windows puede tomar de semanas, meses, años o nunca salir, aca ese tipo de agujeros en horas esta tapado, gracias a que el codigo es abierto!!

Saludos y por mas que quieran decirlo, linux es un universo diferente al universo windows!!

---

### Post by MeduZa on 2008-02-20
> **niko_3100 said:**
> Che mas alla de la noticia avg tiene un antivirus para linux. Aca dejo el link:

[http://free.grisoft.com/doc/5390/us/frt/0](http://free.grisoft.com/doc/5390/us/frt/0)

es para chequear virus para windows en linux!

---

### Post by newtonfn on 2008-02-20
Si bien soy usuario de Linux desde hace ya varios años, no entiendo el por qué todos estan tan en contra de tener un antivirus.

Yo no lo tengo, es cierto, y tambien estoy de acuerdo que no se necesita si se toman las medidas correspondientes, pero lo mismo se aplica a Winodws, en donde antes de pasarme a linux viví toda mi vida, y aún en el trabajo empleo, sin jamas haber tenido un virus. (y sin tener tampoco antivirus)

La mayoría de los virus ahora se transmiten por ingeniería social. La gente es tan tonta que recibe por msn un mensaje que dice, mirá este archivo con tu foto ! y a pesar de ser un .RAR que dentro tiene un .EXE lo abren y lo ejecutan ! (conozco casos, más de uno, que hacen esto)

En Windows esto es aún peor porque está la filosofía de que los usuarios son Administradores por defecto (y si no se hace eso no anda casi nada) pero en linux también existe en gran medida esa irresponsabilidad. (Gracias a SUDO no le doy permisos de root a nadie, pero por si tienen que instalar algo les digo que existe sudo, y adivinen que hacen muchos... como algo les dice que requiere permisos lo ejecutan con sudo sin siquiera pensar en que es o las consecuencias. Por suerte no hay aun mucha ingeniería social, pero si la hubiera como lo hay en windows.... como se evita eso?)

Lo que si, entre mas usuarios haya en linux mas usuario idiotas habrá y llegara el momento en que se envíe por pidgin un script de perl que no requiera ni permisos de administrador y te envie tus archivos a otra pc, o te abra un puerto no privilegiado donde otra persona pueda chusmear o atacarte y demás cosas.

En fin, no veo que haya que descartar tan asi de la nada la idea de un antivirus pecando de la soberbia de que este sistema operativo no tiene virus y/o es difícil hacerlos y bla bla bla.. hay que asumir que para determinados perfiles de usuarios, un antivirus  es algo que podría serles util al menos para informarle de comportamientos extraños.

Y obviamente, el que no lo necesite, puede seguir tranquilo sin antivirus.

---

### Post by MeduZa on 2008-02-20
> **atari130xe said:**
> extractado del sitio [www.vivalinux.com.ar](www.vivalinux.com.ar)
 :)

menos de 48hs :S
MICROSOFT en 48hs todavia no saben por donde empezar :S

48hs no le da tiempo casi a un hacker de sacarle probecho !

---

### Post by MeduZa on 2008-02-20
> **newtonfn said:**
> Si bien soy usuario de Linux desde hace ya varios años, no entiendo el por qué todos estan tan en contra de tener un antivirus.

Yo no lo tengo, es cierto, y tambien estoy de acuerdo que no se necesita si se toman las medidas correspondientes, pero lo mismo se aplica a Winodws, en donde antes de pasarme a linux viví toda mi vida, y aún en el trabajo empleo, sin jamas haber tenido un virus. (y sin tener tampoco antivirus)

La mayoría de los virus ahora se transmiten por ingeniería social. La gente es tan tonta que recibe por msn un mensaje que dice, mirá este archivo con tu foto ! y a pesar de ser un .RAR que dentro tiene un .EXE lo abren y lo ejecutan ! (conozco casos, más de uno, que hacen esto)

En Windows esto es aún peor porque está la filosofía de que los usuarios son Administradores por defecto (y si no se hace eso no anda casi nada) pero en linux también existe en gran medida esa irresponsabilidad.

Lo que si, entre mas usuarios haya en linux mas usuario idiotas habrá y llegara el momento en que se envíe por pidgin un script de perl que no requiera ni permisos de administrador y te envie tus archivos a otra pc, o te abra un puerto no privilegiado donde otra persona pueda chusmear o atacarte y demás cosas.

En fin, no veo que haya que descartar tan asi de la nada la idea de un antivirus pecando de la soberbia de que este sistema operativo no tiene virus y/o es difícil hacerlos y bla bla bla.. hay que asumir que para determinados perfiles de usuarios, un antivirus  es algo que podría serles util al menos para informarle de comportamientos extraños.

Y obviamente, el que no lo necesite, puede seguir tranquilo sin antivirus.

yo tampoco usaba el antivirus en windows, pero tenia instalado uno por si acaso, en linux realmente no le veo sentido ya que todo lo que bajo son documentos y los programas estan en el repositorio, la verdad es medio jodido agarrarse un bicho en linux pero soy consiente que es posible!

---

### Post by faktorqm on 2008-02-20
newtonfn: Leete esto [http://es.wikipedia.org/wiki/Sudo](http://es.wikipedia.org/wiki/Sudo) (es cortito) y/o alguna bibliografia mas extendida y mas profunda sobre el tema de los permisos, y sudo. Despues lee tu post anterior y comenta que te parece usar antivirus bajo sistemas gnu/linux (sin contar los recursos que gastamos en ejecutarlo y el tiempo mientras escaneamos esos 24gb de juegos que te trajo tu hermano en su disco extraible) Salu2!!

---

### Post by Mauro22 on 2008-02-20
Yo creo que en el caso que si hayan "virus" para linux, es una perdida de tiempo y recursos instalar un antivirus y estar corriendolo todo el dia.


Esto se basa en la comunidad mundial, un "virus" no sobreviviria mas de un dia, enseguida seria neutralizado por alguna actualizacion.

Muy distinto es el paronama de windows, en donde todos los dias salen cientos de virus, adware, spyware etc etc




Aparte siempre se ataca a los mas popular, y aunque linux viene levantando muchisimo, windows esta al frente todavia.

---

### Post by niko_3100 on 2008-02-20
Mauro22 tiene razon, lo que hace fuerte a linux es la comunidad que hay atras.

---

### Post by Hei Ku on 2008-02-20
La noticia hace sensacionalismo de un exploit que no es virus, sino un rootkit, porque necesita acceso local. Diganme si Windows sobrevive al acceso local y charlamos.

Mas alla de eso, yo uso ClamAV para el correo, y lo tengo instalado para correrlo manualmente si lo necesito alguna vez. Sirve para que no le mande algun correo con virus a un usuario de Windows sin darme cuenta, por mas que a mi no me afecte.

Nunca esta de mas, como tener un firewall por mas que no tenga puertos abiertos.Son herramientas que vienen bien en ciertos casos y mejor tenerlas a mano y no tener que bajarlas en el momento.

Como comentario, ClamAV esta considerado uno de los mejores antivirus. Barracuda por ejemplo los utiliza en sus boxes para control de AV empresarial. Y de paso, no se si se enteraron, pero hace poco Trend los denuncio por infringir una patente ridicula. Lo que muestra que estan desesperados, y atacan en todos los frentes. 

El Software Libre avanza, y cosas como estas van a ser cada vez comunes. 

Primero te ignoran, despues se rien de ti, luego te atacan, y entonces ganas (Gandhi)

---

### Post by newtonfn on 2008-02-20
> **faktorqm said:**
> newtonfn: Leete esto [http://es.wikipedia.org/wiki/Sudo](http://es.wikipedia.org/wiki/Sudo) (es cortito) y/o alguna bibliografia mas extendida y mas profunda sobre el tema de los permisos, y sudo. Despues lee tu post anterior y comenta que te parece usar antivirus bajo sistemas gnu/linux (sin contar los recursos que gastamos en ejecutarlo y el tiempo mientras escaneamos esos 24gb de juegos que te trajo tu hermano en su disco extraible) Salu2!!

Imagino que tu intensión honesta es intentar instruirme sobre el uso de SUDO. Tambien imagino que no me supe explicar bien en mi post anterior. En base a estos supuestos trataré de explicarme nuevamente haciendo especial incapie en el tema SUDO.

Primero, aclaro que es una muy linda idea y funciona muy bien sudo y me parece excelente como en Ubuntu, root por default esta desactivado lo cual es posible (o al menos útil) gracias a SUDO

Pero te comento, que esta és. de las pocas distribuciones que yo conozco, la única que viene configurada así por default. Dado que ni Debian ni Slackware lo traen así.

También te comento que he trabajado en varios servidores, basados en Slackware y Debian, que cuando pedí acceso al sistema me dieron el usuario y la contraseña de root y pude ver que era el único usuario que todos los que debían administrar el equipo empleaban (por suerte eramos solo tres)

Podrás decirme que los que configuraron y administraban ese equipo eran unos tontos o ingenuos o descuidados, y tal vez tengas razón, pero si esas personas, con conocimientos suficientes como para instalar en un slackware un bind, apache, postfix y otros programas más y que hacian eso por varios años y por tal motivo ya estan por arriba de la media de los usuarios de pcs (y digo usuarios en gral, incluyendo usuarios de windows) accedian al sistema directamente por root. ¿Que podemos esperar del resto del común de los mortales?

Ahora bien, si me decis que Linux puede sobrevivir a cualquier acción maliciosa ejecutada por root (aunque sea sin querer) entonces la verdad admito que no entiendo absolutamente nada de linux.

Mi punto iba precisamente en que la gente normal, que le gustan las cosas simples fáciles y rápidas, si tuvieran acceso a root, usarían root para cualquier acción, e incluso en Ubuntu, muchas de esas personas activarían la cuenta de root precisamente para no tener que tipear contraseñas (y te aseguro que muchos (no digo la mayoria.. solo digo muchos) en este foro ya hicieron eso e incluso varios que comprenden los riesgos que se corren)

Ahora imaginemos que usemos SUDO, y te pido me corrijas si me equivoco en lo que digo ya que honestamente no leí todo el articulo de la wikipedia sobre SUDO por tal vez ser un poco soberbio y creer que tengo un entendimiento sobre el funcionamiento de sudo, lo cual puede no ser así.

Si no me equivoco SUDO genera una temporal elevación de privilegios para ejecutar un programa, los cuales descarta inmediatamente después para que no se pueda ejecutar otra cosa con permisos de root o el usuario que sea que este configurado.

Si bien se que se pueden limitar los programas que se permite ejecutar con SUDO, algun usuario, para que tenga sentido el tener root totalmente deshabilitado, debería poder ejecutar cualquier cosa, y en Ubuntu, ese usuario es el usuario por defecto, el que estoy seguro el 90% usamos.

Ahora imaginate que yo hago un programa en C que lo que haga sea tan simple  como formatearte una particion, y te logro convencer de que lo ejecutes con SUDO. Lamentablemente el programa va a hacer lo que fue creado para hacer sin chistar ya que lo estas ejecutando con SUDO.

Obviamente, depues me odiarás por haberte convencido de hacer eso, pero el nabo serías vos.. Eso es ingeniería social.

Si el programa no hiciera un format, sino que instale un demonio que se ejecute como root (lo cual puede hacer porque el programa fue ejecutado con sudo originalmente) y este demonio escuchara conexiones entrantes por medio de las cuales se le pueda hacer realizar ciertas acciones... ¿Que diferencia tendría con un backdoor? ¿que limitación tiene sudo para impedir eso? ¿que limitaciones para actuar tendría este demonio?

Ahora imaginemos que mi programita no hace un format, ni abre el puerto 45 de mi pc para conexiones entrantes, sino que abre el puerto 23499 y permite por medio de ese puerto ejecutar ciertas acciones, inocuas en teoria. O sea que no requiere permisos de superusuario para ninguna acción. ¿Entonces para que necesitaría siquiera sudo?

Obviamente, esta version del programa no podría afectar al sistema de una forma que lo deje inservible, ya que solo podría tocar archivos del usuario, pero con mis archivos podría hacer lo que sea. Lamentablemente, y ese es el motivo de los backups, justo esa es la información mas importante. Honestamente, si se me rompiera el disco rígido por un problema físico, no lloraría por haber perdido el firefox o el gimp, sino por haber perdido los trabajos de la facultad, la musica, fotos, y ni hablar si fuera la pc de mi trabajo en donde si tengo información que me costaría mucho recuperar. (este es el motivo de los backups!)

Ahora, mezcla todo esto con un poco de ingeniería social y verás que cualquier persona incauta podría (o aun alguien cauto en un descuido) caer en algo como lo que te planteo.

Podrás decirme, eso no es un virus, sino que es un ataque dirigido a una persona en particular. Y tendrías toda la razón, pero en los últimos tiempos he visto muchos "virus" por llamarlos de alguna manera que se transmiten con el simple metodo de  mandar mensajes por el msn diciendo que descargues tal archivo o enviandote directamente el archivo y lo ejecutes con diferentes excusas de por medio. Y aunque no lo creas MUCHISIMA gente lo hace ! 

Obviamente no son personas con un alto conocimiento, sino mas que nada usuarios comunes y corrientes que solo saben usar el la pc para crear un documento y navegar por internet. Y es a estos usuarios a los que van dirigidos, en cierta parte, los antivirus incluso en Windows (Es verdad.. en windows podes pegarte virus incluso sin interacción del usuario, o sea en forma 100% automática, pero quitando algunos famosos bugs, que bien podrían existir en cualquier sistema operativo, es bastante complicado)

Con toda esta base, es que digo que no se debería descartar tan de lleno la idea de un antivirus en su sentido amplio, o sea con heuristicas, y detección de cosas que no son estrictamente virus.

Un antivirus no es una mala palabra, tanto así como no lo es firewall. Pero obviamente, no todo el mundo necesita un antivirus pero si alguna parte de este mundo la requiere, y al menos yo veo motivos para que así sea, debería tener el derecho de usarlo. (Esto es que exista uno y que no se lo tilden de estúpidos por el simple hecho de usarlo)

Espero haberme explicado mejor, y pido perdón si en toda esta verborragia he dicho algo que no sea correcto.

Y perdón a todos los que leyeron esto y seguro lo encontraron terriblemente aburrido.

---

### Post by leo_rockway on 2008-02-20
> **newtonfn said:**
> 
Obviamente, depues me odiarás por haberte convencido de hacer eso, pero el nabo serías vos.. Eso es ingeniería social.


Como los famosos casos de # rm -rf

De todas formas, un usuario normal que instala de los repos oficiales y no tiene el root facil no deberia tener que usar un pesado antirootkit (porque no son virus) mas si tenemos en cuenta que las cosas en linux son de codigo abierto.

En todo caso, antes que un antirootkit un antiingenieria social seria mucho mas util...

---

### Post by newtonfn on 2008-02-21
> **leo_rockway said:**
> Como los famosos casos de # rm -rf

De todas formas, un usuario normal que instala de los repos oficiales y no tiene el root facil no deberia tener que usar un pesado antirootkit (porque no son virus) mas si tenemos en cuenta que las cosas en linux son de codigo abierto.

En todo caso, antes que un antirootkit un antiingenieria social seria mucho mas util...

Estoy de acuerdo, no digo que no tengan razón. De hecho incluso antes que un anti-ingeniería social sería mucho más util algo tan simple como la "Educación".

Sin embargo, tal vez sea pesimista, la gente no le interesa aprender (y no tiene porqué hacerlo si no les sirve, al igual que a mi no me interesa aprender como funciona mi auto para manejarlo) 

Solo un comentario, que recién ahora se me ocurre y tal vez sea una estupidez lo que digo. Si llegara a proliferar más el software comercial no open-source, lo cual no es una locura decir (conozco mucha gente que usaría Linux si el photoshop, aun siendo pago, funcionara bien por citar solo una aplicación) y se comience a hacer comun instalar algunos softwares así... no se expondría el sistema operativo a un nivel de inseguridad, introducido por los bugs de estas aplicaciones cerradas que tal vez deban ejecutarse con privilegios de root, similar al que está expuesto windows?

(Por favor, ahorrense las respuestas a este post relacionadas con open-source, free-software, gnu, bsd, las bondades de las comunidades y demás que ya sería demasiado off-topic y aviso que aun siendo un gran defensor de todo eso reconozco que es en el fondo, un tema muy personal donde no hay ni bien ni mal)

---

### Post by leo_rockway on 2008-02-21
> **newtonfn said:**
> Si llegara a proliferar más el software comercial no open-source [...] no se expondría el sistema operativo a un nivel de inseguridad introducido por los bugs de estas aplicaciones cerradas que tal vez deban ejecutarse con privilegios de root al que esta expuesto windows?

A veces tengo pesadillas de este tipo. Me despierto y le rezo a San IGNUcius [0] que nunca pase. Estoy totalmente de acuerdo con vos.

[0] [http://www.stallman.org/saint.html](http://www.stallman.org/saint.html)

---

### Post by facundocorradini on 2008-02-21
newtonfn: 

Esto va más allá de SUDO o no sudo. Simplemente el usuario que es capaz de caer en ese tipo de trampas no debería tener privilegios de usar sudo.

Administrar un sistema no es joda, pero si el sistema tiene un buen administrador, entonces podés estar tranquilo.

---

### Post by newtonfn on 2008-02-21
Estoy 100% de acuerdo en el ambito empresarial.

Un buen administrador que sepa lo que hace y te olvidas de todos los problemas. Ese es un ejemplo de caso en donde un antivirus o cualquier cosa similar es practicamente innecesario.

Esto es verdad, hasta cierto punto, incluso en un ambiente Windows.

Pero en una casa, en una pc familiar, donde no hay nadie que entienda nada ¿que hacemos?

---

### Post by facundocorradini on 2008-02-21
En casa se puede poner una tener un usuario con poder de hacer sudo. Ese usuario debería ser lo suficientemente inteligente como para no caer en estas cosas. 

El resto de los usrs, que le pidan ayuda cuando necesiten instalar algo...

---

### Post by andy_91 on 2008-02-21
esa es buena idea pero creo que la forma mas facil es tratar de evitar la consola

para que querría un usuario común usar la consola ?

el único comando con sudo que podría llegar a usar frecuentemente es el sudo pppoeconf

jeje XD dependiendo de la distribución por que en algunas solo es necesario usarlo una vez y después arranca con el sistema(salvo que reinicies el pc con el bastoncillo)

y un poco de educación creo que si te envían algo antes de aceptarlo simplemente hablarle al contacto
si responde preguntare pr el paquete y ver lo que dice, de ahí es responsabilidad tuya si lo abrís o no

si no contesta no que da mas que rechazar y cerrar la conversación

y es verdad lo del sudo que puede hacer un antivirus contra el sudo?

si algún usuario ejecuta el sudo nombre_del_virus chau se ejecuta y quien lo para (el antivirus no XD, ya me paso en windows)

por eso creo que un usuario común no tocaría la terminal por si solo

además el simple hecho de usar Linux significa:
a) le vino en la pc (que lo mas probable es que lo vuele en menos de 24hs)

b) que lo instale por su cuenta, lo que implica una investigación previa

así  que no se si un antivirus ayude, considerando que no ayuda en windows (por mas antivirus que tenga los bichotes me los agarraba igual)

bueno esa es mi opinión un virus te agarra con windows, Linux, mac
con o sin antivirus

por suerte ubuntu tiene su comunidad que trabaja duro para volver e sistema lo mas estable y rudo posible jeje
a y también aprenden unos de otros y colaboran entre si

---

### Post by Mauro22 on 2008-02-21
Hoy me agarro una duda.


Supuestamente un Antivirus anda dando vueltas por todo el disco. Para esto no necesitaria permisos de root?

O sea, una aplicacion corriendo todo el dia como root??


:confused::confused:

---

### Post by Hei Ku on 2008-02-21
> **Mauro22 said:**
> Hoy me agarro una duda.


Supuestamente un Antivirus anda dando vueltas por todo el disco. Para esto no necesitaria permisos de root?

O sea, una aplicacion corriendo todo el dia como root??


:confused::confused:

Correría como daemon, igual que varios otros servicios que hoy tenes corriendo en tu pc.

---

### Post by newtonfn on 2008-02-21
Andy, me encantó tu lógica :)

Me dejaste sin argumentos, en especial de los motivos por los cuales un usuario tendría Linux (al menos en lo que yo concidero el comun denominador de usuarios) y el porqué no es tan importante el tema de los antivirus.

Sin embargo, espero algun día ver convertido Linux en un sistema tan masivo como lo es Windows. Pero por ahora, no puedo discutirte nada.

Tambien es verdad, un usuario comun se mantendría alejado de la terminal, y haciendo doble click no se ejecuta nunca magicamente ningun gksudo por lo que no hay riesgo.

El riesgo sigue estando para aquellos "quasi virus" que no requieren permisos de superusuarios, pero sin embargo pueden hacer gran mal.  Borrar archivos, encriptar archivos, dar acceso remoto aunque sea a usuarios sin privilegios..

Igualmente, un antivirus en windows no es la cura magica a los virus, pero he visto mas de un caso en que ayudó a evitar acciones tontas. Y en algunos casos hay que esforzarse bastante para ejecutar un virus super detectado si tenes un antivirus en windows que funcione bien... pero no viene el caso todo esto.

Con respecto a lo que dice Mauro22, la verdad, no lo se. Pero hay muchos progrmas que se ejecutan como root. Afortunadamente la mayoría estan bien programados, asi que descartan los permisos (o casi todos de inmediato) por ejemplo, un servidor apache o postfix  que necesitan abrir puertos privilegiados, incluso la interfaz grafica se ejecuta gracias setuid pero siempre algo de los permisos mantienen y tal vez, no lo se, por ahi siempre haya un vector de ataque, pero aca honestamente estoy entrando al terreno de lo que desconozco y otra persona sabrá mejor que yo.

En fin, sigo pensando que en la pc de mi papa, en donde yo le instale Linux como experimento, sería lindo tener, si existirian realmente que amenazas, un antivirus para evitar que el, que  tiene acceso a sudo, pueda algun día, ejecutar algun escript malicioso.

Pero en verdad me alegra saber, que al menos no para todos, "antivirus" es una palabra prohibida que el simple hecho de concevirla en la mente es motivo de la concepcion de palabras que jamas deberian ser pronunciadas.

Saludos

---

### Post by faktorqm on 2008-02-21
Uhh me voy un dia y pasa de todo.....

newtonfn: espero que no te hayas ofendido, mi intencion es que todos aprendan, solo que no sabia que sabias :D

Con sudo vos podes especificar exactamente que comandos y que usuario puede ejecutarlos.
Para instalar un servidor, obvio que en muchas cosas necesitas ser root, pero despues, para mantenimiento, le podes poner al sudo algun que otro comando que necesites, pero nada mas para el usuario "mantenimiento". El resto, o root o usuario. Otro error muy comun y muy grave por cierto, es que muchos se agregan su usuario al grupo de root, o sea, hacen lo mismo que en windows, y ahi chau.
Particularmente en ubuntu, sudo te deja escribir cualquier comando, lo cual es bastante "peligroso", y no contento con eso, te pone la misma contraseña que el root, cuando en ambitos de servidores esto jamas es asi.
Bueno, sacando en limpio, los usuarios IGNORANTES en el sistema gnu/linux (todos lo fuimos al principio) capaz les convendria utilizar algun tipo de antivirus o similar hasta que aprendan, si es que los virus/rootkits/spyware/malware/adware/etcetcetc son tan masivos (cosa que no creo que pase, pero nunca se sabe). Luego, cuando se consideren duchos para administrar un sistema "bien" y hayan leido mucha documentacion y manuales, cada uno bajo su propio riesgo utiliza el sistema de la manera que cree mejor. y todos contentos :D

Salu2!!

---

