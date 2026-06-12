---
title: "Ubuntu x64 o x86?"
date: 2008-05-10
forum: Argentina Team
---

### Post by smrdelj on 2008-05-10
Hola q tal. Tengo una maquina AMD Athlon 64 y me pregunto si realmente me conviene la version AMD 64 de Ubuntu antes que la i386...

En este momento tengo la x64, pero leyendo un par de cosas pareciera ser que la i386 es mas conveniente.

Qué opinan?

Saludos

---

### Post by Kabezon on 2008-05-10
Yo uso la i386, te ahorrás muchos dolores de cabeza. Además, tengo entendido que la versión 64 es medio al ****, que las aplicaciones de 64 bits corren igual o no sé qué o.o

---

### Post by brunovecchi on 2008-05-10
A mi también me interesaría saber si ya está listo el terreno para pasarse a 64 bits... hace dos o tres meses me había puesto a leer en los foros qué decían, y parecía que habia problemas, por ejemplo, con el Flash...

---

### Post by guillermolisi on 2008-05-10
Personalmente y siempre suponiendo que tenes hardware para 64 bits, la mejora sustancial que logras con la distribucion de 64b es que podes utilizar hasta 8Gb de RAM.
No hay razones tecnicas para pensar que logras una sustancial mejora de rendimiento respecto de la misma alternativa en 32b y tenes como contrapartida que algunas cosas aun no estan suficientemente maduras como para lograr una instalacion y funcionamiento fluidos, sin mayores trabas, por lo menos por ahora.

Es cierto que en cada nueva version las mejoras son muchas pero la evaluacion que haria es si realmente voy a aprovechar las reales ventajas de un entorno de 64 bits (respecto de lo mismo en 32).

Otro tema a considerar es que no recomiendo usar 32bits si la maquina es de 64b y tendra mas de 4Gb de RAM. Ya hice la experiencia y fue un verdadero desastre cuando puse la maquina en produccion (la instalacion fue libre de problemas. Los problemas vinieron cuando el rendimiento del sistema se mostro muy por debajo de su equivalente en 32b).

Esta experiencia la hice con Ubuntu 8.04 32b server y Vmware para virtualizar en una maquina con Opteron y 8 Gb RAM (VmWare es solo de 32 bits por ahora, es decir que permite correr VMs de solo 32 bits).

Luego se probo con la misma version de Ubunut pero 64b. Es condujo a probar dos placas de red para servers, una 3Com con chip Broadcom y una Intel que no funcionaron. Si funciono bien la interface de red incorporada a la motherboard (Asus M2N-E SLI, chipset nForce 500) gracias a que nVidia proveyo los paquetes para ese chipset.

Igual, si tienen tiempo y ganas, nada como hacer epxeriencia propia para aprender.

---

### Post by smrdelj on 2008-05-10
Oka

Ya instalé el x86 para probar...la verdad q mucha diferencia no noto por ahora. Pero puede ser q sea un poco mas rapido

---

### Post by euzkoarima on 2008-05-12
Dos preguntas relacionadas con lo que cuenta guillermolisi:

1) Tenía ganas de probar una version 64 bits, pero para no hacer mucho lío pensaba correrla como máquina virtual. La pregunta es si con esta combinación se puede probar o por estar en 32 se sabe de antemano que no va a funcionar:

_Procesador_ amd 5200+ (o sea, 64)
_Sistema instalado_: ubuntu 7.10 de 32
_Programa para virtualizar_: virtual box 1.5.4 de 32 (baje el .deb de la pagina de ellos)

2) en ubuntu 32 si tenes exactamente 4gb, anda todo ok, o cae el rendimiento como cuando tenes 8 Gb. De otro modo: hasta cuanta ram puedo tener si mi ubuntu es 32 sin meterme en problemas.

Saludos

---

### Post by tzulberti on 2008-05-12
Mira: al menos que uses el procesador de 32bits al 100% no creo que notes alguna diferencia demasiado grande entre ubuntu 64 y 32. 
El problema con 64bits se encuentran en los programas propietarios:
-> algunos plugins de firefox (puede ser que este mal en este tema)
-> flash
-> codecs de video 

Por lo tanto te recomiendo ubuntu de 32 bits.

---

### Post by guillermolisi on 2008-05-12
> **euzkoarima said:**
> Dos preguntas relacionadas con lo que cuenta guillermolisi:

1) Tenía ganas de probar una version 64 bits, pero para no hacer mucho lío pensaba correrla como máquina virtual. La pregunta es si con esta combinación se puede probar o por estar en 32 se sabe de antemano que no va a funcionar:

_Procesador_ amd 5200+ (o sea, 64)
_Sistema instalado_: ubuntu 7.10 de 32
_Programa para virtualizar_: virtual box 1.5.4 de 32 (baje el .deb de la pagina de ellos)

2) en ubuntu 32 si tenes exactamente 4gb, anda todo ok, o cae el rendimiento como cuando tenes 8 Gb. De otro modo: hasta cuanta ram puedo tener si mi ubuntu es 32 sin meterme en problemas.

Saludos

Hasta donde se, los productos para virtualizacion, VirtualBox y VmWare que son los dos que mas uso, son solamente de 32 bits con lo cual no deberias lograr una instalacion de 64 exitosa dentro de una VM con esas caracteristicas.

Si lo haces y te va bien, avisa asi nos enteramos que en una VM SI se puede.

La principal ventaja de una VM es la abstraccion que se logra respecto del hardware del host (o sea, la maquina que alberga a las virtuales) y que te permite instalar alguna software que no se lleva bien con cierta tecnologia moderna y que dentro de una VM y gracias a esa abstraccion, funciona lo mas bien.

De hecho en el laburo se hicieron dos VMs con SCO Unix OpenServer (version del año 1992 aprox.) que no funcionaban ni a palos en ningun servidor moderno y en las virtuales anda una barbaridad.

Las maquinas de 32 bits, Intel o AMD, solo aceptan hasta 4Gb RAM por una limitacion de hardware y de como la arquitectura Intel administra la memoria. Generalmente en las fichas tecnicas de las motherboards mencionan este limite.

---

### Post by euzkoarima on 2008-05-13
> **tzulberti said:**
> Mira: al menos que uses el procesador de 32bits al 100% no creo que notes alguna diferencia demasiado grande entre ubuntu 64 y 32. 


Totalmente de acuerdo, en realidad solo quiero instalar para: probar, aprender, etc. De ahí que quería hacerlo en VM para no tener que reiniciar cada vez que tenga tiempo para investigar la versión de 64.

> **guillermolisi said:**
> Hasta donde se, los productos para virtualizacion, VirtualBox y VmWare que son los dos que mas uso, son solamente de 32 bits con lo cual no deberias lograr una instalacion de 64 exitosa dentro de una VM con esas caracteristicas.

Si lo haces y te va bien, avisa asi nos enteramos que en una VM SI se puede.


Ok, ya que estamos lo pruebo y cuento como me salió, pero sabiendo que lo previsible es que no funcione.

> **guillermolisi said:**
> 
Las maquinas de 32 bits, Intel o AMD, solo aceptan hasta 4Gb RAM por una limitacion de hardware y de como la arquitectura Intel administra la memoria. Generalmente en las fichas tecnicas de las motherboards mencionan este limite.

Si, justamente, el límite teórico de 32 bits es 4GB por lo que supongo que si pongo 4Gb de una pc y le pongo ubuntu 32 debería comportarse similar a como lo haría de haber puesto 2 Gb y no en forma similar a haber puesto 8Gb (la prueba que hiciste y que dio que andaba muy lento, si mal no recuerdo era porque arma un mapeo tipo swap pero de memoria en memoria)

Mi duda es generó porque un amigo se compró una pc con 4Gb, le puso winbugs vista 32 y no solo no le reconocía los 4Gb (tomaba algo asi como 3,6) sino que además le funcionaba mal. Tuvo que instalar winbugs 64. Yo creo que es un tema de winbugs y no de 32bits.

Gracias por las respuestas y saludos

---

### Post by margori on 2008-05-13
Estmados amigos: Voy a intentar quebrar algunos mitos sobre la version de 64 bits de ubuntu, que justamente tengo instalada en mi maquina desde hace unos 4 meses.

No existen problemas con firefox, plugins y demas yerbas. De hecho con Hardy me funciona el sonido de flash, cosa que con gusty no tenia. Incluso ya tengo instalado Skype "64" desde el repositorio de medibuntu.

He encontrado practicamente todos los paquetes en 64 bits que he buscado.

Si virtualbox esta instalado sobre un OS de 32b el procesador virtualizado tambien es de 32b. Lo intente varias veces y no me dejaba instalar hardy 64b en una maquina virtual sobre un SO de 32.

Admito que VMware no he visto nada. Es pago así que, como no quiero pagarlo, no voy a violar la licencia.

He tenido la sensasión que el rendimiento ha caido un poquito desde que pase a 64b debido a mayor uso del CPU. Aunque el tiempo que tardo en ripear un DVD a Xvid sigue siendo el mismo. No puedo hacer mas pruebas debido a que es una maquina compartida.

Conclusion, no veo diferencia apreciable entre la la version de 32 y 64b. Creo que aun no se le saca el jugo a este cambio.

---

### Post by guillermolisi on 2008-05-13
> **euzkoarima said:**
> 

Si, justamente, el límite teórico de 32 bits es 4GB por lo que supongo que si pongo 4Gb de una pc y le pongo ubuntu 32 debería comportarse similar a como lo haría de haber puesto 2 Gb y no en forma similar a haber puesto 8Gb (la prueba que hiciste y que dio que andaba muy lento, si mal no recuerdo era porque arma un mapeo tipo swap pero de memoria en memoria)

Mi duda es generó porque un amigo se compró una pc con 4Gb, le puso winbugs vista 32 y no solo no le reconocía los 4Gb (tomaba algo asi como 3,6) sino que además le funcionaba mal. Tuvo que instalar winbugs 64. Yo creo que es un tema de winbugs y no de 32bits.

Gracias por las respuestas y saludos

Una PC de 32 bits con SO de 32 bits y 4Gb RAM deberia funcionar perfectamente bien, sin perdida de rendimiento. La merma en la cantidad de memoria total disponible se debe a la famosa administracion de RAM que hace la arquitectura Intel, donde necesita reserva para su uso una parte de esa RAM para llegar a direccionar el total de memoria instalada. Es mas, en algunas maquinas esa merma es menor que en otras (y en esto le doy credito a tecnicos que han hecho esta experiencia de campo) dependiendo del BIOS, la motherboard, procesador, etc.

Cuando pones SO de 64 ves los 4Gb RAM en forma completa (porque el hardware tambien permite direccionar directamente toda esa cantidad de RAM al ser una arquitectura diferente).

---

### Post by guillermolisi on 2008-05-13
> **margori said:**
> Estmados amigos: Voy a intentar quebrar algunos mitos sobre la version de 64 bits de ubuntu, que justamente tengo instalada en mi maquina desde hace unos 4 meses.

No existen problemas con firefox, plugins y demas yerbas. De hecho con Hardy me funciona el sonido de flash, cosa que con gusty no tenia. Incluso ya tengo instalado Skype "64" desde el repositorio de medibuntu.

He encontrado practicamente todos los paquetes en 64 bits que he buscado.

Si virtualbox esta instalado sobre un OS de 32b el procesador virtualizado tambien es de 32b. Lo intente varias veces y no me dejaba instalar hardy 64b en una maquina virtual sobre un SO de 32.

Admito que VMware no he visto nada. Es pago así que, como no quiero pagarlo, no voy a violar la licencia.

He tenido la sensasión que el rendimiento ha caido un poquito desde que pase a 64b debido a mayor uso del CPU. Aunque el tiempo que tardo en ripear un DVD a Xvid sigue siendo el mismo. No puedo hacer mas pruebas debido a que es una maquina compartida.

Conclusion, no veo diferencia apreciable entre la la version de 32 y 64b. Creo que aun no se le saca el jugo a este cambio.

VMware te ofrece para uso personal una licencia gratuita para su version server (que incluye la consola de administracion de VMs), por eso la uso.

De forma similar VBox hace lo propio para su version no-OSE.

Si el OS del host es de 32 Vbox permite configurar una VM de 32bits. Ahora, si el OS del host es de 64 Vbox permite configurar VMs de 64 bits ?

Tenia entendido que Vbox solo ofrece versiones a la fecha de 32 bits only.

---

### Post by euzkoarima on 2008-05-13
> **guillermolisi said:**
> Una PC de 32 bits con SO de 32 bits y 4Gb RAM deberia funcionar perfectamente bien, sin perdida de rendimiento.

Hasta aca clarísimo maestro. Pregunto por las dudas, si la pc tiene procesador de 64 y mother con soporte para 8 gb pero instalo ubuntu 32 y le pongo 4gb debería ser también sin perdida de rendimiento, no?

---

### Post by euzkoarima on 2008-05-13
> **margori said:**
> Conclusion, no veo diferencia apreciable entre la la version de 32 y 64b. Creo que aun no se le saca el jugo a este cambio.

Si, como conté antes, simplemente quería probar. Tengo leído por ahí que donde si hay diferencia es en programas que aprovechan bien los 64 bits, como por ejemplo algunos de base de datos. Dicen que cuando se los "tuneo" en serio para 64 se logra un 25 a 30% de mejora en velocidad sobre el mismo hard con respecto a la version 32 birs. Lamentablemente no me acuerdo donde leí ese test comparativo.

Saludos.

---

### Post by guillermolisi on 2008-05-13
> **euzkoarima said:**
> Hasta aca clarísimo maestro. Pregunto por las dudas, si la pc tiene procesador de 64 y mother con soporte para 8 gb pero instalo ubuntu 32 y le pongo 4gb debería ser también sin perdida de rendimiento, no?

Exacto, deberia funcionar perfectamente bien bajo esas condiciones. Por eso hable de sistemas con mas de 4Gb RAM porque hasta ahi no deberia haber problemas.

---

### Post by euzkoarima on 2008-05-14
> **euzkoarima said:**
> 
Ok, ya que estamos lo pruebo y cuento como me salió, pero sabiendo que lo previsible es que no funcione.

y ... no funcionó no más, como era previsible.

---

### Post by oktubrer on 2008-05-16
> **margori said:**
> Estmados amigos: Voy a intentar quebrar algunos mitos sobre la version de 64 bits de ubuntu, que justamente tengo instalada en mi maquina desde hace unos 4 meses.

No existen problemas con firefox, plugins y demas yerbas. De hecho con Hardy me funciona el sonido de flash, cosa que con gusty no tenia. Incluso ya tengo instalado Skype "64" desde el repositorio de medibuntu.

He encontrado practicamente todos los paquetes en 64 bits que he buscado.
.........
Conclusion, no veo diferencia apreciable entre la la version de 32 y 64b. Creo que aun no se le saca el jugo a este cambio.

Coincido 100%, no tengo ningún problema con flash, todos los paquetes que busqué los encontré, idem también acerca del rendimiento.  
Creo que instalé la versión de 64 bits porque es la que "corresponde" al hardware que tengo, y soy cabezadura, si corresponde esa versión quería tener instalada esa versión.
Al principio, en 7.04 tuve que instalar algunos plugins para 32 bits y tuve que andar buscandole la vuelta a muchas cosas.  Pero con las versiones posteriores nunca tuve problemas (creo que cuando instalé Gutsy desde cero ya arrancó solo el flash).

---

### Post by Apipote on 2008-05-16
Se puede ver Youtube sin problemas con Ubuntu 64 bits??
Ya existe Flash para 64 bits?
Como es la cosa?
Gracias.

---

### Post by odiseo77 on 2008-05-17
> **Apipote said:**
> Se puede ver Youtube sin problemas con Ubuntu 64 bits??
Ya existe Flash para 64 bits?
Como es la cosa?
Gracias.

No existe el flash de adobe para 64 bits, pero en Hardy 64 bits, al instalar el paquete flashplugin-nonfree, esto te instala nspluginwrapper (o algo asi), que te permite usar el flash de adobe en 64 bits. Y si, se pueden ver los videos de youtube despues de instalar el plugin.

De todas formas, como ya se ha dicho antes aqui, no es muy notable la diferencia de rendimiento entre 32 bits y 64 bits.

---

### Post by Apipote on 2008-05-18
Vos sabes Odiseo que en mi compaq f566la la version de 64 anda mejor, ya que, no me sale un famoso "bug bios" que si veo en la de 32. 

En rendimiento, *me parece* que es más suave y responde mejor con 64.

Espero Intrepid.

Slds

---

### Post by Barasuishou on 2008-05-20
hola yo instale wubi hace 1 día 2 si contamos hoy :P, y tengo un prosesador de 64 bits, ahora nose que versión de ubuntu me instalo si la x86 o la x64, la verdad esta bien dicen que la x64 tiene algunos problemas no me importa es la que corresponde con mi prosesador, por más que tenga 1gb de ram, ahora como puedo saber si tengo la x64 o la x86???? y si depaso alguien está medio generoso me puede explicar la dif entre los 64 bits y los 32bits(en prosesador obvio), por que entiendo que ocmo que prosesan mas información, pero los dual core también lo hacen y no son lo mismo :S, bueno me despido suerte chauuuuuuu

---

### Post by Barasuishou on 2008-05-20
aa y me olvide instalando un plugin para firefox de flash, me tiro failed, había leido que en la version x64 pasaba eso pero que con "nose que cosa" se arreglaba, alguien sabe??, gracias y ahora si chauuuuuu

---

