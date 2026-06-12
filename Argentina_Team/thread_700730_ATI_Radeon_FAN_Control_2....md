---
title: "ATI Radeon FAN Control 2..."
date: 2008-02-18
forum: Argentina Team
---

### Post by LuKas7 on 2008-02-18
Hola, este es un copy paste de un thread que inicie en "Absolute Beginner Talk" y no obtuve respuesta...espero que ustedes puedan ayudarme =)

> 
ATI Radeon FAN Control...
Hello All.
I'm very new at Ubuntu...

I was trying to configure my ATI Radeon x1950xt.... the matter is that that VGA get to warm on the FAN default config, On windows os i was using soft like Omega Drivers, ATI tool or Rivatuner...
I'm trying to left MS behind and the only thing stops me is this matter, right now my VGA is almost 80°C....unacceptable.

Do u know any way i can dynamically change the VGA FAN speed??

(i have installed the latest ATI driver for linux....)

(Sry about my english)

Thank you in advance.
Lucas.


---

### Post by faktorqm on 2008-02-18
¬¬ ponelo en castellano ¬¬

---

### Post by LuKas7 on 2008-02-18
jajajaj bueno
Resulta que mi placa de video (ATI Radeon x1950xt) calienta mucho con el FAN configurado de fabrica, en windows uso programas como Omega drivers o ATI Tool para regular dinamicamente (deacuerdo a la temperatura) las revoluciones del FAN....instale ubuntu 7.10 e instala los drivers de mi placa de video para linux pero no encuentro ningun soft para recualr las revoluciones del fan y mi placa esta sin hacer nada a 85°C.....lo cual hace imposible trabajar en ubuntu mas de 30 hora; no quiero fundir todo :S...

Espero que alguien me diga una forma de regular las RPM del FAN =)

desde ya muchas gracias...

---

### Post by clasificado on 2008-02-18
Mi placa de video tiene un disipador pasivo :KS

Pero podrias (Hasta que encuentres una manera) de injertarle un segundo ventilador justo encima del primero.

clasificado

---

### Post by faktorqm on 2008-02-18
solucion rapida (cabeza): el chupete tiene 3 cables, uno si es rojo, lo conectas al conector de la fuente rojo, (si es amarillo va al amarillo ;)) y el negro a cualquier negro, tonces te queda girando al taco todo el tiempo y te olvidas si calienta o no calienta.
solucion lenta: busca un soft que haga eso bajo gnu/linux, si no existe, programalo! :D

---

### Post by LuKas7 on 2008-02-18
> **faktorqm said:**
> solucion rapida (cabeza): el chupete tiene 3 cables, uno si es rojo, lo conectas al conector de la fuente rojo, (si es amarillo va al amarillo ;)) y el negro a cualquier negro, tonces te queda girando al taco todo el tiempo y te olvidas si calienta o no calienta.
solucion lenta: busca un soft que haga eso bajo gnu/linux, si no existe, programalo! :D

Bien.... eso me paso x la cabeza pero la cosa es q a 100% el fan es bastante ruidoso :@
Bajo que lenguaje se puede hacer, se programar pero no bajo linux. serias tan amable de pasarme algun link sobre info de este tema pls? 

Gracias

---

### Post by niko_3100 on 2008-02-19
Sobre que lenguaje? c, c++, java, python, tls, tal ves se podria hacer algo con un buen script shell. Muy probablemente tengas que programar a muy bajo nivel, no te convendria comprar un fan mas? Otra cosa eso es la temperatura del gpu?? porque esos valoresno estan mal fijate la temperatura bajo windows y contanos cuanto hay de diferencia. Para que te des una dia ahora escribiendo solo este mensaje el GPU de mi nvidia geforce 6150 de mi notebook compaq v3415 esta en 85 grados, AAAHH!! me olvide y perdon a todos pero estoy en windows xp, recien termine de jugar al sonic heroes y bueno entre a chusmear, o sea que en xp mi gpu esta a 80 grados.

---

### Post by faktorqm on 2008-02-19
Hola, con lo de programacion es un tema, depende en que sabes programar vos... La idea general es que te atengas a programar bajo estandares iso, ansi, o el que venga y tambien depende del lenguaje. 
En C por ejemplo, tenes que usar ansi, (o posix) eso significa que ni bien queres usar cosas del estilo de conio.h estas completamente equivocado. (el equivalente por decirlo de alguna manera, aunque 10000 veces mas potente, es la biblioteca ncurses.h)
Sobre como manejar el ventilador la verdad no tengo ni idea, si me decis que hay un script o algo en el driver que lo maneja, ahi si, pero no tengo idea intuitiva de donde puede llegar a estar. salu2!

---

### Post by LuKas7 on 2008-02-19
> **niko_3100 said:**
> Sobre que lenguaje? c, c++, java, python, tls, tal ves se podria hacer algo con un buen script shell. Muy probablemente tengas que programar a muy bajo nivel, no te convendria comprar un fan mas? Otra cosa eso es la temperatura del gpu?? porque esos valoresno estan mal fijate la temperatura bajo windows y contanos cuanto hay de diferencia. Para que te des una dia ahora escribiendo solo este mensaje el GPU de mi nvidia geforce 6150 de mi notebook compaq v3415 esta en 85 grados, AAAHH!! me olvide y perdon a todos pero estoy en windows xp, recien termine de jugar al sonic heroes y bueno entre a chusmear, o sea que en xp mi gpu esta a 80 grados.

jkajkam, no, no estoy usando un "sensor" en ubuntu para medir la temperatura, uso mi mano atras de la placa, la tengo re calada xq hice muchos experimentos en windows y se a q temperatura corre con solo poner la mano atras....


> **faktorqm said:**
> Hola, con lo de programacion es un tema, depende en que sabes programar vos... La idea general es que te atengas a programar bajo estandares iso, ansi, o el que venga y tambien depende del lenguaje. 
En C por ejemplo, tenes que usar ansi, (o posix) eso significa que ni bien queres usar cosas del estilo de conio.h estas completamente equivocado. (el equivalente por decirlo de alguna manera, aunque 10000 veces mas potente, es la biblioteca ncurses.h)
Sobre como manejar el ventilador la verdad no tengo ni idea, si me decis que hay un script o algo en el driver que lo maneja, ahi si, pero no tengo idea intuitiva de donde puede llegar a estar. salu2!

opa, mas complicado de lo q pense...voy a tener q aprender denuevo a programar en c jajajaj, la cosa es que todo esto tenia pensado aprenderlo con la pc estable. En este momento no puedo tener la pc corriendo ubuntu por mas de 30 min xq se me funde...

Bueno, voy a tener q seguir siendo esclavo de Microsoft que si bien es una m***da tiene mas soporte T_T

Gracias a todos.

---

### Post by User21 on 2008-02-19
Mandale un mega cooler de los nuevos dentro del gabinete! cero ruido, cero grados! ;)

---

### Post by clasificado on 2008-02-19
> **LuKas7 said:**
> 
Bueno, voy a tener q seguir siendo esclavo de Microsoft que si bien es una m***da tiene mas soporte T_T

Gracias a todos.

¡Vaya nomás! Nosotros lo esperamos de este lado. 

Con los que tendrias que conversar es con los amigos de ATI, que te venden plaquetas con mucha funcionalidad y te enchufan drivers que las aprovechan al 20%.

¡Mas suerte para la próxima!

---

### Post by LuKas7 on 2008-02-20
> **clasificado said:**
> ¡Vaya nomás! Nosotros lo esperamos de este lado. 

Con los que tendrias que conversar es con los amigos de ATI, que te venden plaquetas con mucha funcionalidad y te enchufan drivers que las aprovechan al 20%.

¡Mas suerte para la próxima!

Ya que usted lo comenta, permitame decirle; concuerdo con usted acerca de los drivers de ATI.
En lo que no concuerdo y radica aca mi desconformidad es en cuanto al soporte recibido en este foro, solo una persona posteo una respuesta coherente, yo necesito soluciones concretas, no inventos de particulares para convertir mi placa de video en una quimera, y siendo este el foro oficial del os esperaba encontrarlas aca...

---

### Post by facundocorradini on 2008-02-20
Pues si necesitas soporte, canonical ltd. te lo brinda con mucho gusto...

Nosotros estamos aquí para ayudar **en lo que podemos**

---

### Post by leo_rockway on 2008-02-21
> **LuKas7 said:**
> 
En lo que no concuerdo y radica aca mi desconformidad es en cuanto al soporte recibido en este foro, solo una persona posteo una respuesta coherente, yo necesito soluciones concretas, no inventos de particulares para convertir mi placa de video en una quimera, y siendo este el foro oficial del os esperaba encontrarlas aca...

Te faltan varios beans...

[http://www.canonical.com/services/support](http://www.canonical.com/services/support)
[http://support.ati.com/ics/support/default.asp?deptID=894](http://support.ati.com/ics/support/default.asp?deptID=894)

Que tengas un buen día.

---

### Post by niko_3100 on 2008-02-21
Lukaz7 mira mejor que no encuentres solucion asi no te pasas para ubuntu y te quedas renegando o conforme con windows porque la verdad con esa mala onda mejor anda para otros lados porque aca la gente que postea trata de ayudar y si no se soluciona, mala leche, pero la intencion esta, si tanto te esta molestando hace la facil ponele otro fan y listo y no postees mas y chau. Sino para la proxima comprate una placa de video que sabes que anda 10 puntos en linux y listo, total para que te ande bien linux fluido y con todo no necesitas la super guachi guau placa de video. OK? LISTO CHAU!!!

---

### Post by Hei Ku on 2008-02-21
> **LuKas7 said:**
> Ya que usted lo comenta, permitame decirle; concuerdo con usted acerca de los drivers de ATI.
En lo que no concuerdo y radica aca mi desconformidad es en cuanto al soporte recibido en este foro, solo una persona posteo una respuesta coherente, yo necesito soluciones concretas, no inventos de particulares para convertir mi placa de video en una quimera, y siendo este el foro oficial del os esperaba encontrarlas aca...

Corrección: este es el foro oficial de la comunidad argentina, no el foro oficial de soporte. Si bien ayudamos en lo que podemos, no tenemos todas las respuestas, y mucho menos la respuesta oficial de Canonical, la compañia detras de Ubuntu. Para eso, están los foros de soporte especificos en inglés, o el soporte pago de Canonical, o el soporte oficial de ATI si instalaste el driver oficial.
Nosotros somos voluntarios. Hacemos esto en nuestro tiempo libre y con la mejor voluntad posible.
La proxima, antes de quejarte, informate bien.

---

### Post by clasificado on 2008-03-02
> **LuKas7 said:**
> yo necesito soluciones concretas, no inventos de particulares 

Tenes una placa ATI, le pagaste a ATI por una placa de video con coler regulable, te recomiendo dirigirte a tu proveedor ATI y preguntarles porqué no funciona lo que ellos te vendieron.

En una de esas te solucionan tu problema y nos llevamos una sorpresa todos :)

clasificado

---

