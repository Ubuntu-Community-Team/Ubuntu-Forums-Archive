---
title: "Ayuda y sugerencias sobre optimizacion, tweaks, etc"
date: 2007-04-16
forum: Argentina Team
---

### Post by sebas.rhcp on 2007-04-16
El tema es asi, mi novia se canso de Windows !!! Siempre ando chusmeando el tema de Linux y Ubuntu, asi que dije "Le instalo Ubunto y vemos". Ya esta instalando e inicia perfectamente. Yo me preguntaba si hay algo que se pueda hacer para que el sistema responda mas rapido...

La PC es esta:

Asus P4VP-MX
Celeron 1.86ghz
256MB de RAM

Si alguno conoce una configuracion parecida, me gustaría saber que tal le anda o que hizo para aumentar el rendimiento. Gracias :D

EDIT: Esta cosa tiene un cooler muy bochinchero, algun soft para controlar y cambiar los rpm's del fan?

---

### Post by clasificado on 2007-04-16
¡No le pidas peras al olmo!

:P Ahi lo primero que te jodió es la ram. Lo primero que te diria, es **que le cambies la swappiness**. Aunque es un valor muy personal, yo recomiendo un valor un poco mayor para pcs con poca memoria:
[cite]
1-Consultamos el valor inicial:

$ sudo cat /proc/sys/vm/swappiness

Después de introducir la contraseña, nos muestra un valor de 10 (si ya nos muestra 60, no hay nada que hacer).

2-Probamos cómo responde el sistema al bajar el valor:

$ sudo sysctl -w vm.swappiness=60

3-Ejecutamos después un par de aplicaciones.

Si el resultado es satisfactorio, vamos a modificar un archivo de configuración para que el cambio sea permanente:

[B]$ sudo gedit /etc/sysctl.conf

y agregamos lo siguiente: vm.swappiness=60 y salvamos los cambios. [/B]
[/cite]
La explicación del cambio, es que el swappiness dice con cuanto ímpetu se pone a bajar partes de la memoria. Los ubuntu modernos vienen con 10, por lo que bajan poco y nada porque esperan que uno tenga una pc remoderna con mucho ram y que no se va a llenar nunca.

La otra cosa que te diria, ¡no la tortures! consideráte xfce en lugar de gnome,  ponerle un [xubuntu]("http://www.xubuntu.org/") en lugar del ubuntu.

Clasificado.

PD: Por lo del cooler, no lo sé. Pero no estaria NADA mal

---

### Post by sebas.rhcp on 2007-04-16
Tengo una mini turbina encima es el stock cooler del Celeron y esta andando a 2900RPM ojala el cooler de mi Core 2 Duo anduviera asi, parece un Athlon Thunderbird. La de instalar xubuntu no estaria mal es mucho mas liviana pero primero me gustaria saber que tanto se puede mejorar la cosa. Por mi parte estoy esperando a esta semana o la otra para instalar ubuntu en mi pc, con un disco rigido nuevo.

---

### Post by kowal on 2007-04-16
Podrías empezar mirando estos links, hay un rejunte de "tips".

[http://www.guia-ubuntu.org/index.php?title=Categor%C3%ADa:Optimizaci%C3%B3n](http://www.guia-ubuntu.org/index.php?title=Categor%C3%ADa:Optimizaci%C3%B3n)
[http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html](http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html)

Saludos.

---

### Post by sebas.rhcp on 2007-04-17
Quedo con ubuntu e hice lo q pude, igual me parece que era mas rapida con windows xp... :confused:

---

### Post by clasificado on 2007-04-17
Y puede ser, digo: ¿Porque no?

En mi caso fue al revés. pero bue!

clasificado

---

### Post by Hex_Mandos on 2007-04-17
Yo a esa máquina le mandaría Xubuntu... o buscaría un Linux más pensado para velocidad. Ubuntu no es particularmente rápido. Es fácil, completo, tiene muchos paquetes y el mejor gestor del mundo, pero rápido no es. En una PII con 256 megas de RAM que usé en el verano para hacer pruebas había distros que andaban mucho mejor que otras, aún con el mismo DE. Por ejemplo, SUSE andaba lento con TODO, pero Knoppix con KDE (como LiveCD) y Debian con Gnome andaban bien los dos. Yo que vos probaría con Xubuntu y/o Debian, aprovechando que salió Etch y es fácil de instalar.

---

### Post by el_itur on 2007-04-17
Posta, xubuntu de pecho, además me tomaría un rato para quitar del init algunos servicios que no necesitas. De cualquier manera un windows pelado es mucho más rápido que ubuntu que tiene bocha de servicios y giladas que a lo mejor no necesitas vos específicamente.

Hay otros tunning más finos pero son para frikis de alto nivel. Como por ejemplo:
Un sistema de archivos para cada tarea (al root un ext2 al home un ext3 a lo demás raiser) y otras giladas pero como dije, son medio harcore.

---

### Post by sdm_cacto on 2007-04-18
> **kowal said:**
> Podrías empezar mirando estos links, hay un rejunte de "tips".

[http://www.guia-ubuntu.org/index.php?title=Categor%C3%ADa:Optimizaci%C3%B3n](http://www.guia-ubuntu.org/index.php?title=Categor%C3%ADa:Optimizaci%C3%B3n)
[http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html](http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html)

Saludos.


KOWAL, excelente y 100% recomendado gracias

---

### Post by jpmorelli on 2007-04-18
> **sebas.rhcp said:**
> Quedo con ubuntu e hice lo q pude, igual me parece que era mas rapida con windows xp... :confused:

Tené en cuenta que la versión de Ubuntu que le cargaste seguramente no tiene más de 1 año y WinXP tiene 6 años de viejo !!!, te acordás cual era la máquina que usabas en ese momento ??? :lolflag:

---

### Post by clasificado on 2007-04-18
> Tené en cuenta que la versión de Ubuntu que le cargaste seguramente no tiene más de 1 año y WinXP tiene 6 años de viejo !!!

No se si es muy buena excusa... Que es la que siempre usa Microsoft te acepto, pero que realmente tiene fundamento...

Clasificado.

---

### Post by jpmorelli on 2007-04-19
> **clasificado said:**
> No se si es muy buena excusa... Que es la que siempre usa Microsoft te acepto, pero que realmente tiene fundamento...

Clasificado.

Lo digo en favor de Ubuntu, imaginate lo torpe del XP que recién ahora puede andar decentemente en la máquina mientras que Ubuntu pasó por varias mejoras hasta necesitar una máquina con un poco mas de potencia. :lolflag:

---

### Post by lavaramano on 2007-04-19
si queres algo rapido, fluxbox. es medio molesto al principio, despues es una belleza.
si queres algo mas intuitivo tenes al fvwm, incluso hay un coso para que tenga transparencias y demas.

googlea un cacho y vas a encontrar varias cosas.

**update:** 
fijate aca, tenes miles de window managers ligeritos : [http://xwinman.org/](http://xwinman.org/) 
deberias fijarte de en lugar de cargar al metacity, cargar algun window manager de esa pagina (mas liviano, claro). quizas eso mejora el rendimiento.
despues con el gnome-settings-daemon cargas las settings (valga la redundancia) (aunque calculo que este lo cargara automaticamente cuando cargue al DE)

y sino checkea esto [http://ubuntuforums.org/showthread.php?t=42873](http://ubuntuforums.org/showthread.php?t=42873) el chabon que hacia/hace al ubuntulite tira data como hacer una instalacion liviana pero con todas las cosas del ubuntu

---

### Post by sebas.rhcp on 2007-04-23
Gracias a todos, cuando tenga oportunidad de tenerla de nuevo por ahora la usuaria esta satisfecha y jugando al mario con tux :P

---

### Post by lugonesjoaquin on 2007-04-23
La cosa no es el entorno, es Ubuntu, no es muy rapida que digamos ...
Conseguite el primer CD de Debian, Instalas común y a la hora de elegir que vas a instalar elegí el sistema base nomás.

Despues cuando termine de instalar, vas a tener que estar un rato en la consola para instalar desde ahi Gnome.
Te logueas.

*$su* (para loguearte como root)
*#apt-cdrom add* (Inserta el primer cd de debian, asi te carga la lista de paquetes al source.list.

Ahora haces esto:
[I]
#apt-get install gnome-core[/I]

Se te va a instalar Gnome BASICO. Cuando se termine de instalar haces un startx y comienzas a instalar todo lo que haya en el primer cd de Debian y que te sirva desde Synaptic (No te olvides del GDM). Cuando termines abres una consola y escribes

*$su* (para loguearte como root)
*#gedit /etc/apt/souces.list*

borras todo y le agregas este repo:
[I]
deb [http://ftp.fi.debian.org/debian/](http://ftp.fi.debian.org/debian/) testing main contrib non-free[/I]

Guardas y cerras el editor. Ahora desde la misma consola escribis

*#apt-get update*

Listo, con ese repo nomás tenes montones de paquetes para seguir instalando.
Quizá no es tan fácil como en Ubuntu, pero Debian es mil veces más rapido...

---

### Post by sebas.rhcp on 2007-04-23
Lo voy a tener en cuenta, se agradece.

---

