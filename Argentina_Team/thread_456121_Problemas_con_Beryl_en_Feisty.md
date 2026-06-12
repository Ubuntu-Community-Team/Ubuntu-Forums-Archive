---
title: "Problemas con Beryl en Feisty"
date: 2007-05-27
forum: Argentina Team
---

### Post by konstantin88 on 2007-05-27
Hace un mes actualicé a Feisty y la verdad no tengo ningún problema, estoy muy conforme, pero si tuve un problema cuando hace unos días instalé Beryl. 
Los tres primeros días anduvo de maravilla, me sorpendió, la verdad que es fantástico...lo que sí, siempre tenía que iniciarlo yo manualmente luego de iniciado Ubuntu, no sé si hay alguna opción para que se inicie automáticamente desde la carga. 
El punto es que hoy cuando inicio Ubuntu y luego Beryl, no funciona como antes, es decir, solo me agrega un área de trabajo, impidiéndome muchas funcionalidades, como las del cubo o la de elegir ventanas. Además se reinició toda la configuración del tema que había elegido.
No sé que puede haber pasado porque no hice nada en particular solo apagarla anoche funcionando y hoy encenderla viendo que ya no funciona como antes.
Deshabilité los efectos de escritorio, los volví a habilitar e inicié Beryl y sigue igual, mismo resultado al reiniciar el sistema.
Saben a qué se puede deber?
Gracias

---

### Post by jajajavi on 2007-05-27
> **konstantin88 said:**
> ...lo que sí, siempre tenía que iniciarlo yo manualmente luego de iniciado Ubuntu, no sé si hay alguna opción para que se inicie automáticamente desde la carga. 


Probá agregando **beryl-manager** en Sistema>Preferencias>Sesiones>Programas de inicio. En cuanto a lo otro no se me ocurre. A mí me pasa que desde que hice el upgrade Beryl no me reconoce la "decoración" de las ventanas.

---

### Post by konstantin88 on 2007-05-28
Si jajajavi, agregándolo ahí empieza desde el inicio...

Ahora vamos a ver si alguien sabe que hacer para volverlo al estado original, para que reconozca los temas, funcionen las áreas de trabajo como cubo y se puedan usar la mayoría de las opciones de Beryl.
Me olvidé de comentar, creo que algo debe tener que ver, que antes cuando entraba a mi sesión aparecía el cartel vertical celeste y blanco de Gnome y desde que falla Beryl aparece uno similar a los de Edgy y Dapper, horizontal con la inscipción Ubuntu. No sé si les da algún dato eso.

Gracias

---

### Post by jajajavi on 2007-05-29
Si acá no encontrás cómo resolverlo te recomiendo que preguntes en [http://www.ubuntu-es.org/](http://www.ubuntu-es.org/) y después comentás cómo lo hiciste. Suerte.

---

### Post by jpmorelli on 2007-05-30
> **konstantin88 said:**
> Si jajajavi, agregándolo ahí empieza desde el inicio...

Ahora vamos a ver si alguien sabe que hacer para volverlo al estado original, para que reconozca los temas, funcionen las áreas de trabajo como cubo y se puedan usar la mayoría de las opciones de Beryl.
Me olvidé de comentar, creo que algo debe tener que ver, que antes cuando entraba a mi sesión aparecía el cartel vertical celeste y blanco de Gnome y desde que falla Beryl aparece uno similar a los de Edgy y Dapper, horizontal con la inscipción Ubuntu. No sé si les da algún dato eso.

Gracias

Para resetear todas las opciones a cero, habilitá la opción de ver archivos ocultos y borrás el directorio .beryl

---

### Post by konstantin88 on 2007-05-30
Borré la carpeta .beryl y sigue igual. 
Lo desinstalé y volví a instalarlo y hay diferencia. 
No sé entonces si el problema es de Beryl, quizá algunas configuración de efectos de escritorio, de algo más general, porque nunca recuperé los cuatro espacios de trabajo, sólo se agrega uno al habilitarlos, sin cambios al activar Beryl. 
Para instalarlo en las dos ocasiones seguí la guía de [http://linuxman.blogsome.com/2007/04/21/beryl-en-ubuntu-feisty-fawn/](http://linuxman.blogsome.com/2007/04/21/beryl-en-ubuntu-feisty-fawn/) 
No sé que hacer y estoy antojado, porque me dejó muy sorprendido Beryl y me da bronca que no pueda utlizarlo, como decía en otro blog, se extraña cuando lo perdés.
Gracias

---

### Post by konstantin88 on 2007-05-30
Hay otro thread que trata tmb de problemas con Beryl pero yo siendo bastante novato me pierdo y no quiero hacer nada sin saber con seguridad es lo que tengo que hacer.
Es [http://ubuntuforums.org/showthread.php?t=441897](http://ubuntuforums.org/showthread.php?t=441897)

---

### Post by jajajavi on 2007-05-31
> **jajajavi said:**
> Probá agregando [B]desde que hice el upgrade Beryl no me reconoce la "decoración" de las ventanas.
Esto se arregla así: Opciones avanzadas de Beryl > Ruta de renderización > Copia

---

### Post by agrelot on 2007-05-31
Yo usé este MiniTuto y anduvo de maravillas.

[http://www.preguntaslinux.com.ar/showthread.php?tid=3044](http://www.preguntaslinux.com.ar/showthread.php?tid=3044)

Quizás sirva

---

