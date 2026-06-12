---
title: "X86 o AMD64???"
date: 2007-10-12
forum: Argentina Team
---

### Post by Thalskarth on 2007-10-12
[COLOR="Indigo"]Hola buenas, anteriormente me han ayudado bastante asi que ahora vuelvo a molestar...[/COLOR]

[COLOR="Indigo"]Mi pregunta es, aprovechando la proxima salida de ubuntu, que versión me conviene descargar y usar en mi PC???


Tengo un AMD Sempron 2600+ con 512 de RAM. Y al menos con la version 7.04 de Ubuntu, andaban tanto la X86 como la AMD64. Y es debido a eso mi interrogante?


Cual es la diferencia entre ambas? o cual me conviene usar?  para dar un uso estandar de la PC por alguien que hace pocos meses empezo?

Desde ya muchas gracias[/COLOR]

---

### Post by angelqpro on 2007-10-12
No soy nada experto en Linux, de hecho aqui estoy pidiendo ayuda, pero si en hardware.
Y los procesadores AMD 64 funcionan en 64 bits. por lo que me parece que será mejor un sistema operativo del mismo tipo, para aprovechar toda su potencialidad. No olvidemos que un n umero de 64 bits es 4800 millones de veces mas grande que uno de 32 bits.
Aunque eso será completamente aplicable cuando haya mas soft que trabaje en ese entorno. pero aun asi, los sis op de 64 son retrocompatibles para atras, es decir, con 32 bits.
Espero haber sido acertado en el concepto.

---

### Post by Hei Ku on 2007-10-12
si empezaste hace poco, te conviene la x86, porque hay mas packages preparados para esa version. Para 64, a veces tenes que compilarlos vos porque no estan disponibles.

---

### Post by rretamar on 2007-10-13
Mi modesto consejo es que huyas de la versión de 64 bits, y más si estás empezando. Te puede dar varios dolores de cabeza. 

Saludetes !

---

### Post by Thalskarth on 2007-10-14
Ok. Muchas gracias por su ayuda.

Entonces, mejor uso la version X86.

Gracias

---

### Post by matog on 2007-10-14
Yo tengo la de 64 bits, y estoy lejos de ser un experto en linux. Lo complicado es el tema del flash en firefox, pero tampoco es dificil. Cada vez existen mas paquetes para 64bits, casi no noto diferencia. Es mas, nunca tuve que compilar nada...

---

### Post by tzulberti on 2007-10-15
Veamos cuales son las aplicaciones "dificiles" de instalar en Amd64:
-> Flash: en Gutsy el apt lo permite instalar automaticamente
-> Skype: en el foro hay un how-to excelente que te explicaca paso a paso como instalarlo:
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
-> RealPlayer: este sigue siendo dificil de instalar
-> Java (el plugin para firefox): tambien sigue siendo + - o dificil de instalar
-> Acrobar Reader: no tengo ni idea porque no lo uso....

Como vez todas las aplicaciones que no se pueden instalar son las propietarias (no se si me abre olvidado de alguna, pero esas son las mas comunes).

Saludos,
TZ

---

### Post by Hei Ku on 2007-10-15
Desgraciadamente, te olvidaste de varias. Cualquier aplicación que no esté en los repositorios de ubuntu, y la consigas en, por ejemplo, kde-apps, qt-apps, o los similares de gnome, tenes la probabilidad de que este el paquete .deb para ubuntu o kubuntu, pero para x86.

Otro ejemplo que me viene a la mente es el Enemy Territory, en el momento que lo quise instalar, sólo estaba el paquete para x86.

kooldock solo estaba para x86. El kicker y la taskbar de kde para compiz solo estaban para x86. 

En fin, la mayor parte de las bases no pasa de ser configure, make, make install, y ya esta. Pero a un usuario normal, si le dicen que tiene q compilar algo, le parece una cosa imposible. Y una de las razones es que Ubuntu no trae por defecto los programas de compilación, asi que la primera que prueban les tira un monton de errores. Recien cuando instalan el paquete build-essential pueden compilar algo.

Todo esto lo sé por experiencia, porque doy soporte de compilación para programas en Kubuntu, y si bien es simple, y no toma más de un par de mails para explicarlo, se nota una casi "angustia" cuando un usuario nuevo de Linux pregunta qué tiene que hacer.

Una de las grandes ventajas de usar distribuciones populares, es que los paquetes generalmente ya estan hechos, aunque no esten en el repositorio. Pero en la mayoria de los casos no esta el paquete para 64 bits.

---

### Post by tzulberti on 2007-10-15
Como nunca instalo un paquete que no se pueda conseguir por apt-get, porque no tengo necesidad, entonces nunca tuve ese problema

---

### Post by Mister X on 2007-10-15
Yo tengo la version de 64 bits y anda espectacular, con el tema de los paquetes .deb fuera de los repositorios y que solo tienen la version x86, se instalan perfecto con dpkg --force architecture (yo tengo varios instalados asi y cero problemas)

---

### Post by Thalskarth on 2007-10-15
Bueno, gracias por los consejos... pero ahora me han creado otra duda...

Hablando mal y pronto, digamos... cual es la diferencia entre las 2 versiones?? que tiene una que le falte a la otra?? En donde se nota la diferencia para el usuario???

Gracias

---

### Post by tzulberti on 2007-10-15
> **Thalskarth said:**
> Bueno, gracias por los consejos... pero ahora me han creado otra duda...

Hablando mal y pronto, digamos... cual es la diferencia entre las 2 versiones?? que tiene una que le falte a la otra?? En donde se nota la diferencia para el usuario???

Gracias

Si el usuario es el mismo que el admin, entonces la diferencia la vas a notar en la instalacion de programas. 
Aunque hay un poco de mejora en la performance (dependiendo de para que uses la maquina) no es nada del otro mundo.

Como te comentaron anteriormente, la version de 32bits tiene una instalacion mas simple de los paquetes que no estan en los repositorios oficiales, y de los programas propietarios

---

### Post by matog on 2007-10-16
Como dice MisterX, con el dpkg --force architecture hago funcionar bastantes cosas. Aunque tambien tiene razon Hei Ku. Depende el uso que le des. 

Pregunta del millon: Se nota la diferencia de rendimiento entre un procesador de 64 bits al instalar la versión de 32 (respecto a la de 64)? Porque si no se nota, por ahí la de 32 bits para novatos como yo biene bien.

Hei Ku, en cualquier momento te pido ayuda para compilar. Uso ubuntu desde la 5.04 y nunca pude compilar nada, pero es tema de otro post ;)

---

### Post by eldragon on 2007-10-16
hay que aclarar una cosa........

no veo la necesidad de pasar a un sistema 64bit si no lo vas a aprovechar.

512 de ram? estas lejos del limite de los 4gb.

necesitas trabajar con presicion de 64bit? lo dudo mucho. incluso los displays no superan los 24bits. asi que ni mejoria en la calidad de la imagen de tu pantalla.

por estas razones, no utilizaria 64bits yo. si a esto le sumamos la agregada complejidad de instalar algunos paquetes...no vale la pena

saludos.

---

### Post by tzulberti on 2007-10-16
> **matog said:**
> 
Pregunta del millon: Se nota la diferencia de rendimiento entre un procesador de 64 bits al instalar la versión de 32 (respecto a la de 64)? Porque si no se nota, por ahí la de 32 bits para novatos como yo biene bien.


La verdad es que ni se nota la diferencia... Yo soy programador (uso mi pc para programas chicos de la facultad principalmente, aunque ahora estoy haciendo uno grande), y la verdad es que no noto la diferencia entre una de 32bits y una de 64.

Personalmente uso 64bits para aprdender un poco mas... Es decir, con 32bits es todo apt-get, pero con 64bits, por lo menos googleas un sec hasta encontrar lo que estabas buscando...

Saludos,
TZ

---

### Post by Thalskarth on 2007-10-16
OK. Gracias... hacia eso apuntaba mi pregunta... entonces, hoy en dia... y para un usuario como yo... realmente no vale la pena la de 64bist. Porque al menos ahora, es más compleja sin añadir un beneficio notorio


Muchas gracias a todos por su ayuda... les comento, que voy a seguir en los 32bits entonces... :), gracias

---

