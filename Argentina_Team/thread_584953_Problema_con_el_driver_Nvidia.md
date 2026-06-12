---
title: "Problema con el driver Nvidia"
date: 2007-10-21
forum: Argentina Team
---

### Post by steve_ignorant on 2007-10-21
hola a todos nuevamente. 

estoy luchando desde ayer par instalar los drivers Nvidia para la placa( TI 4200) el modelo de driver es 96.43.01, resulta que a la hora de instalar me pide un kernel, precompilado, y con moño rojo..... 

el hecho es este, probe todos los kernels que hay en el synaptic y nada siempre el mismo error...  en el tutorial que habia bajado decia que tenia que actualizar al kernel de la maquina, no me levanta el foro d eubuntu-es, asique si me pueden decir eso se lo agradeceria

y si saben cual es el kernel source para una Ti 4200 avisenme porq estoy podrido de ver la maquina en 800x600


gracias, y disculpen si e smedi ofensivo pero ya estoy podrido en srio de no poder hacerlo andar como se debe

---

### Post by steve_ignorant on 2007-10-21
a ver... logre hacer la instalacion de los drivers, ahora el controlador de drivers lo reconoce y lo habilita pero dice que "no esta en uso" como puedo hacer para que este en uso ese controlador.

---

### Post by steve_ignorant on 2007-10-21
[IMG]http://img228.imageshack.us/img228/7066/pantallazoxx5.png[/IMG]



eso es lo que pone, no se que mas hacer... siempre que le pongo "reiniciar" por active/desactive/habilite/deshabilite, me pone a modo aprueba de errores, y a configurar el monitor y la placa otra vez...

---

### Post by ariel on 2007-10-21
Es raro, el driver que estas usando no parece ser ninguno de los drivers nvidia oficiales de gutsy.

Fijate en synaptics, busca "nvdia". Hay dos packages: "nvidia-glx" == driver 9639, y "nvidia-glx-new" == 100.14.19.

Yo estoy usando el driver oficial / package nvidia-glx-new en un placa 6200 y anda fantastico.

---

### Post by steve_ignorant on 2007-10-21
es que apartir de que puse el glx-new, se me pudrio el guiso y el gutsy...

---

### Post by faktorqm on 2007-10-21
usaste el envy?

---

