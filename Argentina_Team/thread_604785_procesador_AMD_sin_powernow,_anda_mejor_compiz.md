---
title: "procesador AMD sin powernow, anda mejor compiz"
date: 2007-11-06
forum: Argentina Team
---

### Post by niko_3100 on 2007-11-06
Bueno gente le comento que con el conky la mayoria del tiempo mi amd sempron 3500+ corria a 800 mhz solo se iba a 1600 o 1800 mhz cuando lo requeria, esto es bueno por un lado pero opr el lado de compiz fussion anda mejor a 1800 mhz entonces lo que hice fue desintalar desde synaptics powernow que instalo ubuntu por defecto, ahora conky me tira que el procesador se mantiene constante a 1800 mhz y me doy cuenta porque ahjora compiz anda mucho mas fluido pero tambien conky me muestra que la temperatura es un poco mayor que antes dos grados o 3 grados mas o menos. Entonces mi pregunta es la siguiente es conveniente lo que estoy haciendo? O es preferible tener instalado powernow? ya que por lo que parece esto tambien influye en la temperatura del procesador, pero tambien es logico ya que siempre esta trabajando 1800 mhz es obvio que va a tener un poquito mas de temperatura, entonces me encuentro en esta situacion de que hacer.

Me falto mencionar que la temperatura promedio del procesador es 40 grados pero llega hasta 38 grados y no mas de dos veces supero los 51 grados.

---

### Post by Mauro22 on 2007-11-06
A mayor temperatura y mayor frecuencia la vida útil del micro decae. 
Asi generas mas calor, mas desgaste y tenes un consumo electrico mayor. 
Pensá que va a estar asi, jueges, mires una pelicula o no hagas nada...


Yo creo que por algo se rompieron la cabeza tratando de regular la frecuencias del micro.

Yo dejaría que regule la frecuencia del micro.

---

### Post by niko_3100 on 2007-11-06
Pero cuanto es que decae? realmente es significativo? cuanto tiene de vida util un sempron? 5 años? La verdad que se nota bastante la diferencia no solo para copiz sino para abrir cualquier programa pesadito lo levanta mucho mas rapido. Me parece que lo que lo hace alenta mas es el tiempo que tarde el procesador de ir de 800 a 1800, o sea parece que tengo un amd de 800 y en compiz se nota y cuando abro el Myeclipse o openoffice tambien.

---

### Post by Moonlit Knight on 2007-11-07
Mirá yo tengo una Pentium IV 3.0 y resulta que cuando tenía instalado el powernowd la pc se me tildaba, por eso lo desinstalé. Estuve investigando en el foro y el powernowd es un paquete que lo que hace es regular la frecuencia del procesador, pero si te fijás en la descripción del paquete, está hecho para procesadores del tipo mobile (o sea notebooks) y me parece lógico porque en esas necesitan regular la frecuencia para que dure más la batería. 

O sea que me parece que el paquete es inutil en las desktop. Además por lo menos a mi el procesador no me trabaja al máximo todo el tiempo, lo hace cuando lo requiere.

---

### Post by niko_3100 on 2007-11-08
Bueno estoy sin el powernow desde hace unos dias y la verdad que la notebook esta mas agil que antes, se nota que ahora si trabaja a 1,8 ghz en ves de 800 mhz todo el tiempo. En cuant a la temperatura tiene un promedio de 42 grados llegando a bajar hasta 37 grados y con un maximo de 46 practicamente 2 grados mas que con powernow con lo cual no me parece preocupante :D

---

### Post by leo_rockway on 2007-11-08
en kde tengo un programita en la tray que me deja cambiar entre dynamic, performance o powersave, ya sea en corriente o bateria.

en general lo dejo en dynamic para corriente y powersave para bateria.

---

### Post by niko_3100 on 2007-11-08
Muy groso tira el nombre del programita chabon... no me dejes con las ganas. Ese programa regula la frecuencia del micro??

---

### Post by leo_rockway on 2007-11-09
el paquete se llama kde-guidance-powermanager. tire un apt-cache search y hay uno que se llama gnome-power-manager (no se si seran mas o menos lo mismo)

kde-guidance-powermanager tb me servia para cambiar el nivel de luz de la pantalla de la laptop, pero toque algo y esa opcion desaparecio (?)

se que este paquete depende de algun otro para regular la frecuencia del micro, creo que es powernowd, pero al menos, como aclare antes, te da la opcion de poner al procesador a laburar al mango si asi lo quisieras.

---

