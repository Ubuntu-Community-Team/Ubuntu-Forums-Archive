---
title: "Unas dudas para instalar Ubuntu"
date: 2007-07-12
forum: Argentina Team
---

### Post by Thalskarth on 2007-07-12
Hola buenas... he decidido instalar Ubuntu en mi maquina... pero tengo algunas dudas antes de empezar...

yo tengo el win xp en una particion... puedo intalar ubuntu tranquilamente en otro sindramas, no???

me han recomendado que que ademas de la particion swap, no instale ubuntu en una sola particion sino que lo haga en dos poniendo el ubuntu en la particion A y lo que serie el /home en la particion B... eso es conveniente?? y de ser asi, que tamaño me conviene ponerle a cada particion aproximadamente???

Para el Swap me dijeron que como tengo 512 de ram, le de un giga de tamaño... pero al resto? que tamaño le doy??

y otra preguntita mas... que me conviene mas para empezar: Ubuntu o Kubuntu???

Agradeceria sus respuestas. y muchas gracias!

---

### Post by gepatino on 2007-07-12
Buenas... bienvenido.

vamos por orden...

si, podes instalar ubuntu junto a xp sin problemas, cada uno en su particion.

En cuanto a particiones separadar para /home y para el SO, si, es recomendable. Para el sistema operativo, con 4Gb es suficiente, pero si podes ponele un poco mas. Para los homes de usuario el tamaño que quieras, pero que no sea demasiado poco porque si se quedan sin espacia no van a poder loguearse en el entorno gráfico. Para que los usuarios puedan hacer algo interesante, yo pensaria en al menos 2Gb por usuario.

Para el swap generalmente se recomienda el doble de la RAM. Inicialmente esto no es una regla obligatoria, pero si vas a usar la funcion de hibernacion, necesitas mas swap que la memoria (ahi el doble esta bien) porque sino podes quedarte sin espacio para hibernar.

En cuanto a la versión, Ubuntu y Kubuntu tienen el mismo soporte de hardware/aplicaciones, etc, y el rendimiento es muy similar entre los dos. Es una cuestion de gustos, Ubuntu (Gnome) es mas simple, con menos opciones de configuracion en lo visual. Kubuntu (KDE) tiene mas opciones de ese tipo, pero para los Gnomeros no es tan 'prolijo'. Cuestion de gustos.

---

### Post by Hex_Mandos on 2007-07-12
A mi me embola bastante armar una partición separada para /home. Soy un instalador y desinstalador crónico (de cosas pesadas, tipo entornos de escritorio... siempre tengo por lo menos GNOME y KDE, más varios manejadores de ventanas livianos). No digo que la partición separada no tenga ventajas, pero a mi no me sirve.

Para empezar, yo usaría Ubuntu. LA mayoría de los tutoriales asumen que tenés instalado GNOME. Pero ambos manejadores son igualmente buenos, cada uno a su manera.

---

### Post by Thalskarth on 2007-07-12
> **gepatino said:**
> Buenas... bienvenido.

vamos por orden...

si, podes instalar ubuntu junto a xp sin problemas, cada uno en su particion.

En cuanto a particiones separadar para /home y para el SO, si, es recomendable. Para el sistema operativo, con 4Gb es suficiente, pero si podes ponele un poco mas. Para los homes de usuario el tamaño que quieras, pero que no sea demasiado poco porque si se quedan sin espacia no van a poder loguearse en el entorno gráfico. Para que los usuarios puedan hacer algo interesante, yo pensaria en al menos 2Gb por usuario.

Para el swap generalmente se recomienda el doble de la RAM. Inicialmente esto no es una regla obligatoria, pero si vas a usar la funcion de hibernacion, necesitas mas swap que la memoria (ahi el doble esta bien) porque sino podes quedarte sin espacio para hibernar.
Ok, gracias por la respuesta... entonces si le pongo
 [LIST]
[*]
[*]SWAP = 1gb
[*]SO = 6 o 10 GB
[*]/HOME (unico usuario)=el resto del rigido
[/LIST]
andaria de maravillas?

> **gepatino said:**
> En cuanto a la versión, Ubuntu y Kubuntu tienen el mismo soporte de hardware/aplicaciones, etc, y el rendimiento es muy similar entre los dos. Es una cuestion de gustos, Ubuntu (Gnome) es mas simple, con menos opciones de configuracion en lo visual. Kubuntu (KDE) tiene mas opciones de ese tipo, pero para los Gnomeros no es tan 'prolijo'. Cuestion de gustos.
> **Hex_Mandos said:**
> A mi me embola bastante armar una partición separada para /home. Soy un instalador y desinstalador crónico (de cosas pesadas, tipo entornos de escritorio... siempre tengo por lo menos GNOME y KDE, más varios manejadores de ventanas livianos). No digo que la partición separada no tenga ventajas, pero a mi no me sirve.

Para empezar, yo usaría Ubuntu. LA mayoría de los tutoriales asumen que tenés instalado GNOME. Pero ambos manejadores son igualmente buenos, cada uno a su manera.
Entonces mejor pongo ubuntu... y luego pruebo con ambos para ver cual me parece mejor para mi??
Hay una forma facil de cambiar de Gnome a Kde sin tener que intalar ubntu o kubuntu cada vez???

Gracias!!

---

### Post by marianom on 2007-07-12
Es relativamente sencillo, Pone "kubuntu" en el buscador de este subforo y vas a encontrar varios threads que discuten el tema.

---

### Post by gepatino on 2007-07-13
> **Thalskarth said:**
> Ok, gracias por la respuesta... entonces si le pongo
 [LIST]
[*]
[*]SWAP = 1gb
[*]SO = 6 o 10 GB
[*]/HOME (unico usuario)=el resto del rigido
[/LIST]
andaria de maravillas?

Mas que bien...

> **Thalskarth said:**
> Entonces mejor pongo ubuntu... y luego pruebo con ambos para ver cual me parece mejor para mi??
Hay una forma facil de cambiar de Gnome a Kde sin tener que intalar ubntu o kubuntu cada vez???

Por supuesto que se puede hacer de forma fácil, reinstalar en Linux es algo muy excepcional.

Una vez que instalas Ubuntu, podes instalar kde seleccionando el paquete kubuntu-desktop en el administrador de paquetes (synaptic). Después de instalarlo, en el login vas a la opcion de Sesion y elegis si queres usar KDE o Gnome. 

Saludos,

Tambien podes probar xfce (xubuntu-desktop) y edubuntu (edubuntu-desktop).

---

### Post by Thalskarth on 2007-07-13
> **gepatino said:**
> Por supuesto que se puede hacer de forma fácil, reinstalar en Linux es algo muy excepcional.

Una vez que instalas Ubuntu, podes instalar kde seleccionando el paquete kubuntu-desktop en el administrador de paquetes (synaptic). Después de instalarlo, en el login vas a la opcion de Sesion y elegis si queres usar KDE o Gnome. 

Saludos,

Tambien podes probar xfce (xubuntu-desktop) y edubuntu (edubuntu-desktop).
Buenisimo!! entonces este mismo finde lo instalo y voy a probar con eso asi luego decido con cual me quedo (si gnome, kde. Xfce, etc)....

Muchas gracias por la ayuda y los consejos!!


PD: cualquier cosita o problemita, puedo seguir molestando con preguntas, no??? XDDD

---

### Post by gepatino on 2007-07-13
> **Thalskarth said:**
> Buenisimo!! entonces este mismo finde lo instalo y voy a probar con eso asi luego decido con cual me quedo (si gnome, kde. Xfce, etc)....

Muchas gracias por la ayuda y los consejos!!


PD: cualquier cosita o problemita, puedo seguir molestando con preguntas, no??? XDDD

seguro... para eso estamos ;)

---

### Post by Thalskarth on 2007-07-13
Entonces me aprovecho de eso :P

pero hago una pregunta mas... como se dijeron que se puede... lo voy a instalar con dualboot junto a winxp que ya tengo...

Acutalmente, yo tengo una particion con el windows (c: ) y otra como si fuera "mis documentos" (d: ) mas el espacio libre donde instalare las particiones de ubuntu...
entonces,  al poner ubuntu... podria seguir usando esa particion (d: ) sin dramas para leer y copiar archivos?... (esta en NTFS)... es decir para asi poder accceder a los archivos que tenga desde ambos SO porque se que las particiones de linux, el windows no las lee... o que debo hacer para poder tener eso o algo similar???

nuevamente, gracias!!

---

### Post by Al_maverick on 2007-07-13
hay un driver para leer y escribir las particiones ntfs, lo tenes en el paquete ntfs-3g

---

### Post by clasificado on 2007-07-15
> **Thalskarth said:**
> al poner ubuntu... podria seguir usando esa particion (d: ) sin dramas para leer y copiar archivos?... (esta en NTFS)... 

¡Apa!
El ubuntu tiene su propio sistema de archivos (ext3), lo mas probable, es que cuando quieras instalarlo en la particion "d:", la borre y la reformateé a ext3 perdiendo todos sus datos.

Lo que se suele hacer, es decirle al instalador de ubuntu que no reemplace las particiones, sino que les quite el espacio libre, lo suficiente como para hacer una nueva particion y que se acomode ahi (una 3ra particion en tu caso).

Con esta segunda opcion, no vas a perder nada.

Despues de eso, linux puede leer particiones ntfs de varias formas, y windows puede leer las [ext3 instalandole un driver especial]("http://www.fs-driver.org/download.html").

Pero del vamos, sacate la idea de tratar de instalar ubuntu en una partición ntfs :)

Clasificado

---

### Post by Thalskarth on 2007-07-15
> **Al_maverick said:**
> hay un driver para leer y escribir las particiones ntfs, lo tenes en el paquete ntfs-3g
Con ese driver, entonces podria leer y escribir en la particion NTFS tranquilamente?? sin riesgos??

> **clasificado said:**
> ¡Apa!
El ubuntu tiene su propio sistema de archivos (ext3), lo mas probable, es que cuando quieras instalarlo en la particion "d:", la borre y la reformateé a ext3 perdiendo todos sus datos.

Lo que se suele hacer, es decirle al instalador de ubuntu que no reemplace las particiones, sino que les quite el espacio libre, lo suficiente como para hacer una nueva particion y que se acomode ahi (una 3ra particion en tu caso).

Con esta segunda opcion, no vas a perder nada.

Despues de eso, linux puede leer particiones ntfs de varias formas, y windows puede leer las [ext3 instalandole un driver especial]("http://www.fs-driver.org/download.html").

Pero del vamos, sacate la idea de tratar de instalar ubuntu en una partición ntfs :)

Clasificado
No queria decir eso, en si el Ubuntu lo voy a instalar en una tercer particion aparte... esa particion D: es donde tengo todos mis archivos como (las fotos, etc) lo que queria saber era si podia acceder a leer y escribir en esa particion desde el ubuntu sin peligro de algun fallo o problema... porque me habian dicho que el linux leia NTFS pero que era peligroso escribir en una particion NTFS pero como hace tiempo me dijeron eso... queria quitarme la duda antes de hacer lio o mandarme una macana :P

Gracias por su ayuda

---

### Post by Al_maverick on 2007-07-15
Personalmente, yo no he usado el ntfs-3g. El driver tiene bastante tiempo ya en su release final y aca hay varios que lo usan sin problemas.
En mi caso, yo soy mas conservador y prefiero el probado metodo de usar una particion fat32 para compartir archivos entre los SO, pero en tu caso no creo que sea posible. Mi consejo es que busques en los foros los problemas conocidos que hay con ntfs-3g (si hay alguno), y por supuesto, que hagas backup antes de modificar las particiones. Esto último es imprescindible, además de una buena costumbre. :D

---

### Post by Thalskarth on 2007-07-16
> **Al_maverick said:**
> Personalmente, yo no he usado el ntfs-3g. El driver tiene bastante tiempo ya en su release final y aca hay varios que lo usan sin problemas.
En mi caso, yo soy mas conservador y prefiero el probado metodo de usar una particion fat32 para compartir archivos entre los SO, pero en tu caso no creo que sea posible. Mi consejo es que busques en los foros los problemas conocidos que hay con ntfs-3g (si hay alguno)
Listo, gracias por el consejo...ahora me pongo a buscar eso... de paso comento que anoche instale el ubuntu y empeze a tener mis primeros encuentros con linux :)

> **Al_maverick said:**
> y por supuesto, que hagas backup antes de modificar las particiones. Esto último es imprescindible, además de una buena costumbre. :D
Si... esa es una excelente costumbre, que al menos en mi caso, la tube que aprender por experiencia en el pasado...desde entonces siempre hago backups periodicamente...

---

### Post by josedamico on 2007-07-17
ojo..si lo instalas en d: te va a borrar lo que tengas en d. Tenes que decirle a ubuntu que te lo instale en "lo que queda libre del disco,es decir, en e: o sea..tenes que hacer una nueva particion (que en win se llamaria e:) para no perder lo de c y lo de d.
saludos

---

### Post by Thalskarth on 2007-07-22
Bueno... gracias... lo pude instalar y luego de probar ubuntu, kubuntu y xubuntu... he decidido quedarme con el Xubuntu que es el que mas me gusto..

Ahora tengo una duda nueva... he hecho una instalacion limpia con el cd de Xubuntu... como puedo hacer para habilitat el compiz??? y tener los efectos?? ya que no aparece la opcion en el menu...(funciona en Xfce el compiz o uso Beryl????

gracias.....

---

