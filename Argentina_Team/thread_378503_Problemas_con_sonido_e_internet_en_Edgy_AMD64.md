---
title: "Problemas con sonido e internet en Edgy AMD64"
date: 2007-03-07
forum: Argentina Team
---

### Post by walden2 on 2007-03-07
Bueh, antes que nada, mil perdones si temas como este ya están posteados. Lo posteé en otra sección del foro (en inglés) pero nadie ha respondido y quiero soluciones lo más rápido posible antes que tenga que empezar la facu de nuevo.
La cosa es esta: hace unos días tuve la suerte de poder actualizar mi querida compu a un flamante Athlon 3200+ de 64 bits, pero tengo horribles problemas para instalar Ubuntu. 
Primero traté con Dapper para AMD64 y tanto ese como Dapper para x86 me tiran el mismo problema al tratar de arrancar el live CD: problemas con el X server. Después intenté con Edgy para x86 dos veces: la instalación nunca pudo pasar el 75%, siempre se "tildaba" ahí.
Finalmente tuve suerte con la instalación de Edgy para AMD64. Pero cuando arranqué por primera vez el sistema, mi emoción y alegría recibieron un cascotazo desmoralizador: no andaban ni el sonido, ni internet.
Parece que Edgy no se da cuenta que tengo una placa de sonido. En cuanto a internet, no logra detectar la conexión de red entre la ethernet y mi cablemodem. Ninguna de estas dos cosas me pasó jamás con mi compu vieja.
Mi computadora nueva de la desgracia es esta:

AMD Athlon 64 3200+
Motherboard Asrock AM2NF6G-VSTA con placa de video onboard nVidia GeForce 6100 nForce 405, y placa de sonido onboard 7.1 Realtek ALC888. La placa de red también esta incluída en la mother.
512 MB de RAM DDR2
Disco Western Digital WD1600JS-00NCB1, 160 GB SATAII

Entonces, ¿qué puedo hacer para que Edgy ande bien? Si de última es imposible hacerlo funcar, ¿qué otra distribución me recomiendan? Muchísimas gracias, y espero que me contesten, por favor. Lo que queda de mis vacaciones depende de esto.

---

### Post by scrooge_74 on 2007-03-07
Creo que lei en algún lugar que es problemas de drivers para la version de 64, no sé que tan factible sea que pruebes con las versiones de Debian directamente

---

### Post by walden2 on 2007-03-07
Si son problemas de drivers, ¿de dónde puedo sacar los drivers para Edgy64?

---

### Post by beuno on 2007-03-07
> **walden2 said:**
> Si son problemas de drivers, ¿de dónde puedo sacar los drivers para Edgy64?

Con 64bit, probablemente tengas que empezar a compilarlos.
Te recomiento pasarte a 32bit si no tenes el tiempo/conocimiento para estar resolviendo los problemas que tienen las distro 64bit hoy en dia.

---

### Post by walden2 on 2007-03-08
> **beuno said:**
> Con 64bit, probablemente tengas que empezar a compilarlos.
Te recomiento pasarte a 32bit si no tenes el tiempo/conocimiento para estar resolviendo los problemas que tienen las distro 64bit hoy en dia.

En verdad no tengo los conocimientos, es uno de mis pendientes. Ahora, tomo el consejo de volver a una distro de 32 bits, pero ¿cuál instalo? Todas las versiones de Ubuntu que intenté me dejaron a pata, como lo puse en el primer post.

---

### Post by Jpedros2 on 2007-03-08
Yo he instalado, sin ningún problema, Edgy 32 bits en un AMD thurion a 64 bits.
No me funciona el sonido ni la tarjeta wireless,
pero supongo que lo terminaré arreglando.
Debe ser cosa de localizar los drivers.
Me pasa porque es un ordenador de empresa,
si fuera mío me hubiera asegurado antes de comprarlo de que los componentes son 100% compatibles con GNU/LINUX.
--
Jesús

---

### Post by DuckMan on 2007-03-09
tengo un amd64 dual core y me pasaba lo mismo, tenes q instalar feisty o compilar el kernel nuevo (supongo)

---

### Post by walden2 on 2007-03-10
> **DuckMan said:**
> tengo un amd64 dual core y me pasaba lo mismo, tenes q instalar feisty o compilar el kernel nuevo (supongo)

Lo que pasa es que por lo que tengo entendido Feisty está en etapa de desarrollo, no sé si será lo suficientemente estable como para manejarme con él en el día a día. Si tuviese que recompilar el kernel, ¿me pasan algún lugar de donde sacar información sobre cómo hacerlo?
Aún no he tenido tiempo para probar instalar algunos drivers, pero si eso no funciona me coy a tirar a compilar el kernel, y, en última instancia, instalar Feisty o esperar al lanzamiento.

---

### Post by DuckMan on 2007-03-10
mira, es verdad eso.. pero en tu caso es lo mas facil. yo lo estuve usando y realmente es estable, yo lo recomendaria, ademas falta 1 mes solamente para q salga..

igual si no te queres arriesgar, lo de compilar el kernel no estoy seguro, pero hay guias para hacerlo. es mas, creo q en este foro hay una en castellano, fijese

---

### Post by scrooge_74 on 2007-03-10
Los teams de Argentina tenienen un thread donde sale como compilar el kernel es bastante informativo.

A Feisty no le falta mucho casi que puedes decir que está llegando a la versión final, probablemente en un par de semanas saquen en anuncio de congelar el código y preparar la versión final

---

