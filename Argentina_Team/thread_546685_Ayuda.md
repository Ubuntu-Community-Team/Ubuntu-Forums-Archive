---
title: "Ayuda"
date: 2007-09-09
forum: Argentina Team
---

### Post by rustyx on 2007-09-09
Hola amigos, Buen Dia! XD. Les comento que e usado windows toda mi vida :confused:  y e decidido pasarme a ubuntu  ya que me hablaron muy bien de el !!!:) Si me pueden explicar como instalarlo ( si borrar el win Xp:confused: , para poder utilizar los dos sitemas) , cual version tengo que bajar y los requerimientos para que funcione optimo ( mi pc es  pentium 4 ,  CPU 2.66 GHz , 1,23 GB de Ram ) , y que programas  se usan para el mantenimiento ( como tune up) , para grabar cds , msn ,bajar ( como emule)  tengan en cuenta que no tengo ni idea  jejeje  , asi q espero su ayuda XD.
Gracias!!!
Un abrazo:popcorn:

---

### Post by eggdeng on 2007-09-09
Probablemente la 7.04 (Feisty Fawn) es la mejor versión para un novato ya qua muchas de las tares de configuración (controladores de la tarjeta grafica, codecs) estan automatizadas. A no ser que quieras esperar a la siguiente (7.10) que se espera para Octubre.
Te bajas un imagen del CD, lo grabas como ISO (ver p ej [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)) y a instalar.
Este es un live CD y te da la opcion de cargar ubuntu desde el CD, asi q puedes ver como funciona con tu hardware sin instalar nada. Si te decides a instalar, lo mas aconsejable es mantener tu particion de XP y crear nuevas particiones para q se instale ubuntu. Esto se puede hacer con la CD de instalación, o si prefieres una herramienta + potente, te bajas el live CD de gparted. Lo normal es crear una particion para la instalacion que se llama / o raíz, y otra que se llama swap  (2X el tamaño de la memoria fisica). Esta particion hace las veces del archivo de paginacion en W*nd*ws. Cuand instalas, el gestor de arranque q ubuntu incluye (GRUB) reconocera automaticamente la particion de XP y te dara la opcion de arrancar en cualquier de los dos sistemas.
Tienes sufficiente procesador y memoria para poder usar ubuntu sin problemas. Para bajar archivos, esta, entre muchos otros,el amule q es un clon para linux de emule, y un monton de clientes bittorrent como azureus q te dan velocidades d transferencia mucho mayores. Tambien hay un clon (algo cutre) del messenger q se llama amsn aunque muchos prefieren gaim (ahora se llama pidgin) ya q tiene mejor interfaz es compatible con mas protocolos. Con cualquier d los dos puedes chatear todo lo q quieres. Para grabar CDs, mi aplicación preferida es la muy estable y completa Gnome Baker. Por lo demas,hay distintas herramientas para tunear distintos aspectos del funcionamiento del sistema.

---

### Post by rustyx on 2007-09-09
Buen dia eggdeng , que rapidez :)  gracias amigo por contestar !!!!:) , Ya baje el archivo creo que es este " ubuntu-7.04-desktop-i386 " pero no me da la opcion para instale ubuntu :confused: !!!!!!!!!!!!, figura  para instalar unicamente el Mozilla Firefox ,Mozilla Thunderbird ,Blender , etc. :confused:
Si me puedes ayudar!!!!Gracias!!!

---

### Post by rustyx on 2007-09-09
Gracias ya lo pude solucionar!!!:popcorn:

---

### Post by undiaperfecto on 2007-09-09
booteaste con el live cd?
una vez que te carga el escritorio vas a encontrar el icono instalar, de ahi en adelante es una papa.

---

### Post by rustyx on 2007-09-11
La verdad que todabia no e podido , podrian decirme de donde bajarlo , porque creo que baje cualuiera :confused:

---

### Post by facundocorradini on 2007-09-11
bajalo de acá:

[http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=)

igualmente, si desde windows te muestra las opciones de instalar firefox y eso, entonces debes haber bajado la versión correcta.

Para instalar Ubuntu, solo debes arrancar la PC con el disco puesto (y el bios configurado para bootear desde el CD).

------------------------------------------------------------------------------
Tal vez te convenga darle una mirada a algun manual de instalación , por ejemplo: [http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar](http://www.guia-ubuntu.org/index.php?title=Instalaci%C3%B3n_est%C3%A1ndar)

saludos y bienvenido

---

### Post by rustyx on 2007-09-11
Gracias!!!!!!!!:popcorn:

---

### Post by rustyx on 2007-09-11
Ya e podido instalar ubuntu  , lo unico  si me pueden ayudr ahora  no se como instalar los soft  SmartAX MT810 ( modem) y GeForce2 MX 400 ( placa de video) , en verdad no se como se instalan los soft , jajja:) . si me pueden dar una mano  o algun manual para que me guie , tengan en cuenta que hace horas que empeze a utilizar ubuntu :)

---

### Post by FlyerDie on 2007-09-11
> **rustyx said:**
> Ya e podido instalar ubuntu  , lo unico  si me pueden ayudr ahora  no se como instalar los soft  SmartAX MT810 ( modem) y GeForce2 MX 400 ( placa de video) , en verdad no se como se instalan los soft , jajja:) . si me pueden dar una mano  o algun manual para que me guie , tengan en cuenta que hace horas que empeze a utilizar ubuntu :)

Rustyx, vos te referis a los drivers?

En el caso del modem USB:
[http://www.ubuntu-es.org/index.php?q=node/19203](http://www.ubuntu-es.org/index.php?q=node/19203)

Si te manejas con el ingles te va a servir ya que es un How-To ;)

Y para la placa de video:

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Ahi tenes los links para bajar los drivers y una pequeña referencia.


Ahora mi pregunta es...los drivers de video no te los toma directamente? quiero creer que para una GForce 2 te tiene que detectar los drivers automaticamente, salvo que haya algun tema de copyright con Nvidia (desconozco porque no uso drivers nvidia).

Saludos!:guitar:

---

### Post by rustyx on 2007-09-11
Buenas Noches FlyerDie , gracias por responder!!! Trato instalalos  y comento ,gracias igual a todos por la paciencia XD :)

---

### Post by rustyx on 2007-09-12
Hola amigos!!!Buen dia , comoe estan!! Voy dando mis primeros pasos en    Ubuntu!! XD:confused:  es visto en el internet cosas muy guapas ! como tener multi escritorios , saben de donde lo puedo descargar y algun sof  o plugin para arbrir el msn en varias sesiones
Un abrazo!!!!!:popcorn:

---

### Post by FlyerDie on 2007-09-12
hey hey...pero ya pudiste hacer andar al modem y la placa de video??

vamos por partes dijo Jack ;)

---

### Post by eggdeng on 2007-09-12
Para tu tarjeta, necesitas el legacy-driver 1.0-96. Ver [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-a.html)

---

### Post by rustyx on 2007-09-12
Hola amigos!!!! FlyerDie no , jaja  . La verdad  me estoy volviendo loco no se como instalar nada:confused: , el modem  entre a la pagina q me psaste pero un link no anda !! y mucho no entiendo :)( soy de madera) tantos codigos parece para un programador XD:confused: , llame a mi empresa de internet y no da soporte sobre linux :confused::confused: la verdad no se que hacer quiero instalar el modem para despues poder bajar todo lo q me falta , pero bueno parece q no puedo arrancar( tengan en cuenta que estaba acostubrado a ejecutar un archivo .exe y listo ya estaba instalado). 
Si alguien me puede orientar , porque quiero dejar de usar win:confused::confused:.
Un Abrazo a la banda!!!:)
Saludos, que terminen bien el dia!!!

---

### Post by faktorqm on 2007-09-13
hola, para instalar el modem, ya hay un post que te dice exactamente todo y bien. te lo pongo mas abajo.......
para la placa de video, te recomiendo que te bajes el envy, y lo instales con eso, por que hay un modulo precompilado del kernel que no esta, y el envy lo hace.

MODEM: [http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810](http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810)

VIDEO: [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

mas claro, hechale vodka papá!! salu2!!

---

### Post by rustyx on 2007-09-13
Hola.Buen dia! faktorqm segui el tuto que me dijiste pero no pude el modem  , el archivo eagle-usb  no me deja descomprimirlo en la carpeta  /lib/firmware/ me dice que no tengo permiso y el otro archivo br2684ctl_20040226-1_i386.deb cuando lo quiero ejecutar me da error ( libatml) y el de la placa de sondo lo ejecuto y me da error ( build-essesial)
:confused::confused: amigos gracias a todos  los que me dieron una mano ,pero bueno parece que esto no e slo mio y voy a tener que seguir con mi sistema operativo anterior :confused:
Un abrazo!!!!:):)

---

### Post by FlyerDie on 2007-09-13
> **rustyx said:**
> Hola.Buen dia! faktorqm segui el tuto que me dijiste pero no pude el modem  , el archivo eagle-usb  no me deja descomprimirlo en la carpeta  /lib/firmware/ me dice que no tengo permiso y el otro archivo br2684ctl_20040226-1_i386.deb cuando lo quiero ejecutar me da error ( libatml) y el de la placa de sondo lo ejecuto y me da error ( build-essesial)
:confused::confused: amigos gracias a todos  los que me dieron una mano ,pero bueno parece que esto no e slo mio y voy a tener que seguir con mi sistema operativo anterior :confused:
Un abrazo!!!!:):)

Rustyx, si te dice que no tenes permisos es que no estas con usuario root, la descompresion hacela desde una terminal, fijate que en el TUTO dice que te logonees como root o que hagas un sudo **antes de cada comando**

Osea, seria algo asi:

```
cd /lib/firmware/

sudo mkdir ueagle-atm

cd /home/USUARIO/Desktop

sudo tar -zxvf ueagle-data-1.1.tar.gz

cd ueagle-data-1.1

sudo cp * /lib/firmware/ueagle-atm
```

---

### Post by rustyx on 2007-09-13
y como entro como usuario root?? :lolflag:

---

### Post by FlyerDie on 2007-09-13
:?

Me parece que no leiste el TUTO, ni leiste lo que te escribi...

Si no sabes como entrar con usuario root, tenes la opcion de ingresar con sudo, que es la explicacion que te puse mas abajo.
:guitar:

---

### Post by rustyx on 2007-09-13
:confused: lo lei mas de 10 veces  al tuto! que es sudo:confused: trate de entar de la pantalla de inicio con root y el pass q le asigne y me dice que de ahi no se puede :confused::confused:, amigo tene en cuenta que es la primera vez que uso este sistema operativo:popcorn:

---

### Post by Mafber on 2007-09-13
Hola Rustyx!!! El "sudo" es para que ubuntu te deje hacer algunas cosas que vos como usuario común no podes hacer (es para tu protección)
Por ejemplo: si queres abrir un archivo que es del sistema, lo vas a poder leer pero no cambiar el contenido (se abre como de solo lectura). Con el "sudo" vas a poder abrir el archivo pero tambien editar el contenido (copiar, pegar, cortar...)
Suerte!!!

---

### Post by LaHire on 2007-09-13
> **Mafber said:**
> Hola Rustyx!!! El "sudo" es para que ubuntu te deje hacer algunas cosas que vos como usuario común no podes hacer (es para tu protección)
Por ejemplo: si queres abrir un archivo que es del sistema, lo vas a poder leer pero no cambiar el contenido (se abre como de solo lectura). Con el "sudo" vas a poder abrir el archivo pero tambien editar el contenido (copiar, pegar, cortar...)
Suerte!!!


Siguiendo lo que dice mi camarada Mafber aqui, trabajar con el comando sudo es muy facil

supongamos que tenemos un comando, como por ejemplo 
```
apt-get update
```

si lo ponemos asi nomas en una consola comun y corriente, nos va a decir que no podemos hacer ese comando, porq tenemos el acceso denegado
entonces, cuando decimos que "usar sudo" es...anteponerle la palabra" sudo" al comando que queremos correr

entonces, tomando el ejemplo que di antes, para poder correr el comando apt-get update
tendria que quedar asi
```
sudo apt-get update
```
cuando presiones enter, te va a pedir una contrasenia

cual contrasenia? la tuya, la contrasenia que usas para ingresar a tu secion
Cuando la ingreses y presiones enter, va a ejecutar el comando como si fueras superusuario.-

Entonces, siempre que escuches por ahi "usa el comando sudo para hacer tal cosa o tal otra", significa que debes anteponer el comando "sudo" antes de cualquier comando que necesites

para mas informacion (en ingles, alguien sabe si desde Launchpad se puied traducir?), ve a una consola y pon "man sudo"

Por cierto, el comando "man", te permite leer el manual/ ayuda que tenga el comando/programa que quieras, su uso es bastante simple

```
man <programa/comando>
```

Suerte con la instalacion! :)

---

### Post by rustyx on 2007-09-13
Hola!!!:):) Cada vez me acerco mas XD jejej .Amigo LaHire si tu me puedes ayudar lo que todabia no entiendo!! que nadie me dice esos codiogos que me pasan  "apt-get update" " sudo tar -zxvf ueagle-data-1.1.tar.gz" donde los inserto!!Gracias por la paciencia :):)

---

### Post by LaHire on 2007-09-13
> **rustyx said:**
> Hola!!!:):) Cada vez me acerco mas XD jejej .Amigo LaHire si tu me puedes ayudar lo que todabia no entiendo!! que nadie me dice esos codiogos que me pasan  "apt-get update" " sudo tar -zxvf ueagle-data-1.1.tar.gz" donde los inserto!!Gracias por la paciencia :):)

Oh!, perdoname, q no te explique eso antes :)

todos esos comandos se hacen desde Consola 
La consola, es como un DOS, donde uno pueded colocar comandos...sin interfaz grafica de por medio

Para entrar tenes varias formas

Apretando
Ctrl + Alt + F2,  directamente saltas a la consola en pantalla completa (y para volver al entorno grafico, usamos Ctrl + Alt + F7)

y luego, depende en que tipo de escritorio estes

Apretando la combinacion de teclas

Alt + F2, nos va a abrir una ventana que nos dejara ejecuitar una aplicacion, solo tenemos que especificar el nombre de la misma

la consola, el nombre varia con el entorno de escritorio

si instalaste Ubuntu (y no Kubuntu), es "gnome-terminal" (aunq seguro te autocompleta el nombre apenas escribas "gnome-ter")

Una vez ahi, vas a poder ingresar todos los comandos que quieras :)

por asi decirlo, esa Consola (o Shell), corre constantemente cuando encendemos la pc, pero nosostros solo vemos el escritorio y demas cosas, que corren arriba de la misma

asi que para ingresar todo tipo de comandos, usamos consola

te recomiendo que uses gnome-terminal, o xterm, ya que te abre una consola en una ventana...y no te obliga a trabajar en pantalla completa (entonces podes abrir el chat y estar en consola al mismo tiempo)

y bueno, acordate del sudo :P

por cierto, no?
"sudo tar -zxvf ueagle-data-1.1.tar.gz"

te recuerdo que bueno, cuando esta en consola, le aparece algo asi como 

ubuntu@ubuntu:~$ 
esto te indica el nombre de usuario @ nombre de la maquina

para poder usar el "tar -zxvf ueagle bla bla bla", vas a tener que ubicarte en la carpeta donde descargaste el archivo

para eso, se usa el comando CD, como en DOS ;)

si lo bajaste en el escritorio, tenes que ir al escritorio

para eso
cd /home/TuUsuario/Desktop/

y ya esta :)

AH!, siempre que trabajes con esa clase de cosas (arboles de carpetas.../home/usuario y demas), Linux tiene autocompletar...cosa que es GENIAL

Digamos, escribi (en consola) /ho y apreta la tecla TAB...te va a autocompletar!, si no hay nada con ese nombre, va a hacer un ruidito...pero si hay muchas alternaticas...apreta tab dos veces, y te va a mostrar las carpetas que empiecen con ese nombre

espero no marearte

suerte!

---

### Post by FlyerDie on 2007-09-13
LaHire...avisale como volver de la tty 2, porque sino se va a volver loco:lolflag::lolflag:

Una vez que hiciste CTRL+ALT+F2 y pudiste usar la consola, para volver al entorno grafico, debes apretar CTRL+ALT+F7

---

### Post by LaHire on 2007-09-13
> **FlyerDie said:**
> LaHire...avisale como volver de la tty 2, porque sino se va a volver loco:lolflag::lolflag:

Una vez que hiciste CTRL+ALT+F2 y pudiste usar la consola, para volver al entorno grafico, debes apretar CTRL+ALT+F7

" (y para volver al entorno grafico, usamos Ctrl + Alt + F7)" :D

---

### Post by rustyx on 2007-09-13
Gracias amigos!!!ahora me pongo a probar  , esta noche  se la dedico  a  ubuntu , haber si lo hago funcionar bien a todo :):):)

---

### Post by lopulus on 2007-09-24
Hola: Como yo tambien soy nuevo y no se como empezar un post, utilizo este. Tengo Win XP
Yo ya me he bajado el mismo que Rustyx, lo he quemado en un CD y lo he probado. Mi Compu es un pentiun II creo (Como hago para saberlo) con 384 MB de ram. Sera suficiente?
Cuento con dos discos uno que tiene 20 G y contiene el WXP y otro con 80 el cual eta a un 50% completo.
Quisiera que me ayuden a instalarlo y si esta version es la que tiene el cubo (que se ve en youtube) que me dejo fascinado.
Les agradezco desde ya.
Saludos y un abrazo 

Lopulus

---

### Post by sajnox on 2007-09-24
Hola Lopulus,

En primer lugar Bienvenido!!! 

Vamos por partes, 

1) Para iniciar un nuevo mensaje: cuando entras abajo de la barra marron que dice Argentina Loco team tenes un cuadro naranja que dice "Make new post" (Crear mensaje nuevo), siempre es util que lo uses y que puedas especificar lo mejor posible que es lo que necesitas.

2) Esta claro que bajaste el cd y lo quemaste, bajaste la version Live CD?? eso significa que si arrancas la maquina desde el cd vas a poder ver si el programa reconoce tu hard sin problemas. Sabes como iniciar la maquina desde el cd??

3) Un Pentium II me parece que es un poco corto, probalo..sino tenes otras opciones un poco menos vistosas pero igualmente efectivas, si tenes las ventaja de tener + de 256mb de ram para que el sistema corra bien.

4) La instalacion del sistema requiere de 4gb de disco por lo que me animo a recomendarte que uses el disco en el que tenes el xp y no el que usas para guardar archivos, si es que lo tenes armado asi (antes de instalar defragmenta el disco)

5) Si el motivo que mas te atrae de ubuntu es el cubo, primero fijate que placa de video tenes FUNDAMENTAL!!!!. Para saber si te reconoce el cubo, inicia la maquina con el cd y seleccionas en sistema/Preferencias/efectos de escritorio. la combinacion de teclas para que ande el famosos cubo es crtl + alt + boton izquierdo del mouse (y move el mouse obvio). Si esto te anda despues te explicamos como instalar compiz/beryl que son los efectos a toda maquina.

Bueno ya escribi mucho, fijate como anda y contanos

Saludos

---

### Post by sajnox on 2007-09-24
Me olvidaba,

Te dejo un link con una guia muy facil de como instalar el sistema

[http://linux-es-libre.org/moodle/mod/resource/view.php?id=125](http://linux-es-libre.org/moodle/mod/resource/view.php?id=125)

Nuevamente saludos

---

### Post by lopulus on 2007-09-25
> **sajnox said:**
> Hola Lopulus,

En primer lugar Bienvenido!!! 

Vamos por partes, 

1) Para iniciar un nuevo mensaje: cuando entras abajo de la barra marron que dice Argentina Loco team tenes un cuadro naranja que dice "Make new post" (Crear mensaje nuevo), siempre es util que lo uses y que puedas especificar lo mejor posible que es lo que necesitas.

2) Esta claro que bajaste el cd y lo quemaste, bajaste la version Live CD?? eso significa que si arrancas la maquina desde el cd vas a poder ver si el programa reconoce tu hard sin problemas. Sabes como iniciar la maquina desde el cd??

3) Un Pentium II me parece que es un poco corto, probalo..sino tenes otras opciones un poco menos vistosas pero igualmente efectivas, si tenes las ventaja de tener + de 256mb de ram para que el sistema corra bien.

4) La instalacion del sistema requiere de 4gb de disco por lo que me animo a recomendarte que uses el disco en el que tenes el xp y no el que usas para guardar archivos, si es que lo tenes armado asi (antes de instalar defragmenta el disco)

5) Si el motivo que mas te atrae de ubuntu es el cubo, primero fijate que placa de video tenes FUNDAMENTAL!!!!. Para saber si te reconoce el cubo, inicia la maquina con el cd y seleccionas en sistema/Preferencias/efectos de escritorio. la combinacion de teclas para que ande el famosos cubo es crtl + alt + boton izquierdo del mouse (y move el mouse obvio). Si esto te anda despues te explicamos como instalar compiz/beryl que son los efectos a toda maquina.

Bueno ya escribi mucho, fijate como anda y contanos

Saludos

Hola sajnox!
Gracias por la info que me mandaste. La vi y me parecio muy completa, si bien me quedaron algunas dudas ya que la he leido muy apresurado pera ya la tengo agendada.
En relacion a tus 5 items... veamos...
1) Ya lo encontre antes de leer tu mensaje. Gracias

2) Con este punto esta todo Ok, inclusive empece la instalacion pero a la hora de las particiones me heche atras. Gracias

3) Lo probe con el live CD y anduvo bien, Si es que anduvo un poco lento lo atribui a que era porque estaba trabajando con el CD. Lo que no entendi aca es que si con +256 me anda el SO que baje u las otras opciones que decis. Pero gracias igual.

4) Con este no habria problemas, si bien estuve preparando el disco mas grande para instalarlo ahi. Pero lo instalo en el que tengo XP si decis que es mejor.  y

5) Placa de video tengo Nvidia GeForce MX400. De todos modos pruebo con el Live CD. Gracias

Si bien te parece reiterativo vuelvo a agradecerte.
Saludos y un abrazo.

Lopulus

PD: Como hago para recibir las respuestas al foro en mi mail???

Cha gracias

---

### Post by sajnox on 2007-09-25
> **lopulus said:**
> Hola sajnox!
Gracias por la info que me mandaste. La vi y me parecio muy completa, si bien me quedaron algunas dudas ya que la he leido muy apresurado pera ya la tengo agendada.
En relacion a tus 5 items... veamos...
1) Ya lo encontre antes de leer tu mensaje. Gracias

2) Con este punto esta todo Ok, inclusive empece la instalacion pero a la hora de las particiones me heche atras. Gracias

3) Lo probe con el live CD y anduvo bien, Si es que anduvo un poco lento lo atribui a que era porque estaba trabajando con el CD. Lo que no entendi aca es que si con +256 me anda el SO que baje u las otras opciones que decis. Pero gracias igual.

Con otras opciones me refiero a basicamente a xubuntu que es una version de Ubunutu para maquinas un poco mas viejas con menos requerimientos de hardware, esta soportado por Canonnical (empresa que desarrolla ubuntu)

> **lopulus said:**
> 
4) Con este no habria problemas, si bien estuve preparando el disco mas grande para instalarlo ahi. Pero lo instalo en el que tengo XP si decis que es mejor.  y

No se si es "mejor" pero es mas facil de organizar y es menos riesgo para tus datos ya que si haces "lio" en el disco del sistema operativo es mas facil de recuperar que tudas datos
> **lopulus said:**
> 
5) Placa de video tengo Nvidia GeForce MX400. De todos modos pruebo con el Live CD. Gracias

Si bien te parece reiterativo vuelvo a agradecerte.
Saludos y un abrazo.

Lopulus

PD: Como hago para recibir las respuestas al foro en mi mail???


Hasta donde yo se no se puede, tenes que entrar al foro y revisarlo (Marianom estoy en lo correcto?)
> **lopulus said:**
> 
Cha gracias
[/QUOTE]

De nada

---

### Post by leo_rockway on 2007-09-25
> **lopulus said:**
> Como hago para recibir las respuestas al foro en mi mail???

arriba hay un menu que dice Thread Tools. Haces click en el menu y elegis la opcion "Suscribe to this thread". En notification type le pones "Instant notification by email".

Esto va a hacer que te avise cuando alguien responda a este thread (solo te avisa una vez... para que te vuelva a avisar en caso de una nueva respuesta tenes que visitar el thread).

Es lo mas cercano a recibir respuestas del foro por email.

Saludos,
Leo

---

### Post by marianom on 2007-09-25
Al correcto comentario de Leo, te cuento que en caso que quieras  automaticamente siempre recibir un mensaje de cualquier thread donde hayas colaborado (no importa si preguntaste o respondiste) podes hacerlo desde la opción "User CP" que tenés en el menú superior. Ahí vas a "Edit Options" y buscás "Default Thread Subscription Mode" donde elegís "Instant Email Notification" y listo.

Fair warning: hay veces que uno se mete en algunos threads que siguen por meses y meses y meses... es posible que en ese momento te arrepientas un poquito de tener la opción pero generalmente es muy útil.

---

### Post by lopulus on 2007-09-26
Gracias, Gracias, Gracias, Gracias, Gracias, !
Ahora una ultima pregunta
¿Puedo hacer el backup en el disco de 80G?

Vuelvo a agradecer

Lopulus

---

### Post by sajnox on 2007-09-26
> **lopulus said:**
> 
¿Puedo hacer el backup en el disco de 80G?
Lopulus

Como poder podes, pero si en ese disco guardas datos y se te rompe, se te rompe el backup tambien, generalmente los backups los haces en discos distintos al que estas usando.

Saludos

---

### Post by lopulus on 2007-09-28
Sajonx:
Al windows lo tengo en otro disco de 20G, en el de 80 tengo solo archivos y a Ubuntu lo instalo en el de 20 G

Asi es como tenia pensado

---

### Post by sajnox on 2007-09-28
> **lopulus said:**
> Sajonx:
Al windows lo tengo en otro disco de 20G, en el de 80 tengo solo archivos y a Ubuntu lo instalo en el de 20 G

Asi es como tenia pensado

Estabamos de acuerdo entonces

Suerte con tu instalacion y contanos como te fue

---

### Post by lopulus on 2007-10-03
> **sajnox said:**
> Me olvidaba,

Te dejo un link con una guia muy facil de como instalar el sistema

[http://linux-es-libre.org/moodle/mod/resource/view.php?id=125](http://linux-es-libre.org/moodle/mod/resource/view.php?id=125)

Nuevamente saludos

Hola: Como estas? Yo no muy bien ya que no pude instalar Ubuntu 7.04 y esta guia que me pasaste es de otra version.
El problema me aparece a la hora de seleccionar el disco. Me aparece como espacio libre solo 8M cuando en realidad teng 6.7 G libres.
Con estos datos podran ayudarme'

Busque otras guias para instalarlo pero igualmente tengo problemas. 
Conocen a alguien de la comunidad que viva en Villa Constitucion?

Saludos y un abrazo

---

### Post by sajnox on 2007-10-03
Estas seguro de a donde estas apuntando la instalacion, si estas seguro de tener 6.7 gb eso no tiene por que pasar.

Que metodo de instalacion estas utilizando? hay varios en el live cd y si el que elegis es el de tomar el espacio libre probablemente no lo puedas hacer.

Probaste con el metodo manual?? creo que es la ultima opcion que tenes en el Live CD pero sinceramente no lo recuerdo

Saludos

---

### Post by vk-cdg on 2007-10-03
> **lopulus said:**
> Hola: Como estas? Yo no muy bien ya que no pude instalar Ubuntu 7.04 y esta guia que me pasaste es de otra version.
El problema me aparece a la hora de seleccionar el disco. Me aparece como espacio libre solo 8M cuando en realidad teng 6.7 G libres.
Con estos datos podran ayudarme'

Busque otras guias para instalarlo pero igualmente tengo problemas. 
Conocen a alguien de la comunidad que viva en Villa Constitucion?

Saludos y un abrazo

En este [link](http://www.configurarequipos.com/doc461.html) hay un tuto de como instalar Ubuntu 7.04. Espero que te sirva.

---

