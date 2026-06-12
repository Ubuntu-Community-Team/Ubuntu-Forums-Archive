---
title: "Chau PHP4"
date: 2007-04-03
forum: Argentina Team
---

### Post by felipelerena on 2007-04-03
Investigando por que no tenia PHP4 en los repos, me entere de esta poco agradable y desepcionante respuesta: [http://ubuntuforums.org/showthread.php?t=385052](http://ubuntuforums.org/showthread.php?t=385052)

PHP4 es obsoleto? no me tomes el pelo... nadie desarrolla PHP5.

ESTOY MUY decepcionado

---

### Post by marianom on 2007-04-03
Lo dicho: a compilar de fuente. La buena noticia es que es muy fácil. Yo tengo experiencia en eso. 
Si te hace falta me avisas, no tengo php en esta máquina y no me costaría nada intentar un poco de configure, make, make install, asi no me oxido.

---

### Post by felipelerena on 2007-04-03
si, pero es volver a la edad de piedra. es cualquiera y aparte es un enorme error de marketing, es decir: "ubuntu no sigue al mercado"

---

### Post by lavaramano on 2007-04-03
linux para humanos. (si.)

---

### Post by marianom on 2007-04-03
Me puse a investigar un poco ya que me parecía super extraño lo que me decís que Ubuntu se largara por su lado dejando de lado el soporte para una versión de php que según vos es la del mercado.
Miré el resumen de los distros más renombrados en DistroWatch (Debian,RH,OpenSuse,Gentoo,Mandriva) y según puedo ver, todos están saliendo con php 5 desde hace por lo menos algunos meses.

Ejemplos:
[Mandriva]("http://distrowatch.com/table.php?distribution=mandriva").
[OpenSuse]("http://distrowatch.com/table.php?distribution=opensuse").
[Debian]("http://distrowatch.com/table.php?distribution=debian").
[RH]("http://distrowatch.com/table.php?distribution=redhat").
[Gentoo]("http://distrowatch.com/table.php?distribution=gentoo").
[Ubuntu]("http://distrowatch.com/table.php?distribution=ubuntu").

Coincido con vos sin embargo que posiblemente deberían dar soporte para el php4 pero está claro que es no es la arquitectura de punta y no se cuanto tiempo puede pasar antes que se convierta en un php3.
Donde yo trabajo, donde vendemos nuestro producto con php, estamos usando 5 desde, umm, mediados del año pasado.

Creo seriamente que todo aquel que use, desarrolle o mantenga software con php debería estar contemplando ya a php 5 a riesgo de quedar eventualmente congelado (lo que no está mal: si tu soft funciona con php 4 dejalo ahí, es 1000 veces mejor que innovar a riesgo de dolores de cabeza).
De todos modos que no te pase como con apache donde ahora tenes que ver al diablo en calzoncillos para encontrar algo que no sea Apache 2 o 1.3.34

---

### Post by MeduZa on 2007-04-06
segun lo que leo ahi, agregando los repos de edgy lo tenes para instalar

---

### Post by guidorossi on 2007-04-07
Antes que nada me presento por q es mi primer post acá
Mi nombre es Guido Rossi, estudio Cs. Económicas en la UCA y soy desarrollador PHP desde hace 3 años

Con respecto a este tema de PHP es verdad que la version 4 es obsoleta, la gran mayoria de los frameworks como CakePHP, Zend actuales usan PHP5. En mi caso uso el framework Code Igniter que anda con PHP4 y PHP5 pero tuve mejores experiencias corriendolo sobre PHP5

Además hay un rumor desde hace un tiempito que dentro de no mucho va a salir una version 6, lo que terminará de enterrar a PHP4.

No se que usan ustedes pero yo estoy usando XAMPP 1.6

---

### Post by Sicarul on 2007-04-09
No entiendo bien cual es el problema si el codigo de PHP4 funciona perfectamente en el PHP5... =s

---

### Post by DuckMan on 2007-04-09
no se si funciona "perfectamente" pero bueno, tampoco es tan grave..

---

### Post by clasificado on 2007-04-10
No estoy seguro de que no sea tan grave, pero los programadores en php medio estan acostumbrados a los dolores de cabeza por las configuraciones de cada server.

---

### Post by felipelerena on 2007-04-12
> No estoy seguro de que no sea tan grave. mmm... hay dobles negacionse que me confunden...
quisiste decir que SI era grave o que NO?

---

### Post by clasificado on 2007-04-12
> **felipelerena said:**
> mmm... hay dobles negacionse que me confunden...
quisiste decir que SI era grave o que NO?

Que si es grave, aunque yo no esté seguro.

De lo que estoy seguro es de que los sysadmin configuran a los servers como quieren

Esto ultimo es un resentimiento personal. Pero fue tan irritante que me separó un rato de la programacion php. Eso de que el php.ini se configura para todo el server y no se puede cambiar por sitio, pero te afectan al modo de programar, fue algo que no pude superar.

Clasificado.

---

