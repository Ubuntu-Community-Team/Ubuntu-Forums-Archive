---
title: "Cambiar coma por punto para separar miles"
date: 2008-02-05
forum: Argentina Team
---

### Post by margori on 2008-02-05
Estimados amigos:

He encontrado un bug en la calculadora de gnome ([https://bugs.launchpad.net/bugs/189101]("https://bugs.launchpad.net/bugs/189101"))

Quisiera saber si lo pueden confirmar a este problema.

La cosa es que un numero como 123456789.012 lo presenta como 123,456.789.012 y eso esta muy mal.

Así que para probar si es la configuración regional, quiero cambiar separador de miles como "punto" en ves de "coma" y "coma" como separador de decimal en vez de "punto", pero no encontré el lugar donde se especifica esas opciones. Me pueden ayudar.

Gracias.

---

### Post by marianom on 2008-02-05
Si haces 
```
locale
```
en una terminal, ¿qué te tira (en especial para LC_NUMERIC)?

---

### Post by facundocorradini on 2008-02-06
Confirmo el problema.

El comando locale me tira LC_NUMERIC="es_AR.UTF-8"

Con números inferiores a mil, usa la coma como separador (como debe ser) 

Con números mayores a mil, empieza a usar el punto en lugar de coma, y coma en lugar de punto. algo MUY confuso.

La más extraño llega cuando superás el millón... Ahí separa los millones con coma, los miles con punto, y los decimales con punto. ALTO bug!

---

### Post by marianom on 2008-02-06
EL locale esta bien, pensé que podrian tener algun otro donde ese compartiamiento fuera aceptable. Confirman que es solo un problema en gnome-calc?

---

### Post by faktorqm on 2008-02-06
yo le pongo ver con separador de miles y no me los muestra........ :S tengo gnome tb. salu2!

---

### Post by anka on 2008-02-06
mh.., :( la coma la usa solo en el primer millar contando desde la izquierda, despues puro punto hasta para los decimales:

1,000
1,000.000
10,000.000.05
900,000.000.000.1

---

### Post by margori on 2008-02-06
Salida de "locale":

LANG=es_AR.UTF-8
LC_CTYPE="es_AR.UTF-8"
LC_NUMERIC="es_AR.UTF-8"
LC_TIME="es_AR.UTF-8"
LC_COLLATE="es_AR.UTF-8"
LC_MONETARY="es_AR.UTF-8"
LC_MESSAGES="es_AR.UTF-8"
LC_PAPER="es_AR.UTF-8"
LC_NAME="es_AR.UTF-8"
LC_ADDRESS="es_AR.UTF-8"
LC_TELEPHONE="es_AR.UTF-8"
LC_MEASUREMENT="es_AR.UTF-8"
LC_IDENTIFICATION="es_AR.UTF-8"
LC_ALL=

---

### Post by anka on 2008-02-06
Bueno, estube dando unas vueltas por los irc preguntando quien queria ser conejito de indias. La cosa es que me pase por #ubuntu, #ubuntu-es #gnome y #ubuntu-ru (aca estaban todos durmiendo).

En #ubuntu-es:

Sapote me ayudo, le pedi que se fije (le dije que sea un locale diferente al mio) y luego de unos segundos me dice que le hace lo mismo.., con el mismo locale que el mio (que parte de diferente no se lee?). Todo bien, muchas gracias igual. Nadie mas quiso colaborar y no insisti demasiado igual.

En #ubuntu:

Me ayudo muy amablemente una persona que no me acuerdo como se llama (Ballzack3 o algo parecido, crei que lo habia anotado y cuando volvi se fue :( ). Con un locale en USA ni siquiera le mostraba el separador de miles.

En #gnome:

Me ayudo trentg, con en_CA.UTF-8, la calculadora le imprime bien 1,000,000.5.

Hasta ahi lo que probe, en #ubuntu-ru estaban mudos.

Tal vez sirva de algo.

Suerte!

---

### Post by margori on 2008-02-08
Bien, es un lindo bug para arreglar, aunque la verdad que me supera. El codigo de gcalctool es "grande" para mi y poco se de C.

Sugiero que den sus aportes también al sitio [donde reporte el bug]("https://bugs.launchpad.net/bugs/189101"). Sobretodo que muestren que existe en otros lados aparte de Argentina y den datos para que los desarrolladores reproduzcan el error en sus computadoras.

Gracias

---

### Post by margori on 2008-02-08
Bueno chicos. Tengo buenas y malas noticias. He encontrado el problema en el codigo. Adjunto los archivos que modifican el archivo display.c del codigo fuente de gcalctool 5.20.1 y 5.20.2 de Gutsy y Hardy respectivamente.

Esa es la buena noticia. La mala es que no lo pude probar debido a problemas de compilación, me faltan paquetes para compilar y la verdad no tengo ganas de investigar como hacerlo. así que les dejo un poquito de trabajo para ustedes: necesito que prueben el código, reporten problemas y que lo distribuyan en la medida de lo posible.

Esto mismo ya lo he comentado en el reporte de bug en Ubuntu.

---

### Post by Hei Ku on 2008-02-08
subiste este patch al site donde reportaste el bug? Como desarrollador, te digo que te van a estar muy agradecidos, aunque no sea el arreglo exacto.

---

### Post by facundocorradini on 2008-02-08
Que grande che!!!!  Bien ahí!!!

Ahora, subite ese archivo al launchpad, así los desarrolladores lo implementan rapidito, y en poco tiempo estamos todos con una actualización que aplica ese parche. 

;)

---

