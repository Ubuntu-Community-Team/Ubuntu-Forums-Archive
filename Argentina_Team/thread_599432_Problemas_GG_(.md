---
title: "Problemas GG :("
date: 2007-11-01
forum: Argentina Team
---

### Post by faktorqm on 2007-11-01
Hola, bueno ahora me toco el 8 a mi.................

El primer problema y principal, es el siguiente, estoy cursando Algoritmos y programación en la facultad, y yo usaba el anjuta chocho de la vida. En el laburo actualice a GG... y trajo una nueva versión muy copada del Anjuta, pero para compilar usa make y no gcc!! Esto en realidad no es que me "traba", pero es mas facil apretar F11 -> F3 que ir a la consola... Ahora bien, dentro de un tiempo bastante corto, sí tenemos que compilar con make,  asi que tampoco me gustaria quedarme sin make y con gcc jajaja
A alguien le paso? Yo me pasee por todas las opciones y no encontre nada. :'( 
Espero que me puedan ayudar, por que la verdad es que buske en internet y hay uno solo que le paso en espaciolinux y nadie le respondio...........
Desde ya aviso que tengo instalado build-essential,  autoconf,  automake, m4, etcetcetc
y que ademas de eso se usar Makefile y demas menesteres, pero ahora particularmente necesito gcc. 

El segundo problema es que por ejemplo, yo no quiero tener Evolution, ni Firefox, Ni soporte para Bluetooth, ni para cosas inalambricas, y cada vez que quiero desinstalar algo de todo eso, me dice que me va a borrar ubuntu-desktop, ubuntu-minimal, y ubuntu-standard. NO quiero ocupar espacio en disco con cosas que no me sirven, como hago para desinstalar todo eso??

El tercer problema es que, entre la pantalla del grub, y la pantalla de logueo, donde tengo que ingresar usuario y contraseña digamos, el monitor me tira el cartel de fuera de frecuencia!!! supuestamente en lugar de ese cartel deberia ver la barrita naranja de ubuntu cargandose. Le pongo la opcion nosplash al grub cuando arranca? o como le digo que la frecuencia de mi monitor es tal o cual asi me aparece "normal" digamos?

El cuarto problema e irresoluble problema in eternum: el chipset vt8237, mas conocido como via chrome9 o como k8m890. No hay driver, no hay un soto, estoy un poco harto de ver mi escritorio cuadrado y lento cuando todos estan felices con su cubo :'( y no es una compu que no de para hacer eso.................... alguna recomendacion? ya tengo las ****las al plato de buscar en internet y probar 15000 drivers.

El quinto problema, si bien es el menor de todos, es mas a modo de curiosidad que otra cosa: Aca en el trabajo compraron unos switches 3COM que administro yo, por lo tanto cuando los tuve que instalar tuve que arrancar si o si en M$ por que el programa que usan ellos (se llama Discoverer) en linux no anda. Traté de emularlo pero no hubo caso. tardo una eternidad escribiendo cosas en el disco y despues se paro y no pasaba nada. Existe o alguien conoce una alternativa a ese programa?

Che bueno, para mantener el orden POR FAVOR respondan a cada pregunta por separado, no es posts separados, sino claramente. :P
Desde ya gracias a todos por su ayuda. Nos vemos!!!! ^_^

---

### Post by niko_3100 on 2007-11-01
Mira no entiendo bien la primer pregunta estaria bueno porque no se, la diferencia entre make y gcc jejeje!!

La segunda no probe a desintalar firefox y evolution pero si desintale el soporte para bluetooth y me lo desintalo solo, proba desinstalando de a uno... no se.

La tercera a mi en esta computadora del laburo me paso lo mismo puse el "nosplash" en el grub y santo remedio, me tira lo que va levantando el SO a mi putno de vista es mucho mas informativo y linuxero ver esa informacion que una imagen cargando algo que no muestra :D

El cuarto problema no intentaste comprando una placa de video ati o nvidia?? jejeej

Quinto ni idea.

---

### Post by marianom on 2007-11-03
faktor, si da, probá de tirar tus consultas a la lista. Capaz que alguien de ahí -hay mucha gente que no visita los foros- te puede ser de ayuda con alguno de estos temas.

---

### Post by por100pre1 on 2007-11-03
> **faktorqm said:**
> El segundo problema es que por ejemplo, yo no quiero tener Evolution, ni Firefox, Ni soporte para Bluetooth, ni para cosas inalambricas, y cada vez que quiero desinstalar algo de todo eso, me dice que me va a borrar ubuntu-desktop, ubuntu-minimal, y ubuntu-standard. NO quiero ocupar espacio en disco con cosas que no me sirven, como hago para desinstalar todo eso??

Esos tres paquetes son metapaquetes, no se rompera tu sistema. Ubuntu-desktop se remueve con solo quitar algun programa como Firefox o Evolution. Los otros se van si quitas inalámbricos o servicios similares. Quítalos sin miedo. Solo no quites servicios obviamente indispensables y recuerda reinstalar los 3 metapaquetes antes del próximo dist-upgrade de Ubuntu.

> **faktorqm said:**
> El tercer problema es que, entre la pantalla del grub, y la pantalla de logueo, donde tengo que ingresar usuario y contraseña digamos, el monitor me tira el cartel de fuera de frecuencia!!! supuestamente en lugar de ese cartel deberia ver la barrita naranja de ubuntu cargandose. Le pongo la opcion nosplash al grub cuando arranca? o como le digo que la frecuencia de mi monitor es tal o cual asi me aparece "normal" digamos

Lee [esto]("http://ubuntuforums.org/showpost.php?p=3700169&postcount=2"), a algunos le funciona. Es posible que tengas que verificar el driver de tu tarjeta gráfica, eso me sirvió a mí.

---

### Post by faktorqm on 2007-11-05
gracias x100pre1, con respecto a lo primero que pusiste se me rompio "un poquito", borre el metacity!!! despues lo volvi a instalar y quedo todo ok. ahora estoy sin firefox ni evolution ni bluetooth ni nada. 

con lo otro, hice lo que me dijiste, pero paso algo que no esperaba.... segui lo que decia tu post... y cuando apaga, me empezo a mostrar bien la barrita naranja.... pero cuando prende no! O.O
asi que bueno, despues voy a revisar bien el xorg.conf y veo que onda.

niko_3100: es la pc del laburo, no pienso gastar un solo centavo como te imaginaras ;) Lo que mas me molesta en realidad, es que si yo tuviera esa compu en mi casa estaria pateandola mas o menos, o pateandole las puertas a los de via..... no puede ser que no tengan drivers decentes para esos chipsets, aparte venden mucho, no es que no los conoce nadie.... we, no importa. gracias a todos, salu2!!!!


p.d.: apreciacion personal: el 7.10 me anda peor que el 7.04 en el laburo, a alguien le paso? jaja espero no ser yo el "lokito". yo se que tiene mejor soporte para hardware y demas, pero la verdad me anda bastante para atras a mi :( mepa que voy a terminar probando un debian............

---

### Post by niko_3100 on 2007-11-05
Nono, no sos el unico yo tambien noto que el 7.04 me anda mejorcito que el 7.10. En mi notebook no lo pude instalar no me levanta ni siquiera el live CD me tira un error de microcode con el bcm43xx que tiene que ver con mi placa WIFI broadcom... tube que volver a feisty que la verdad anda de 10.

---

### Post by por100pre1 on 2007-11-07
> **faktorqm said:**
> p.d.: apreciacion personal: el 7.10 me anda peor que el 7.04 en el laburo, a alguien le paso? jaja espero no ser yo el "lokito". yo se que tiene mejor soporte para hardware y demas, pero la verdad me anda bastante para atras a mi :( mepa que voy a terminar probando un debian............

No, no eres el unico enfrentando estos dilemas. La verdad es que GG posee cambios bastante radicales y grandes cambios acarrean posibles rupturas. Puedes volver a Feisty si así lo deseas, y entonces hacer una instalación fresca de Hardy. Si aún así decides instalar Debian haznos saber como esta andando Debian en estos días. :)

---

