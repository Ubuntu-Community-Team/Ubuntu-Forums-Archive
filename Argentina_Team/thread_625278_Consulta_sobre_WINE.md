---
title: "Consulta sobre WINE"
date: 2007-11-27
forum: Argentina Team
---

### Post by fedeavila on 2007-11-27
[FONT="Comic Sans MS"][SIZE="2"]Hola q tal gente? Como andan? Espero q bien.. 
Bueno yo aca, ya pasaron varios dias desde q me he instalado ubuntu 7.04 
e intentando instalar el 7.10 pero no es algo tan primordial.

Basicamente les cuento q andube metiendo mano a este SO tan diferente a WindowsXP, 
primero intentando buscar donde se instalaban los programas..
Me he dado cuenta q todas las carpetas del sistemas tienen nombres cortitos, mayormente de 3 letras, 
supongo q para hacerlo cool.. Me parece bien!

Con respecto a lo de los videos de youtube y el sonido bla bla bla creo q me di cuenta q me funciona a medias no por un tema de software 
sino mas bien porq tengo conectado el equipo de musica a la compu y como q no se da cuenta de eso el sistema, no se aviva.
Lo mas extraño es q lo unico q me funciona y se escucha (por suerte) es el Rhythmbox, 
todo lo otro, tomem y la otra cosa, navegadores web, etc etc no se escucha nada..
Ya no le doy tanta importancia porq directamente no le doy tanta importancia a la compu en su totalidad..

Hay algo q si me extraño y mucho y es el tema de la aplicacion WINE..
Me he instalado un par de programas como Ares y PhotoshopCS, aqllos programas indispensables en toda pc..
Como dije en mi anterior post, hay una herramienta q tiene el photoshop q otras aplicaciones no la tienen, 
estoy hablando de la "curita" una especie de clonador q basicamente tiene la funcion de "reparar" ciertos puntos de la imagen.

Yo lo uso mucho para borrar granitos o puntos negros o cualquier otra ******* q solo con ESA herramienta se puede corregir. 
El clonador generalmente te deja una marca en la imagen y se nota q hay photoshop y justamente el objetivo es el contrario, 
q parezca una imagen "al natural"

Bueno lo pude instalar perfectamente el unico inconveniente es q a la hora de marcar un "punto de origen" 
donde necesito teclear "Alt+Clic" no lo hace..

Al principio me di cuenta q haciendo eso y moviendo el punto del mouse se me movia la ventana entera, 
entonces fui a las preferencias de las ventanas y quite esa funcion..

Volvi a probar y buenisimo! la ventana no se movio! pero tampoco me marcaba el punto de origen :(

Como si el "clic" en si, no se estableciera.. 
Apreto ALT y el puntero se me pone punteado.. como preparado para q haga clic y marq el punto de origen, 
pero cuando hago el clic no pasa nada.. como q apreto ALT y se me deshabilita la funcion del clic..

En mi desesperacion hasta cometi la locura de poner el mouse para zurdos para ver si tenia algo q ver.. 
Tampoco, el clic derecho (funcionando como clic principal) tambien se me deshabilitaba y no hacia nada.

Asi q agarre, cerre el programa y apague la compu..

Luego reflexione y me dije, vamos a escribirles a los masters de ubuntu en el foro a ver q me dicen..
Prendi el estabilizador, encendi la maquina, y aca estoy.. A ver si alguien me puede ayudar..
Aunq sea para encontrar algun sustituto del photoshop (q no sea el gimp) porq lo re contra verifiq en todas y c/u de sus herramientas 
y la mas parecida era el clonador pero como q no me servia de mucho..

Haciendo a un lado eso y el tema del sonido me di cuenta tambien urgando un poco la compu (sin romper nada, creo) 
vi una cosa q me llamo un poco la atencion y hasta me dio un toq de bronca..
Me di cuenta q donde se guarda la aplicacion Wine estaba como una especie de Windows metido adentro de mi compu.. 
Encontre la unidad "C" con sus respectivas carpetillas dentro..
Cosa q me parece bastante logico.. 
Pero tambien vi, luego.. q habia una q se llama "Mis documentos" y adentro: "Mis imagenes", "Mi musica", "Mis videos".. 
y cuando me metia en c/u de ellas Oh sorpresa!.. 
Estaban todos los archivos tal y cual yo habia creado pero en la carpeta de Ubuntu (Personal, Fotos, Audio y Video) 
tonces tengo un poco de miedo de q este programa WINE me este copiando todos los archivos de la carpeta personal 
y les haga "un doble" y los ponga en la carpeta Home>Fede>.wine>Unidad-C>etc..

Como q tengo mi carpeta "Personal>Fede" y una copia de eso q se llama "Mis documentos" q lo utiliza Wine.

Por ultimo para darme cuenta me fije si todo eso no eran Accesos directos, q seria lo mas obvio.. 
Me di cuenta q no lo son, son archivos fisicos q tienen un peso y un volumen.. 
Ahora como este SO se llama Ubuntu y Ubuntu significa "hola no soy windows" 
capaz q Sí son accesos directos pero se muestran de tal manera como si no lo fueran, 
como si pesaran una X cantidad de MB (pero en realidad son enlaces y me quisiera engañar).

Tengo un humilde disco de 40 gigas por lo q me sobran 25, 
o sea q 15 gigas (digamos 10, xq en realidad no son exactamente 40 gigas en total sino 37) 
estan destinados a mis fotos, mis mp3 y algun q otro videito de coleccion..

Asi q nada.. Espero q opinen al respecto, ya sea x lo del sonido.. O por lo de Wine o por lo del sustituto del Photoshop.

Muchas gracias desde ya 
y aguante Ubuntu desde aca 
hasta q lo entienda!

Atte. Fede[/SIZE][/FONT]

---

### Post by juanman on 2007-11-28
El tema del wine: en linux existes los llamados enlaces simbolicos, q son algo parecido a los accesos directos pero más potentes, ya q no solo se puede acceder a la otra carpeta con doble click sino tambien desde cualquier programa o desde la consola. Entonces lo q ves en el Mis documentos del disco c de wine son enlaces simbolicos a la carpetas Mis Imagenes, Fotos, q estan en tu home. Es como tener una carpeta a la q se accede de 2 lugares distintos, por lo tanto, no te ocupa el espacio 2 veces... Es realmente muy útil, yo lo uso muchísimo...

[Mas info]("http://es.wikipedia.org/wiki/Enlace_simbólico")

El tema del photoshop, yo hago lo q decis con el clonador del gimp, claro q se requiere mas cuidado y esfuerzo, pero se puede...

---

### Post by facundocorradini on 2007-11-28
Hola Fede

Con respectoa lo del wine, es como te dice juan. Lo que estás viendo son enlaces simbólicos. El archivo está fisicamente una sola vez.

Lo del photoshop, estaría bueno que nos dijeras que versión de wine tenés, porque sé que en las últimas se han hecho muchas mejoras, y photoshop ha sido una de las priridades...

---

### Post by fedeavila on 2007-11-28
> **juanman said:**
> El tema del wine: en linux existes los llamados enlaces simbolicos, q son algo parecido a los accesos directos pero más potentes, ya q no solo se puede acceder a la otra carpeta con doble click sino tambien desde cualquier programa o desde la consola. Entonces lo q ves en el Mis documentos del disco c de wine son enlaces simbolicos a la carpetas Mis Imagenes, Fotos, q estan en tu home. Es como tener una carpeta a la q se accede de 2 lugares distintos, por lo tanto, no te ocupa el espacio 2 veces... Es realmente muy útil, yo lo uso muchísimo...

[Mas info]("http://es.wikipedia.org/wiki/Enlace_simbólico")

El tema del photoshop, yo hago lo q decis con el clonador del gimp, claro q se requiere mas cuidado y esfuerzo, pero se puede...
Hola che! Muchas gracias por toda la info! Si si ya me di cuenta sabes como? Fui a Aplicaciones>Accesorios>Analizador de uso de disco 
Entonces me fije en la carpeta de Home>.wine y me di cuenta que pesaba re poquito...
Y nada... Gracias master del Ubuntu! :D

---

### Post by fedeavila on 2007-11-28
> **facundocorradini said:**
> Hola Fede

Con respectoa lo del wine, es como te dice juan. Lo que estás viendo son enlaces simbólicos. El archivo está fisicamente una sola vez.

Lo del photoshop, estaría bueno que nos dijeras que versión de wine tenés, porque sé que en las últimas se han hecho muchas mejoras, y photoshop ha sido una de las priridades...
Yo instale el Wine con un programilla que se llama Automatix... Eso y un par de cosillas mas que al final las termine volando porque no las uso... Pero voy a ir directamente a la web de Wine e intentar bajarme la ultima version... Muchas gracias!!

---

