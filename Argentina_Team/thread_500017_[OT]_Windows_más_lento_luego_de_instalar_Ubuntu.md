---
title: "[OT] Windows más lento luego de instalar Ubuntu"
date: 2007-07-13
forum: Argentina Team
---

### Post by gepatino on 2007-07-13
Perdón por el OT, pero no sé a donde recurrir. Por suerte no tengo mucha experiencia en Windows (lo último que instalé fue un win 2000), y no creo que hayan comunidades interesantes de soporte para windows, no? ;)

El tema es el siguiente:

Estuve 'evangelizando' un par de máquinas de conocidos, instalándoles Ubuntu sin eliminar el windows (xp en todos los casos). Como nadie acostumbra a tener el disco particionado, siempre use la opción de redimensionar la partición de windows al instalar el ubuntu.

Todo bien, ubuntu es un chiche, el grub muestra la opción para volver al xp, todos contentos... hasta que vino el primero y me dice que desde que le instale el ubuntu, windows es mas lento.. :confused: 

Mi primer respuesta fue 'te parece... ubuntu es rápido en esa maquina y ahora te parece que windows es lento...'

Ayer instale otra notebook, y ahora pude comprobar yo mismo, que el windows queda como rengo después de achicarle su partición. 

Después de tanta introducción... ¿hay alguna herramienta en xp para decirle que optimice su partición o reconozca lo que tenga que reconocer?

De nuevo, perdón por el OT, y gracias por adelantado.

---

### Post by benjaminwr on 2007-07-13
Buenas,

Tecnicamente no deberia haber dejado de reconocer nada, simplemente se ha fragmentado el disco duro de Windows, la optimizacion del emplazamiento de archivos en el disco se habra ido al ******. Lo que tienes que hacer es pasarle un buen programa de defrag, Diskeeper o PerfectDisk. Aparte de eso no se me ocurre nada mas.

---

### Post by Kantier on 2007-07-13
creo que esto te puede servir: [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

@wikipedia: [http://en.wikipedia.org/wiki/JkDefrag](http://en.wikipedia.org/wiki/JkDefrag)

---

### Post by Mauro22 on 2007-07-13
Es rarisimo que se haga mas lento, ya que al achicar la particion, el disco tiene menos lugar para buscar info, con lo que el tiempo de busqueda aumenta, aparentando un rendimiento mayor del disco. 

Pero a nivel soft, puede ser que windows "intente" hacer algo con la particion ext3 o swap, y eso lo haga parecer mas despacio.


Habria que comprar la actividad de CPU antes y despues de instalar Ubuntu!


Salu2!

---

### Post by Al_maverick on 2007-07-13
el tamaño del disco fisico es el mismo, asi que los tiempos de busqueda no se achican. Lo que puede pasar es que al crear la particion de ubuntu, haya fragmentado la de windows, y archivos que antes estaban juntos hayan quedado fragmentados. Proba con un desfragmentador y contanos que sucede.

---

### Post by sebas.rhcp on 2007-07-13
Creo que esta relacionado con la memoria virtual o con la fragmentacion

---

### Post by gepatino on 2007-07-14
bueno... gracias a todos.

yo tambien pense que era un tema de fragmentacion, pero no tuve oportunidad de volver a defragmentar despues de instalar, y no queria mandar fruta :)

la primera vez que se inicia con windows después de achicar la particion tarda un monton en arrancar porque vaya uno a saber que esta reconstruyendo, despues inicia normal, pero el funcionamente general es lento.

y bueno... ya sabemos lo bien que esta diseñado ese 'sistema' ;)

---

### Post by Mafber on 2007-07-14
Hola, coincido con que hay que tratar de desfracmentar. Pero te recomiendo un programa, System Mechanic Professional. tiene una herramienta que te desfracmenta el starup. Es muy bueno el programa.
Suerte!!!

---

### Post by MeduZa on 2007-07-14
> **gepatino said:**
> 

El tema es el siguiente:

Estuve 'evangelizando' un par de máquinas de conocidos, instalándoles Ubuntu sin eliminar el windows (xp en todos los casos). Como nadie acostumbra a tener el disco particionado, siempre use la opción de redimensionar la partición de windows al instalar el ubuntu.

Todo bien, ubuntu es un chiche, el grub muestra la opción para volver al xp, todos contentos... hasta que vino el primero y me dice que desde que le instale el ubuntu, windows es mas lento.. :confused: 

Mi primer respuesta fue 'te parece... ubuntu es rápido en esa maquina y ahora te parece que windows es lento...'

Ayer instale otra notebook, y ahora pude comprobar yo mismo, que el windows queda como rengo después de achicarle su partición. 

Después de tanta introducción... ¿hay alguna herramienta en xp para decirle que optimice su partición o reconozca lo que tenga que reconocer?

De nuevo, perdón por el OT, y gracias por adelantado.
Hola
primero que nada congrats por la evangelizacion XD
segundo: para mi que es porque windows se pone celoso.
Ahora hablando en serio tambien puede ser problemas de swap de windows pero no creo que le hayas dejado poco espacio en disco aunque por ahi defragmentando se recupera la velocidad, tambien me cabe la duda si es que windows tenia 100% y ahora tiene 50% y eso lo afecto en algo (algun bug que se yo)

Suerte

---

### Post by guillermolisi on 2007-07-15
Gabriel

Tambien pienso que el tema pasa primero por desfragmentar toda la particion Windows, swap file incluido (esto se puede hacer con Diskeeper y probablemente con alguno de los que se mencionaron antes).

Luego y solo para confirmar, revisa el tamaño del swap file. No deberia haberse modificado del que tenia originalmente. De paso confirma si su tamaño es fijo o variable administrado por el sistema. Yo prefiero fijo y generalmente del maximo recomendado por Windows, a veces hasta tres veces mas (si se usa para edicion de escritorio/diseño grafico).

Y por ultimo, y no por eso menos importante, revisa cuanto espacio libre queda en la particion Windows. Si esta por debajo del 20% del total del disco esa puede ser una razon del pobre rendimiento relativo, sobre todo si el swap file lo administra el sistema y es de tamaño variable.

---

