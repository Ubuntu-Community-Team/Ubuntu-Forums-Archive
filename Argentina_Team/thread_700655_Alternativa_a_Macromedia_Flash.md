---
title: "Alternativa a Macromedia Flash"
date: 2008-02-18
forum: Argentina Team
---

### Post by Bizware on 2008-02-18
Hola a todos.

Soy nuevo en linux. Mi consulta es si ustedes saben de una alternativa (software libre) para el macromedia flash. He buscado mucho en los foros y solo encuentro la sugerencia de usar "wine" o el "officecrossover" para luego usar el macromedia flash. El tema es que no tengo el macromedia flash y no quiero usarlo pirateado (es ilegal) ya que por eso dejo el mundo windows y me paso al linux.

Ah me olvidaba, ya estuve viendo el Flash 4 Linux pero el proyecto está muerto por lo que se ve por sus actualizaciones.

Gracias de antemano por sus comentarios.

Bizware.

---

### Post by clasificado on 2008-02-18
> alternativa (software libre) para el macromedia flash

Que tema jodido che!

Mi opinión personal: Tal cosa no existe. No hay nada igual a macromedia flash pero libre, porque en si mismo, flash no es libre, la cosa no funciona, no hay "pago pero no pago" "igual pero distinto".

La palabra pivote en esa oración es "Alternativa":

-) Una alternativa para gráficos vectoriales es SVG. Combinado con SMIL y Scripting puede volverse muy completo.

-) Una alternativa para plugin gráfico de web es Java o Moonlight

-) Una alternativa a un entorno gráfico de dibujo puede ser Inkscape o OpenLaszlo

-) Una alternativa a usar Flash es no usar Flash. Eso es libertad.

Clasificado

---

### Post by Bizware on 2008-02-19
Ok Clasificado,

Anoche estuve mirando muchas opciones en la web, y lo más cercano que ví es usar: Inkscape + gimp para lograr las animaciones "parecidas" a M-flash.

¿Alguien tiene experiencia en haber usado estos programas para lograr resultados "dignos" (leáse: "aceptables")?


Bizware.

---

### Post by facundocorradini on 2008-02-19
Bizware: qué uso le querés dar??? 

hacer animaciones? para web?

---

### Post by Bizware on 2008-02-19
Hola facundocorradini. Gracias por preguntar.

El uso que quiero darle es para animación de sitios web. Es el uso que mas me interesa ahora. En M-flash me permite no solo la animación sino también el incorporar sonido (música más especificamente).

Estoy haciendo pruebas con Gimp + Inkscape pero no hallo la forma de hacer algo "funcional" o aceptable.

En Gimp estoy trabajando con las capas para hacer la animación pero no encuentro como agregar el sonido. Con Inkscape hago el diseño (por ahora me cuesta encontrar las opciones que necesito, pero mediante tutoriales, algun manual online y helps voy encontrando todo).

El tema es que me gustaría simplificar un poco todo esto que estoy haciendo mediante una alternativa al M-flash, no es que estoy buscando un programa que sea identico, sino uno que me permita trabajar en condiciones similares, no se si me explico bien.

Cualquier dato o ayuda (como por ejemplo como puedo añadir sonido a las capas en Gimp) se los voy a agradecer mucho, no solo porque me ayudará en el trabajo sino también porque me permitirá crecer en el mundo linux.

Un abrazo.


Bizware.

P.D.: Recalco que no quiero utilizar el Wine pues no tengo el M-flash, y no deseo usar programas pirateados, estoy mudandome al mundo linux para encontrar salidas legales.

---

### Post by atari130xe on 2008-02-19
Fijate si en este link encontrás algo que te sirva:
[http://alts.homelinux.net/task.php?task=graphics&view=alt]("http://alts.homelinux.net/task.php?task=graphics&view=alt")
suerte!:)

---

### Post by facundocorradini on 2008-02-19
Soy enemigo de Flash, trato de mantenerlo al mínimo posible en todos mis desarrollos -y ese mínimo generalmente es cero absoluto- pero bueh, 

fijate si te sirve: [http://ktoon.toonka.com/](http://ktoon.toonka.com/)

---

### Post by Bizware on 2008-02-19
Gracias a atari130xe y a facundocorradini por sus respuestas.

atari130xe te comento que estoy mirando el link que pasaste. En particular voy a examinar el CINEPAINT que está al comienzo, ya que dice que hace animación frame-by-frame.

facundocorradini mientras examino el link posteado por vos, me llamó la atención el que digas que mantenés al minimo posible el uso de animacion via flash. ¿Cómo realizas entonces los efectos que se pueden lograr con M-flash? Estuve viendo por ahí que ponderan el uso de editores SVG por ejemplo. ¿Eso usas vos cuando te es posible? Si ese es el caso... ¿qué editor (o programa) es conveniente?

Nuevamente gracias a ambos.

Saludos.

Bizware.

---

### Post by facundocorradini on 2008-02-19
Yo pq soy muy limado. 

Los sitios los hago en XHTML 1.0 strict y CSS 2, bajo estándares W3C. Le doy muchísima importancia a la accesibilidad y a la usabildad de las webs.

No hay peor enemigo de la accesibilidad y de la usabilidad -y del posicionamiento en buscadores- que el flash. 

Por eso, cuando es estrictamente necesaria algún tipo de animación, uso algún framework de javascript, como mootools.

---

### Post by leo_rockway on 2008-02-19
> **facundocorradini said:**
> 
Por eso, cuando es estrictamente necesaria algún tipo de animación, uso algún framework de javascript, como mootools.

Justo iba a comentar eso. Aclaro que no hago NADA de disenio web, pero mootools [0] y script.aculo.us[1] me llamaron la atencion porque odio flash con toda el alma.

Otra alternativa tipo ktoon seria synfig studio [2]

[0] [http://mootools.net/](http://mootools.net/)
[1] [http://script.aculo.us/](http://script.aculo.us/)
[2] [http://www.synfig.org/](http://www.synfig.org/)

---

### Post by Bizware on 2008-02-19
Sigo leyendo con atención y tratando de seguirles los pasos a sus comentarios muchachos. Desde ya gracias por continuar con sus ayudas.

Voy examinando con detenimiento lo que sugieren. Facundo, es muy bueno lo que planteas de la accesibilidad y la usabilidad, pero se complica bastante convencer al cliente de ello cuando sucede que el cliente vio la página web de su competidor que tiene una intro muy buena con imagenes que parecen de peliculas. Mirá por ejemplo el link **[www.gx.com.ar](www.gx.com.ar)**  Está hecho con M-flash. ¿Cómo lograr efectos "parecidos"? Ni qué hablar de muchísimas otras páginas cuyas intros parecen copetes de peliculas. La mayoría son bastantes pesadas para conexiones lentas, pero si el cliente la quiere así... Por eso se vuelve difícil en muchos casos convencer al cliente que piense en accesibilidad y usabilidad.

Sigo estudiando todas las soluciones que me van presentando.

Saludos para todos.

Bizware.

---

### Post by leo_rockway on 2008-02-19
Una de las razones por las que odio tanto Flash es porque cuando uso Lynx por ssh o en una maquina lenta, si la pagina esta solo en flash me quedo sin contenido. Si la pagina esta en Flash, tiene que existir al menos la posibilidad de ver el mismo contenido pero sin flash.

---

### Post by rretamar on 2008-02-20
Poco a poco la web se va pareciendo a un televisor, donde tenés que tragarte el contenido sin poder hacer nada.
Más de una vez busqué infructuosamente el botón "saltar presentación".

Pego a continuación un texto que publicaron hace mucho en Barrapunto. Para pensarlo...

>          No. Ahora sin bromas. La usabilidad de una pagina con flash cuando no tienes el plugin es 0%. Una pagina web es un texto, y flash es un binario, eso para empezar para a todos los buscadores. Luego la navegabilidad es imposible en flash. Pulsas un boton y vas de una nube a otra, pero si pulsas el boton del navegador no vuelves... Un desastre, vamos. 

pagina web 
* 1 pagina 
* texto (indexable) 
* navegable 
* barato de mantener 

pagina flash 
* 1 pelicula 
* binario (no indexable) 
* no navegable 
* caro de mantener 

Yo ni las llamaria paginas web, son.... otra cosa, pero no una pagina web. Eso si, bastante espectacular, aunque una cosa es efectismos y otra efectivadad. Flash suele perder las energias para lo segundo en lo primero. 

Antes pensaba que flash era una **curiosa herramienta** que normalmente era muy mal usada y entorpecía la navagación por pesada y lenta, ahora pienso que es **peligrosa**. 
 
 Consideremos dos hechos:
 
 - Flash es el plugin más usado en todo internet. 
 
- Flash MX, la última versión de Flash tiene nuevas herramientas para hacer scrolls, composición, transiciones entre contenidos y plugins para el plugin (llamados xtras o algo así). 
 
El resultado es que Macromedia está **fabricando un nuevo navegador** dentro mismo plugin que no depende en nada del HTML que lo contiene. El siguiente paso evidentemente es eliminar ese caparazón superfluo que son IE Mozilla u Opera, y usar una posición líder de mercado para una alternativa creíble a la navegación tradicional, una alternativa con animación 2D y 3D, sónido digital streamable, fuentes embebidas, accesos a bases de datos mediante PHP o ASP...; Ni siquiera habría que hacer grandes cambios en los servidores, quizás un módulo para Apache y otro para IIS. 
 
Personalmente, pienso que Macromedia se ha dado cuenta de que es hora de hacer otra internet, que el http se queda pequeño, nadie está sacando nuevo nada, que el aparato XML no se está traduciendo en mejoras multimedia que la gente realmente aprecia, y en cambio ellos pueden revolucionar la internet. Estaríamos ante otro tecnología de un sólo fabricante, una situación que no me atrae en absoluto, lo más peligroso es la certeza de que la gente prefiere las ventanas a la línea de comandos y los entornos multimedia interactivos al impasible HTML. Saludos !

---

### Post by facundocorradini on 2008-02-21
Bizware: 

Las intros en flash son la peor idea, van realmente muy en contra de como debe ser una web.

Si haces una intro en flash, solo la va a ver un usuario: tu cliente.  Muy probablemente, la mayoría de los usuarios apretarán el botón "saltear" tan pronto como sea posible (si es que haz tenido la gentileza de darles ese botón en html), mientras que otros tantos huirán despavoridos. 


Mi concepto de web es mucho más simple, y a la vez he logrado que sea mucho más efectivo: 
- sencillez (que hace que la gente entre y se quede)
- Usabilidad (para que el "usuario abuela" pueda usarla)
- Compatibilidad y Accesibilidad (para que todos puedan verla)
- Orientado a objetivos (que la web diga: comprá, comprá, comprá.)

Todo esto se resume en una palabra: clientes. Y esto es lo que las empresas quieren. Convencerlos de que flash no les sirve, una vez que apredés firmemente sus desventajas, es muy facil. 

------------------------------------------------

Por otra parte, hacer con mootools una web como la que mostrás de ejemplo es más que sencillo. 

Puede que te interese, por ejemplo, el accordion jquery [http://dev.portalzine.de/index?/Horizontal_Accordion--print](http://dev.portalzine.de/index?/Horizontal_Accordion--print) 

O alguno de los scripts de phatfusion: [http://www.phatfusion.net/](http://www.phatfusion.net/)

[http://www.phatfusion.net/imagemenu/](http://www.phatfusion.net/imagemenu/)
[http://www.phatfusion.net/lightbox/](http://www.phatfusion.net/lightbox/)
[http://www.phatfusion.net/slideshow/](http://www.phatfusion.net/slideshow/)


Un lindo slideshow: [http://www.electricprism.com/aeron/slideshow/](http://www.electricprism.com/aeron/slideshow/)
e2 Photop Gallery: [http://www.e2interactive.com/e2_photo_gallery/demo.php](http://www.e2interactive.com/e2_photo_gallery/demo.php)

En fín... es la tendencia actual... quedarse en flash es quedarse en el tiempo

saludos!

---

### Post by Bizware on 2008-02-22
Hola,

Estoy probando cada sugerencia que voy recibiendo. (Por eso me demore en contestar).

Facundo los links que posteaste son muy buenos. Esos efectos me van a ser de mucha utilidad. Ahora estoy buscando tomarle la mano a mootools y ver como le hago para entenderlo y usarlo. La web ya me ayudara en eso. Me va a costar bastante porque con Windows me mal acostumbre... todo era más sencillo: instalaba el programa (setup.exe por lo general) y ya estaba. Ahora tengo que buscar librerias y otras menudencias. Pero bueno, cuando me agiorne a Linux me parece que voy a poder manejarme como lo hacia con Win.

De todas formas me parece raro que no hayan hecho una alternativa a M-flash, la hay para otros como photoshop, corel, ¿cómo puede ser que no la haya para M-flash?

Sigo en la busqueda mientras procuro aprender las alternativas que me están pasando.

Saludos.

Bizware.

---

### Post by facundocorradini on 2008-02-22
Ni idea man, puede que haya alguna especie de M-flash, pero realmente lo desconzco. 


No es una cuestión de linux/ windows. Es una cuestión de dos puntos de vista totalmente opuestos sobre como se desarrolla una web.

Por un lado, tenés las desarrolladas en Dreamweaver y Flash, y por el otro las hechas "hard coding", a puro código. 

Pero mi consejo es que tomes este nuevo camino. Pronto notarás que es incluso más facil, y la calidad de los trabajos está totalmente en otro nivel: y eso hace que tu trabajo valga mucho más.

saludos.

---

### Post by rretamar on 2008-02-23
Caramba.

No conocía Motools, así que me dí una vuelta por la web para ver los demos. Impresionante lo que se puede hacer con javacript.

Saludos !

---

