---
title: "Aplicativos de Afip"
date: 2007-07-02
forum: Argentina Team
---

### Post by jcorengia on 2007-07-02
Existe alguna forma de correr los aplicativos de Afip como el SIAP en un sistema Linux?
No puedo creer que la gente de AFIP desprecien el software libre. En un estudio contable, el único problema para instalar Ubuntu o cualquier otro Linux es correr los aplicativos que obliga la Afip para realizar cualquier trámite.
Alguien sabe como se pueden correr estos boluprogramas en Linux ?

Un Saludo
Juan Carlos

---

### Post by juanman on 2007-07-02
El SIAp segun tengo entendido funciona con una base de datos de MS Access codificada q debe ser dificil hacerla andar bien en linux bajo wine... La unica forma q seguro anda es usar una maquina virtual (como virtualbox), que levanta una maquina con windows en una ventana... Y con seamless virtualization va a parecer q se esta ejecutando sobre linux... Pero esto no es muy eficiente y vas a necesitas una buena maquina, y al fin y al cabo, seguirias usando windows (aunq solo para ese programa)...
Habria q exigirle a la AFIP q haga programas multiplataforma y no usar Access?! La peor base de datos q existe, no es para nada profesional...

---

### Post by jcorengia on 2007-07-02
Gracias por la respuesta.
Coincido plenamente en que lo más lógico sería que Afip brinde una posibilidad de usar software libre, ya que de una u otra manera está promocionando guindows ya sean oficiales o truchos.
Voy a comenzar a molestar (por así decirlo) al sector de sistemas de la Afip para ver si entran en razón.
Obviamente ya se que va a pasar con mis molestias, pero si hay una campaña y reciben miles de molestias.... quien sabe. ;)
No me critiquen mi posición de Llanero solitario debenido en Don Quijote luchador contra molinos de viento, ya lo tengo bien asumido.

Un Saludo
Juan Carlos

---

### Post by Cripton on 2007-07-02
jajajaja, es que es verdad, "deberían" hacerlos, no importa, yo te apoyo, tenés mi voto/ firma, sinó vamo' y lo' molemo' a patada'

voy a ver que onda, si se puede hacer andar o no, luego posteo algo al respecto

---

### Post by guillermolisi on 2007-07-02
+1 al SIAP bajo Linux !!

El tema es que, y aunque algunos no lo crean, la AFIP tuvo, hasta no hace mucho tiempo, software libre en sus servidores y proyectos (como el SIAP y Factura Electronica) tambien para SL.

El gran problema para este pais, y en particular la AFIP, es que M$ corrompe a funcionarios (ya sea tentandolos o accediendo a pedidos) o tuvo la suerte de tratar con corruptos, con el negocio de las licencias.

Por otra parte, la mayoria de los estudios contables corren Windows (antes era DOS) y la AFIP considera esto al momento de definir para que plataforma desarrollar sus aplicativos.

Esta conversion cultural se dara cuando la masa critica de usuarios no sea mas la de Windows y sea la de Linux. Necesariamente la AFIP, y otras dependencias/vendors/providers/etc. se vean "obligados" a darle satisfaccion a sus clientes desplegando aplicaciones que corran en SOs libres.

---

### Post by sdm_cacto on 2007-07-02
Ésto de correr una instalacion virtual de windows me tiene bastante confundido... asiq pido por facvor q alguien q la tenga clara me responda:

1-Alguien conoce una buena guia para usar VMWARE??
o cual seria el mejor soft para correr una instalacion virtual de windows??

2-hay manera de correr la instalacion windows q ya tengo en la pc desde linux??

Molte Grazie Arrivederci

---

### Post by Al_maverick on 2007-07-02
una de las soluciones seria que la afip entregue el codigo de las aplicaciones. eso se podria promover a traves de la defensoria del pueblo, con la justificacion que es informacion publica, pagada con plata de todos y que tenemos derecho a eso. despues de eso, se podria portar a linux.

El unico problema es que si mal no recuerdo, esos programas estan hechos en VB o alguna cosa peor, pero seria un principio. Y obviamente lo ideal seria avanzar a que usen protocolos libres, como QIF (de transacciones financieras) y bases de datos tambien libres.

Hmmm, ya me imagino una manifestacion de tux frente a la AFIP, y ninguno K. jajajajja!

---

### Post by marianom on 2007-07-02
Coincido y comparto. Para esta clase de operaciones ya hay organizaciones que lideran la movida y a las cuales todos podemos aportar con nuestra colaboración y voluntad (por supuesto, si estamos de acuerdo con los principios que enarbolan). Vía Libre es una de esas organizaciones. [Aca]("http://www.vialibre.org.ar/?p=3577#more-3577") les dejo un documento de interés a esta discusión. Si bien para todos nosotros lo que allí cuentan no es novedad, hay un apartado sobre la AFIP.

---

### Post by guillermolisi on 2007-07-02
Pregunto, suponiendo que alguien consigue los fuentes del SIAP, otro los porta a SL para correr bajo Linux, se supone que la AFIP no deberia j***r siempre que reciba en tiempo y en forma lo producido por esa distribucion portada (que en definitiva es su foco, la recaudacion, no con que fue realizada).

Luego esta el tema del mantenimiento ante las actualizaciones. Mas complicado porque la persona que pudo haber conseguido los fuentes en el primer caso podria no tener la misma suerte en este otro, con lo cual el SIAP Libre quedaria fuera de uso con el paso del tiempo.

Al margen de esto, el SIAP en si mismo es un contenedor de modulos. Son estos modulos los que en realidad importan (el SIAP los integra en una interface). Asi es que uno puede agregarle modulos que antes no necesitaba y continua corriendo la misma aplicacion (visualmente hablando) pero con mas funcionalidades.

Por otro lado, la AFIP deberia publicar sus algoritmos de encriptacion de las tablas de las bases de datos que utilizan los modulos del SIAP. Y esto no es negocible, a tal punto que por considerarse algo de interes nacional y que tiene que ver con la seguridad de la informacion recibida por esa Administracion, no veo posible que algun juez de este pais dictamine a favor de esa publicacion, solo porque cualquiera podria fraguar declaraciones juradas y provocarle "perdidas" en la recaudacion al fisco.


Esto incluye el algoritmo de generacion de claves fiscales, tema por demas delicado si se hace publico.

---

### Post by marianom on 2007-07-03
¿Vos me querés decir que toda su seguridad se basa en cuan secreto es el nombre del algoritmo que usan? (no creo que hayan inventado uno, deben tener una base de datos que implementa un método común y corriente al cual cualquiera tiene acceso) 
Que mala política, la security through obscurity es una mala forma de vivir la vida.

---

### Post by guillermolisi on 2007-07-03
La AFIP piensa que es lo mejor para ellos y para la seguridad del contribuyente. Cuestiones de eleccion.

No por nada cambiaron su plataforma de SL a propietario, en eso son coherentes con esa actitud oscurantista.

Recien con el tema de factura electronica han introducido XML y SSL (con certificacion digital) para asegurar los datos transmitidos.

---

### Post by jcorengia on 2007-07-03
Bueno, veo que este es un tema delicado y que tiene muchas facetas. Como usuario de los sistemas de Afip, hay otra cuestión problemática, bien tocada en la Fundación Via Libre. Al ser programas propietarios y evidentemente no muy bien desarrollados en estabilidad, tienen la manía de colgarse frecuentemente. Y casi siempre con pérdida de información. A mi me pasó hace tres días. Tira un error 3353 (no se puede leer el archivo Afip.mdb) El soporte de Afip siempre responde lo mismo. Reinstale el SIAP haciendo una copia de los archivos Afip.mdb y Afip.bak. Luego de reinstalar remplazar esos archivos en la nueva instalación. Es un circulo vicioso porque la nueva instalación también tira el error 3353. Consecuencia se pierden todos los datos y hay que empezar de cero. El tema es que el soporte es tremendamente ineficiente y no dan soluciones prácticas.

Bueno yo ya mandé dos mails pidiendo Aplicativos para Linux. Hasta ahora hay silencio total.
Sigamos molestando.... a ver que pasa.

---

### Post by Al_maverick on 2007-07-03
El tema de la seguridad es algo solucionable. Si se trata de encripcion, los algoritmos y posibilidades en ese tema son conocidas. Y no me digan que trabajar con una base Access encriptada es algo seguro porque no aguantan un script kid con una tarde aburrida.

Otro problema es la falta de pericia tecnica de la AFIP (que cualquiera que haya tenido que lidiar con el soporte de AFIP puede atestiguar, y ni hablar si se trata de la implementacion de una norma nueva) y la comodidad que les representa trabajar con codigo cerrado. Por eso propuse abordar el tema no a traves del soporte de AFIP, sino de la defensoria del pueblo, donde el tema puede tomar mas estado publico y encararse no como un tema tecnico sino como un tema de libertad individual y de difusion de informacion publica, pagada por todos nosotros.

---

### Post by Mafber on 2007-07-04
Apoyo la moción de empezar a mandarles mails e insistir que den soporte de SIAP en linux.

---

### Post by juanman on 2007-07-04
Otro voto mas para el SIAp libre!
Ahora, alguien probo al SIAp bajo wine en produccion? Lo digo porque a pesar d q yo fui el q primero respondio este post y dije q era dificil d q funque bajo wine...
Se me ocurrio probarlo xq nunca lo habia hecho y... sorpresa... Se instalo, arranco, sin ningun problema. OJO, lo unico q hice luego fue crear un contribuyente ficticio y abrir el IVA y jugue un poco y no encontre errores... Salvo que no se puede abrir la ayuda...

Alguien lo probo al SIAp bajo wine en produccion???

Aun si funcionara, creo q el programa deberia ser libre, y correr nativamente en linux y windows...

---

### Post by vk-cdg on 2007-07-05
El año pasado cursé en la facultad con un flaco que es desarrollador de soft para el ANSES, pero que trabaja en el edificio de la AFIP, cerca de los programadores de estos "maravillosos" utilitarios. 

El comentaba que esta gente no salía de Visual 6, que no sabían demasiado. En fin. Cada uno puede sacar sus propias conclusiones.

---

### Post by guillermors on 2007-07-05
Yo labure un tiempo en el estado y de puedo decir que nadie sabe nada, todo esta hecho asi nomas .Los que aprenden un poco se van a alguna empresa.

---

### Post by guillermolisi on 2007-07-05
Hable con la persona encargada de fundamentar el tema de SIAP en SL dentro de la AFIP.

Me comento brevemente que habian recibido cantidad de presentaciones sobre el tema y que a raiz de esto le asignaron generar un documento en el cual se fundamenten ventajas y desventajas, posibilidades, limitaciones, etc., de migrar la aplicacion (o los modulos) a SL.

Aparentemente parece ser que problemas politicos para llevar a cabo esta movida no hay (contrariamente a lo que yo suponia).
Uno de los escollos es la falta de personas idoneas y disponibles para llevar a cabo la tarea y la dificultad mas fuerte esta en pasar unas DLLs que fueron desarrolladas para la AFIP por terceros, que aparentemente no estan mas disponibles para apoyar la migracion.

Le comente a esta persona que una solucion seria abrir un proyecto comunitario controlado por la AFIP para resolver la cuestion humana.

Quedamos que seguiamos la charla luego, ya que los dos teniamos que continuar con otras obligaciones.

---

### Post by beuno on 2007-07-05
> **guillermolisi said:**
> 
Le comente a esta persona que una solucion seria abrir un proyecto comunitario controlado por la AFIP para resolver la cuestion humana..

Si esto fuese una posibilidad, me encantaria ayudar.

---

### Post by marianom on 2007-07-05
Definitivamente, contá conmigo también. Mantenemos por favor al tanto y avisá si tenemos que ayudar con algo en esta etapa.

---

### Post by guillermolisi on 2007-07-05
Creo que el tema de solicitar, presionar, etc., por las vias formales ayuda.

Toda esta movida necesita de un cambio cultural, sobre todo cuando quienes hacen software te dicen "es que la masa critica de la base instalada de PCs es Windows".

Hay que hacerles ver que la ola esta en marcha, creciendo y, personalmente, veo muy dificil pararla.

Por otra parte, algo que ya mencionaron en mensajes de este thread, la AFIP no se destaca por contar con personal tecnico de calidad. Son unos cuantos pocos los que estan a la altura de las circunstancias (tal vez por eso cambiaron el rumbo de SL a propietario).

Ojala se de el cambio ....

Por otra parte, el SIAP es un proyecto con origenes en los años 80 y pico/90. El movimiento de SL era mas bien incipiente frente a lo que es hoy. La gente que lo desarrollo en esa epoca estaba contratada, no era de la planta funcional de la AFIP.

---

### Post by Al_maverick on 2007-07-06
Si necesitan gente para migrarlo a C, C++, cuenten conmigo. Lo unico que pido es que me cuenten el tiempo invertido como donaciones, a ver si me baja un poco el impuesto a las Ganancias, **********! :D

Respecto a la capacidad técnica, yo tuve la experiencia de vivir la primera implementacion de factura electronica y les puedo asegurar que era horrible. Las noches en vela que me hicieron pasar por ese modelo de datos salido del infierno! :evil:

---

### Post by andy_91 on 2007-07-09
esperose concrete proyecto seria lo mas democratico el estado debe venefisiar a todos no a unos cuantos seria este caso XD pero la ola libre crece y tener compatiblidad con ambas plataformas le daria una oportunidad de crecimiento economico a las empresas y una mejor gestion de administracion unos pesos mas en el bolsillo de la empresa o de algun desonesto q se la lleve

---

### Post by alas on 2007-09-27
bueno programador en c c++ delphi java o arendo el que usen, mi mail es alastors _at_ gmail.com

---

### Post by sajnox on 2007-09-27
Hola a todos,

Sinceramente no sabia que este thread estaba abierto y recien cuando lo vi lo lei enterito enterito.

Estoy a pocas materias de recibirme de contador y si bien no estoy actualmente usando el SIAP si lo hice y tengo cierta experiencia desde el lado del usuario final. Obviamente mi ayuda no sera del lado de la programacion pero me gustaria colaborar "desde el otro lado"

Saludos a todos y encantado de que esto exista

Precisamente hoy hablaba con un amigo al que le estoy por instalar ubuntu en su maquina y me comentaba que lo que mas lo frena es el uso del SIAP y sus aplicativos.

Lo instalare en wine y vere como funciona para luego contarles, voy a ver si puedo generar un archivo y presentarlo en la AFIP  a ver que pasa. En teoria no deberia cambiar no??

---

### Post by sajnox on 2007-09-27
De nuevo yo, me quede colgado con el tema.

Comparto lo dicho de que la forma de presionar con esto seria por el lado de la justicia y no presionando a la AFIP (salvo que alguno sea el dueño de una empresa que figure inscripte como gran contribuyente nacional no creo que den importancia al tema)

Viendo que hay tanta gente interesada en el tema creo que podriamos coordinar algo un poco mas formal y darle marcha al tema. 

Ya vi que hay varios voluntarios para programar lo que es fundamental en todo esto. Algun abogado en el foro ? Alguien tienen algun amigo/hermano/pareja abogado que quiera dar una mano ? Lo de via libre es muy interesante, algun conocido por ahi para contactar?

---

### Post by jcorengia on 2007-09-28
Como no soy dueño de una gran empresa, igualmente estoy reclamando via mail y las sugerencias de la página Afip, que se pongan las pilas para implementar SIAP en plataforma Linux.
No se si sirve pero es como clavar un clavo, muchos martillazos son mejores que uno solo grande. :)

---

### Post by faktorqm on 2007-09-28
che yo lo emulo y llego hasta la parte de "verifiando modulos instalados", y ahi se me cierrra. con el wine claro. debe ser facil hacerlo funcionar, por que esa cosa trabaja con las vb runtimes me parece, y alguna que otra cosa mas, asi que voy a ver que onda si instalo ese paquete con wine tambien a ver como se porta.

por ahora llamen: ¡¡¡¡LLOREN CHIKOS LLOREN!!!!!!! 

MESA DE AYUDA AL CONTRIBUYENTE

Los usuarios de esta aplicación pueden efectuar consultas en la Mesa de Ayuda, los días hábiles de Lunes a Viernes en el horario de 8hs a 20hs, comunicándose con los siguientes números telefónicos:


(011) 4347-2103
(011) 4347-2104
(011) 4347-3152
(011) 4347-3208
(011) 4347-3209
(011) 4347-3210
(011) 4347-3589
(011) 4347-3956

CORREO ELECTRÓNICO
[email]mayuda@afip.gov.ar[/email]

salu2 gente!!

---

### Post by facundocorradini on 2007-09-28
bueno gentes, me sumo a la movida...

cualquier cosa que necesiten cuenten conmigo...

---

### Post by juanman on 2007-09-28
Gente, segun he estado leyendo y probando, el siap funciona con wine, pero fallan los modulos iva y ganancias al generar la declaracion o imprimir...

[http://www.grulic.org.ar/lurker/message/20060110.220438.e3076f31.en.html]("http://www.grulic.org.ar/lurker/message/20060110.220438.e3076f31.en.html")

En este post estaban probando con las dlls originales a ver si lo podian hacer andar, pero parece  q desistieron:
[http://preguntaslinux.org/archive/index.php/thread-3311.html]("http://preguntaslinux.org/archive/index.php/thread-3311.html")

Tambien lei por ahi rumores q con Crossover Office funcionaba bien, alguien lo probo?

Saludos

---

### Post by leo_rockway on 2007-09-28
> **juanman said:**
> Tambien lei por ahi rumores q con Crossover Office funcionaba bien, alguien lo probo?

pero ahi es lo mismo. crossover es propietario, o no?

---

### Post by sajnox on 2007-09-28
Crossover es propietario y pago, si mal no recuerdo en los repos de automatix habia una version de prueba (el limite era por dias de uso)

Si te interesan otras opciones pedimelo por privado

---

### Post by leo_rockway on 2007-09-28
> **sajnox said:**
> 
Si te interesan otras opciones pedimelo por privado

a mi? no... yo ni siquiera necesito los aplicativos afip, solo estaba siguiendo el hilo y comente lo de crossover porque me parece que no seria una alternativa real.

yo tengo cedega, wine y una instalacion de xp (real, no virtual) y nunca uso ninguno de los tres :lolflag:

gracias de todas formas.

---

### Post by juanman on 2007-09-30
Puede ser una solucion temporal. El problema de muchos contadores es q no pueden migrar a Linux xq no pueden correr el SIAP, si anda con crossover podrian...
Crossover es cerrado, pago (40 dolares) y tiene una demo por 30 dias...

---

### Post by marianom on 2007-09-30
Que bueno que reflotó este thread (¡bien por ese entusiamo Miguel! -tengo un par de mails tuyos para responder, lamento la demora-).

Creo que la forma de avanzar con algo que sea mínimamente viable es crear la aplicación y mostrarla, si la aceptan como opción viable será tiempo bien invertido en una gran causa, si no la aceptan, habremos perdido tiempo pero no la causa.

Seguramente hay partes que no podremos descifrar porque están hundidas en el código compilado pero tampoco estoy pensando en una aplicación 100% funcional, sino una demostración lo más cercana posible a algo de calidad de producción. Lo que falte, será a cambio de las fuentes del programa original para replicar el funcionamiento (y quien te dice que no, mejorarlo).

Ahora bien, no conozco la aplicación así que mi opinión se basa en el sentido común, supongo que se puede armar 2 grupos básicos: los analistas funcionales que usan la aplicación y entienden contabilidad (la pasé con un 6 de lástima tooodo el secundario) y aquellos que sabemos programar y podemos crearla guiados por los primeros.

Bueno, les dejo el tema en la mesa para que les caliente los dedos y antes que todo, seamos concientes de los grandes riesgos que esto tiene:

1- ponernos de acuerdo en una plataforma de trabajo común para la aplicación (¡¡yo voto por python!!): no será fácil: cada uno sabe lo que sabe y, a veces, amamos fanaticamente lo que sabemos.
2- constancia: aquellos que llevamos un tiempito (y con mucha humildad lo digo: he sido un lurker más tiempo que participante) en la comunidad del soft libre sabemos que mucha gente abandona cualquier proyecto bastante rápido: por aburrimiento, por necesidad, por enojos, por urgencias, etc. Muchos proyectos de soft libre lo terminan haciendo dos, tres personas (y muchas veces uno solo). Si vamos a hacer algo, que nadie pierda su tiempo.

Espero sus comentarios con respecto a este propuesta. Con tiempo lo podemos charlar.

---

### Post by Pse on 2007-09-30
> **marianom said:**
> 
1- ponernos de acuerdo en una plataforma de trabajo común para la aplicación (¡¡yo voto por python!!): no será fácil: cada uno sabe lo que sabe y, a veces, amamos fanaticamente lo que sabemos.
2- constancia: aquellos que llevamos un tiempito (y con mucha humildad lo digo: he sido un lurker más tiempo que participante) en la comunidad del soft libre sabemos que mucha gente abandona cualquier proyecto bastante rápido: por aburrimiento, por necesidad, por enojos, por urgencias, etc. Muchos proyectos de soft libre lo terminan haciendo dos, tres personas (y muchas veces uno solo). Si vamos a hacer algo, que nadie pierda su tiempo.


1. Me inclinaría por C# (sobre Mono). Excelente compatibilidad con plataformas MS + aguante de Novell (mucho menos riesgo a futuro). Esto importa, particularmente si se pretende reconocimiento oficial de un ente gubernamental.
Si esa opción no es viable, C++ o Python serían mis primeras elecciones.

[EDIT]
Algo fundamental a tomar en cuenta a la hora de la elección del lenguaje es tomar nota de los requerimientos sobre los cuales se va a apoyar el programa, de manera tal que no se termine alienando a una buena parte de los usuarios actuales del sistema (lo cual representaría un serio problema para la AFIP y claramente dejaría de hacer viable al proyecto).
Los factores limitantes en la elección del programa son la base de datos y la interfaz gráfica (y tal vez el módulo criptográfico, pero no estoy seguro de qué manera debería implementarse esto). Quizás los que conocen mejor Python puedan fijarse cuáles son las opciones más viables para cada caso dentro del lenguaje. PyGTK probablemente sería lo más adecuado, aunque si no recuerdo mal eso crearía limitaciones en relación a las plataformas MS sobre las cuales podría correr el programa (¿cuál es el estado del port a Windows? ¿Cuál es la librería GTK mínima soportada por PyGTK? (creo que Win98 es poco soportado por versiones de GTK mayores a la 2.6 ó 2.8 )).
Con C++ todas las bases están cubiertas, salvo la parte gráfica, en la que se cae en el mismo problema que con Python. El soporte multiplataforma para sistemas antiguos es limitado.
Con .NET no sé qué tan bien se está. Supongo que el soporte de .NET 1.1 y 2.0 es completo en todas las plataformas MS a partir de Win98, mientras que en los UNIXes está Mono, lo cual simplificaría la cuestión.

---

### Post by tzulberti on 2007-10-01
Como estoy en otras listas de mail, puntalmente en el LugFi (Lug de Facultad de Ingenieria de Buenos Aires), ahi justo se hablo sobre ese tema, alguien dijo que se estan pasando los programas para que tengan una interface web. Se dio una presentacion sobre este tema, y la misma se puede bajar aca: 
[http://jornadas.grulic.org.ar/7/contenido/programa/charlas/charla151](http://jornadas.grulic.org.ar/7/contenido/programa/charlas/charla151)

hilo del tema:
[http://listas.fi.uba.ar/pipermail/lug/2007-September/026087.html](http://listas.fi.uba.ar/pipermail/lug/2007-September/026087.html)

Saludos,
TZ

---

### Post by sajnox on 2007-10-01
Hola,

Me alegro que el tema haya prendido, y hace rato que me quede con esto en la cabeza y hay algunas cosas que me gustaria compertir con UDS.

Por lo que veo hay dos caminos abiertos, uno es empezar a programar los aplicativos de la AFIP y darselos medianamente hechos para que lo vean y empezar a "negociar", la otra es ejercer algun tipo de presion para que la misma AFIP lo haga.

En cualquiera de los dos casos lograrlo  seria una "victoria", pero yendo un poco mas alla, cual es el verdadero proposito de todo esto? entiendo que la promocion del software libre y de mostrar que hay otras alternativas. En este escenario les digo "no solo del aplicativo de la AFIP" vive el contador". 

Me plantee lo siguiente: Voy a ver a un contador y le digo: "Sr. Contador no le interesa migrar sus equipos informaticos a SL?" seguramente me preguntaria "y que ganancia/ventaja tengo?" a lo que podria nombrarle infinitas ventajas y todas cosas que ya sabemos, para que me termine preguntando "y el software contable de mi cliente? las aplicaciones de errepar?" Y calculo que le tendria que responder que lo podria hacer con wine y tendria que meterlo en un lio que hoy no tiene.

Esto lo digo con la intencion de ver como comunidad podemos generar ideas y propuestas para implementaciones reales que cubran las necesidades concretas de determinadas profesiones (tomo la del contador por que es la mia y es la que conozco un poco mas, pero me intereso por todas). Seguro que si el SL empieza a crecer las compañias que desarrollan soft lo empezaran a hacer con soporte para Linux pero por el momento es solo una utopia.

Tomas lei el thread de los Lugfi y si bien hablan de migrar a programas basados en la WEB me parece bastante poco serio el planteo debido a que no todo el pais tiene el acceso a internet que puede haber en las grandes ciudades, y legalmente le veo algunas limitaciones al dia de hoy.

Obvio que me propongo como usuario evaluador de lo que se haga y ademas le acercare la propuesta a un par de amigos para que tambien lo evaluen.

Gracias por su tiempo, eran las ganas de tirar un par de ideas

Saludos

---

### Post by marianom on 2007-10-01
Cool then. Si hay web services disponibles la mitad del laburo está hecha. Solo hace falta una GUI simpatica para conectarse y usarlos y listo el pollo.
Ahora, esos ws son para la parte de factura y/o para la otra aplicación también? Alguien que me explique la diferencia entre facturas y el otro sistema que no entiendo nada.

Voy a ver que puedo conseguir sobre lo que se presentó en las jornadas de soft libre.

---

### Post by Mafber on 2007-10-01
Hola!!! Sobre el lenguaje tengan en cuenta que debería funcionar en pcs muy viejas (k6 o pentiums y por qué no decir en 386).
Con respecto a lo que planteas Sajnox, tenés razón en que el SIAP es solo una parte de un conjunto cliente&#8211;contador. Igualmente creo que si se logra que AFIP de soporte en Linux, seria un catalizador para que los programadores tengan un incentivo para hacer lo suyo.
Marianom: que es lo que no entendes de las facturas? ¿lo de A, B o C?

-Si sos "responsable inscripto" emitis facturas A o B dependiendo a quien le estas vendiendo (facturando) :
                 # si le estas facturas a otro inscripto le emites factura A. 
                  #si le vendes a a otro que no se inscripto (exento, monotributista, consumidor final) le das factura B.
-Si NO sos "responsable inscripto" emitís únicamente facturas C y no importa a quien le vendas.
La distinción tiene que ver con el IVA y la discriminación de este.

---

### Post by marianom on 2007-10-01
Hola Mafber. Mi duda es con respecto a los 2 sistemas que parecen nombrar: uno de ellos es el SIAP y he visto que mencionan algo sobre Factura ¿Electronica?. Parecen ser 2 sistemas o módulos y la verdad es que no se de que tratan ninguno de ellos.

---

### Post by Hei Ku on 2007-10-01
> **Pse said:**
> 1. Me inclinaría por C# (sobre Mono). Excelente compatibilidad con plataformas MS + aguante de Novell (mucho menos riesgo a futuro). Esto importa, particularmente si se pretende reconocimiento oficial de un ente gubernamental.
Si esa opción no es viable, C++ o Python serían mis primeras elecciones.


Deberías leer la letra chica de ese acuerdo, porque la "proteccion" de Novell sólo corre para los clientes de Novell. 
Personalmente, no me gusta que vengan y me digan: "Sería una lástima que algo malo le pasara a ese lindo código, pero nosotros podemos "darte protección" ;) " :lolflag:

En ese sentido, creo que C++ ofrece la mejor opción de portabilidad, con alguna base de datos embebida como SQLite. (Firefox va a usar SQLite para los bookmarks en su versión 3, para más datos)

---

### Post by Hei Ku on 2007-10-01
> **marianom said:**
> Hola Mafber. Mi duda es con respecto a los 2 sistemas que parecen nombrar: uno de ellos es el SIAP y he visto que mencionan algo sobre Factura ¿Electronica?. Parecen ser 2 sistemas o módulos y la verdad es que no se de que tratan ninguno de ellos.

Factura electronica es en realidad un móduio que permite firmar los archivos de factura electronica de las empresas que generan ese tipo de fáctura. Es en realidad un módulo dentro del SIAP, o al menos era así hasta hace un par de años. El SIAP es en realidad como un programa básico donde se le pueden agregar distintos módulos: ganancias, bienes personales, devolución de IVA por exportaciones, etc. Es la "madre de todos los programas de la AFIP", por así decirlo.

Si bien me tocó participar en uno de los primeros proyectos de fáctura electrónica, las cosas pueden haber cambiado desde ese tiempo, así que pueden corregirme.

---

### Post by marianom on 2007-10-01
> **Hei Ku said:**
> Deberías leer la letra chica de ese acuerdo, porque la "proteccion" de Novell sólo corre para los clientes de Novell. 
Personalmente, no me gusta que vengan y me digan: "Sería una lástima que algo malo le pasara a ese lindo código, pero nosotros podemos "darte protección" ;) " :lolflag:

¿La [GPLv3]("http://www.groklaw.net/article.php?story=20070828105447144") no soluciona eso? Igual Mono no es muy popular en el mundo del soft libre y me parece que elegirlo es abrir otro desgastante frente de batalla (por razones que obviamente no tienen nada que ver con las capacidades de Mono en si o las ventajas que se mencionan).

> **Hei Ku said:**
> En ese sentido, creo que C++ ofrece la mejor opción de portabilidad, con alguna base de datos embebida como SQLite. (Firefox va a usar SQLite para los bookmarks en su versión 3, para más datos)

Bueno, yo hace bastante que estoy loco por hacer algo con [XulRunner]("http://developer.mozilla.org/es/docs/XULRunner")+[pyXpCom]("http://developer.mozilla.org/en/docs/PyXPCOM")
(con un lindo sqlite embebido) pero todos piensan que no vale la pena.

---

### Post by tzulberti on 2007-10-02
Mientras den un poco de tiempo para aprender la tecnologia a usar, lo que usemos me es indeferente. 
Me les uno no importa que lenguaje eligan (se algo de C++, y una punta de python).

Saludos,
TZ

---

### Post by Pse on 2007-10-02
> **Hei Ku said:**
> Deberías leer la letra chica de ese acuerdo, porque la "proteccion" de Novell sólo corre para los clientes de Novell. 
Personalmente, no me gusta que vengan y me digan: "Sería una lástima que algo malo le pasara a ese lindo código, pero nosotros podemos "darte protección" ;) " :lolflag:
Es una preocupación válida la tuya, pero no te referiste a las cuestiones técnicas que enumeré en el post anterior. Si la cuestión de las patentes es lo que te preocupa, la única parte del proyecto que se vería comprometida sería la interfaz gráfica, y eso sólo si se usa WinForms (C# y la CLI son estándares por sí solos). En todo caso, si tal barbaridad llegase a ocurrir, lo único necesario sería reconstruir esa parte del código en otra cosa, como GTK#, y eso sólo para los clientes que corran en plataformas NO MS (es decir, todos aquéllos que estén usando Windows NO se verían comprometidos). Insisto, sólo para los NO MS. ¿Por qué? Porque no es tu código lo que se ve comprometido, sino Mono como runtime. Si se usa .NET tranquilamente se puede saltar a plataformas de desarrollo MS. A eso me refiero con "seguridad a futuro". No hay manera de que el entorno quede abandonado.

> 
En ese sentido, creo que C++ ofrece la mejor opción de portabilidad, con alguna base de datos embebida como SQLite. (Firefox va a usar SQLite para los bookmarks en su versión 3, para más datos)

Estoy de acuerdo con la base de datos. Cualquier cosa, PostgreSQL, SQLite, incluso una Berkeley DB sirve. La rapidez con la que se pueda implementar el código es lo importante en este caso (léase: "la API"), ya que no me parece que haga falta hacer cosas muy avanzadas con la base de datos en sí.
Con respecto a C++ y el tema de "portabilidad", insisto con lo dicho anteriormente. Yo estoy de acuerdo, C++ es una opción, se puede hacer en eso, sí, pero hay una limitación grosera: soporte a plataformas antiguas. ¿Cómo proponés dar soporte a Windows y Linux en cada módulo del programa sin duplicar código usando sólo C++? Y aclaro, Windows no es 2000, no creo que la AFIP quiera colgar a todos los que siguen con 98. Leé mi post anterior.

> ¿La GPLv3 no soluciona eso? Igual Mono no es muy popular en el mundo del soft libre y me parece que elegirlo es abrir otro desgastante frente de batalla (por razones que obviamente no tienen nada que ver con las capacidades de Mono en si o las ventajas que se mencionan).
¿No es popular? Para los amigos de Ubuntu Feisty:
```
dpkg -l | grep mono
```
¿"Desgastante frente de batalla"? ¿De qué me estás hablando? C# y la CLI son estándares. IronPython, F-Spot, Beagle, Banshee, GTK#, IKVM, WTF?! Si hay algo que .NET logró es tremendo soporte de la comunidad libre, incluso a pesar de estar asociado a MS. Incluso yo me sorprendo de que haya tanto soporte en *tan poco tiempo* y de proyectos tan variados, e incluso de tan buena calidad.

Mencionaste los gustos personales. Hey, yo en general prefiero evitar .NET, pero los méritos que tiene para este proyecto son innegables.

Con respecto a XUL, no lo había pensado, puede ser una buena opción. Pensá en los sistemas en los que debe andar el proyecto, ¿qué tal funciona ahí? ¿Cuál es el grado de productividad alcanzable utilizándolo?

Por último, sí, una plataforma web sería ideal para esto, y, de hecho, solucionaría más de uno de los problemas que se han planteado hasta acá.

Con respecto a lo del soporte para 386, 486, Windows 3.1. Olvídalo, eso sólo si se hace en web, y hasta ahí es dudoso, dependiendo del browser que puedas usar. Si se quiere dar soporte a esas plataformas, tiene que ser a través del software viejo.

---

### Post by Hei Ku on 2007-10-02
Dejé de leer con atención en la parte que sugerís .NET y hablas del soporte que tiene de la comunidad libre. El resto cae bajo la definición de troll. Algo que parece cierto, pero en realidad no lo es.

Si querés un entorno realmente libre y de ámbito empresarial, se puede utilizar Java. Los runtimes son libres, los ambientes de desarrollos son libres, y tenés la posibilidad de hacerlo web o swing, que es verdaderamente multiplataforma.

En definitiva, la opción del lenguaje queda a elección de las personas que vayan a realmente poner los dedos en el teclado. Sólo creo que si es una idea que sale de este foro, sería bueno que siga los lineamientos de software libre (como en libre expresión). Lo siguiente es llegar a la mayor cantidad de gente, que después de todo es el sueño de todo programador, que su programa lo use todo el mundo. Para eso existen varias opciones de lenguajes y bases de datos, todas ellas libres. Dentro de esas, es eleccion de los que pongan los deditos en el teclado.

Pido disculpas por el tono fuerte del post, pero hay cosas que me pareció importante aclarar.

---

### Post by marianom on 2007-10-02
(Aca es donde me está faltando un moderador más porque yo ya opiné y es posible que mis comentarios no sean vistos como objetivos).

Pse, 2 aclaraciones:

1- tené en cuenta que yo soy fanatico de Tomboy así que uso programas mono sin problemas (e Icaza hasta me cae simpatico). La acepción de la palabra "popular" no estaba en cuantos proyectos se están desarrollando con mono (perdé cuidado que sé cuales son) si no más bien en lo poco que lo veía como lenguaje sugerido/en utilización en los círculos de soft libre en los cuales me muevo (no son muchos pero tampoco son pocos). Eso me daba la pauta que iba a ser más complicado encontrar desarrolladores en mono que en, por ejemplo, python. 

2- "Frente de batalla": otra vez, el círculo en el cual me muevo, si yo/cualquiera me pongo a promocionar un soft libre como el que estamos charlando aca (ver el contexto: afip, gobierno, soft libre, etc, etc), buscando testers, desarrolladores, usuarios, etc, a mi me parece que el mono va a ser un píldora dificil de tragar en muchos casos,algo que no pasaría con otros. ¿Injustificada mala fama? ¿FUD? ¿Fanaticos irascibles? Puede ser (o puede no serlo: no estamos acá ni somos quienes para debatir lo bueno y malo de mono). A eso me refiero con el "desgastante": además de todos los problemas que vas a tener por convertir una aplicación cerrada de código propietario a libre, tenés que lidiar con ese extra. 
 
Obvio que mis puntos son rebatibles y están viciados por mi experiencia (al fin de cuentas es una opinión). Te pido que no lo tomes como una afrenta hacia mono, no es mi estilo. 

Por el resto de los temas, vamos a dejar que las cosas se calmen un poco en este thread, no? Vean la situación de esta forma... si ya nos estamos agarrando a las piñas ahora que no hemos hecho nada, ¿qué quedará para el día que -hipoteticamente- hagamos algo?

¡Abrazo fiscal!

---

### Post by Pse on 2007-10-03
> **Hei Ku said:**
> Dejé de leer con atención en la parte que sugerís .NET y hablas del soporte que tiene de la comunidad libre. El resto cae bajo la definición de troll. Algo que parece cierto, pero en realidad no lo es.
Mmh... mirá, no estoy de acuerdo. Entiendo que quizás el tono del post pueda sonar un tanto fuerte o incluso arrogante pero no deberías confundirlo con algo carente de argumentos. Mi objetivo no es crear una discusión (que vendría a ser, en efecto, la definición de troll), sino más bien presentar argumentos técnicos válidos. Que el grado de retórica te resulte excesivo quizás se deba a que suelo frecuentar lugares en los que hacer un argumento fuerte y válido es interpretado simplemente como un alto grado de compromiso por resolver el problema y no como una actitud que busca desvalorizar la postura del otro. Te aclaro: más que tener razón, me interesa resolver el problema. El problema acá no es "elegir el lenguaje porque me gusta", sino más bien fijarte qué plataforma de desarrollo (y fijate que no digo "lenguaje") es la más conveniente y productiva para el caso. Yo te dije cuál me parece que se ajusta mejor y por qué. Si en cambio vos tenés alguna otra preferencia, estaría copado que la justifiques, de manera que yo, y todos los demás, podamos ver por qué te parece que es válida. Ya te dije cuáles son las complicaciones de lo que parece ser tu elección; si hay algún elemento que no te quedó del todo claro, o incluso, que te pareció poco justificado, estaría bueno que lo preguntes, y te voy a dar mi respuesta. Si en cambio elegís concentrarte en la redacción de lo que digo, bueno, no puedo hacer más que responderte esto. Claramente no te puedo aportar mucho así.

De cualquier manera, y a pesar de que te moleste, sería bueno que termines de leer mi post porque hay buenos argumentos sobre otras cosas que también se mencionaron (luego de la parte de .NET) y que tal vez te puedan interesar.

> 
Si querés un entorno realmente libre y de ámbito empresarial, se puede utilizar Java. Los runtimes son libres, los ambientes de desarrollos son libres, y tenés la posibilidad de hacerlo web o swing, que es verdaderamente multiplataforma.
Java no es una opción hasta que se pueda confiar en una VM realmente liviana. Esto sí tiene que ver más con experiencia personal que con otra cosa, pero la idea de un Windows 98 corriendo un programa de Java con una base de datos embebida no me ilusiona. Menos si usa una interfaz Swing (léase: no nativa).
Sería posible usar código pre-JITeado, pero si se va a hacer eso, es preferible usar un lenguaje compilado y ya (C++, o lo que te guste).
Podría decirse también que usar Java es comparable a correr sobre .NET, que, en efecto, es re-JIT; pero, y de nuevo lo digo de manera anecdótica, me resulta más liviano tanto Mono como la .NET framework. Desde luego, usar .NET con WinForms tendría la ventaja de usar una interfaz gráfica nativa, lo que IMHO mejoraría el rendimiento considerablemente en comparación con Java. También tenés la cuestión de la interoperabilidad con código externo (lo cual es particularmente importante si se va a utilizar alguna librería para proveer alguna función extra al programa). En esto .NET es un poco más laxo y presenta menos restricciones que Java, por lo cual me parece que es un poco más conveniente.

Por último, las características que le atribuís a Java las comparte C#: los runtimes son libres (mono), los entornos de desarrollo son libres (mono), y de yapa, la especificación de C# es estándar (ISO y ECMA) al igual que la CLI. Desde ya, qué pensarás si te digo que hay implementaciones de Java sobre .NET.

Creo que una buena propuesta a favor del lenguaje que mencionabas en alguno de tus posts, C++, sería utilizar wxWidgets (ya que mi argumento en contra es la falta de compatibilidad con sistemas antiguos). Hay que ver cómo viene la mano por ahí con esa librería. Lo mismo que con XUL, que era lo que mencionaba marionom.

> 
En definitiva, la opción del lenguaje queda a elección de las personas que vayan a realmente poner los dedos en el teclado. Sólo creo que si es una idea que sale de este foro, sería bueno que siga los lineamientos de software libre (como en libre expresión). Lo siguiente es llegar a la mayor cantidad de gente, que después de todo es el sueño de todo programador, que su programa lo use todo el mundo. Para eso existen varias opciones de lenguajes y bases de datos, todas ellas libres. Dentro de esas, es eleccion de los que pongan los deditos en el teclado.
Desde luego, pero más importante que el lenguaje en sí, como impliqué en lo que te decía arriba, es la plataforma de desarrollo. Vos tenés que ponerte del lado de la AFIP ('tá bien que seguramente no hay mucha gente ahí que le dé pelota a esto, pero bue), y asegurarte una plataforma bancada por grandes empresas tiene sus ventajas. Más aún, usar .NET no te limita a un lenguaje (que parece ser lo que te interesa). Si hoy hacés esto en C#, mañana podés usar Python y Java si querés. Esa es la magia de .NET. No limitarte a un lenguaje, todo es interoperable. IronPython, IronRuby, C#, C++/CLI, Java, incluso Visual Basic (sí, sobre Linux, god). Igual, si la gente de la FIUBA opinó que lo mejor es orientarlo a una plataforma Web, por algo será. Es válida su interpretación del problema.

Con respecto a la cantidad de gente, este es el típico proyecto de alcance selectivo. El que participe no debería esperar grandes reconocimientos en el mundo open y/o free. Sin embargo, visto que en Argentina estas cosas son novedosas, tal vez algún reconocimiento de la comunidad hay. Igual, me parece lo de menos eso, por lo menos en el comienzo. La motivación del proyecto debe ser otra.

Por último, estoy totalmente de acuerdo en que si sale algo, ese algo debería respetar seguir los lineamientos del software libre y abierto. Esta ya es más una cuestión ideológica, pero no le daría importancia de otra manera.

> Pido disculpas por el tono fuerte del post, pero hay cosas que me pareció importante aclarar.
Por mí lado está todo bien :)

---

### Post by Pse on 2007-10-03
> **marianom said:**
> (Aca es donde me está faltando un moderador más porque yo ya opiné y es posible que mis comentarios no sean vistos como objetivos).
Yo veo como 20 ahí abajo cuando entro al foro, ¿hacen falta más? :shock:
Te pido disculpas por haber respondido, pero se ve que mientras escribía vos estabas posteando y por eso no vi tu último post. Así que bue, como ya pisé el charco, aprovecho para responderte otras cosas :) Todo técnico, no te preocupes.

> 
1- tené en cuenta que yo soy fanatico de Tomboy así que uso programas mono sin problemas (e Icaza hasta me cae simpatico). La acepción de la palabra "popular" no estaba en cuantos proyectos se están desarrollando con mono (perdé cuidado que sé cuales son) si no más bien en lo poco que lo veía como lenguaje sugerido/en utilización en los círculos de soft libre en los cuales me muevo (no son muchos pero tampoco son pocos). Eso me daba la pauta que iba a ser más complicado encontrar desarrolladores en mono que en, por ejemplo, python. 
No sé a qué te referís. Mono corre Python ([link]("http://www.codeplex.com/Wiki/View.aspx?ProjectName=IronPython")) , y muchas otras cosas extremadamente bizarras (F# anyone?). Así que no sé por qué decís que sería más ****** encontrar gente que programe para Mono que gente que programe para Python. Después de todo ésta era una de las ideas de Microsoft cuando hizo la .NET framework. 
Igual me interesaría saber a qué te referís con eso de que Mono no es muy bien visto. ¿En qué proyectos de soft libre te movés? Es cierto que ha habido un cierto backlash desde el acuerdo de Novell con MS (ojo, me parece desecrable el acuerdo, eh), pero en general eso estuvo orientado a Novell, no tanto a Mono. Por lo menos yo no vi a nadie diciendo "ah, no, ahora no toco más .NET ni Mono". Por el contrario, cada vez veo más gente metida en esto (y mirá que a mí todo lo que use un JIT realmente no me atrae, ¿pero qué le voy a hacer? Hay mérito).

> 
2- "Frente de batalla": otra vez, el círculo en el cual me muevo, si yo/cualquiera me pongo a promocionar un soft libre como el que estamos charlando aca (ver el contexto: afip, gobierno, soft libre, etc, etc), buscando testers, desarrolladores, usuarios, etc, a mi me parece que el mono va a ser un píldora dificil de tragar en muchos casos,algo que no pasaría con otros. ¿Injustificada mala fama? ¿FUD? ¿Fanaticos irascibles? Puede ser (o puede no serlo: no estamos acá ni somos quienes para debatir lo bueno y malo de mono). A eso me refiero con el "desgastante": además de todos los problemas que vas a tener por convertir una aplicación cerrada de código propietario a libre, tenés que lidiar con ese extra. 
Justamente en este contexto (gobierno/AFIP) es dónde mejor veo parado a .NET. ¿Por qué? Porque lleva el nombre "MS" pegado (que parece ser irónicamente el problema acá).
En cuestión de usuarios, más ****** que pedirle a un flaco que instale Python (y todas las librerías que se utilizarían) en Windows no puede ser. En Linux, Mono se consigue (o directamente viene) para cualquier distro.
En razón de devs, la verdad .NET es una de las cosas que más veo que se pide en acá (en conjunto con C++, Java y Web), así que imagino que más de uno estará familiarizado con la plataforma.
Igual no niego que pueda haber una cierta negativa de más de uno a usar la plataforma (por cualquiera de los motivos que vos ya mencionás). Sinceramente, en razón de los claros beneficios con los que viene esto, me parece que es un buen compromiso. IMHO, las desventajas de las otras opciones son más preocupantes. La única que (por ahora) me convence tanto como .NET es una plataforma Web.

> 
Obvio que mis puntos son rebatibles y están viciados por mi experiencia (al fin de cuentas es una opinión). Te pido que no lo tomes como una afrenta hacia mono, no es mi estilo. 
Para nada, ni Mono ni .NET son mi estilo :)

> 
Por el resto de los temas, vamos a dejar que las cosas se calmen un poco en este thread, no? Vean la situación de esta forma... si ya nos estamos agarrando a las piñas ahora que no hemos hecho nada, ¿qué quedará para el día que -hipoteticamente- hagamos algo?

¡Abrazo fiscal!
Ah, por esto te pido disculpas. Como te dije antes, posteé justo después de que vos escribieras lo tuyo y no lo vi.
Bueno, en fin, voy a tratar de seguir el thread, y si las charlas siguen en el momento que a vos te parezca adecuado, responderé.

Bye.

---

### Post by Hei Ku on 2007-10-03
Entendé que en primer medida es una cuestión de principios, la plataforma .NET está contaminada de propiedad intelectual, patentes y amenazas de MS. Realmente me cuesta, como programador de software GPL en Linux, pensar en programar en la plataforma de una empresa que formula constantemente amenazas hacia nosotros.

En el aspecto técnico, C y C++ gana en performance y portabilidad a ojos cerrados. Todas las plataformas lo corren y lo corren más rápido. Con una arquitectura orientada a servicios, se puede hacer el núcleo de la aplicación agnóstico a la interfaz, hacer una interfaz para todas las plataformas modernas (QT de KDE y GTK de Gnome corren en todas esas plataformas), otra para plataformas mas viejitas, y si les parece una web, para aquellos casos que es imposible correrlo localmente.

En cuanto a python sobre 98, depende, porque el framework .NET tampoco es nativo de 98, asi que ahi dependera de cada implementacion. Pero no todos los 98 tienen el framework .NET, ni todos los win 2000, o si lo tienen, tienen que actualizarlo, porque MS la compatibilidad.

En cuanto a Java, la versión 6 tiene optimización en tiempo de compilación, o sea que la performance ha mejorado mucho, aunque personalmente prefiero la capacidad de multiplataforma, que optimizaciones locales por tratarse de una interfaz "integrada" al sistema (como dije, .NET no es nativo en 98, 95 o 2000, asi que esta integracion no es tan cierta como parece).

En cuanto a conexión con código externo, la cantidad de código externo libre disponible para Java, C y C++ supera ampliamente a .NET, y con licencias mucho más claras en cuanto a su uso (GPL, BSD, Apache, etc.) respecto a .NET (shared source, permissive license) Solo pueden fijarse en Sourceforge para esto.

Respecto a Mono, no sería mi primer opción usar un lenguaje sponsoreado por Novell y cuyo líder opina que "OOXML es un protocolo excelente" y trata de copiar cada cosa que hace MS (Silverlight, etc.) , pero esto es cuestión de principios personales.

Personalmente, creo que la discusión debería retomar los carriles de si es viable hacerlo, y quiénes, antes de volver sobre la discusión de plataforma.

---

### Post by marianom on 2007-10-03
> **Pse said:**
> Yo veo como 20 ahí abajo cuando entro al foro, ¿hacen falta más? :shock:
Pero el único que modera en castellano esta parte, hoy por hoy, soy yo.

> **Pse said:**
> 
Bueno, en fin, voy a tratar de seguir el thread, y si las charlas siguen en el momento que a vos te parezca adecuado, responderé.
Realmente no entendí que quisiste decir.

---

### Post by LaHire on 2007-10-03
Sería interesante ver un SIAP web. (pero seguro va a ver despelote por el tema de transmisión de datos, aunque seguro estoy diciendo blasfemias.

Por cierto, 
C++ , Java o Python?

los tres son excelentes lenguajes...y cada uno sabrá uno más que el otro (yo cuando quise compilar C++ a mi pc le salieron patitas eh intentó escaparce. por suerte soy más rapido)...pero me inclino (personalmente) por Python

no soy programador "profesional" ni mucho menos, lo único "salvable" que hice fue un convertidor de unidades totalmente alocado (de km a pársec, por ej.)...y bueno

Solo decía que, entre los 3, es le lenguaje más "fácil de aprender", y , creo yo, si trabajamos en conjunto, es el mas sencillo de entender para todos (principalmente porque se lee como pseudocódigo y no cuesta aprenderlo)

pero bueno, discusión acerca de que usar o no, primero hay que organizarnos ( a lo que voy: una forma de comunicarnos, como el IRC o una mail-list aparte), entendernos y compartir :P

Por cierto, vamos a usar Launchpad? :P


Bueno, es mi opinión, espero q no moleste a nadie :)

---

### Post by Pse on 2007-10-03
> **Hei Ku said:**
> Entendé que en primer medida es una cuestión de principios, la plataforma .NET está contaminada de propiedad intelectual, patentes y amenazas de MS. Realmente me cuesta, como programador de software GPL en Linux, pensar en programar en la plataforma de una empresa que formula constantemente amenazas hacia nosotros.
*Sigh*
Mirá, a partir de tus útlimos posts estoy empezando a creer que esto tiene más que ver con una cuestión emocional que con algo político o técnico. Igualmente voy a tratar de ponerte en claro por dónde viene la mano. ¿Hay partes de .NET que corren riesgo por patentes? Sí. ¿Se usaría alguna de ellas? Yo propongo una: WinForms. ¿Alguna otra? No. ¿Necesitás estar seguro? [Link]("http://www.mono-project.com/FAQ:_Licensing#Could_patents_be_used_to_completely_disable_Mono.3F"). ¿Es un compromiso aceptable para este proyecto? Sí. ¿Por qué? Porque no compromete la funcionalidad de los clientes más importantes: los que corren en Windows. Si mañana Mono desaparece, tenés todos los demás proyectos open que implementan .NET (DotGNU, CrossNet). ¿Nuestro código se ve afectado? No, sigue corriendo. ¿Y pero Linux? Se reescribe la porción necesaria de código. ¿Pero no es hacer todo de nuevo? No, sólo una pequeña parte. ¿Es probable que esto ocurra? No. ¿Por qué? Porque alejaría el mercado de la plataforma .NET. ¿No es medio subjetivo afirmar eso? Sí, afortunadamente no soy el único que lo cree. ¿Pero entonces cuál es la ventaja de .NET? WinForms y compatibilidad directa con múltiples lenguajes. ¿Alguna otra plataforma provee esto? No.

En lugar de afirmar que ".NET está contaminada de propiedad intelectual, patentes y amenazas de MS" estaría bueno que especifiques qué amenazas, y qué propiedad intelectual te preocupan. Tus palabras me convencen de que realmente no tenés muy bien estudiado la cuestión política y legal detrás de todo esto.
Peor aún, me parece que desestimás todas las claras ventajas que le da al proyecto la plataforma, tan sólo por una cuestión emotiva (?). Lo que es más terrible es que hables de Java y no hagas referencia a todas estas cuestiones. Sun jamás fue muy amiga de Linux. De hecho, el código fuente del JRE y JDK sólo recientemente fue liberado, y la especificación de Java durante años fue controlada por Sun (hoy es manejada por una fundación independiente, pero sigue sin ser estándar, wtf?). Es más, me arriesgaría a afirmar que esto es consecuencia simplemente de la existencia de .NET. ¿Quién cree que el JRE y el JDK serían open hoy si .NET no estuviera absorbiendo el mercado de Java? Vamos. Igual no voy a argumentar que ambas plataformas, hoy por hoy, no son comparables. Por el contrario, son ambas muy buenas. De ahí  a que uses estos arguementos contra .NET y los olvides para Java realmente me parece poco objetivo.

> 
En el aspecto técnico, C y C++ gana en performance y portabilidad a ojos cerrados. Todas las plataformas lo corren y lo corren más rápido. Con una arquitectura orientada a servicios, se puede hacer el núcleo de la aplicación agnóstico a la interfaz, hacer una interfaz para todas las plataformas modernas (QT de KDE y GTK de Gnome corren en todas esas plataformas), otra para plataformas mas viejitas, y si les parece una web, para aquellos casos que es imposible correrlo localmente.
Es totalmente inútil duplicar código cuando podés solucionar esto con una única plataforma. Por eso XUL y wxWidgets me parecieron buenas propuestas. Al igual que Web y .NET. GTK y QT, lo dudo. ¿Y muy bien con portabilidad y performance, pero compatibilidad? Pensá en términos de la plataforma, no del lenguaje.

> En cuanto a python sobre 98, depende, porque el framework .NET tampoco es nativo de 98, asi que ahi dependera de cada implementacion. Pero no todos los 98 tienen el framework .NET, ni todos los win 2000, o si lo tienen, tienen que actualizarlo, porque MS la compatibilidad.
¿De qué me hablás? ¿Cuándo dije que Python no es nativo (y no lo es, pero..)? :shock: Sí hablé sobre Java y Swing..pero Python? Jamás lo comparé con .NET en ese sentido.

> En cuanto a Java, la versión 6 tiene optimización en tiempo de compilación, o sea que la performance ha mejorado mucho, aunque personalmente prefiero la capacidad de multiplataforma, que optimizaciones locales por tratarse de una interfaz "integrada" al sistema (como dije, .NET no es nativo en 98, 95 o 2000, asi que esta integracion no es tan cierta como parece).
¿De qué me estás hablando? Cuando dije "nativo" y "Java" en una misma oración fue para referirme al uso de Swing como entorno gráfico. ¿Vos te das cuenta de que Swing pasa por Java2D para ser dibujado en pantalla? Por eso no es "nativo" (y de hecho, ni siquiera se suele *ver* nativo). En la Wiki está bien explicado todo esto por si tenés alguna duda. .NET llama directamente a la Win32-API si usás WinForms, y no me queda ninguna duda de que es mucho más eficiente en este sentido.

> 
En cuanto a conexión con código externo, la cantidad de código externo libre disponible para Java, C y C++ supera ampliamente a .NET, y con licencias mucho más claras en cuanto a su uso (GPL, BSD, Apache, etc.) respecto a .NET (shared source, permissive license) Solo pueden fijarse en Sourceforge para esto.
Yo nunca hablé de cantidad de código. ¿Nuevamente, de qué me hablás? Java impone reestricciones más claras a la hora de llamar a código *no manejado por la VM*. .NET es más hábil a la hora de interoperar con *unmanaged code*. [Link]("http://en.wikipedia.org/wiki/Comparison_of_C_Sharp_and_Java#Lower_level_code").

> 
Respecto a Mono, no sería mi primer opción usar un lenguaje sponsoreado por Novell y cuyo líder opina que "OOXML es un protocolo excelente" y trata de copiar cada cosa que hace MS (Silverlight, etc.) , pero esto es cuestión de principios personales.
Sí, lo de OOXML la verdad me parece cualquiera, pero bueno, eso no me impide ver los méritos técnicos de las cosas que hace el flaco.
Y con respecto a Silverlight, si eso nos permite liberarnos de Flash y otras cosas propietarias, por mí está bárbaro.

> 
Personalmente, creo que la discusión debería retomar los carriles de si es viable hacerlo, y quiénes, antes de volver sobre la discusión de plataforma.
Es viable hacerlo. ¿Quiénes? Dependerá de la plataforma elegida, seguramente.

[QUOTE=marianom]Realmente no entendí que quisiste decir.[/QUOTE]
Ah, nada, como decías que era mejor dejar calmar los aires, pensé que ibas a cerrar el thread por un tiempo... Por eso decía que iba a mirarlo a ver si había alguna respuesta más adelante. Nada más :)

---

### Post by Mafber on 2007-10-03
Hola como andan, veo que en una discusión muy muy técnica... que no entiendo nada (¿¿qué tienen que ver los monos con la pc?? jajajja) 
Solo quería agregar que me ofrezco para probar el programa (algo así como un alfa-test :confused:)

PD: Marianom... es un lujo tenerte como moderador!!!

---

### Post by Hei Ku on 2007-10-03
Sería bueno poder informarme mejor si estamos o no bajo riesgo de una demanda de patentes. Pero sabes por qué no podemos saberlo? Porque MS sólo informa que GNU/Linux infringe un número x de patentes, sin decir cuáles. Mismo juego que implementó a través de SCO, pero ahora sin intermediarios. Lo único que me resta esperar en ese sentido es que si no aprenden terminen igual que su bufón (ahora en convocatoria de acreedores, para más datos). Si sólo me dicen que "usar Linux es un riesgo dentro de su hoja de balances" me suena a "sería una lástima que algo malo le pasara". Mafioso, liso y llano. Y algo a lo que siento la obligación de oponerme.

En cuanto a la cuestión emocional, puede ser verdad. Pero dado que estamos en un foro de Ubuntu, no de MS, creo que es entendible. No me siento a programar todas las noches cuando vuelvo del trabajo porque quiera hacer un peso extra. No reviso los foros en busca de hacerme un nombre profesional (de hecho, uso un seudónimo), lo hago porque quiero ayudar a otros, así como me ayudaron a mí. Eso es ideológico, y emocional, y es por lo que muchos estamos acá. No se trata de que Linux sea grátis. Por lo mismo podría usar OpenBSD. Se trata de que es libre. Y a la libertad se la defiende, sin compromisos. Como leí en un post, "arrancándola de las manos de los enémigos de la libertad, si fuera necesario". 

Y como ventaja extra, y tomando el punto de vista de Linus, la apertura es un modelo de desarrollo superior. Vamos a ir a buscar performance en la misma plataforma que nos dio Vista? Que requiere una maquina último modelo para hacer menos de lo que puedo hacer en mi PC de 4 años?

Respecto a la plataforma, desde mi punto de vista, 98, 95 y 2000 son lo menos importante. Por que? Porque ya esta el software oficial de la AFIP para eso. O sea, vamos a apuntar a los que ya tienen acceso, o justamente a los que no pueden tenerlo hoy? Y sobre eso, otra cuestión, nos vamos a quejar de la AFIP porque hace todo en código cerrado sobre MS, y vamos a hacer lo mismo en una plataforma de MS, pero mostrando el código? No, creo que no.

Evidentemente estas mal informado, porque QT corre en mas plataformas que .NET. De hecho, varios de los programas que uso en mi MS del trabajo son KDE. Pero mi KDE no corre .NET.

En cuanto a Java, y una gran ventaja sobre .NET, es que ya no tienen que importarme las intenciones de Sun (y en varios posts de otros temas he mostrado ejemplos en los que Sun es poco confiable). Lo bueno es que es GPL ahora, y por eso Sun dejó de tener control sobre eso. Las ventajas de GPL sobre shared source, permissive license y el resto de pobres excusas de licencias "abiertas" que quiere vender MS.

Y en cuanto a fiabilidad tecnica, trabajo hace mucho en desarrollo, y todos los sistemas grandes que hicimos ultimamente (7 años) fue en Java, porque es mucho mas confiable que .NET. Y no estoy hablando de paginitas web, sino cosas en serio, donde el downtime cuesta millones. Y en esos lugares donde el tiempo fuera de servicio cuesta plata, .NET es solo un chiste.

Por eso, desde un punto de vista emocional, personal y tecnico, considero que no tiene sentido seguir una discusion en un sitio de GNU/Linux que proponga trabajar en .NET.

---

### Post by facundocorradini on 2007-10-03
En mi opinion, desarrollarlo en .net es hasta ridículo... 

Para estas cosas habría que pensar en C, C++ o phyton. 

Y si va a ser web, entonces veo bastante fiable trabajarlo en perl o php...

---

### Post by tzulberti on 2007-10-03
Para web ya lo va a hacer la AFIP (bue... seguramante lo haga para IE).
Yo me concentraria en hacerla para escritorios. Sin mebargo, estoy de acuerdo en que deberiamos elegir entre C++ y Python.
Java me parece demasiado pesado (lo uso tanto en casa como en el trabajo(, y python es rapido y tiene librerias multiplataformas. 

En mi opinion personal, yo NO tendria en cuenta las pcs con Win98.

Saludos, 
TZ

---

### Post by Pse on 2007-10-03
> **Hei Ku said:**
> Las ventajas que mencionas de interfaz de interfaz son despreciables cuando hablamos de una aplicación contable. Lo único que tiene que mostrar son widgets, no gráficos. Por lo tanto la diferencia, si existe, es despreciable.
¿Alguna vez corriste GTK sobre Windows 98 en un AMD K6 de 300MHz y 64MB de RAM? Bueno, si lo hiciste, imaginate lo que será Swing. En una JVM. Lo más rápido en esos casos es usar la Win32 API. Como evidentemente este proyecto pretende soporte para Linux, eso no se va a hacer, entonces hay que buscar alternativas :). .NET hace JIT igual que Java (y evidentemente te mata ese micro), pero te da la ventaja de no pasar por ninguna otra layer más que .NET. De última se pre-JITea. ¿Qué toolkit se te ocurre que pueda hacer lo mismo sin duplicar código? A mí se me ocurren Ultimate++, XUL (bah, creo), y wxWidgets. Ésas son las verdaderas alternativas. Que, desde luego, te limitan en algunas cuestiones. Por ejemplo, Ultimate++ te limita a C++. ¿Y por qué nombro a estos y no a GTK? Porque el soporte para W9x desapareció entre la versión 2.6 y 2.8 (y en Windows no dibuja de manera nativa los widgets). QT, que vos lo mencionás, es una opción interesante. Ahora más abajo te digo lo que opino.

> En cuanto a la cuestión emocional, puede ser verdad. Pero dado que estamos en un foro de Ubuntu, no de MS, creo que es entendible. Y respecto a la plataforma, desde mi punto de vista, 98, 95 y 2000 son lo menos importante.
Bueno, quizás este sea el origen de las diferencias que hay entre lo que proponemos. Yo estoy considerando el soporte para plataformas MS (W98 en adelante) como algo inamovible. De hecho, si no fuera así, ni siquiera pensaría en Mono y .NET :) Me inclinaría por C++, o Python, o algo más exótico (D? Vala?). Un programa como este me parece que pierde mucho recortando el soporte para la plataforma del prácticamente 90% de los usuarios.

> 
Por que? Porque ya esta el software oficial de la AFIP para eso. O sea, vamos a apuntar a los que ya tienen acceso, o justamente a los que no pueden tenerlo hoy?
En realidad mi objetivo sería reemplazar el programa de la AFIP y absorber todos sus usuarios, integrando, justamente, a todos aquéllos que no pueden acceder hoy. Lo que estaría dispuesto a comprometer es a aquéllos que se ven cerrados en plataformas excesivamente viejas, como los que corren Windows 3.1 o Windows 95, que, especulo, deben ser los menos.

> 
Y sobre eso, otra cuestión, nos vamos a quejar de la AFIP porque hace todo en código cerrado sobre MS, y vamos a hacer lo mismo en una plataforma de MS, pero mostrando el código?
No entiendo bien lo que querés decir. ¿Qué es "lo mismo" que vamos a hacer? ¿Cómo podemos hacer "código cerrado" pero "mostrando el código"? :shock:
Creo que ya entendiste esto, pero por las dudas te lo repito: C# y la CLI son estándares. Internacionales, ISO, ECMA. Mono, una de las implementaciones (hay otras) además es free. GPL. ¿Cuál es el "código cerrado" al que te referís?

> 
Evidentemente estas mal informado, porque QT corre en mas plataformas que .NET. De hecho, varios de los programas que uso en mi MS del trabajo son KDE.
No recuerdo haber dicho que QT corría en menos plataformas que .NET (?). Sí me referí a la necesidad de duplicar código para correr en varios entornos. Igualmente tenés razón, QT es una buena opción, tal como wxWidgets, XUL o Ultimate++. De las cuales obviamente prefiero QT =). La confusión quizás surgió porque pensaba que QT4 no corría en W98, pero me acabo de fijar y sí, así que es una opción tan válida como las ya mencionadas.

> 
En cuanto a Java, y una gran ventaja sobre .NET, es que ya no tienen que importarme las intenciones (en varios posts de otros temas he mostrado ejemplos en los que Sun es poco confiable). Lo bueno es que es GPL ahora, y por eso Sun dejó de tener control sobre eso. Las ventajas de GPL sobre shared source, permissive license y el resto de pobres excusas de licencias "abiertas" que quiere vender MS.
Me gustaría que me indiques, concretamente, cuáles son las "pobres excusas de licencias abiertas que quiere vender MS", y cuál de ellas afecta a Mono y al proyecto (esto es lo importante).

> 
Y en cuanto a fiabilidad tecnica, trabajo hace mucho en desarrollo, y todos los sistemas grandes que hicimos ultimamente (7 años) fue en Java, porque es mucho mas confiable que .NET. Y no estoy hablando de paginitas web, sino cosas en serio, donde el downtime cuesta millones. Y donde el tiempo fuera de servicio cuesta plata, .NET es solo un chiste.
Supongo que tu experiencia vale. Sin embargo, dudo terriblemente que .NET sea un "chiste". ¿Qué otra cosa más que .NET podía hacer que se libere el código de Java en menos de 5 años?
Vale aclarar que tu experiencia tampoco es del todo concluyente. Hace 7 años .NET no existía, mientras que Java era una plataforma establecida. Es natural que no se hayan realizado cantidad de desarrollos comparables en ese tiempo. Sin embargo, me arriesgaría a decir que el alto grado de productividad mostrado por las plataformas .NET es indicativo de la calidad de la misma. Por lo menos en el mundo open, la cantidad de progreso que se ha visto .NET en poco tiempo no creo que sea comparable al de ninguna otra plataforma. Ni siquiera Java (que, dicho sea de paso, no ha visto grandes desarrollos en este entorno en un buen tiempo). De cualquier manera, en el ámbito profesional esto puede ser radicalmente distinto. Igual, como te digo, y como pintan las cosas hoy por hoy, yo no veo a Java en mejor posición que .NET. Ya hoy .NET es competitivo con Java, si sigue su curso no creo que la porción de mercado que tiene disminuya. Por el contrario, todo apunta a que aumentará. Y esto tiene que ver con muchas otras cuestiones propias del diseño de .NET que no tienen cabida en los paradigmas de Java (en otras palabras, esto no puede resumirse en un "C# vs. Java", sino que hay que tomar otras cosas en cuenta). Personalmente, si hoy me ofrecen un proyecto y las opciones son .NET o Java, me quedo con .NET. A mis ojos todo es mejor salvo una cosa: la cantidad de código existente. Ni siquiera se trata de una cuestión de gusto por el lenguaje, si me gusta Java, programo en Java y lo corro sobre .NET (insisto en este punto porque me da la sensación de que no tenés en claro que .NET no tiene que ver del todo con el lenguaje usado).

> 
Por eso, desde un punto de vista emocional, personal y tecnico, considero que no tiene sentido seguir una discusion en un sitio de GNU/Linux que proponga trabajar en .NET.
Supongo que podemos estar coordialmente en desacuerdo :)

[EDIT]
Como editaste el post y parece que no me avivé (¿me quedó abierta una ventana vieja del foro?), te respondo algunas cosas más acá:

> Sería bueno poder informarme mejor si estamos o no bajo riesgo de una demanda de patentes. Pero sabes por qué no podemos saberlo? Porque MS sólo informa que GNU/Linux infringe un número x de patentes, sin decir cuáles. Mismo juego que implementó a través de SCO, pero ahora sin intermediarios. Lo único que me resta esperar en ese sentido es que si no aprenden terminen igual que su bufón (ahora en convocatoria de acreedores, para más datos). Si sólo me dicen que "usar Linux es un riesgo dentro de su hoja de balances" me suena a "sería una lástima que algo malo le pasara". Mafioso, liso y llano. Y algo a lo que siento la obligación de oponerme.
Sí, definitivamente, me parece totalmente desagradable la actitud de MS a la hora de realizar esas declaraciones (alto FUD ahí). Afortunadamente vos mismo dijiste "GNU/Linux", por lo que Mono puede ser excluido de la ecuación. Igualmente comprendo que en esto vos encuentres una carga emocional considerable en contra de MS y de todo lo que salga de allí. Desde luego, .NET es una de esas cosas. Bueno, contra esto no puedo decir mucho más que lo que yo veo. Creo que .NET está bien hecho, y desde que tanto C# como el CLI son estándares (y ya no son controlados exclusivamente por MS), no tengo muchas excusas para oponerme a su uso. Igual, te aclaro, suelo evitar usar .NET. VMs, JIT, y todas esas cosas no me atraen demasiado. Igual hay que reconocer los méritos, el CLI para mí es de lo mejorcito de los últimos tiempos.

> Y como ventaja extra, y tomando el punto de vista de Linus, la apertura es un modelo de desarrollo superior. Vamos a ir a buscar performance en la misma plataforma que nos dio Vista? Que requiere una maquina último modelo para hacer menos de lo que puedo hacer en mi PC de 4 años?
Jaja, no, por supuesto, Vista claramente no está en mi lista de prioridades (además, 1 luca por un SO :shock: MS debería implementar algún programa acá también para vender licencias a buen precio, mientras tanto puede olvidarse). Lo interesante de lo que vos decís es que estás comparando a Mono con los desarrollos de MS. Mono no es de MS, sino que es una implementación independiente de la plataforma .NET. No hay código de Microsoft en él, y eso es lo copado. Pensá en esto como una analogía de lo que ocurría hace un par de años con Sun y Java: tenías Java, desarrollado por Sun de manera cerrada, y por otro lado un montón de implementaciones independientes (open o no, como GNU Classpath + GCJ y demás). Hoy tenés a la .NET framework, desarrollada en gran parte por MS, que provee una implementación cerrada (los runtimes que bajás de la página de ellos), y por otro lado tenés implementaciones independientes y open, como Mono. La diferencia radica en que, en este caso, una gran parte de la .NET Framework es estándar (y por lo tanto MS no tiene poder legal sobre las implementaciones alternativas, a diferencia de lo que ocurría entre Sun y la comunidad libre antes de que se liberara el código fuente de Java). Igualmente sí hay porciones, como bien se ha indicado antes, que no son parte del estándar y que pudieran estar cubiertas por patentes. Esas partes de la implementación son las que Mono claramente indica en su página (fundamentalmente ASP.NET y WinForms). El resto sí es open, y no corre riesgo. Si mañana MS decide bloquear el uso de Mono de estas partes (lo cual sería suicidio), Mono lo único que tiene que hacer es borrar esa parte del código, nada más. El proyecto en sí no corre riesgo, y todo el resto de la .NET que también ha sido implementada se encuentra a salvo.
No me agrada demasiado MS, pero tiene mérito técnico lo que ha hecho. .NET es, por lo menos, interesante, y abre muchas nuevas posibilidades. Igual no puedo dejar de aclararte que sí podés entrar fácilmente en un conflicto de intereses en estos casos. MS no haría lo que hace si no supiera que es lo que más le conviene, y MS sabe que salvo que pueda lograr que su entorno se haga fuerte, eventualmente va a terminar perdiendo (por esto, si bien es mera especulación, es que estoy tan seguro de que ni Mono, ni cualquier proyecto open corre riesgos, MS quiere que su plataforma se use, y su plataforma es .NET). Si te gusta el ajedrez, podés pensarlo como que MS se encontró con su rey en jaque y rápidamente tuvo que idear una estrategia que le permitiera adaptarse a la nueva amenaza. Imaginate que el código cerrado y la interfaz de su plataforma son su reina. Bueno, para evitar el jaque, decidió sacrificar su reina (o bueno, tal vez una torre). ¿Por qué? Porque igual le permite adaptarse a la nueva estrategia del otro. La pregunta es: ¿quién es el otro?

---

### Post by LaHire on 2007-10-03
> **facundocorradini said:**
> En mi opinion, desarrollarlo en .net es hasta ridículo... 

Para estas cosas habría que pensar en C, C++ o phyton. 

Y si va a ser web, entonces veo bastante fiable trabajarlo en perl o php...

Ridículo no sé (tendrá sus puntos positivos, pero no soy nadie para decirlo)

y más que C, si se me permite ser un poco "elitista" :), diría C# y C++ (aunq son todos gatos de la misma bolsa, al final de cuentas)

Python embedido en -lo que sea- puede funcionar también. Yo solo lo mencioné (y apoyo y promuevo su uso) porque es facil, potente y a los que sabemos poco nos cuesta menos...y los que saben mucho (pero usan otros lenguajes) lo puedan leer como "pseudocódigo en inglés" :P

y bueno, por cierto que si queremos hacer algo, tiene que ser Multiplataforma, lo más sencillo de mantener y entender posible (tanto como para los developers como para los usuarios finales).

Y también seguro es una cuestión personal mía (porq adoro todo lo que es la filosofía del Software Libre), pero si vamos a hacer una aplicación Libre...¿qué mejor que usar lenguajes/frameworks libres y gratuitos?...No sé, es solo una sensación que tengo :)

Y bueno, no soy nadie para opinar sobre estas cosas...pero bueno, es un país libre, ¿no? :guitar:

---

### Post by Pse on 2007-10-04
> **facundocorradini said:**
> En mi opinion, desarrollarlo en .net es hasta ridículo... 

Para estas cosas habría que pensar en C, C++ o phyton. 

Y si va a ser web, entonces veo bastante fiable trabajarlo en perl o php...
Agh, media pila, me mato escribiendo tremendo post para justificar el uso de .NET y lo que consigo es respuestas como ésta. ¿Por qué te parece ridículo? ¿Qué fundamento técnico (o el que fuere) tenés para elegir otras opciones?

Muchachos, esto parece una heladería:
- "No, a mí dámelo de frutilla con crema en el medio".
- "A mí de tiramisú y sambayón".
- "Ah, ponele chocolate".

A ver si en vez de tirar nombres y lenguajes por ahí nos ponemos un poco serios y hablamos de esto como corresponde. Se necesita hablar de librerías, entornos de trabajo, plataformas de desarrollo, los sistemas en los cuales se pretende correr, etc. Y hay que justificar las respuestas, no alcanza un "y...yo prefiero OCaml", o un "no, yo si no es Logo no participo"; "aguante COBOL" (Dios).

¿Por qué C++, por qué Python, Facundo? ¿Por qué no Python + C# sobre .NET con WinForms?

[QUOTE=tzulberti]
Para web ya lo va a hacer la AFIP (bue... seguramante lo haga para IE).
Yo me concentraria en hacerla para escritorios. Sin mebargo, estoy de acuerdo en que deberiamos elegir entre C++ y Python.
Java me parece demasiado pesado (lo uso tanto en casa como en el trabajo(, y python es rapido y tiene librerias multiplataformas.

En mi opinion personal, yo NO tendria en cuenta las pcs con Win98.

Saludos,
TZ[/QUOTE]

A mí Web me parece una muy buena idea. Es decir, si se hace de esa forma, para mí no tiene sentido la implementación como programa cliente de escritorio.
Concuerdo con que, hoy por hoy, Java es pesado.

¿Por qué no tendrías en cuenta las PCs con W98? ¿No te parece que más de uno va a tener problemas? (Aunque es cierto que MS ya removió el soporte para W98, por lo tanto sería conveniente obviarlo, pero, seamos honestos: ¿quién de los que usan estos programas tienen W98 original y han recurrido al soporte técnico oficial frente a un problema?).

[QUOTE=LaHire]Y también seguro es una cuestión personal mía (porq adoro todo lo que es la filosofía del Software Libre), pero si vamos a hacer una aplicación Libre...¿qué mejor que usar lenguajes/frameworks libres y gratuitos?...No sé, es solo una sensación que tengo [/QUOTE]
Estoy de acuerdo. El código debe ser open y la plataforma de desarrollo debe tener una implementación también abierta.

P.D.: Sorry por el double post, postean cuando tipeo.

---

### Post by LaHire on 2007-10-04
> **Pse said:**
> Agh, media pila, me mato escribiendo tremendo post para justificar el uso de .NET y lo que consigo es respuestas como ésta. ¿Por qué te parece ridículo? ¿Qué fundamento técnico (o el que fuere) tenés para elegir otras opciones?

Muchachos, esto parece una heladería:
- "No, a mí dámelo de frutilla con crema en el medio".
- "A mí de tiramisú y sambayón".
- "Ah, ponele chocolate".

A ver si en vez de tirar nombres y lenguajes por ahí nos ponemos un poco serios y hablamos de esto como corresponde. Se necesita hablar de librerías, entornos de trabajo, plataformas de desarrollo, los sistemas en los cuales se pretende correr, etc. Y hay que justificar las respuestas, no alcanza un "y...yo prefiero OCaml", o un "no, yo si no es Logo no participo"; "aguante COBOL" (Dios).

¿Por qué C++, por qué Python, Facundo? ¿Por qué no Python + C# sobre .NET con WinForms?

P.D.: Sorry por el double post, postean cuando tipeo.

Aguante COBOL <- mentira .-.
Y perdón mi ignorancia...hay algún otro framework....¿libre?
Mono? con MonoDevelop?

hay alguna otra alternativa?

y si lo hacemos via web? , con TG?

---

### Post by marianom on 2007-10-04
> **Pse said:**
> Ah, nada, como decías que era mejor dejar calmar los aires, pensé que ibas a cerrar el thread por un tiempo... Por eso decía que iba a mirarlo a ver si había alguna respuesta más adelante. Nada más :)

No, cerrar un thread es un recurso de última cuando todo está prendido fuego. Este thread parece chamuscado por el momento :).

Ahora en serio, creo que la mayoría de los participantes están dando muy buenos argumentos de ida y vuelta y está bueno que podamos discutir este tema. Les pido eso sí -y como favor personal- que piensen 2 veces antes de postear y relean el mensaje: si ven un término que "hipoteticamente" les parece que puede llegar a dar para trifulca, intenten cambiarlo por otro más cortés. 
Las posiciones que uno esgrime no se debilitan por escoger un bueno tono para decirlas.

---

### Post by Pse on 2007-10-04
> **LaHire said:**
> Aguante COBOL <- mentira .-.
Y perdón mi ignorancia...hay algún otro framework....¿libre?
Mono? con MonoDevelop?

hay alguna otra alternativa?

y si lo hacemos via web? , con TG?
¿Te referís a .NET? Sí, hay otras implementaciones libres, pero ninguna llega al grado de funcionalidad que tiene Mono (aclaro, Mono es GPL). Algunas son DotGNU y CrossNet, Googlealas si te interesan.

En el mundo open siempre hay alternativas :)

Y web no estaría mal (te simplifica completamente la cuestión de dar soporte a distintas plataformas, te da un buen grado de seguridad e incluso aumenta el grado de control que la AFIP puede tener sobre los datos). Cualquier cosa sirve en estos casos. El ideal open para esto sería LAMP, que no me parece mala idea.

---

### Post by facundocorradini on 2007-10-04
lo mío fue simplemente opinión. 

Si se hace web, pues eso es lo mío. (php)  y estaría orgulloso de participar. 

Yo le veo muchísimas ventajas a hacerlo web....

Si se hace con cliente en la PC, pues mi opinión vale poco, ya que no puedo ayudar. (estoy muy oxidado con c++).

Mi punto contra .net es que simplemente me parecía (y me sigue pareciendo) ridículo desarrollar basandonos en microsoft... Pero bueno, seguramente sos analista y se lo dificil q es quitarles el .net... me retiro del post antes que se vuelva un flame inparable.

Avisenme si puedo ayudalos en algo.

saludos y éxitos con el proyecto.

---

### Post by Hei Ku on 2007-10-04
Seguis mencionando que .NET es una especificacion de ECMA, como si eso fuera una cosa buena. ECMA es la misma asociacion que tuvo el gusto de traernos OOXML e intenta meterlo por la puerta de atras de ISO, con el resultado que vimos (acusaciones de sobornos, paises votando como robots, asociaciones intervenidas, renuncias, etc.)

Asi que si decis .NET es una especificacion de ECMA (hacemos el standard a la medida, y lo cambiamos si es necesario), y otra de las implementaciones es Mono (con Miguel de Icaza a la cabeza) para mi es un punto en contra. Y para el resto deberia ser al menos un llamado de atención.

---

### Post by Pse on 2007-10-04
> **facundocorradini said:**
> 
Mi punto contra .net es que simplemente me parecía (y me sigue pareciendo) ridículo desarrollar basandonos en microsoft... Pero bueno, seguramente sos analista y se lo dificil q es quitarles el .net... me retiro del post antes que se vuelva un flame inparable.

Naa, ¿flame por qué?

¿Te parece ridículo desarrollar basándote en MS cuando es obvio que tu programa tiene por objetivo principal correr en esa plataforma? Ridículo es hacer un programa para Windows creyendo que de alguna manera te estás oponiendo al Imperio (TM) por no utilizar sus herramientas de desarrollo. Las herramientas no importan, desde el momento en que decidiste que tu principal plataforma de usuarios es Windows ya no hay más vuelta al asunto. No ganás nada con hacerlo en cualquier otra cosa si igual tiene que correr ahí. Lo que importa es donde va a correr el programa, no cómo vas a hacer que lo haga. Lo que sí podés hacer es simplificarte la vida y meter de yapa soporte para lo que a vos te interesa (en este caso, plataformas distintas: Linux, BSD, lo que te interese). Y eso sí me parece un compromiso sensible frente al problema.

Esto lo aclaré en posts anteriores, pero lo repito: normalmente no consideraría .NET una prioridad (porque normalmente no me interesa correr el programas en Windows), pero éste no es el caso: Windows sí importa, por lo menos si pretendés que la AFIP diga "ah, mirá, es interesante lo que hicieron estos flacos".

Por otra parte, sí, tenés razón, la plataforma Web eliminaría todas estas cuestiones.

[QUOTE=Hei Ku]
Seguis mencionando que .NET es una especificacion de ECMA, como si eso fuera una cosa buena. ECMA es la misma asociacion que tuvo el gusto de traernos OOXML e intenta meterlo por la puerta de atras de ISO, con el resultado que vimos (acusaciones de sobornos, paises votando como robots, asociaciones intervenidas, renuncias, etc.)

Asi que si decis .NET es una especificacion de ECMA (hacemos el standard a la medida, y lo cambiamos si es necesario), y otra de las implementaciones es Mono (con Miguel de Icaza a la cabeza) para mi es un punto en contra. Y para el resto deberia ser al menos un llamado de atención.[/QUOTE]

Sí, jeje, en esto puede que efectivamente tengas razón. Los del ECMA han mostrado una actitud poco sensible frente a la problemática que se crea para las otras implementaciones de documentos estándar. Bueno, afortunadamente los del ISO parecen un poco más sensatos, y definitivamente la comunidad no se va a quedar callada frente a toda esta cuestión (te recuerdo que no ha habido grandes cuestionamientos acerca del proceso de estandarización de .NET, a dif. de lo que ocurre con OOXML). De cualquier manera me parece que no deberías subestimar la importancia legal de que algo es ratificado estándar (más allá de lo cuestionable que resulte el proceso y la validez del estándar mismo): esto pone a MS frente a la imposibilidad de usar patentes contra los que implementen el estándar. No interesa demasiado lo demás, para este caso, porque justamente ése es el gran miedo de los que implementan de manera open lo que hace MS. Para el nuestro, Mono (ni cualquier otra implementación) corren riesgos en las partes más importantes, y eso, definitivamente es lo que nos importa. Para el caso de OOXML esto es un tanto distinto, pero no tiene demasiado sentido ahondar en el tema. Tu punto definitivamente es válido, pero acordate: esto de que C# y el CLI sean estándares es sólo una yapa, y es lo que te da seguridad a la hora de hacer el proyecto, nada más. El único motivo por el cual se menciona es porque simplemente le agrega más seguridad a una cuestión que parece generar dudas en la comunidad. (Ah, y vuelvo a aclarar: nada de todo esto pone en riesgo el código que teóricamente se escribiría, el programa de ninguna manera corre riesgo, eso es quizás lo más imporante).

Quizás no sea del todo importante, pero qué sorpresa me di hoy cuando leí esto: [Releasing the Source Code for the .NET Framework Libraries]("http://weblogs.asp.net/scottgu/archive/2007/10/03/releasing-the-source-code-for-the-net-framework-libraries.aspx").
La licencia es ultra-reestrictiva igual :) Pero qué julepe me pegué, dije: "estos muchachos de MS nos están espiando". Seguro fue alguno de acá que entró con IE al foro ;)

---

### Post by facundocorradini on 2007-10-04
> ¿Te parece ridículo desarrollar basándote en MS cuando es obvio que tu programa tiene por objetivo principal correr en esa plataforma?

Si ese es tu objetivo principal, entonces decididamente estoy fuera.  Un programa debería tener por objetivo que **todos** lo puedan usar. 

I'm out. llamenme cuando decidan algo.

---

### Post by Mafber on 2007-10-04
¿el objetivo no era dar a la afip un soft que sirva para los que usamos linux? por que hay que armar algo para todos, si la afip ya decidió y esta haciendo en .net???

---

### Post by Pse on 2007-10-04
> **facundocorradini said:**
> Si ese es tu objetivo principal, entonces decididamente estoy fuera.  Un programa debería tener por objetivo que **todos** lo puedan usar. 

I'm out. llamenme cuando decidan algo.

¿Y cuándo dije que no sería para *todos*? :shock: Es más, mi preocupación justamente es esa: no dejar a todos los flacos que están corriendo Windows afuera, incluso los que están en W9x. Hey, por mí estaríamos todos en Ubuntu :) Pero éste claramente no es el caso. Pongámonos en tema, estás hablando de:
a) Un programa para Argentina (lo cual limita terriblemente el espectro de devs y usuarios que se encuentran en contacto con el sistema).
b) Un programa relativo a las funciones de una institución gubernamental.
c) Que tiene que ser usado por Argentinos. Muchos. De distintos intereses y conocimientos técnicos.

A partir de lo que decís yo deduzco una de dos cosas:
a) O no tenés interés por dar soporte a la plataforma que corren todos (Windows). Lo cual no me parece que esté mal, es decir, cada uno decide cómo hacer sus desarrollos y a qué dar soporte y a qué no, pero este no es el proyecto para hacer eso.
b) Te interesa dar soporte a Windows pero sin tocar las herramientas de desarrollo de la plataforma (?).

Voy a ser claro nuevamente: estás haciendo un programa para Windows (y todas las demás plataformas que quieras). No al revés. Si querés concentrarte en algo que todos los argentinos podamos usar tenés que pensar de esta manera, sino otro proyecto sería más adecuado.

Por último, te insisto: hacer un programa que va a ser utilizado en su mayor parte por usuarios que corren Windows (y no digo que esté bien eso) creyendo que por no tocar las herramientas de desarrollo que tienen origen en esa plataforma (y mirá que ni siquiera digo que corren ahí, sino que tienen sus orígenes *conceptuales* en ella) estás de alguna manera alejándote de MS y provocándole un bien a la comunidad, estás equivocado. En el momento que tu programa tiene que correr en Windows ya está, las herramientas de desarrollo no importan, porque ellas no definen justamente quiénes van a usar el programa, eso está predefinido. Si tu intención es producir un cambio a nivel ideológico, o a nivel comunidad, lo mejor que podés hacer es educar a tus usuarios; decirles "mirá, hay otra posibilidad, este programita también corre en Linux, no necesitás Windows :), podés usarlo ahí, y es muy fácil". Vas e instalás Ubuntu. Pero hacer un programa como éste y esperar que imponer la plataforma genere aceptación del mismo es francamente...ingenuo. En resumen, buscar aceptación imponiendo la plataforma a los usuarios es autoritario, ingenuo e incluso contraproducente.

[QUOTE=Mafber]¿el objetivo no era dar a la afip un soft que sirva para los que usamos linux? por que hay que armar algo para todos, si la afip ya decidió y esta haciendo en .net???[/QUOTE] ¡¿La AFIP ya está haciendo algo en .NET?! :shock: Eso cambia todo :shock:

---

### Post by marianom on 2007-10-04
1- Según entendí por el link provisto por Tomás lo que la AFIP está haciendo es publicar web services para que las aplicaciones (web/escritorio) lean y comuniquen la info. 

Fair warning: opinión right ahead

2- la aplicación "debería" ser:
 * multiplataforma -> hacer solo una aplicación para linux es hacer exactamente lo mismo que ellos hacen: nuestro objetivo debería ser demostrar la filosofia del soft libre y de la colaboración comunitaria sin importar que SO tengan los usuarios. Yo no trabajaría por simpatía a la AFIP, lo haría para demostrar un punto, claro y fuerte.Si usan linux mejor para ellos, nos van a caer mas simpaticos.

 * de escritorio -> no creo que hacer una aplicación web sea la solución: ¿quien la hostearía? ¿que pasa con quienes no pueden disponer de conexión para subir info? ¿que pasa con aquellos que simplemente no quieren?

---

### Post by tzulberti on 2007-10-04
Personalmente estoy de acuerdo con marianom...

No se podria directamente hacer una encuesta para ver cual lenguaje elegimos y listo?
Es decir, todas los lenguajes tienen cosas buenas y malas:
-> C++ el famoso segmentation fault
-> Java es demasiado pesado
-> .Net: fue empezado por Microsoft
-> Python: Es mas lento que C++...

Siempre se van a poder decir cosas buenas de los todos los lenguajes, por lo que creo que directamente tendriamos que armar una encuesta.

---

### Post by Mafber on 2007-10-04
Marianom, lo que traté de preguntar (pero me expresé mal) es si afip esta dispuesta a aceptar algo que sea para win2 (por más que sea multiplataforma).
Pero para linux, ellos no tienen nada concreto. 
Por eso digo, no vaya a ser que se trabaje y que después nos enteremos que estaba descartado de entrada.

Aclaro que de este tema estoy "tocando de oido", tal vez lo que estoy planteando sea incorrecto.
Sea lo que sea que se decida, sigo ofreciéndome para probar y colabora en lo que pueda :)

---

### Post by marianom on 2007-10-04
> **Mafber said:**
> Sea lo que sea que se decida, sigo ofreciéndome para probar y colabora en lo que pueda :)

Y tu oferta es muy bien recibida y aceptada.  :)

La verdad es que no se realmente que quiere la AFIP [1] pero puestos a trabajar, creo que deberíamos encarar para el lado del multiplataforma (o sea, que el código/framework -sea el que sea- ya esté pensado teniendo en cuenta las diferencias de SO a SO).
Sé que el pedido original era de una forma de hacer correr una aplicación nativa en Linux pero por ahí algunos de los participantes le dimos un giro más ambicioso.

Como dije en el post anterior, lo mío es una opinión: llegado el momento de trabajar, los que estén se verán la cara y decidirán lo mejor para el proyecto.

[1] lo que yo sugería en un primer momento es no darle muchas vueltas a comunicarnos con la AFIP de entrada: no me quiero desanimar con burocracia desde el momento cero.
O sea, armemos una "demo" útil, una prueba de concepto, una maqueta (el nombre que quieran darle), dejando de lado las cuestiones "cerradas" que el sistema tenga para más adelante.

---

### Post by Hei Ku on 2007-10-04
Mi opinión es que hay que tratar de abarcar a la mayor cantidad de usuarios posibles. Pero si hay que sacrificar la compatibilidad con 98, 95 o 2000, tampoco lo pensaría 2 veces.

"Aquellos que sacrifican su libertad a cambio de un poco de seguridad, no merecen ni libertad ni seguridad"
- Benjamin Franklin

---

### Post by rretamar on 2007-10-04
> **Hei Ku said:**
> Pero si hay que sacrificar la compatibilidad con 98, 95 o 2000, tampoco lo pensaría 2 veces.

Hay muchas, muchísimas máquinas corriendo Windows 98. Además para lo que hacen esos programas (que, seamos sinceros, no es gran cosa), con un equipo chico (64 Mb) debería estar más que sobrado.

Y ahí es cuando quedan afuera muchos lenguajes interpretados o basados en máquinas virtuales. Que serán muy lindos o están muy a la moda, pero que chupan recursos que dan miedo. Mejor un compilador de toda la vida, o bien basar los sistemas en una interfaz web (muy a mi pesar, optaría en lo posible por esta última alternativa).

Saludetes ! :)

---

### Post by Hei Ku on 2007-10-04
La opcion de C o C++ suena cada vez mas conveniente. El problema es encontrar gente que sepa programar en esos lenguajes sin querer tirarse de la terraza. Quedamos pocos de la vieja guardia. Igualmente, coincido en q para esas maquinas lo mejor es una solucion web.

---

### Post by sajnox on 2007-10-04
Si bien no tengo conocimiento sobre el lenguaje a utilizar, no puedo dejar de reconocer que me cae muy simpatica la idea de poder hacerlo en formato totalmente abierto (aunque se distribuya cerrado) como un buen ejemplo de lo que se puede hacer con software libre.

Si estan de acuerdo me puedo ofrecer para investigar un poco en la AFIP el tema, solo que lo debo hacer por la via burocratica y en forma personal (no creo que ubuntu-ar tenga personeria alguna, si es asi corrijanme), si alguien conoce gente de sistemas dentro de la AFIP tambien es una buena punta para empezar.

Saludos

---

### Post by facundocorradini on 2007-10-04
> **Hei Ku said:**
> La opcion de C o C++ suena cada vez mas conveniente. El problema es encontrar gente que sepa programar en esos lenguajes sin querer tirarse de la terraza. Quedamos pocos de la vieja guardia. Igualmente, coincido en q para esas maquinas lo mejor es una solucion web.

Si se hace en C++, pueden contar conmigo, solo denme una semanita para refrescarme en el lenguaje (estoy un poco oxidado, pero en su momento lo manejé muy bien...)

---

### Post by tzulberti on 2007-10-04
> **Hei Ku said:**
> La opcion de C o C++ suena cada vez mas conveniente. El problema es encontrar gente que sepa programar en esos lenguajes sin querer tirarse de la terraza. Quedamos pocos de la vieja guardia. Igualmente, coincido en q para esas maquinas lo mejor es una solucion web.


Para que mi hicistes sentir un viejo acabado y no tengo ni 25 años...
Aunque de C++ no se nada de la parte grafica ni base de datos, me manejo bien con los datos basicos (lo uso para hacer los tps de la facu).

Saludos,
TZ

---

### Post by Hei Ku on 2007-10-04
Jua. Yo tengo 29, pero programé de chico en C, y despues en C++. Pero parece que ahora todos empiezan con html, vb, javascript, java, python y esas cosas. A mi me hacen sentir viejo cuando les cuento que programo en C++ y me miran como a un gurú.:lolflag:

---

### Post by facundocorradini on 2007-10-04
juaz, no es cierto eso che!... ahora (y desde q tengo memoria) se arranca con pascal!... :P :P: P:P diganme la verdad... quien no arrancó por ahí?? ...

Y eso! tambien me haces sentir viejo a mí!. Yo tambien se programar en C++ (y solía hacerlo hasta q me metía full en web con PHP), y apenas tengo 21 años...

---

### Post by rretamar on 2007-10-05
Ofrecer asesoramiento a la gente de sistemas de la AFIP ...SI.

Hacerles el trabajo gratis....NO.

Pd: Otros empezamos con Pascal y al día de hoy seguimos usándolo. :)

Saludetes !

---

### Post by tzulberti on 2007-10-05
> **facundocorradini said:**
> juaz, no es cierto eso che!... ahora (y desde q tengo memoria) se arranca con pascal!... :P :P: P:P diganme la verdad... quien no arrancó por ahí?? ...

Y eso! tambien me haces sentir viejo a mí!. Yo tambien se programar en C++ (y solía hacerlo hasta q me metía full en web con PHP), y apenas tengo 21 años...

Si haces la carrera de Ing en Informatica en la UBA, si empezas usando pascal. Pero sn Lic en Ciencias de la Computacion (tambien de la UBA), se empieza con C++ (aunque no dan mucha explicacion de POO).

Saludos,
TZ

---

### Post by Mafber on 2007-10-05
> **rretamar said:**
> Ofrecer asesoramiento a la gente de sistemas de la AFIP ...SI.

Hacerles el trabajo gratis....NO.

Pd: Otros empezamos con Pascal y al día de hoy seguimos usándolo. :)

Saludetes !

No creo que se pueda cobrar.
La idea es presentarles soft, pero es porque esta comunidad quiere, no porque nos hayan encargado un trabajo.

---

### Post by Pse on 2007-10-05
> **marianom said:**
> 
2- la aplicación "debería" ser:
 * multiplataforma -> hacer solo una aplicación para linux es hacer exactamente lo mismo que ellos hacen: nuestro objetivo debería ser demostrar la filosofia del soft libre y de la colaboración comunitaria sin importar que SO tengan los usuarios. Yo no trabajaría por simpatía a la AFIP, lo haría para demostrar un punto, claro y fuerte.Si usan linux mejor para ellos, nos van a caer mas simpaticos.
Estoy de acuerdo. Si la AFIP se aviva y dice "Linux, qué bueno", bien por ellos, sino también. Es parte de la filosofía libre :)

> 
 * de escritorio -> no creo que hacer una aplicación web sea la solución: ¿quien la hostearía? ¿que pasa con quienes no pueden disponer de conexión para subir info? ¿que pasa con aquellos que simplemente no quieren?
Yo creo que la plataforma web tiene sus claras ventajas. Aunque es muy cierto que eso impone a los usuarios tener acceso a la red. Si bien no tengo datos concretos sobre esto, me arriesgaría a decir que realmente hoy no hay mucho drama en este sentido. Todos tienen acceso a web, y si no lo tienen, generalmente pueden conseguirlo. Más si se trata de los usuarios de la AFIP (una buena parte de las cosas que suele realizar la AFIP ya son web).
No niego que simpatizo más con lo desktop, sin embargo :)

> **Mafber]
Por eso digo, no vaya a ser que se trabaje y que después nos enteremos que estaba descartado de entrada.[/QUOTE]
Y...es una posibilidad. Supongo que es parte de los riesgos del proyecto. Igual, como dice Mariano, no deberíamos preocuparnos demasiado por este aspecto, es parte de la filosofía open/free :)

[QUOTE=rretamar]
Hay muchas, muchísimas máquinas corriendo Windows 98. Además para lo que hacen esos programas (que, seamos sinceros, no es gran cosa), con un equipo chico (64 Mb) debería estar más que sobrado.

Y ahí es cuando quedan afuera muchos lenguajes interpretados o basados en máquinas virtuales. Que serán muy lindos o están muy a la moda, pero que chupan recursos que dan miedo. Mejor un compilador de toda la vida, o bien basar los sistemas en una interfaz web (muy a mi pesar, optaría en lo posible por esta última alternativa).[/QUOTE]
Me parece que es cierto lo de las máquinas con 98. Me imagino que más de uno de los que usan estos programas no ha tenido necesidad de actualizar tan sólo por el hecho de que lo que tiene le sirve para lo que hace. Sí me tiraría a sacar Win95 del medio, las desventajas de darle soporte son más que cualquier ventaja que pueda darle al programa el soportarlo, y generalmente la dif. en requerimientos entre Win98 y 95 es mínima, por lo cual es probable que el que tenga 95 no tenga mucho drama en dar el salto (y probablemente ya lo haya hecho).

Con respecto a los lenguajes compilados/interpretados, en realidad no tenemos por qué pensar tanto en diferencias de performance. Sería posible hacer esto en un lenguaje interpretado y precompilarlo (AOT en lugar de JIT). La ventaja de los lenguajes interpretados tiene que ver con el grado de productividad que es posible alcanzar con ellos, y en un proyecto como éste eso nos da beneficios:
a) Los conocimientos y los estilos de programación son desconocidos y variados. Hay una alta probabilidad de que la productividad y el grado de interés en el proyecto se vea comprometido por la dificultad de trabajo en él.
b) No se requieren altos niveles de optimización (ninguno de nosotros se va a poner a unrollear loops o escribir código de máquina para mejorar el rendimiento del programa).
c) La cantidad de desarrolladores es limitada por tratarse de un programa altamente específico, con usos limitados, y sólamente aplicable a nuestro país. Si a eso le agregamos la complicación de usar plataformas de desarrollo ofuscadas, reducimos la posibilidad de que el proyecto dé buenos frutos.
d) Si vemos que la performance cae demasiado por el JIT, lo precompilamos y ya (igual esto no nos salva del peso de los runtimes con GCs y otras cosas que consumen tiempo de CPU). Sería interesante probar la performance de dos o tres programas simples en equipos viejos, tanto haciendo JIT como AOT. Tal vez nos llevamos una sorpresa agradable.

[QUOTE=Hei Ku]La opcion de C o C++ suena cada vez mas conveniente. El problema es encontrar gente que sepa programar en esos lenguajes sin querer tirarse de la terraza. Quedamos pocos de la vieja guardia. Igualmente, coincido en q para esas maquinas lo mejor es una solucion web.[/QUOTE]
En el caso de C++, creo que con que haya uno o dos devs que tengan una idea y estén dispuestos a hacer reviews periódicos del código, alcanza, particularmente para resolver los potenciales problemas que puedan aparecer por la inexperiencia de aquéllos que no manejan mucho los lenguajes. Vale aclarar que con C/C++ se corre más riesgo de cometer errores que pueden terminar volviéndose importantes. Pensemos en buffer overflows (peligroso desde el punto de vista de la seguridad) y memory leaks (si una aplicación como esta consume 100MB de RAM *algo* está mal). Es decir, tendríamos que cuidarnos de lo típico para los lenguajes que no manejan su memoria (también está la opción de usar un GC para C++, pero me parece que para eso directamente nos conviene irnos a otro lenguaje).
Con respecto a la diferencia entre C y C++, esto es claro: C++ o nada said:**
> 
Si bien no tengo conocimiento sobre el lenguaje a utilizar, no puedo dejar de reconocer que me cae muy simpatica la idea de poder hacerlo en formato totalmente abierto (aunque se distribuya cerrado) como un buen ejemplo de lo que se puede hacer con software libre.

Si estan de acuerdo me puedo ofrecer para investigar un poco en la AFIP el tema, solo que lo debo hacer por la via burocratica y en forma personal (no creo que ubuntu-ar tenga personeria alguna, si es asi corrijanme), si alguien conoce gente de sistemas dentro de la AFIP tambien es una buena punta para empezar.
Me parece muy buena la idea. Igual supongo que sea cual sea la respuesta, más de uno no se sentirá limitado y seguirá adelante. Siempre fue ese el espíritu libre ;)

Con respecto a los lenguajes, no te preocupes, siempre hay maneras copadas de colaborar con un proyecto que no implican necesariamente saber programar. Y si no sabés ningún lenguaje, o estás oxidado con el que se utilice, siempre podés hacer alguna task de mantenimiento o incluso de control que te pueda ir poniendo en contacto con las partes internas del progra. Así además vas aprendiendo. De seguro cosas como formatear bien el código, realizar la documentación, poner los comentarios de la manera que corresponde, te pueden ser muy útiles a vos y al proyecto y te permiten colaborar. Siempre se respeta el espíritu open.

> **facundocorradini]
Si se hace en C++, pueden contar conmigo, solo denme una semanita para refrescarme en el lenguaje (estoy un poco oxidado, pero en su momento lo manejé muy bien...)[/QUOTE]
Uff, seguro. Yo también estoy durísimo con algunas cosas. Algo importante acá es poner en claro que si se hace algo, tiene que ser por espíritu y diversión. Siempre con buena onda. De otra manera no tiene sentido y termina siendo desgastante para todos :)

[QUOTE=Hei Ku]Jua. Yo tengo 29, pero programé de chico en C, y despues en C++. Pero parece que ahora todos empiezan con html, vb, javascript, java, python y esas cosas. A mi me hacen sentir viejo cuando les cuento que programo en C++ y me miran como a un gurú.[/QUOTE]
Jaja :) Sabés que a mí me parece mal eso de que se arranque tanto con cosas como HTML, Javascript o incluso Python. Te quita mucho de lo que sólo realmente ves cuando te vas acercando cada vez más al hard. Ayuda mucho a entender realmente qué es lo que estás haciendo y cuál es la importancia de tomar los recaudos y las consideraciones necesarias mientras usás determinados lenguajes y modelos de programación. Igual yo seguro cometí esos errores  said:**
> 
juaz, no es cierto eso che!... ahora (y desde q tengo memoria) se arranca con pascal!
PASCAL! Dios, nunca pude entender cuál era la función práctica de ponerle un "begin" a una rutina. Igual lo digo sin nunca haber programado en él, me dicen que puede ser agradable :)

[QUOTE=Mafber]
No creo que se pueda cobrar.
La idea es presentarles soft, pero es porque esta comunidad quiere, no porque nos hayan encargado un trabajo.[/QUOTE]
Claro, es decir, la idea es mantener el espíritu open. Sería copado sin embargo que en la AFIP digan "ah, mirá qué copado" y se interesen de alguna manera por integrar el proyecto. No hablemos de guita porque no tiene sentido igual, eh, no debería ser lo que nos importe acá.

[QUOTE=tzulberti]
Si haces la carrera de Ing en Informatica en la UBA, si empezas usando pascal. Pero sn Lic en Ciencias de la Computacion (tambien de la UBA), se empieza con C++ (aunque no dan mucha explicacion de POO).[/QUOTE]
Igual supongo que más adelante en alguna materia se verán los paradigmas de programación más comunes o más importantes hoy en día... ¿No? :S

---

### Post by tzulberti on 2007-10-05
> **Pse said:**
> 
PASCAL! Dios, nunca pude entender cuál era la función práctica de ponerle un "begin" a una rutina. Igual lo digo sin nunca haber programado en él, me dicen que puede ser agradable :)


Pascal es bastante lindo para aprender. A diferencia de C, C++, los errores se entienden facilmente y si encuentra un error para de compilar cosa que te ayuda a ver donde esta el error. Por ultimo no es case sensitive, lo que tambien ayuda a no hacer errores tontos (pascal no tiene un IDE como Eclipse con autocompletar y esas cosas asique eso ayuda bastante).

Lo del begin... end no me molesta porque son como las llaves de C++, asique no me molestaban esas cosas... 

> **Pse said:**
> 
Igual supongo que más adelante en alguna materia se verán los paradigmas de programación más comunes o más importantes hoy en día... ¿No? :S

Yo hice un año de Ing en Informatica antes de cambiarme de carrera, y en las dos primeras materias de programacion se usaba pascal. Aunque en la segunda, al final se veia un "poco" (algo asi como 2 semanas) de C/C++.

---

### Post by marianom on 2007-10-05
> **Pse said:**
> PASCAL! Dios, nunca pude entender cuál era la función práctica de ponerle un "begin" a una rutina. 
¿Atomicidad? Del mundo de donde yo vengo -bases de datos- el begin y end son muy importantes (y ni hablemos del commit). En Pascal no sé.

¿Así que C++ es la opción popular en este momento? Recuerdos de Informatica II vuelven a mi mente... y son bastante aburridos. No importa: vox populi, vox dei dicen.

Preguntas: ¿con que se hacen las interfaces gráficas en C++? ¿Cúal es la complejidad de hacer una aplicación multiplataforma?

---

### Post by tzulberti on 2007-10-05
> **marianom said:**
> 

Preguntas: ¿con que se hacen las interfaces gráficas en C++? ¿Cúal es la complejidad de hacer una aplicación multiplataforma?


Para la interface grafica que pueden usar todas las mismas que python:
-> Gtk
-> Qt
-> WxWidgets.

Nunca use ninguna asique no puedo comentar sobre este punto.

---

### Post by MeduZa on 2007-10-05
> **Al_maverick said:**
> El unico problema es que si mal no recuerdo, esos programas estan hechos en VB o alguna cosa peor
!

creo que no existe cosa peor que eso, el logo (la tortuga logo) era mejor en su tiempo y el basic de c64 tambien (y eso que eran muy rudimentarios pero cumplian su funcion)


+1 para la pelea para el soft bajo linux

---

### Post by MeduZa on 2007-10-05
> **marianom said:**
> 
Preguntas: ¿con que se hacen las interfaces gráficas en C++? ¿Cúal es la complejidad de hacer una aplicación multiplataforma?


Glade 3 es muy facil de usar y las que dijeron arriba!

---

### Post by Hei Ku on 2007-10-05
Qt también es multiplataforma, y simple de usar. Al menos para lo que tiene que ser la interfaz gráfica (combos, listas, textos) no ofrecería problemas. Lo que desconozco es la performance. Yo uso programas Qt bajo windows y no tengo problema, pero mi PC del laburo es una bestia último modelo (que se traba cuando quiero abrir el menu Start) :lolflag:

Y para seguir la charla OT, yo empece con Logo y Basic en un IT99 4/A. Y segui por mi cuenta despues con C (alguien se acuerda de las Norton Guides?). Recien en la facu me hicieron sufrir con Pascal. Pero bueno, si aprendiste a programar en la facu, es como aprender a andar en bicicleta en un profesorado de gimnasia. TARDE!!!! :lolflag:
(todo va con onda, admito que mi vida era solitaria, y en el colegio me golpeaban por nerd. Y yo programaba virus y se los metia en las PC del colegio :D )

---

### Post by LaHire on 2007-10-06
> **Hei Ku said:**
> (...)
(todo va con onda, admito que mi vida era solitaria, y en el colegio me golpeaban por nerd. Y yo programaba virus y se los metia en las PC del colegio :D )

Quedate tranquilo que estás entre pares.... :P

---

### Post by Pse on 2007-10-06
> **marianom]Preguntas: ¿con que se hacen las interfaces gráficas en C++? ¿Cúal es la complejidad de hacer una aplicación multiplataforma?[/QUOTE]

[QUOTE=tzulberti said:**
> Para la interface grafica que pueden usar todas las mismas que python:
-> Gtk
-> Qt
-> WxWidgets.

Nunca use ninguna asique no puedo comentar sobre este punto.

Tal como dice tzulberti, las opciones más comunes son esas. También está Ultimate++. Hay algunas cuestiones que tomar en cuenta sin embargo. De entrada ya te digo que mi elección personal es QT.

wxWidgets no me agrada por un motivo sencillamente subjetivo: nunca vi una aplicación hecha en wxWidgets que terminara de convencerme. Siempre hay algo que se ve un poquito fuera de lugar, o la interfaz no termina de ser del todo utilizable, o es complicada, o algo. Siempre hay algo que no cierra. Pensemos en ejemplos notables: VLC, XaraXtreme, Code::Blocks, Audacity. Claro está que eso puede ser tranquilamente culpa del programador, que se manda algún moco y hace la interfaz como le sale, pero bueno... Tal vez alguien tenga experiencia programando en wxWidgets y pueda decirnos cuales son los puntos realmente fuertes al lado de las otras opciones.

En el caso de GTK, hay una serie de cuestiones que lo hacen poco atractivo para hacer interfaces en Windows. Pero más allá de eso hay un detalle que realmente lo elimina de la ecuación (y que debo haber nombrado en algún post): GTK, a partir de la versión 2.8, no soporta Windows 98 (esto tiene que ver con el soporte para Cairo que fue agregado en esa versión). Y sí, realmente hay cosas muy grosas que se han agregado desde entonces que hacen que no valga la pena quedarnos solamente con GTK 2.6 para hacer un programa para Windows. Desde luego, también está el detalle de que GTK, en Windows, dibuja las cosas "a mano" (es decir, la interfaz no es nativa), lo cual lo hace un poco más lento todo. Les aseguro, un programa súper simple, con un par de ventanas nomás y sin ningún lujo, corriendo en GTK sobre Win98 en un PII o un K6 es tortuoso. Desde luego también están todas las cuestiones de cómo a veces algunas cosas andan en Linux y maravillosamente en Windows fallan (nada más bello que andar debugueando un programa en Windows adentro de una VM mientras todo tu código está Linux afuera de la VM :)). Por último, GTK está hecho en C. Es horrible usarlo así, como mínimo sería necesario recurrir a GTKMM (bindings para C++). Eso agrega una nueva layer de indirección a todo el código que se usaría (o sea, además del millar de librerías de GTK que van a tener que cargarse apenas arranque el programa, van a tener que cargarse todos los wrappers e interfaces de GTKMM). No me parece la mejor opción. Ah, y ni hablar de conseguir paquetes binarios de las librerías que anden bien en cualquier instalación de Windows (sí, creanme, hacer un cross-compile de GTK y/o GTKMM para Windows no es lindo).
Lo mejor de GTK es poder usar cosas como Glade (o ahora el nuevo GtkBuilder) y que es amigable con la STL. También me gusta mucho cómo se ven los programas (en Linux, en Windows suelen verse algo pobres).

Por último está QT (QT4 más específicamente), que gracias a que recientemente se volvió GPL en Windows (recuerden que hasta hace poco sólo era GPL en Linux) lo podemos usar. La interfaz en todas las plataformas es completamente nativa, el entorno de trabajo es realmente bueno (QtDesign, y demás), y te asegurás el soporte de una empresa comercial. Creo que entre los toolkits de C++ es el mejor para algo como esto. Y también la performance es realmente muy buena (tengo entendido). La más grande desventaja para mí es que QT por principio no es muy amigable con la STL, pero bueno, no importa, se puede tener cuidado a la hora de usar esas cosas y buscar los equivalentes para QT.

El detalle clave para mí en relación a C++ es que si se usa hay que definir correctamente cual va a ser la plataforma de desarrollo. No es fácil armar una toolchain que funcione bien en Windows y en Linux siempre (hace un par de meses tuve que rebuildear *varias* veces distintas toolchains porque parecía que andaban joya en las dos plataformas, y luego te dabas cuenta, un mes más tarde, de que había un pequeño bug que ocurría solamente en Windows (o en Linux) y perdías unos 4 días buscando por qué demonios una estúpida línea de código no andaba, claro, qué ibas a saber vos que el código estaba bien y tu compiler era el que se estaba mandando el moco, y bue..). Propongo GCC 3.4.5 para Linux y Windows (Mingw32).

[QUOTE=Hei Ku]Y yo programaba virus y se los metia en las PC del colegio[/QUOTE]
Jaja :D ¡Como Dios manda!

Che, por cierto, imagino que esas apps que usás en Windows y están hechas en QT serán más o menos recientes (QT4), ¿o son comerciales?

---

### Post by Hei Ku on 2007-10-06
en realidad, no tanto. Es KDiff3, el instalador está para bajar desde sourceforge, y por lo que tengo entendido, a Amarok también lo hicieron correr sobre win. Habia un video de eso en youtube.
Obviamente que la interfaz en windows no es tán pulida como un Office 2007, pero corría bien (Estaba haciendo un merge de un proyecto de 300MB de código, más de 2400 archivos) y no tenia errores de interfaz.
Creo que alcanza para armar una interfaz que haga lo que tiene que hacer, sin flashear, pero estamos hablando de un programa utilitario, orientado a contadores, donde lo importante son los números, no mostrar un cubo tipo Beryl.
En cuanto al toolchain, creo que gcc sería lo mejor, junto con gdb. En cuanto al IDE, no estoy al tanto de entornos para windows. Yo utilizo KDevelop, pero no creo que esté para win. Supongo que se puede utilizar Eclipse, que corre en ambas plataformas y se puede utilizar para C++.

---

### Post by tzulberti on 2007-10-06
> **Hei Ku said:**
> en realidad, no tanto. Es KDiff3, el instalador está para bajar desde sourceforge, y por lo que tengo entendido, a Amarok también lo hicieron correr sobre win. Habia un video de eso en youtube.
Obviamente que la interfaz en windows no es tán pulida como un Office 2007, pero corría bien (Estaba haciendo un merge de un proyecto de 300MB de código, más de 2400 archivos) y no tenia errores de interfaz.
Creo que alcanza para armar una interfaz que haga lo que tiene que hacer, sin flashear, pero estamos hablando de un programa utilitario, orientado a contadores, donde lo importante son los números, no mostrar un cubo tipo Beryl.
En cuanto al toolchain, creo que gcc sería lo mejor, junto con gdb. En cuanto al IDE, no estoy al tanto de entornos para windows. Yo utilizo KDevelop, pero no creo que esté para win. Supongo que se puede utilizar Eclipse, que corre en ambas plataformas y se puede utilizar para C++.

Tambien podemos usar el CodeBlocks que es mas liviano que el eclipse y es multiplataforma...

Saludos,
TZ

---

### Post by Pse on 2007-10-06
No creo que haga falta dar vueltas con el tema de los IDEs. O sea, eso lo decide cada uno. Si alguno quiere usar Code::Blocks o Eclipse, o incluso Visual Studio ;) no hay drama, no tiene sentido poner restricciones en ese sentido. Lo mismo con el debugger. Cuando me refiero a la plataforma de desarrollo hablo específicamente de:

1) ¿Qué compilador y qué versiones? (esto tiene que fijarse para evitar incompatibilidades en el código escrito, ya sabemos cómo varían las implementaciones de muchas funciones de C++ entre compiladores). Piensen que las ABIs tienen que ser compatibles con los paquetes de las librerías que vamos a usar (salvo que compilemos para cada plataforma las librerías).
2) Qué build system. Piensen que tiene que soportar las plataformas que vamos a usar de targets y que tienen que andar bien con las librerías que vamos a usar.

1) Propongo GCC 3.4.5. Otro compilador que no sea GCC es un problema en Linux, y francamente no necesitamos complicarnos innecesariamente. Otra versión que no sea de las 3.4.x nos crea problemas en Windows (particularmente las versiones 4.x.x parece que están todas en beta, por lo menos de parte de Mingw32).

2) Propongo CMake. Nomás porque está pensado para ser multiplataforma (!) y porque las Autotools me resultan innecesariamente complicadas (molestas). De yapa, KDE4 usa CMake, así que de seguro no hay dramas con QT :)

Quería agregar que otra cosa cool que tiene QT para este project es que tiene una API de acceso a bases de datos SQL :D Como anillo al dedo.

---

### Post by Hei Ku on 2007-10-06
Acá hay un link a aplicaciones de Qt. [http://qt-apps.org/](http://qt-apps.org/)
Mirando un poco encontré el QDevelop. Similar al KDevelop, pero multiplataforma, un poco más tosco parece, pero livianito.

Creo que por la parte de desarrollo estaría más encaminado. El tema es quién tiene conocimientos contables para encarar la parte funcional. O sea, quién puede especificar qué es lo que tiene que hacer la aplicación, conoce a fondo cómo trabaja hoy el SIAP, y puede hacer las preguntas correctas a la AFIP cuando surjan dudas.

---

### Post by tzulberti on 2007-10-06
Hoy justo en la CafeConf daban una charla de que estaban pasando las aplicaciones de al AFiP a Java. Era a las 11, y me di cuenta 13:30, pero estaria bueno obtener las diapositivas para ver mas o menos que es lo que se esta haciendo...

La charla se llamaba literalmente: "Recaudando impuestos con Software Libre".
En la pagina de la CafeConf figura el mail de la persona que daba la charla ( gbellino arroba afip.gov.ar). Le podriamos mandar un mail informandole de nuestra idea y ver que le parece... Que opinan?

Saludos,
TZ

---

### Post by Hei Ku on 2007-10-06
Alguien estuvo en esa charla, que pueda decir si piensan liberar el código, o se trata simplemente de recaudar impuestos "con" software libre y no "con filosofia libre"?

O sea, quieren bajar costos, o quieren cumplir sus obligaciones y (si es así me caigo de espaldas) trabajar de manera abierta?

---

### Post by facundocorradini on 2007-10-06
mi jermu estudia para contadora y en el laburo usa bastante los aplicativos de AFIP, así que si la convenzo por ahí nos da una mano.
 (ojo, tampoco estoy seguro de que esté complemtente capacitada...)

btw: +1 C++ , +1 QT.

---

### Post by sajnox on 2007-10-08
El sabado en CAFECONF hubo una charla de recaudar impuestos con SL, alguien pudo ir? Alguien sabe si se puede conseguir el material de la charla? creo que nos seria util ver bien de que hablaron ya que no necesariamente es de lo que estamos hablando aca.

---

### Post by tzulberti on 2007-10-19
Esta es las respuesta que me mando Gonzalo con respecto si le parecia interesante el proyecto que nosotros habiamos pensado:

> 
Buenos dias Tomas, te comento que escale tus consulta ya que me parece un
esfuerzo importante el que tienen planeado empezar
y por cierto la politica de AFIP es apuntar a migrar sus aplicaciones de
plataforma Windows a tecnologias abiertas y no acotadas
a esta plataforma propietaria. En este sentido ya se estan iniciando avances
(ej: Siap en Java), es algo que comentamos en la conferencia out the record.
Te pido que me esperes un par de dias ya que la escale para que sea
analizada por mi director y el Arquitecto principal de AFIP.


En un segundo mail, tambien me escribio:
> 
Me olvide de pedirte algo importante, podrias pasarnos un draft del proyecto
que tienen pensado elaborar como para que analicen el tema con mas
precision?.


Asique creo que deberiamos de escribir un draft del proyecto...

---

### Post by facundocorradini on 2007-10-19
genial, estaba empesando a pensar que esto se había estancado.... 

Muy bueno saber que hay interés (y que no nos ignoran como algunos pensaban) 

Tenemos que ponernos a armar ese draft ASAP...

---

### Post by marianom on 2007-10-19
Pero están migrando SIAP a Java según veo (yo creí que solo estaban abriendo ws). ¿Cómo nos deja eso parados?

---

### Post by facundocorradini on 2007-10-19
Nos deja con un gran porcentaje de usuarios aún excluidos: aquellos cuyas maquinolas no pueden con la pesadez de java (si nosotros en el foro podemos llegar a esa conclusión, no entiendo pq la gente de AFIP no puede) 

Pero bueno, no creo que nos convenga hacer lo que ellos ya están haciendo. (sobre todo pq nos quita la chance de que nos den cabida=
.......................................................................................................................

Ahora tengo bastante intriga con que es lo que tenemos que hacer...

---

### Post by sajnox on 2007-10-19
Si la AFIP esta tomando una politica de migrar sus aplicativos a plataformas abiertas !Bienvenido sea!, igual me gustaria saber en que estado esa tema. Ya habra algo en concreto o fue una simple expresion de deseo?

---

### Post by steve_ignorant on 2007-10-19
> **facundocorradini said:**
> Nos deja con un gran porcentaje de usuarios aún excluidos: aquellos cuyas maquinolas no pueden con la pesadez de java (si nosotros en el foro podemos llegar a esa conclusión, no entiendo pq la gente de AFIP no puede) 

Pero bueno, no creo que nos convenga hacer lo que ellos ya están haciendo. (sobre todo pq nos quita la chance de que nos den cabida=
.......................................................................................................................

Ahora tengo bastante intriga con que es lo que tenemos que hacer...

y digo yo, mi vieja es contadora, el tema del SIAP y las otras aplicaciones, se vio en un momento obligada a correrlas en maquinas que  tengan win98 como minimo. quizas eso te ayude hasta ver a que punto pide eso, como para darse una idea. 

el win98 soporta java, y hasta ver videos del youtube, no creo que por lo que es el SIAP(yo lo use un par de veces), sea TAAAAN pesado como para decir que no lo soporte una pc con win98. 

tambien acuerdense que las pc de oficinas son bastante viejas... no todas son AMD 2.0 

al menos si no saben por donde empezar podrian empezar por ver como armar algo que corra desde una pentium 166 para arriba... 

saludos espero que esto ayude, quiero ponerle a las maquinas de la oficina linux asi es mucho mas seguro.

---

### Post by tzulberti on 2007-10-19
Este es el ultimo mail que me mando cuando le respondi que teniamos que hacer el draft:
> 
Si en realidad lo que necesitaba era un draft de los objetivos principales
mas que de todo el proyecto, con eso alcanzaria.


Yo me concentria mas en que es lo que va a hacer el programa que en los requerimientos de soft/hard del mismo. Sin embargo, en la parte de analisis del programa no puedo ayudar porque no tengo ni idea sobre los programas de la AFIP ni sobre administracion.

Este es el link de la charla de donde se pueden bajar el pdf de la misma:
[http://www.cafeconf.org/2007/modules/myconference/viewspeech.php?sid=88&cid=1](http://www.cafeconf.org/2007/modules/myconference/viewspeech.php?sid=88&cid=1)

---

### Post by tzulberti on 2007-10-23
Hola. Estaria bueno que no abandonemos este proyecto...

Me pregunto si alguien esta haciendo el draft del mismo? Creo una lista de mails para manejarnos por ahi?

---

### Post by marianom on 2007-10-23
Buena idea, sino, no arrancamos más.

---

### Post by Duyos on 2007-10-23
buenas noches. Brindo mi apoyo para este proyecto. Recien empiezo en la onda linux pero uso el siap desde hace mas de cinco años asi que  puedo dar una mano en ese aspecto. lo demas lo voy a ir aprendiendo de mirar. salud

---

### Post by facundocorradini on 2007-10-23
+1 a la lista para planificar y desarrollar las aplicaciones.

(obvio, anotenme en la lista!!!)

---

### Post by tzulberti on 2007-10-23
Creado al grupo:
Se tienen que dar de alta: [http://groups.google.com/group/linux-afip](http://groups.google.com/group/linux-afip)

---

### Post by marianom on 2007-10-23
Esperando aprobación...
¿Hay algún CoC? :)

---

### Post by sajnox on 2007-10-23
¿Hay algun CoC?

SI = NO EVADIRAS

---

### Post by tzulberti on 2007-10-23
> **marianom said:**
> Esperando aprobación...
¿Hay algún CoC? :)

Aprobado y puesto como Owner.... Si queres hacer un CoC no tengo problema, pero podemos usar el mismo que usamos aca.

---

### Post by marianom on 2007-10-24
> **tzulberti said:**
> Aprobado y puesto como Owner....

Gracias por el honor... a ver si mis aportes lo ameritan.

> **tzulberti said:**
> Si queres hacer un CoC no tengo problema, pero podemos usar el mismo que usamos aca.

No creo que sea necesario: los que vamos a participar lo haremos porque queremos y no creo que un troll se meta a pelearnos... será cuestión de que nos tratemos civilizadamente. Algo que creo que nos cueste mucho.

Esperemos un par de días a que se sume por lo menos un grupo importante de los que siguen este thread y largamos con las ideas para el draft. ¿Les parece?

---

### Post by tzulberti on 2007-10-24
> **marianom said:**
> 
No creo que sea necesario: los que vamos a participar lo haremos porque queremos y no creo que un troll se meta a pelearnos... será cuestión de que nos tratemos civilizadamente. Algo que creo que nos cueste mucho.

Van a haber un par de pelas tecnicas como las librerias a usar pero salvo eso no creo que tengamos nada muy serio.

> **marianom said:**
> 
Esperemos un par de días a que se sume por lo menos un grupo importante de los que siguen este thread y largamos con las ideas para el draft. ¿Les parece?

Por mi esta bien.

---

### Post by tzulberti on 2007-10-29
Por favor, todos los interesados en apoyar este proyecto dense de alta en la lista asi podriamos empezar el proyecto.

Si estan en duda de si unirse o no, unanse... :)

---

### Post by marianom on 2007-10-29
Si, tenemos que largar de una buena vez, así que los que falten y quieran estar que se vayan sumando rápido.

---

### Post by Alejandro Vidal on 2007-10-30
Buenas,
Aplaudo lo que esta haciendo la gente de AFIP. Me sorprende gratamente que estén haciendo utilización de software libre y que tengan el proyecto de eliminar el actual SIAP reemplazándolo por aplicaciones multi plataforma.
Desde hace más de 10 años que estoy interactuando con los sistemas de AFIP como usuario y tengo que reconocer que han avanzado mucho. En especial al transformar a la página de AFIP en una página de servicios en lugar de una página informativa.
Si realmente logran un sistema que reemplace al SIAP y que no dependa de windows va a ser un gran paso para que se extienda la utilización de Linux.
En mi caso otro impedimento para la adopción de Linux en mis empresas es el sistema de gestión. Actualmente usamos e-flexware de Bejerman y solo corre en windows. ¿Tienen referencia de algún software local contable, de gestión y de sueldos que corra en Linux?

Saludos.

---

### Post by marianom on 2007-10-30
> **Alejandro Vidal said:**
> En mi caso otro impedimento para la adopción de Linux en mis empresas es el sistema de gestión. Actualmente usamos e-flexware de Bejerman y solo corre en windows. ¿Tienen referencia de algún software local contable, de gestión y de sueldos que corra en Linux?

La palabra que me mata es "local". Hace un buen tiempo charlamos de [algo]("http://ubuntuforums.org/showthread.php?t=400734") pero deberías ver vos si cubre tus necesidades.

(En caso que alguien más puede sugerirte algo, lo ideal sería que abran un thread nuevo para seguir el tema específico).

---

### Post by Alejandro Vidal on 2007-10-31
> **marianom said:**
> La palabra que me mata es "local".

Con local me refiero a las particularidades derivadas de nuestra legislación. Regímenes de retención en los pagos a proveedores y de sueldos, posibilidad de exportar reportes que puedan luego importarse en aplicativos de AFIP o cumplir con los requisitos de la registración electrónica de comprobantes, entre otros.

Siguiendo tu sugerencia descargué el live CD de ERP5 para intentar probarlo. Al parecer es muy interesante y completo pero estimo que  requerirá un trabajo importante para su implementación. Sería interesante saber si alguna compañía en la Argentina ya esta realizando ese tipo de implementaciones.

Coincido en que el tema se alejó un poco del tema de AFIP.

Saludos.

---

### Post by santiagoward2000 on 2007-11-01
Hola gente!
Me encanta esta idea, y me gustaría poder ayudar (aunque no se que podria hacer). Ya pedí unirme al grupo en Google.
Espero que podamos hacer andar esto!!!

---

### Post by LaHire on 2007-11-02
> **santiagoward2000 said:**
> Hola gente!
Me encanta esta idea, y me gustaría poder ayudar (aunque no se que podria hacer). Ya pedí unirme al grupo en Google.
Espero que podamos hacer andar esto!!!


Grupo de Google? ¿Dónde?

y me da la sensación que esto va por buen puerto.....
:)

y eh...perdón si postearon el link del grupo, yo lo busqué....y no me tiró nada (o tal vez el buscador me vió la cara)

de todas formas, espero ayudar :)

saludos!

---

### Post by sajnox on 2007-11-02
[Este]("http://groups.google.com/group/linux-afip") es el link al rupo en Google.

Bienvenido!!!!!

---

### Post by faktorqm on 2007-11-02
Hola a todos, lei este post hace mucho y lo deje en la pagina 6 por que como era de esperar se pusieron a discutir....
Yo tiro la idea, después ustedes me dicen si les gusta o no, no me digan que no va con mi filosofia, o alguna de esas pavadas por que no las soporto. Hay que hacer el programa y punto, o no, previo "estudio de mercado".
Ahora bien, yo trabajo en facultad de ciencias economicas (estudio en ingenieria, uba) y conozco bastante de cerca este sistema. No lo sé usar, pero lo sé instalar, rescatar bases de datos, y etcetcetc que los que hacen/hicieron soporte técnico alguna vez saben muy bien de que estoy hablando.
Para mi el primer problema que hay que plantear, es el problema de que todos los que trabajan de esto (cuando digo "todos" me refiero a la gran mayoria xD) no tienen mucha idea de informática, y menos si son gente "grande" (50 promedio), y apenas saben usar M$. Entonces claro, los tipos vienen, conectan la multifuncion al usb, tiran el cd, y se acabo. en gnu/linux capaz no es tan asi. ni hablar si tienen mother con chipset via con video integrados, como le decis que no tiene aceleracion 3d? 
Con esto quiero llegar a que tomen conciencia del FACILISMO que propone (y que estaq presente) el conjunto de usuarios, que ellos quieren usar una herramienta que no saben como funciona, no saben usarla, pero bueno, apretan 2 botones, le ponen 5gb de memoria por que sino no anda, si se les cuelga reinician, y listo el pollo.
Ese facilismo del que hablo (y que por cierto aborresco) es lo que "mata" al SL, conozco a varios contadores y/o actuariales, etcetc y los tipos capaz saben bocha de economia, pero meten el pendrive en el usb y estan 2 horas buscando el icono del PowerPoint..... y cuando lo encuentran, pasan las diapositivas, y cierran. Entonces claro, todos los programas que no corren en gnu/linux, o hay que emularlos, es meter en un embrollo al usuario que por supuesto, se va a hacer mucha malasangre y se va a acordar de nuestros familiares. Lo mismo va a pasar con los formatos propietarios, a veces varios estudios contables trabajan en conjunto, y capaz los .doc's se van "deformando" en odt, o algo y los tipos no los pueden abrir, o sea que habria que estandarizar de alguna manera, o poner de acuerdo a todos, para que usen OO.
Resumen: no saben nada de computacion ni les interesa, y si no les anda se ponen mal en lugar de aprender y resolver el problema.
Ahora bien, la UNICA solucion a esto, es hacer un programa 100% portable, un exe para linux, otro para windows. Siempre y cuando TODOS estemos de acuerdo en este punto, vamos a llegar a buen puerto. Si dividimos todo el tiempo, no llegamos a nada, nos tenemos que unir, y para eso cada uno debe dejar de lado cosas.

Ahora bien, supongamos que resolvemos este problema y que estan todos felices y contentos.

Como bien dijo marianom, hay que hacer 2 equipos, uno que diga como es la formula y que nombre tiene, y el otro que programe eso. No me voy a meter en cuestiones intrinsecas a la programacion, pero la plataforma es vital para llegar a buen puerto.
Yo propondria usar C, o C++ si hay algun fanatico, con GTK2+. simple y facil no? eso es a lo que quiero llegar. Tenemos que definir aqlgo que sea simple, rapido y portable.
Para que sea simple, hay que elegir un lenguaje que sepamos la mayoria, digamos, si hay 9 que saben C y 2 python, bueno, usaremos C y/o migraremos 9 a python xD
Que sea rapido, reside en la sabiduria de cada programador, pero como bien dijo uno por ahi, esto tiene que correr en un k6-2 500mhz con 64mb sin ningún drama. Aparte para lograr esto se pueden usar gráficos SVG, optimizaciones en el compilador para alta velocidad, etc.
Los que saben python me sabran decir si es rapido o no, la verdad, si la cuestion pasara  exclusivamente por mi, yo usaria C, ASM y MySQL, jijijijijij pero esa no es la realidad xD

Con el tema de la portabilidad, yo me ajustaria primariamente a usar estandard POSIX, cosa que ande en ambos sistemas. Propusieron por ahi usar C# (se lee "si yarp"), lo cual no me parece mal existiendo el proyecto mono. Yo no me meto en filosofia, solo en cuestiones técnicas, por lo tanto, si me aseguran, que algo programado en C# es mas rapido, mas simple y mas portable que algo en C o en python, ya mismo me bajo un manual de C#. Si nuestro aplicativo va a tener restricciones o dependencias, como ser .net framework en entornos M$, o algun paquete extra privativo o restringido que haya que instalar para poder correr la aplicacion en entornos unix-like, yo votaria por que analicemos a fondo la propuesta, y la abandonemos luego, SIEMPRE con fundamento.

Una vez que definamos toooodo esto, y realmente estemos todos de acuerdo, nos juntamos los dos equipos, con 2 cajones de birra, y un par de manies (jajajaja) y armamos el boceto del proyecto.

Creo que no me olvide de nada, bueno yo tengo ganas de participar del proyecto, obvio. Sé programar en C, bastante ASM, html y alguna cosa que ande por ahi. (viste que cuando programas en C, despues php, java, y todos los derivados de C son lo mismo ;) )

Y estaria buenisimo que respetaramos la mayor cantidad de estandares posibles. :P
Perdón por escribir tanto, es que me pareció copado hecharle un poco de claridad al tema, algunos tecnicismos, y dejar de lado cuestiones que no hacen a la causa.
salu2!!!!

---

### Post by facundocorradini on 2007-11-02
faktorqm: 

La idea fué desde el principio hacerlo multiplataforma y de bajo consumo de recursos. Y es algo que ya fué discutido y decidido.

En cuanto al lenguaje, aún tenemos que decidirnos entre phyton y C++, y que libs vamos a usar, pero esto es lo de menos...

Si querés colaborar, únete a la lista del grupo de google.

---

### Post by faktorqm on 2007-11-02
grosssoooo. el unico tema es que ... no puedo entrar desde el trabajo!! :(
estoy bloqueado por el proxy que hay aca... desde casa no hay drama.

bueno despues me anoto. yo si usan c++ toy chocho. :D:D:D

---

### Post by faktorqm on 2007-11-02
che ya me registre y todo, quien es el admin? bueno no importa kien, que me apruebe y listo. salu2!

---

### Post by marianom on 2007-11-02
> **faktorqm said:**
> che ya me registre y todo, quien es el admin? bueno no importa kien, que me apruebe y listo. salu2!

Me extraña araña, ya estás aprobado :)

---

### Post by marianom on 2007-11-02
Existiendo ya otro lugar para continuar las charlas relacionadas a este tema, el presente thread no tiene sentido de seguir activo (en el mejor de los casos duplicaría esfuerzos).
A quienes le interese, los invitamos a que nos visiten en [el grupo]("http://groups.google.com/group/linux-afip") que hemos armado a tal fin.

Gracias.

---

