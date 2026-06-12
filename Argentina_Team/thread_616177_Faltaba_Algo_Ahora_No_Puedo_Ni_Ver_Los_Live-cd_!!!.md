---
title: "Faltaba Algo? Ahora No Puedo Ni Ver Los Live-cd !!!!"
date: 2007-11-17
forum: Argentina Team
---

### Post by leonardo83 on 2007-11-17
Que tal gente!
Tengo en la pc ubuntu 7.04 y en otro rigido win ME.
Los dos funcionan bien  hasta el moento, pero aqui vien el drama: un amigo me paso el ubuntu 7.10, coloco el cd y empieza el live cd, eligo iniciar, se carga la barrita y aparece el siguiente error:


```
busybox v1.1.1.3 (Debian 1:1.1.3 -5ubuntu7) built-in shell (ash)
enter 'help' for a list of built- in commands
```

que es esto ???
probe varias veces y siempre se detiene ahi y me aparece el cursor titilando.
Me prestaron xubuntu, edubuntu y kubuntu y no puedo iniciar el live cd de ninguno!!!!
con todos me aparece lo mismo !!! que puedo hacer ?????

Con total desesperacion y maldiciendo totalmente mi rigido
Adrian :(:(:(:(:(:(

---

### Post by leonardo83 on 2007-11-18
Nadie ???  :(  :(  :(  :(

---

### Post by fscodelaro on 2007-11-18
Hola, Leo, la verdad que ni idea a que se puede deber el problema, pero no entiendo algunas cosas:

1) la interfaz grafica te carga o no? en que punto del inicio te tira el error que mencionas?

2) probaste con el CD alternativo? Yo siempre hago las instalaciones con ese porque es mucho mas robusto. Si, no tiene interfaz grafica, es texto coloreado pero las preguntas son las mismas. Aparte creo que lei por ahi que Gutsy live CD necesita mas de 256 mb de ram (mas, 256 no alcanza), no se cuanto tendras pero por ahi viene por ahi el problema. El alternate en cambio se la banca con mucho menos.

---

### Post by leonardo83 on 2007-11-18
> **fscodelaro said:**
> Hola, Leo, la verdad que ni idea a que se puede deber el problema, pero no entiendo algunas cosas:

1) la interfaz grafica te carga o no? en que punto del inicio te tira el error que mencionas?

2) probaste con el CD alternativo? Yo siempre hago las instalaciones con ese porque es mucho mas robusto. Si, no tiene interfaz grafica, es texto coloreado pero las preguntas son las mismas. Aparte creo que lei por ahi que Gutsy live CD necesita mas de 256 mb de ram (mas, 256 no alcanza), no se cuanto tendras pero por ahi viene por ahi el problema. El alternate en cambio se la banca con mucho menos.

Thanxs man!! :)   Pero aclaremos....
 1) me carga el inicio del live cd (donde podes elegir instalar, verificar el cd etc.).Y despues se carga la barrita y ahi es cuando aparece ese mensaje.

2) no tengo el cd alternativo pero como dije, el cd ME FUNCIONO ANTES y ahora no. Es mas, tengo 640 mb de ram asi que creo que es mas que suficiente.
No se que es lo que le pasa pero me parece raro que ningun cd pueda leer, no se si hay que cambiar algo o que, todo lo que hice fue instalar el 7.04, que funciona bien hasta ahora.

Ayuda gente!!!!!!!  :( :( :(
 
Saludos.

---

### Post by clasificado on 2007-11-19
> **william_s said:**
> http://www.ubuntu-es.org/index.php?q=node/61871][/url]
Hace 5 minutos al queres instalar en una maquina me tope con el mismo error y lo solucione de esta manera (lei esta web [http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588))

inicia el live-cd

1.- F2 escoge idioma

2.- F6 al final de la linea quita splash -- y coloca break=top

3.- Cuando te aparezca el error coloca en la consola lo siguinte

   modprobe piix

   exit

4.- Esto te cambiara el estilo de letras

5 .-Espera una cacho (toma su tiempo) y arrancara el sistema y bueno ahora estoy en eso de la instalacion asi que no te podria decir que tanto funciona pero para empezar algo es algo ahora te recomiendo que leas el link que puse aunque esta en ingles ahi podras encontrar mas soluciones interesantes y dudas 

saludos

willi@ms 

La clave de un linuxero es la investigacion y si no investigas mejor borrate y vete por la "ventana"


Si no te funciona avisa y buscamos mas

clasificado

---

### Post by faktorqm on 2007-11-19
hola, perdoname que te diga asi tan libremente pero estas por el mal camino..... por no decir en la m****da.
Eso que te aparece ahi a mi una vez me aparecio cuando habia roto el kernel por hacerme el "compilador de modulos pro" y ser un "queso mar de plata".
eso es un bash como dice ahi que se llama ash (cenizas en ingles) y es una especie de consola de recuperacion. si escribis help te tira una lista de comandos pero la verdad que nunca pude resolver nada. Capaz es un error en el disco, un error en un modulo, un error en el kernel, o algo de eso.
proba cuando arrancas de poner noacpi o acpi=off como dice en el thread de como instalar la hp pavilion 1030. salu2!

p.d.: aguante el metal! no te olvides: 07/03/2008 IRON MAIDEN en ferro.

---

### Post by leonardo83 on 2007-11-19
Gracias gente!!!
ME voya fijar en lo que me decis clasificado y cualquier cosa te chiflo!


faktorqm no creo que sea asi, no compile nada del kernel, y ni siquiera se como se haria.
Secundo Maiden en Ferro y ademas Krisiun en diciembre!!!
Ya me fui al car*jo ja ja ja!
Saludos! 
:guitar:

---

### Post by leonardo83 on 2007-11-21
probe lo que me dijeron de entrar con F6 y borrar splash -- , agregar lo demas y despues escribir modprobe, cambia la letra como dijeron...... se queda pensando unos minutos pero despues vuelve a aparecer el mensaje de error y vuelve cursor que titila.
Tambien probe con noapic nolapic y tampoco.
Tambien acpi=off pero nada.


Alguna ayuda??? :(
No se si me conviene formatear ese rigido e instalarle de cero ubuntu 7.10.

---

### Post by sajnox on 2007-11-21
Perdoname, pero el problema es con gutsy, y no te aconsejo cambiar de version en este estado. 

Cuando levantas el live cd la idea es que no tocas lo que tenes en la maquina, si formateas el disco te vas a quedar sin nada

---

### Post by leonardo83 on 2007-11-22
yo lo decia porque antes d que instale algo, me leia los cd ok, pero despues de 
instalar feisty empezo este problema.
Ahora se me ocurrio sacar el rigido de linux y dejar solo el de win, y probar el live cd a ver que onda, mira lo
que se me ocurre como para ver que esta pasando!!
No creo que sea gutsy porque con kubuntu, edubuntu y versiones
anteriores y con todas pasa lo mismo.
Ahora me prestaron DamnSmall , voy a probar pero no creo que solucione.
Me parece que lña unica que queda es formatear TODO mi ubuntu
:( :( :(

---

### Post by santiagoward2000 on 2007-11-22
Che Leo, una pregunta: ¿probaste poner para que te revise el CD? Si el LiveCD no quiere entrar, no creo que pueda ser por algo que instalaste, supuestamente carga el Kernel directamente del CD.

---

### Post by leonardo83 on 2007-11-22
Si santi, si te fijas eso postee antes.
Los cd's estan ok y ni siquieranson grabados son ORIYINALS.
A ver, mas data:

1) aparece la intro del cd con todas las opciones (elijan cualquier version, kubuntu, xubuntu, con todas pasa la mismo), eligo iniciar o instalar
2) apenas aparece el mensaje que se esta cargando el kernele aparece el siguiente mensaje:
```
  [   0.00000] unable to locate RSDP  
```
3)despues la imagen que se empieza a cargar la barrita, tan tataaaaaaaan......
4) aparece el mensaje en pantalla:
```
Busybox v1.1.1.3 (Debian 1:1.1.3 3-ubuntu -) built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/ash:can't access tty; job control turned off
(initramfs) _
```
y el bendito cursor que titila..... :confused:

Espero esto ayude un poco mas para que me puedan ayudar :(

---

### Post by fscodelaro on 2007-11-22
Leo,

la terminal se ve como esto cuando booteas cierto?

[http://launchpadlibrarian.net/7176358/ubuntu-7.04-beta-tty.jpg](http://launchpadlibrarian.net/7176358/ubuntu-7.04-beta-tty.jpg)

Federico

---

### Post by fscodelaro on 2007-11-22
Ese screenshot es del bug 96084:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)

Es de feisty pero tiene algunas cosas que pueden servir. Si haces cat casper.log en el prompt de busybox y posteas lo que dice puede ayudar a encontrar que es lo que esta causando problemas.

---

### Post by leonardo83 on 2007-11-23
> **fscodelaro said:**
> Ese screenshot es del bug 96084:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)

Es de feisty pero tiene algunas cosas que pueden servir. Si haces cat casper.log en el prompt de busybox y posteas lo que dice puede ayudar a encontrar que es lo que esta causando problemas.

Si, se ve eso que me pones en la foto menos la primer linea, eso non aparece.
Voy a probar escribiendo casper.log en ese cursor y despues pongo que me sale como para ver que puede ser, yo ni idea! :confused:
Gracias man, saludos!

---

### Post by leonardo83 on 2007-11-24
bueno gente ejecute cat casper.log y aca esta el resultado.
Les menciono que este codigo se repitio varias veces diciendo lo mismo asi que les escribo las ultimas lineas, las primeras decian lo mismo:


Aplicamos cat casper.log


```
/init : /init : 1 : cannot open /dev/hda : No such file
/init : /init : 1 : cannot open /dev/hda : No such file
/init : /init : 1 : cannot open /dev/hda1 : No such file
/init : /init : 1 : cannot open /dev/hdb : No such file
/init : /init : 1 : cannot open /dev/fd0 : No such device or address
/init : /init : 1 : cannot open /dev/hda : No such file
unable to find a medium containing a live file system
(initramfs) _ 
```

No se muy bien que pasa pero parece como si no encontrara que es un live cd o algo asi no??? :confused:
Espero respuesta.Gracias!!!!

---

### Post by leonardo83 on 2007-11-25
Ayer probe con Damn small linux version 3, y funciona de 10, se ven los programas y todo!
Pero no funcionan los otros cd y no se porque.
ahi puse como aparece el error :(.

Saludos!

---

### Post by faktorqm on 2007-11-26
para mi tendrias que probar con otro tipo de instalacion, por ejemplo, la de copiar el cd de instalacion al disco rigido y arrancar con un diskette o cd que te arranke el instalador.
o levantar desde otra pc un nfs y hacer la instalacion por lan. debian por ejemplo te la hace por red, por nfs, por http, desde el disco, o desde el cd xD salu2!

---

### Post by leonardo83 on 2007-11-27
> **faktorqm said:**
> para mi tendrias que probar con otro tipo de instalacion, por ejemplo, la de copiar el cd de instalacion al disco rigido y arrancar con un diskette o cd que te arranke el instalador.
o levantar desde otra pc un nfs y hacer la instalacion por lan. debian por ejemplo te la hace por red, por nfs, por http, desde el disco, o desde el cd xD salu2!

Gracias man!
Pero yo digo...
!) no se como podria hacer lo de copiar en el rigido, como dije tengo 2 rigidos, uno para cada sistema, no puedo instalar ubuntu en el segundo rigido, y no quiero hacer una particionj del primero, para eso me compre otro rigido!!
2)otra pc no tengo, no tengo red y tampoco ningun amigo que use linux (es lo mas triste :().
3)igualmente se te agradece la mano man, espero haya alguna solucion desde el cd, no se, cargando algo al momento del booteo... :confused:

---

### Post by faktorqm on 2007-11-29
> **leonardo83 said:**
> Gracias man!
Pero yo digo...
!) no se como podria hacer lo de copiar en el rigido, como dije tengo 2 rigidos, uno para cada sistema, no puedo instalar ubuntu en el segundo rigido, y no quiero hacer una particionj del primero, para eso me compre otro rigido!!

por que no podes en el segundo? cuantas particiones tenes en cada disco y como estan formateadas?

yo tengo:

para el disco 1 (primer maestro): la primera en ntfs, la segunda ext3 (para el home) y la tercera tambien ext3.
para el disco 2 (primer esclavo): en el otro disco tengo, una de sistema "/", otra de swap, y 2 ext3 mas para datos.
en el segundo maestro tengo una lectora de dvd y en el segundo esclavo cambio entre grabadora de dvd y disco de 80gb para backups cada tanto de "lo que no se puede perder".

EN ESTE ENLACE dice como hacer instalaciones alternativas:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

en la parte que dice "Installation without a CD" (instalacion sin CD)
tenes varias alternativas, elegi la que mas te guste y si tenes dudas me preguntas. 

de todas maneras, a mi se me habia ocurrido una forma, capaz es kbza, pero quiza funcione. consiste en copiar el cd de ubuntu a una particion del disco cualquiera que luego vas a borrar (al final del disco claro). poner un diskette tipo super grub disk o algo que arranque """"el cd"""" falso, y que arranque, y aca viene el truco, quiza sea "bobo" y no se de cuenta de que en vez de en un cd esta en una particion, y entonces te arranca y lo instalas normalmente.

por las dudas proba con lo de la pagina que va a ser mejor ;)

> **leonardo83 said:**
> 
2)otra pc no tengo, no tengo red y tampoco ningun amigo que use linux (es lo mas triste :().

como que no? aca en el foro tampoco xDDDDDDDD

> **leonardo83 said:**
> 
3)igualmente se te agradece la mano man, espero haya alguna solucion desde el cd, no se, cargando algo al momento del booteo... :confused:

mira el link. de nada!!! conta como te fue. salu2!

---

### Post by leonardo83 on 2007-11-29
> **faktorqm said:**
> por que no podes en el segundo? cuantas particiones tenes en cada disco y como estan formateadas?

yo tengo:

para el disco 1 (primer maestro): la primera en ntfs, la segunda ext3 (para el home) y la tercera tambien ext3.
para el disco 2 (primer esclavo): en el otro disco tengo, una de sistema "/", otra de swap, y 2 ext3 mas para datos.
en el segundo maestro tengo una lectora de dvd y en el segundo esclavo cambio entre grabadora de dvd y disco de 80gb para backups cada tanto de "lo que no se puede perder".

EN ESTE ENLACE dice como hacer instalaciones alternativas:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

en la parte que dice "Installation without a CD" (instalacion sin CD)
tenes varias alternativas, elegi la que mas te guste y si tenes dudas me preguntas. 

de todas maneras, a mi se me habia ocurrido una forma, capaz es kbza, pero quiza funcione. consiste en copiar el cd de ubuntu a una particion del disco cualquiera que luego vas a borrar (al final del disco claro). poner un diskette tipo super grub disk o algo que arranque """"el cd"""" falso, y que arranque, y aca viene el truco, quiza sea "bobo" y no se de cuenta de que en vez de en un cd esta en una particion, y entonces te arranca y lo instalas normalmente.

por las dudas proba con lo de la pagina que va a ser mejor ;)



como que no? aca en el foro tampoco xDDDDDDDD



mira el link. de nada!!! conta como te fue. salu2!

VERIFICANDO.......
mepa que ya habia puesto como estaba la pc, pero aca va de nuevo
disco rigido master, con win Me, sin ninguna particion, rigido de 60 gb
segundo rigido slave de 80 gb donde esta ubuntu , pero no parti nada! lo instale donde dice usar otra unidad, elegi ese rigido y lo instale en la totalidad del mismo, no hice ninguna particion
grabadora de cd como segunda master y lectora de cd's comun como segunda slave.
Voy a probar esas maneras como el link que me pasas y te cuento como me fue.Grazie! :)

PD : lo de amigos de linux es un decir, obvio que ustedes siempre estan ahi, gracias.No hacen fiestas o mateadas como para que nos conozcamos entre todos , o armar un picadito??? :) Saludos!

---

### Post by sajnox on 2007-11-30
> **leonardo83 said:**
> VERIFICANDO.......
PD : lo de amigos de linux es un decir, obvio que ustedes siempre estan ahi, gracias.No hacen fiestas o mateadas como para que nos conozcamos entre todos , o armar un picadito??? :) Saludos!

Ya algo haremos....lo ultimo fue la release party de Gutsy el 18/10 y estuvo interesante por lo menos.

---

### Post by faktorqm on 2007-12-03
se... nos podriamos juntar para fin de año.... salu2!

---

