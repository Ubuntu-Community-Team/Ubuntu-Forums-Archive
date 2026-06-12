---
title: "Otro novato con Problemas(GRUB)"
date: 2007-05-21
forum: Argentina Team
---

### Post by Axldust on 2007-05-21
Hola, buenos dias!,

ANECDOTA::popcorn:
pues bien empeze casi desde media noche y ya son cerca de las 6 am, tuve infinidad de problemas con linux, pero creo que tambien lo hice todo muy acelerado, en fin, sin mas rollos, termine reinstalando el linux UBUNTU 6.10 y quisiera pedirles ayuda con mi primera duda:

PLANTEAMIENTO:;)
en mi pc tengo 2 discos duros 
-El primero, SATA de 120gb aprox. con 3 particiones, una para el windows y otras dos para archivos de todo tipo.
-El segundo un ATA de 40gb aprox. que es en el cual tengo ubuntu 6.10 recien instalado (desde cero, sin actualizaciones ni nada aun)

PROBLEMA::(
Al iniciar el sistema se carga primero GRUB, y antes de q termine su cuenta regresiva para iniciar ubuntu, le doy ESC para ver la lista de SO a iniciar, PERO solo me aparecen diversas opciones de ubuntu, no me aparece nada de mi particion con WINDOWS, quisiera saber que tengo que hacer para poder verlo, o en todo caso iniciarlo, ya que desde la BIOS intente que arrancara desde el disco duro donde tengo WIN pero sigue iniciando GRUB para pasar a UBUNTU.

GRACIAS:D
de antemano y espero puedan ayudarme pronto ya que ansio conocer mas sobre linux, ahora que tengo tiempo, saludos

---

### Post by Psicolonia on 2007-05-21
intenta colocar-la en inglés. tendras mas hayuda.

necessitas de acrescentar en tu /boot/grub/menu.lst esto:

title Windows
root xxx (VE MENU.LST E BUSCA LAS ENTRADAS DE UBUNTU. HACE UNA ASSI PERO TROCA APENAS ESTA LINEA! QUE DIZ ROOT POR TU HD OU SD)
chainloader +1
makeactive
boot

las otras lineas dexa como estan.

---

### Post by undiaperfecto on 2007-05-21
yo tuve un problema parecido, en google encontre un par de soluciones, pero te recomiendo que instales ubuntu en el mismo disco que tenes windows y dejes el de 40gb para archivos, yo lo tengo asi hace meses y ni un problema. 
o sea la segunda particion de tu disco principal dejala para ubuntu, y esos archivos que tenes ahi mandalos al de 40gb.
pero si lo queres arreglar asi como lo tenes busca en google o en este mismo foro que hay bocha de tutoriales.
saludos.

---

### Post by Axldust on 2007-05-21
Gracias por su atencion, 
pues bien Psicolonia, trate de entender lo que dijiste (soy practicamente 100% NUEVO con linux) y entiendo que tengo que editar el archivo menu.lst agregando esas lineas, eso intente pero me dijo que no tenia los permisos, supongo que tiene que ser desde la terminal (si es asi ojala puedan decirme los comandos)


AH! y disculpenme porque se me paso un pequeño GRAN DETALLE, el disco duro donde tengo winXP y las otras 2 particiones esta en NTFS, por lo que no podia verlos siquiera desde linux (hasta hace un rato que instale AUTOMATIX), y digo esto porque supongo que tiene que ver con el hecho de que GRUB no muestre la opcion para cargar WINxp

Respecto a lo que me dices undiaperfecto, la cuestion seria no perder nada de lo que tengo en esas particiones (las del disco SATA), tengo todo respaldado pero tambien tenia ya todo organizado en cuanto archivos y personalizado en cuanto a windows, por otro lado, ya busque y encontre algunas cosas en ingles, pero no pude realizarlas, gracias d tdos modos.

---

### Post by Psicolonia on 2007-05-21
ola! no problemo con las NTFS!

escribe en terminal

sudo gedit /boot/grub/menu.lst

te le preguntara la password di root. escrebe-la.
si no hays configurado la password hace-lo ahora:

sudo passwd

de seguida coloca: las lineas:

title		Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1

no te olvides de sustituir hd0,0 por tu hd e particion. si teneras windows antes de instalares linux, sera por supuesto hd0,0.

grub eres una buena herramienta por que pudes escribir los comandos manualmente.

assi puede intentar en grub directamiente. Pressiona C en el menu grub e escribe cada alinea seguida de 'enter'.

grub te dara indicaciones de la particion conforme escrives.

perdona el español... ;)

---

### Post by Axldust on 2007-05-24
De verdad quiero agredecer sus mensajes en respuesta, son muy amables (ustedes).

Pero por otro lado les tengo lo que probablemente sean malas noticias para ustedes, o talvez no... en fin, pues despues de tantos problemas con linux, segui intentado lo que me dijeron, pero por mas que incluso desconecte el disco duro ATA (donde instale ubuntu) no podia iniciar el WinXP (!!!!) asi que volvi a conectar el ATA e intente de nuevo con automatix para ver si instalando de nuevo lo necesario para ver discos SATA (ntfs) podia cargarme en el grub el winXP (haciendo los cambios en el archivo que me dijeron) mientras hacia esto estaba checando constantemente por nuevos mensajes aqui en mi post, y por el momento no logre nada, luego resulta que inicio la compu, para volver a intentar resolver este problema y OH! sopresa que no tenia internet!!! nose si fallaba algo con el controlador o con la instalacion o con que... pero esa fue la gota que derramo el vaso y me dispues a formater el disco donde tengia LINUX, asi lo hice, reinicie y OH! otra sorpresa el winXP no cargaba!! OMG!!... inicio con el disco de instalacion de WinXP y formatee de nuevo el ATA, reinicie y nada!, volvi a iniciar e instale otra instancia del WinXP en el ATA, reincie, cargaba bien la nueva instalacion, pero yo queria la que tenia antes, asi q reinicie con el disco de instalacion de XP y le di a la opcion de recueperar instalacion de windows, llegue una linea de comandos (tipo MSDOS) y desde ahi edite lo que seria el boot del XP, reincie y reinciando OH milagro ahi estaba lista para iniciar la DICHOSA instalacion que tanto tiempo he usado, inicie, desintale el winXP del ATA, reinicie y limpie el boot desde mi XP y todo mas que PERFECTO!

La verdad yo apoyo mucho la idea de software libre, creanme entiendo lo que signfica, mas que sea gratis, que sea codigo abierto, pero todavia tiene muchos detalles por pulir linux, sobre todo a la hora de conflictos con el hardware, claro eso lo dice una persona que fallo en tal cosa, quisa hay mas, o quiza es lo de menos, en fin, ayer me consegui Windows Vista, lo instale y estoy encantado, no les voy a mentir, no tiene nada nuevo en lo practico (hasta donde he visto) es mas vistoso que otra cosa, pero ¿que acaso no es de suma importancia la interfaz con la que interactuamos con los SO?... creo que si.

En fin disculpen las molestias y les aseguro que si un dia me puedo hacer de una PC con linux que armonize con hardware, juegos, mp3's, reproductores dvd, y otras cosas la hare mia.

Saludos!

PD. no estoy del lado de nadie, ni de bill gates, ni jobs, ni linux, estoy del lado de la verdad, mi veLdad (jajajajaja):popcorn:

---

### Post by jayflower on 2007-05-24
Las primeras veces esas cosas pasan, pero no te desanimes, ni pienses que Linux es tan negativo o tan pobre con los controladores. Lo digo yo porque lo sufri y lo sufro. Y no es culpa de Linux, en todo caso los que fabrican  hardware estan muy ocupados en vender sus dispositivos para equipos con "otros Sistemas Operativos" y tampoco liberan los drivers porque de esa manera la competencia puede saber como fabrican sus hardware. Así que aplaudo a los que hacen trabajo de ingenieria inversa para saber como funcionan las cosas y a vos o a mi o a cualquiera nos funcione aunque a veces a medias, la placa de video o la mother. Ni hablemos de otras cosas que tampoco apoyan el software el libre como muchos ISPs. Tema largo... un intento más y no molestamos más. ;)

---

### Post by elrengo79 on 2007-05-26
> **Axldust said:**
> De verdad quiero agredecer sus mensajes en respuesta, son muy amables (ustedes).

Pero por otro lado les tengo lo que probablemente sean malas noticias para ustedes, o talvez no... en fin, pues despues de tantos problemas con linux, segui intentado lo que me dijeron, pero por mas que incluso desconecte el disco duro ATA (donde instale ubuntu) no podia iniciar el WinXP (!!!!) asi que volvi a conectar el ATA e intente de nuevo con automatix para ver si instalando de nuevo lo necesario para ver discos SATA (ntfs) podia cargarme en el grub el winXP (haciendo los cambios en el archivo que me dijeron) mientras hacia esto estaba checando constantemente por nuevos mensajes aqui en mi post, y por el momento no logre nada, luego resulta que inicio la compu, para volver a intentar resolver este problema y OH! sopresa que no tenia internet!!! nose si fallaba algo con el controlador o con la instalacion o con que... pero esa fue la gota que derramo el vaso y me dispues a formater el disco donde tengia LINUX, asi lo hice, reinicie y OH! otra sorpresa el winXP no cargaba!! OMG!!... inicio con el disco de instalacion de WinXP y formatee de nuevo el ATA, reinicie y nada!, volvi a iniciar e instale otra instancia del WinXP en el ATA, reincie, cargaba bien la nueva instalacion, pero yo queria la que tenia antes, asi q reinicie con el disco de instalacion de XP y le di a la opcion de recueperar instalacion de windows, llegue una linea de comandos (tipo MSDOS) y desde ahi edite lo que seria el boot del XP, reincie y reinciando OH milagro ahi estaba lista para iniciar la DICHOSA instalacion que tanto tiempo he usado, inicie, desintale el winXP del ATA, reinicie y limpie el boot desde mi XP y todo mas que PERFECTO!

La verdad yo apoyo mucho la idea de software libre, creanme entiendo lo que signfica, mas que sea gratis, que sea codigo abierto, pero todavia tiene muchos detalles por pulir linux, sobre todo a la hora de conflictos con el hardware, claro eso lo dice una persona que fallo en tal cosa, quisa hay mas, o quiza es lo de menos, en fin, ayer me consegui Windows Vista, lo instale y estoy encantado, no les voy a mentir, no tiene nada nuevo en lo practico (hasta donde he visto) es mas vistoso que otra cosa, pero ¿que acaso no es de suma importancia la interfaz con la que interactuamos con los SO?... creo que si.

En fin disculpen las molestias y les aseguro que si un dia me puedo hacer de una PC con linux que armonize con hardware, juegos, mp3's, reproductores dvd, y otras cosas la hare mia.

Saludos!

PD. no estoy del lado de nadie, ni de bill gates, ni jobs, ni linux, estoy del lado de la verdad, mi veLdad (jajajajaja):popcorn:

Yo tengo ubuntu instalado de forma similar a la tuya y sin nungun problema, si seguias los pasos que te dijo Psicolonia lo hibas a hacer andar, no necesitas nada extra para poder bootear una particion ntfs
con abrir el menu.list de grub en modo administrador y agregar los datos para iniciar tu windows ya estaba
ejemplo
en la teminal pones
sudo gedit /boot/grub/menu.list

y al final del archivo agregas

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

cambiando hd0,0 por lo que corresponda

Ademas en caso de no poder iniciar tu windows despues de hacer estas modificaciones en lugar de reinstalar todo podrias haber iniciado con un diskette de inicio y escribir en la "terminal" fdisk /mbr con lo cual se borra grub del registro maestro y la pc al encenderla iniciaria windows

---

### Post by Axldust on 2007-05-27
> **elrengo79 said:**
> Yo tengo ubuntu instalado de forma similar a la tuya y sin nungun problema, si seguias los pasos que te dijo Psicolonia lo hibas a hacer andar, no necesitas nada extra para poder bootear una particion ntfs
con abrir el menu.list de grub en modo administrador y agregar los datos para iniciar tu windows ya estaba
ejemplo
en la teminal pones
sudo gedit /boot/grub/menu.list

y al final del archivo agregas

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

cambiando hd0,0 por lo que corresponda

Ademas en caso de no poder iniciar tu windows despues de hacer estas modificaciones en lugar de reinstalar todo podrias haber iniciado con un diskette de inicio y escribir en la "terminal" fdisk /mbr con lo cual se borra grub del registro maestro y la pc al encenderla iniciaria windows

Pues lamento decirte que no, luego averigue y el detalle es que si eran en menu.list, agregar unas lineas pero no exactamente asi, es decir en lugar de "hd0,0" seria "sdaX,X" pero por supuesto no lo sabia y como quede sin internet tampoco pude seguir pidiendo ayuda aca, en fin mas adelante con animos lo volvere a intentar, gracias igual.;)

---

### Post by Al_maverick on 2007-05-27
> **Axldust said:**
> Pues lamento decirte que no, luego averigue y el detalle es que si eran en menu.list, agregar unas lineas pero no exactamente asi, es decir en lugar de "hd0,0" seria "sdaX,X" pero por supuesto no lo sabia y como quede sin internet tampoco pude seguir pidiendo ayuda aca, en fin mas adelante con animos lo volvere a intentar, gracias igual.;)

hd0,0 seria para cuando tenes discos IDE. Cuando tenes discos SATA, como debe ser tu caso, la notacion es sd0,0. Probablemente sda1.

---

### Post by djthree on 2007-07-07
Hola,
Te comprendo %100, en mi opinion personal, por el tema maldito de los drivers propietarios y toda esa historia, se hace dificil que LINUX avance más rápido en todo lo relacionado con Compatibilidad de Hard... 
Te cuento que siendo un usuario familiiarizo en el manejo de computadoras y no llegando a ser un experto, me costo muchisimo instalar mi version de UBUNTU, tuve grandisimos problemas para correr la instalacion, pero despues de buscar en los foros  logre instalarla, ahi me di cuenta el costo que hay que pagar por usar soft libre,... todavia me falta lograr hacer andar mi router USB ya que se me quemo la placa de RED del modem y de la PC, y este mensaje se envia desde mi particion de win XP.
Aun asi, mensajes como el que iniciaste vos, ayudan muchisimo a otros usuarios para solucionar problemas como el que tuvistes vos y lo puedan resolver rapidamente.
Te propongo que cuando estes tranquilo y con tiempo, vuelvas a intentar cargar un LINUX en alguna particion, ya que por lo que veo, muestras interes en el soft libre, para en el futuro migrarte definitivamente. lUn abrazo!!!

---

### Post by Mauro22 on 2007-07-08
> **Axldust said:**
> 

PROBLEMA::(
Al iniciar el sistema se carga primero GRUB, y antes de q termine su cuenta regresiva para iniciar ubuntu, le doy ESC para ver la lista de SO a iniciar, **PERO solo me aparecen diversas opciones de ubuntu, no me aparece nada de mi particion con WINDOWS**, quisiera saber que tengo que hacer para poder verlo, o en todo caso iniciarlo, ya que desde la BIOS intente que arrancara desde el disco duro donde tengo WIN pero sigue iniciando GRUB para pasar a UBUNTU.


Es rarisimo, te comento, yo tengo 2 discos, uno de 160 y otro de 80, los dos ATA (o IDE).

En el de 80gb:
40gb para XP
40gb para Vista

Despues compre el de 160 y le di:
58gb para linux
2gb de swap (aunque no la usa)

50gb particion NTFS para datos, etc etc
50gb libres


Al instalar Ubuntu en el disco de 160 fue todo OK, cuando booteo por primera vez, salio el menu que decia algo como

kernel x-x.x.x
kernel x-x.x.x (recovery mode)
Other operative systems
Windows Vista Loader

al elegir el vista loader, sale el menu de arraque del vista, preguntando si queria usar vista o xp


Todo esto sin tocar nada, todo solito. 

Eso si, despues con la consola hacer:

```
sudo gedit /boot/grub/menu.list
```

y le cambias los titles y las particiones de arranques


Salu2

---

### Post by andy_91 on 2007-07-08
> **Psicolonia said:**
> ola! no problemo con las NTFS!

escribe en terminal

sudo gedit /boot/grub/menu.lst

te le preguntara la password di root. escrebe-la.
si no hays configurado la password hace-lo ahora:

sudo passwd

de seguida coloca: las lineas:

title		Windows XP Professional
root		(hd0,0)
makeactive
chainloader	+1

no te olvides de sustituir hd0,0 por tu hd e particion. si teneras windows antes de instalares linux, sera por supuesto hd0,0.

grub eres una buena herramienta por que pudes escribir los comandos manualmente.

assi puede intentar en grub directamiente. Pressiona C en el menu grub e escribe cada alinea seguida de 'enter'.

grub te dara indicaciones de la particion conforme escrives.

perdona el español... ;)


la verdad si no hablas español no se nota es muy bueno y si lo hablas y es por el taductor la verdad se entiende bastante yo diria perfectamente XD ahora de aqui a q lo haga la pc no se todavia no tengo ese problema ni me gustaria ahi si q estoy frito por eso no voy a dejar ni rastro de lo q tenia q formate todo XD
es lo mejor si te vas a pasar hace una copia de todo lo q te interese (incluso programas por si te arrepentis) y pasate de una es como tener un crucigrama y la solucion linux es el crucigrama y win xp la solucion si tenes la solucion la vas a mirar y no vas a poder resolver el crucigrama por tus propios medios y si no te sale por vos miosmo pedis ayuda en el foro seguro te van a dar una mano ya lo ultimo es rendirse y abandonar es decir volver a win xp el mejor por ahora no recomiendo vista

---

### Post by andy_91 on 2007-07-08
comentarios como estos asustan a cualquiera yo ya mate un celular jugando con la programacion no quiero q me vuelva a pasar q se queme algo o deje de funcionar algo :$

---

### Post by Auringal on 2007-09-15
y otro mas ...xD

Yo tenia Win en mi maquina y puse tambien Ubuntu y todo bien, salvo problemillas menores y torpezas de mi parte por no conocer nada de linux (hace 3 meses que lo uso)

Ayer al cambar de usuario se me tildo y reiicie la maquina y me aparece la pantalla negra con esto:


[B][Mnimal BASh-like line editing is supported. For the first word, TAB list possible command completions anywhere else TAB list the possible completions of a device/filename]

grub>[/B]

segui indicaciones de otros foros, iniciando con 

**find root/grub/stage2...etc**

y al finalizar me dice que esta todo bien pero vuelvo a la misma pantalla de **"Minimal..."**

Me recomendaron un CD de recuperacion que use, me dice que todo se arreglo satisfactoriamente pero lo mismo.

Podrían darme alguna sugerencia, ya que no quiero embarrar mas la cosa y tengo muchas dudas a la hora de usar la consola. Noquisiera perder los datos. Use un LiveCD y veo que las cosas estan aun dentro, es decir mis 2 partic iones con Win y Ubuntu y aunque la maquina no arranca al menos estan los datos...xD

mis particiones son

/dev/sda1 &#8212;&#8211; ntfs
/dev/sda2 &#8212;&#8211; ext 3
/dev/sda3 &#8212;&#8211; extended
/dev/sda5 &#8212;&#8211; linux-swap

por sugerencia de un foro me decian que mirara el menu.lst del grub y veo que no hay ninguna referencia al WinXp

bien, espero haber sido lo mas claro posible. Si me dieran una pauta les agradeceria infinitamente, ya que no puedo trabajar ni hacer nada

Saludos:)

---

### Post by sajnox on 2007-09-15
Otra cosita mas, el archivo /boot/grub/menu.list no lo podias editar por una cuestion de permisos.

La forma mas facil es usar el comando sudo que da permisos de "administrador del sistema" en Linux usuario root (root = god)

Y aun mas facil en una consola escribis 

$ sudo nautilus

Y desde ahi podes hacer TODO, asi que ojo con lo que haces.

Saludos

---

### Post by sajnox on 2007-09-15
Auringal,

No me queda claro cuando tenes ese problema con tu maquina, es decir:

cuando la reinicias que hace ?? El grub carga ?? Pasas el Grub y eso te lo tira una vez que inicio el sistema?

Saludos

---

### Post by Auringal on 2007-09-15
Hola **Sajnox**, gracias por responder

Al prender la maquina me aparece esto
[B][COLOR="DarkSlateBlue"]
[Mnimal BASh-like line editing is supported. For the first word, TAB list possible command completions anywhere else TAB list the possible completions of a device/filename]

grub>
[/COLOR][/B]


segui varios procedimientos distintos de varios foros y al reiniciar aparece eso nuevamente.
(que si hacen falta los enumero)

a ver si me tiran alguna pauta para solucionarlo.

Desde ya agradecidisimo

Saludos dslde Mardel

---

### Post by sajnox on 2007-09-16
Si bien no soy un experto en el tema me suena a que tenes un problema con el grub, proba lo siguiente bootea la maquina con el live cd y segui los pasos que te dan en esta pagina para reinstalar el grub 

[http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/](http://nand-magazine.net/2006/07/30/recupera-el-grub-que-te-ha-quitado-windows/)

Saludos

---

