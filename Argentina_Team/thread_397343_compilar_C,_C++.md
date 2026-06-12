---
title: "compilar C, C++"
date: 2007-03-30
forum: Argentina Team
---

### Post by fetova on 2007-03-30
hola, ya que por fin estoy en ubuntu quiero poder compilar mis trabajos, y la verdad no se ni como hacerlo, he visto algunos programas, pero nomas no jalan :(

Como le puedo hacer?, si es con entorno grafico, mejor :D

Gracias:)

---

### Post by justin whitaker on 2007-03-30
> **fetova said:**
> hola, ya que por fin estoy en ubuntu quiero poder compilar mis trabajos, y la verdad no se ni como hacerlo, he visto algunos programas, pero nomas no jalan :(

Como le puedo hacer?, si es con entorno grafico, mejor :D

Gracias:)

Fetova, se necesita build-essential para compliar sus programas. 

sudo apt-get install build-essential

---

### Post by lavaramano on 2007-03-30
> **justin whitaker said:**
> Fetova, se necesita build-essential para compliar sus programas. 

sudo apt-get install build-essential

a eso sumale gcc y cpp 
creo que las versiones son 4 y 3.5 (CREO)

al menos yo siempre lo baje asi y siempre me funciono bien.

---

### Post by zspikes on 2007-03-30
como te dijeron arriba, bajate build-essential con este comando

sudo apt-get install build-essential

eso te baja el gcc q es un compilador muy piola pero sin IDE (ocea q vas a tener q hacer el codigo en algun editor de textos, te recomiendo el gedit) y las librerias basicas.

Para compilar, agarras, te abris un gedit
$gedit programa.c

y ahi escribis tu codigo, cuando termines lo guardas y te mandas a la consola, cambias a la carpeta donde esta el archivo y pones lo siguiente

$gcc programa.c -o destino

y para ejecutar pones

./destino

y listo!!! espero q te sea de ayuda, adios!!!

---

### Post by fetova on 2007-04-02
Gracias!!!! 

nunca crei que ne linux seria tan facil compilar :D en linea de comandos, intente con eclipse y la verdad solo tenia problemas gratis!!

gracias por todo, sin enbargo... acabo de terminar en mi escuela C, y ahora va Visual Basic :( De este hay? :confused: :confused: :confused: 

Gracias!!!!

---

### Post by marianom on 2007-04-02
De C pasan a Visual Basic? Astounding!

Lo más cerca que oí mencionar es [Gambas]("http://gambas.sourceforge.net/") pero no se cuantas similitudes puede haber.

---

### Post by Tinchio on 2007-04-03
yo hace unos dias estuve en una situacion similar, aparte de C necesitaba usar VB (lo odio ¬¬) pero lo mas  "parecido" como dice maraniom es gambas pero en el sentido de que es BASIC tambien, pero no es lo mismo, o sea si vos lo que tenes que aprender es VB lo mejor va a ser que te lo instales, lo que hice yo fue instalarlo en una maquina virtual con VMware, fue lo mas rapido y facil.

---

### Post by beuno on 2007-04-03
> **Tinchio said:**
> yo hace unos dias estuve en una situacion similar, aparte de C necesitaba usar VB (lo odio ¬¬) pero lo mas  "parecido" como dice maraniom es gambas pero en el sentido de que es BASIC tambien, pero no es lo mismo, o sea si vos lo que tenes que aprender es VB lo mejor va a ser que te lo instales, lo que hice yo fue instalarlo en una maquina virtual con VMware, fue lo mas rapido y facil.

La version de mono actualmente en beta soporta vb.net

---

### Post by fetova on 2007-04-04
> **marianom said:**
> De C pasan a Visual Basic? Astounding!

Lo más cerca que oí mencionar es [Gambas]("http://gambas.sourceforge.net/") pero no se cuantas similitudes puede haber.

jajajajajajajajaja

Y luego sigue Logo... :-k , asi es el programa de tecnicas de programacion en mi escuela :confused:

Sip, Voy a necesitar VB...  la verdad no entendi muy bien... Gambas no... mono... WMware... si? :confused: Que puede funcionar? :confused: 

Mientras pruebo las 3 opciones...

Gracias :)

---

### Post by beuno on 2007-04-04
> **fetova said:**
> Mientras pruebo las 3 opciones...

¡Ese es el espiritu!

---

### Post by fetova on 2007-04-09
vuelvo con la cola entre las patas...:( 

el gambas efectivamente no es VB
el mono maneja VB.NET, no VB, si es distinto.
y al WMware no le entiendo, ni siquiera para instalarlo :'(

buaaaaaa!!!

Lo bueno es que encontre Anjuta... es compilador de varios: C, C++, Perl... Ta bueno :)

---

### Post by Tinchio on 2007-04-09
> **fetova said:**
> vuelvo con la cola entre las patas...:( 

el gambas efectivamente no es VB
el mono maneja VB.NET, no VB, si es distinto.
y al WMware no le entiendo, ni siquiera para instalarlo :'(

buaaaaaa!!!

Lo bueno es que encontre Anjuta... es compilador de varios: C, C++, Perl... Ta bueno :)

ay ay ay, y yo que te dije? ¬¬


bueno a ver, como te dije antes si lo que necesitas es usar VB la unica q te va a queda es VMware, asi que para empezar, que version de Ubuntu tenes?

---

### Post by fetova on 2007-04-10
> **Tinchio said:**
> ay ay ay, y yo que te dije? ¬¬


bueno a ver, como te dije antes si lo que necesitas es usar VB la unica q te va a queda es VMware, asi que para empezar, que version de Ubuntu tenes?

jajajajajaj

Pues tengo 6.06.1 Dapper Drake... Arriba dice :P, y si deplano no hayo cual es el paquete :(

---

### Post by Tinchio on 2007-04-10
no me acuerdo si en los repositorios de dapper esta pero fijate, vas a tener q instalar el server para poder crear una maquina virtual y despues nada mas usas el player para "usar" esa maquina creada. Si el paquete no esta en los repos en la web oficial te los podes bajar gratis
[http://www.vmware.com/](http://www.vmware.com/)

cualquier duda avisa

---

### Post by kalel on 2007-04-12
Probaste con [Anjuta]("http://es.wikipedia.org/wiki/Anjuta")¿?

---

### Post by fetova on 2007-04-12
> **kalel said:**
> Probaste con [Anjuta]("http://es.wikipedia.org/wiki/Anjuta")¿?

Para c, c++, si, es genial, bastante recomendable ;), pero... el problema que tengo ahorita es acerca de Visual Basic :( 

> **tinchio said:**
> no me acuerdo si en los repositorios de dapper esta pero fijate, vas a tener q instalar el server para poder crear una maquina virtual y despues nada mas usas el player para "usar" esa maquina creada. Si el paquete no esta en los repos en la web oficial te los podes bajar gratis

me encontre en los repos esto 
```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
No se pudo encontrar el paquete "vmware". Sin embargo,
"vmware" aparece en el nombre de los siguientes paquetes:
  vmware-player vmware-player-kernel-modules-2.6.15-23
  vmware-player-kernel-modules-2.6.15-25
  vmware-player-kernel-modules-2.6.15-26
  vmware-player-kernel-modules-2.6.15-27
  vmware-player-kernel-modules-2.6.15-28 xserver-xorg-driver-vmware
  vmware-player-kernel-source vmware-player-kernel-modules

```

alguno es el server o lo tengo que descargar de su pagina? :confused:

---

### Post by kalel on 2007-04-12
que queres emular, que te queres bajarel vmware?

---

### Post by fetova on 2007-04-12
> **kalel said:**
> que queres emular, que te queres bajarel vmware?

Pues lo que quiero realmente es una aplicacion en la cual pueda desarrollar en Visual Basic... por mi escuela :( acabo de entrar al tema y necesito hacer algunas aplicaciones...

Lo de vmware es propuesta de tinchio... que emule el visual basic de windows... pero no hayo muy bien, baje el player, pero no doy en como hacer las maquinas virtuales, y peor aun, no se ni que estoy haciendo :confused: :confused:

Pero bueno... si conoces me podrias ayudar? :)

---

### Post by kalel on 2007-04-12
Yo para emular otro S.O. uso el [VirtualBox]("http://www.virtualbox.org/")

se te va a hacer mas simple de instalar

es un .deb, por lo que te lo bajas, vas al directorio donde lo bajaste y haces

sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386 (todo esto en una terminal)

y listo.


sino le haces boton derecho al .deb y haces que te lo instale con el gestor grafico.

=)

suerte

---

### Post by Tinchio on 2007-04-12
Volvi. Por lo que entendi instalaste el player, pero para crear las maquinas antes necesitas el server, una vez que tengas la maquina creada ahi si podes usar el player.

[http://www.ubuntu-es.org/node/18612](http://www.ubuntu-es.org/node/18612)

---

### Post by OscarLofrano on 2007-05-02
[FONT="Arial"][COLOR="Navy"]Muy buenos días, desde Caracas-Venezuela:

Esta sucediendo lo mismo que con el COBOL en ambiente Microsoft GUI. En el mundo existen millones de personas que conocen dicho lenguaje en ambientes NO GUI, es decir en ambiente texto y se han encontrado con el problema de aprender otros lenguajes de programación es decir comenzar desde ZERO.

La gente que por años ha programado en BASIC se consiguió solo un pequeño inconveniente al pasar a Visual Basic de Microsoft, el cual es un RAD - Rapid Application Development -, hasta la versión 6 (Y SON MUCHÍSIMOS MAS MILLONES HASTA EL MOMENTO), ya que la versión &#8220;.NET&#8221; es como empezar de ZERO como sucedió con el COBOL. 

Al pasar al S.O. LINUX desearíamos poder usar dichos lenguajes aprendidos. En el S.O. Windows de Microsoft el COBOL RAD, es decir Visual, existe y lo tiene FUJITSU, abría que ver si ya lo hicieron para LINUX. 

¡¡¡¡¿Y EL VISUAL BASIC 6, SIMILAR AL DE MICROSOFT?, BINGO!!!!! Lo pueden conseguir en:

[http://www.kbasic.com/](http://www.kbasic.com/) 

Con respecto a VMWare creo haber entendido al proponente y que no lo ha manifestado claramente; el VMWare es un software, el que conozco yo ( [http://www.vmware.com/](http://www.vmware.com/) ), que emula un micro en un micro y se instalaría en ese VMware: Virtual Machine ware :)  el S.O. LINUX O EL S.O. WINDOWS DE MICROSOFT y luego montarías en este: Visual Basic de esa compañía. En resumen tendrías dos Sistemas Operativos en una misma Machina :).

Bueno Amigos les saludo y espero haber sido de ayuda y naturalmente seguir en contacto con ustedes para captar buenas informaciones sobre LINUX sobre el cual estoy peleando desde ZERO.

Oscar
[/COLOR][/FONT]

---

### Post by fetova on 2007-05-04
vap Gracias :) lo pruebo cuando mi maquina sirva de nuevo :P

---

### Post by Tinchio on 2007-05-04
Me habia emocionado cuando lei esto de KBasic y todas sus caracteristicas, pero cuando pase de la teoria  a la practica....... 2 cosas malas mas q nada, 1ero ahora es pago, asiq  podes probar un trial de 30 dias :-( y lo otro es que esta muy "buggy" se me cerraba solo de onda cada tanto :-S

---

### Post by Al_maverick on 2007-05-04
Parece que emularon todos los "features" del original :D

---

### Post by marianom on 2007-05-04
Muy bueno, Al_maverick, muy bueno.

Es raro lo que decís Tinchio ya que me había parecido leer que si el proyecto donde se utilizará Kbasic es open source, tenías el derecho de usarlo sin costo (digamos que tus estudios son un proyecto open surce :))

> The Linux version is free of charge , if you would like to use it for open source development released under the terms of GNU GPL Version 2 as published by the Free Software Foundation.

If you use the Linux version, there are certain licensing conditions that the GNU GPL imposes on you, to ensure that your users enjoy the freedoms guaranteed by the GPL. Users are entitled to: 1. Run your software for any purpose. 2. Obtain and study your software&#8217;s source code, and adapt it to their needs. 3. Redistribute your software and its source code to others (under the same terms). 4. Improve or modify your software, and release these changes to the public. These freedoms apply to all the source code for all the modules your software is based on, regardless of whether they have been written by you or by others. The freedoms also apply to any associated interface definition files, and even include the scripts and control files used to control compilation and installation of the executable; otherwise users could not exercise their rights.

This means that you cannot use the Linux version if your software must be built with any modules that impose conditions on you that contradict the conditions of the GNU GPL, including, but not limited to, software patents, commercial license agreements, copyrighted interface definitions or any sort of non-disclosure agreement. In these circumstances you must use a commercial edition of KBasic.


---

### Post by Tinchio on 2007-05-05
> **marianom said:**
> Muy bueno, Al_maverick, muy bueno.

Es raro lo que decís Tinchio ya que me había parecido leer que si el proyecto donde se utilizará Kbasic es open source, tenías el derecho de usarlo sin costo (digamos que tus estudios son un proyecto open surce :))

Segun lei en la pagina HABIA una version free pero la dejaron y pasaron a una version paga, o trial por 30 dias, es mas lo tengo instalado y me lo recuerda todo el tiempo, le quedan X dias  :(

---

