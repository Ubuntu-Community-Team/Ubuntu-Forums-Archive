---
title: "libreria pcap para desarrollo, duda + extra ;)"
date: 2007-05-16
forum: Argentina Team
---

### Post by MeduZa on 2007-05-16
Hola comunudad...
Estoy desarrolando una aplicacion para gtk gnome y para mi todo esto de desarrollar en linux (ubuntu) me es nuevo y tengo algunas dudas.
Me gustarian saber 2 cosas:
1 cuando uso la libreria pcap las aplicaciones no corren sobre un usuario normal, no se si es algo que yo no hice o que pero solo puedo correr el programa como debe ser desde ROOT o con sudo, sera q la libreria esa solo es para generar porgramas para root? la aplicacion que estoy desarrolando esta destinada al usuario final y no me gustaria que necesitar ingresar el password de root para poder correrla bien

2 donde puedo conseguir informacion util, ejemplos y manuales para C, GTK glade y anjuta?

Desde ya muchisimas gracias a todos

---

### Post by MeduZa on 2007-05-17
viendo que nadie tiene ni 5 de idea agrego esta info:
mi vercion de [glade es 3]("http://glade.gnome.org/docs/index.html")
mi vercion de [GTK+ es 2.2]("http://developer.gnome.org/doc/API/2.2/gtk/")x o sup 
uso Anjuta 2.1.3

(losl link va a lo que encontre)
necesito mas ejemplos :(

---

### Post by fetova on 2007-05-18
> **MeduZa said:**
> viendo que nadie tiene ni 5 de idea agrego esta info:
mi vercion de [glade es 3]("http://glade.gnome.org/docs/index.html")
mi vercion de [GTK+ es 2.2]("http://developer.gnome.org/doc/API/2.2/gtk/")x o sup 
uso Anjuta 2.1.3

(losl link va a lo que encontre)
necesito mas ejemplos :(

prueba devhelp

```
sudo aptitude install devhelp
```

Te da varios manuales dependiendo de lo que tengas instalado

---

### Post by beuno on 2007-05-18
¿Es posible que el ejecutable en si no tenga permisos de ejecucion?

---

### Post by MeduZa on 2007-05-19
> **beuno said:**
> ¿Es posible que el ejecutable en si no tenga permisos de ejecucion?

buen punto dejame ver...

edit: nop, los tiene, es raro pero me parece q el libpcap necesita root para poder capturar datos y dispositivos

---

### Post by ariel on 2007-05-21
Si vas a capturar trafico del stack ethernet/ip, tenes que correr libpcap como root. Solo root puede hacer una operacion de tan bajo nivel y que puede comprometer la seguridad del sistema. Un ejemplo que seguro que ya conoces es wireshark/ethereal, que usa pcap.

Un workaround que se me ocurre que podria andar es usar setuid en la libreria o mas bien el programa tuyo que la invoca. *Me parece* que si activas setuid, permitis al programa impersonar a root, cualquiera sea el usuario que lo ejecute. Ya estoy un poco oxidado para estas cosas pero seguro googleando vas a encontrar buena documentation de setuid.

salu2 

> **MeduZa said:**
> Hola comunudad...
Estoy desarrolando una aplicacion para gtk gnome y para mi todo esto de desarrollar en linux (ubuntu) me es nuevo y tengo algunas dudas.
Me gustarian saber 2 cosas:
1 cuando uso la libreria pcap las aplicaciones no corren sobre un usuario normal, no se si es algo que yo no hice o que pero solo puedo correr el programa como debe ser desde ROOT o con sudo, sera q la libreria esa solo es para generar porgramas para root? la aplicacion que estoy desarrolando esta destinada al usuario final y no me gustaria que necesitar ingresar el password de root para poder correrla bien

2 donde puedo conseguir informacion util, ejemplos y manuales para C, GTK glade y anjuta?

Desde ya muchisimas gracias a todos

---

### Post by MeduZa on 2007-09-24
> **ariel said:**
> Si vas a capturar trafico del stack ethernet/ip, tenes que correr libpcap como root. Solo root puede hacer una operacion de tan bajo nivel y que puede comprometer la seguridad del sistema. Un ejemplo que seguro que ya conoces es wireshark/ethereal, que usa pcap.

Un workaround que se me ocurre que podria andar es usar setuid en la libreria o mas bien el programa tuyo que la invoca. *Me parece* que si activas setuid, permitis al programa impersonar a root, cualquiera sea el usuario que lo ejecute. Ya estoy un poco oxidado para estas cosas pero seguro googleando vas a encontrar buena documentation de setuid.

salu2

muy buena data, voy a inverstigar eso porque por nada quiero que mi programa necesite sudo o root para andar, solo necesito ver que datos pasan por un solo puedo que usa un juego y carpurar esos datos y enviar otros

---

### Post by Hei Ku on 2007-09-24
El puerto al que se envían los datos está abierto por otra aplicación, o es tu aplicación la que debería estar escuchando ahi? Porque por el uso que se le da a esa librería, me parece que lo que hace es espiar el trafico, y por lo que deduzco de tu post, me parece que solo necesitas una aplicacion que escuche en un puerto, procese los datos, y devuelva una respuesta. Si es así, me parece que estas utilizando una librería equivocada, y con abrir un socket te alcanza y sobra. Eso es una función standard de C, y deberías poder hacerlo con GTK sin necesidad de una librería especial.

---

### Post by faktorqm on 2007-09-24
Yo ahora estoy estudiando c para la facultad, pero es ANSI y capaz POSIX, igual ya sabia del secundario, asi que medio embole.
POR FAVOR son bibliotecas, no librerias. saben que tengo razon, asi que no voy a contestar/leer posts al respecto.
La pregunta que hizo hei ku es la misma que iba a hacer yo, para que esta orientado tu programa? capaz lo estas pensando mal, o no, pero existe otra cosa mejor. hay aca programadores con experiencia? o sin? salu2!

---

### Post by Hei Ku on 2007-09-24
por lo que entiendo del post, se parece al famoso TP que les hacen hacer a los de la UTN en C, en sistemas operativos. Nunca cursé ahi, pero lo escuche tantas veces que fue lo primero que se me vino a la cabeza. Basicamente, una aplicacion que escuche un puerto en la red y devuelva datos. Lo escuche en las variantes de IRC, mensajes instantaneos y juego en red. Y lo hacen con las librerias comunes de C, sin necesidad de usar librerias* especiales.

*El uso común se impone a la traducción correcta. :D

---

### Post by faktorqm on 2007-09-24
uhhhhhhhhh yo no estudio en la utn, estudio en la uba y a mi no me hacen hacer eso :(:( esas bibliotecas comunes de las que hablan son ansi / posix o cumplen con algún estándar internacional? si lo hacen, fragmento de codigo de ejemplo y nombre por pm please :lolflag:

---

### Post by Hei Ku on 2007-09-25
Y ahora me acuerdo por qué dejé sistemas en la UBA. jjejeje
Como tampoco fui a la UTN, y solo estudio administración, solo te puedo proveer con este link:

[http://www.gnu.org/software/libc/manual/html_node/Connections.html#Connections](http://www.gnu.org/software/libc/manual/html_node/Connections.html#Connections)

---

### Post by MeduZa on 2007-09-26
Mi programa esta orientado a la comumindad gamer, y es una especie de herramienta ayuda para las personas que hostean un juego en warcraft 3, basicamente deberia llevar una base de datos con informacion sobre la gente que se va del juego (cosa que molesta mucho) darte el ping de cada jugador, nacionalidad y si esta en la lista negra de kiters
ok basicamente lo que mi programa deberia hacer es lo siguiente:
leer el puerto 6112 que el que usa el host, parcear la informacion que por ahi entra, y manejarla, el programa dispara acciones cuando vos escribis mensajes de texto durante la partida, por ejemplo si pones //blast deberia agregar al ultimo que se salio a la base de datos con un mensaje predefinido, o si pones //blast mensaje  con "mensaje" como descripcion
basicamente eso seria por ahora lo que quiero lograr, estoy usando esa biblioteca porque los que hicieron una aplicacion identica pero para w32 usaron winpcap, solo la uso por eso, si saben de alguna mejor barbaro!
tambien en un futuro me gustaria injectar datos "departe" del juego
por ejemplo que mande un mensaje a tal cuenta o muestre informacion de parte del host a los demas jugadores

eso es todo por ahora si se me ocurre mas les digo espero respuestas

---

### Post by faktorqm on 2007-09-26
> **Hei Ku said:**
> Y ahora me acuerdo por qué dejé sistemas en la UBA. jjejeje
Como tampoco fui a la UTN, y solo estudio administración, solo te puedo proveer con este link:

[http://www.gnu.org/software/libc/manual/html_node/Connections.html#Connections](http://www.gnu.org/software/libc/manual/html_node/Connections.html#Connections)

gracias hei ku, sos una masa. cumple con el estandar ISO C. dejo aca la parte que dice eso asi no lo buscan:

```
1 Introduction
The C language provides no built-in facilities for performing such common operations as
input/output, memory management, string manipulation, and the like. Instead, these fa-
cilities are defined in a standard library, which you compile and link with your programs.
    [FONT="Arial Black"][U][B][I][SIZE="4"]The GNU C library, described in this document, defines all of the library functions that
are specified by the ISO C standard, as well as additional features specific to POSIX and
other derivatives of the Unix operating system, and extensions specific to the GNU system.[/SIZE][/I][/B][/U][/FONT]
    The purpose of this manual is to tell you how to use the facilities of the GNU library.
We have mentioned which features belong to which standards to help you identify things
that are potentially non-portable to other systems. But the emphasis in this manual is not
on strict portability.

```

Al final dice que el manual este no pone énfasis en una portabilidad estricta. lease, no es cross-plattform, o no esta orientado. 
salu2!!!

---

