---
title: "No puedo realizar ninguna tarea administrativa"
date: 2007-04-23
forum: Argentina Team
---

### Post by konstantin88 on 2007-04-23
Hola, no encontré ningún tema que tenga respuestas a mi problema, entonces les cuento...hace ya bastante tiempo que uso Ubuntu Dapper Drake y siempre me funcionó a la perfección, mejor que Windows, pero ahora no sé si toqué algo, pero no me deja hacer ninguna tarea administrativa, faltan en el menú y cuando los ejecuto en la terminal, me pide la constraseña que siempre utilicé y no me la acepta. En otros foros me decían que tratara de entrar como root, o cambiar el password del root en la terminal, lo que no me funciona porque es tarea administrativa, o te dicen que actives la opción para permitir a root acceder como GMD en menú sistema>administración>configuración de la pantalla de inicio de sesión, y no tengo esas opciones disponibles. No sé la verdad que hacer y no encuentro soluciones en los otros temas. Siempre recomiendan cosas que no puedo hacer al no tener acceso a ninguna tarea administrativa. Molesta mucho porque no puedo actualizar hace ya tiempo ni instalar nuevos programas.
Gracias por su atención.
Konstantin

---

### Post by lugonesjoaquin on 2007-04-23
Ni idea...

Pero siempre si algo te lia mucho mandale un format y listo...

Aunque serìa mejor si se supiera la razòn del problema, pero bue, antes de perder tanto tiempo.

---

### Post by jayflower on 2007-04-23
con el live cd no podes entrar tampoco?

---

### Post by jayflower on 2007-04-23
Si podés entrar con el live CD y navegar por tus carpetas dentro del disco duro, entra al directorio /etc y ahí buscas el archivo shadow. si te deja borras el contenido de los passwords.

---

### Post by konstantin88 on 2007-04-24
Jayflower: probé lo que me dijiste y no me deja entrar al archivo, el icono aprace con una cruz roja y cuando quiero entrar me sale: "No se pudo mostrar «/etc/shadow»". Yo entrar puedo normalmente, no necesito el Live CD, el problema es que no puedo actualizar, ni instalar nuevos programas, en el menú Sistema/Administración solo tengo las opciones: Administracion de dispositivos, Herramientas de red, Impresoras, Monitor del sistema y Registro de actividad del sistema. En Aplicaciones no tengo la útima opción para agregar o quitar programas. No sé que hacer. 
Lugonesjoaquí: tiene que haber alguna forma de arreglarlo antes
Gracias

---

### Post by felipelerena on 2007-04-24
> **lugonesjoaquin said:**
> Ni idea...

Pero siempre si algo te lia mucho mandale un format y listo...

Aunque serìa mejor si se supiera la razòn del problema, pero bue, antes de perder tanto tiempo.

no te enojes, pero ese consejo no es un consejo logico para linux, si lo es para windows, pero en linux eso no se hace

---

### Post by Al_maverick on 2007-04-24
Podrias fijarte si tu usuario esta en /etc/sudoers. Si no recuerdo mal, ahi estan los usuarios que pueden realizar tareas administrativas.

Esta thread te puede ayudar, sobre todo los consejos de la pagina 2: [http://ubuntuforums.org/showthread.php?t=389537]("http://ubuntuforums.org/showthread.php?t=389537")

---

### Post by konstantin88 on 2007-04-24
Al_maverick: 
1) no me deja entrar a sudoers, me pasa lo mismo que con shadow, no tengo permiso. 
2) sí, en el otro tema tratan algo muy parecido, voy a ver que me responden.
Gracias

---

### Post by clasificado on 2007-04-24
> **felipelerena said:**
> no te enojes, pero ese consejo no es un consejo logico para linux, si lo es para windows, pero en linux eso no se hace

¡Pero si es una opcion! Yo creo que no hay problema

Clasificado

---

### Post by felipelerena on 2007-04-24
creo que la mejor manera de mostrar que somos diferentes y que el sistema es modular y que una cosa no ande no quiere decir que haya que tirar todo a la basura. creo que nunca deberiamos recomendar "formatea el disco"

---

### Post by Al_maverick on 2007-04-24
> **clasificado said:**
> ¡Pero si es una opcion! Yo creo que no hay problema

Clasificado

El problema es que ese enfoque funciona en Windows por la inestibilidad que tiene, pero en Linux, si no sabes que hiciste para producir el error, probablemente termines volviendo a tener el mismo problema. Ademas, en general los problemas son solucionables y aprendes MUCHO al intentar arreglarlos.

Volviendo al tema, probaste de entrar al archivo desde un LiveCD?
Ejecuta desde un LiveCD y despues monta la unidad donde tenes instalado Linux.
Ubica el archivo sudoers y copia el contenido aca.

Corriendo desde el LiveCD sos root, asi que no deberias tener problemas de permisos.

---

### Post by konstantin88 on 2007-04-24
Claro felipe, yo creo que tiene que haber una solución, es muy fácil decir formateo y listo.
Ah, me olvidaba, muy buena tu página :)

---

### Post by konstantin88 on 2007-04-24
Al_maverick: no vi que habías respondido. Cómo entro con el Live CD? parece medio estúpido pero no puedo; antes con windows solo, entraba sin tocar nada, solo cargando con el CD; ahora entra a la pantalla para elegir entre windows o ubuntu, y al Live CD ni lo registra; tengo que apretar algo mientras se carga? decía en otro tema que había que apretar F2, lo hice y no veo que las opciones que aparecen tengan que ver con ésto.
Gracias

---

### Post by lavaramano on 2007-04-24
> **konstantin88 said:**
> Al_maverick: no vi que habías respondido. Cómo entro con el Live CD? parece medio estúpido pero no puedo; antes con windows solo, entraba sin tocar nada, solo cargando con el CD; ahora entra a la pantalla para elegir entre windows o ubuntu, y al Live CD ni lo registra; tengo que apretar algo mientras se carga? decía en otro tema que había que apretar F2, lo hice y no veo que las opciones que aparecen tengan que ver con ésto.
Gracias

tenes que fijarte en el BIOS cuando arranca la maquina (gralmente es con DEL o F1 o F10 o ESC o alguna de esas) y ahi tenes que configurar los dispositivos con los que va a bootear y elegis primero a la lectora y despues al hd.

---

### Post by lugonesjoaquin on 2007-04-24
Psss, pienso lo mismo que ustedes nada mas que no me supe expresar.

Osea por ahi andas corto de tiempo y lo mejor es formatear y listo, aunque si tienes tiempo comienzas a buscarle la razon del problema y listo

Una de las tantas cosas que te permite hacer este sistema es HACER LO QUE QUIERAS.. por lo que si quieres formatear, formatea y listo hombre!

Creo que al ser uin foro es de libre expresion y se puede recomendar cualquier cosa no?

---

### Post by tzulberti on 2007-04-24
Podes intentar cambiarle la contraseña al root... Para hacer eso si tener que editar, cuando te aparezca el grub, tenes que presionar "e" (de Editar).
Luego escribes: "init=/bin/bash" (sin las comillas). Y asegurate el tipo de booteo este en rw en vez de ro (read/write en vez de read/only)... Va a empezar a bootear, pero te va a aparecer mucho texto... Cuando termine de bootear, vas a estar logueado automaticamente como root...

Lo de las contraseñas a mi me pasaba porque tenia mal configurado el ssh y se nota que alguien entraba/entro en mi sistema (se habia creado un user y todo)....


Saludos,
TZ

---

### Post by konstantin88 on 2007-04-25
lavaramano:
soy muy nabo, pero no sé cómo configuro con que va a bootear; te digo lo que hice, apreté F2, entré a la pantalla de BIOS, pero ni idea en que opción meterme, tengo 11 y no sé cual es, te digo cuáles son por las dudas: Soyo Combo Setup, Standard Cmos Setup. Bios Features Setup, Chipset Features Setup, Power Management Setup, PNP/PCI Configuration, Load Setup Defaults, Integrated Peripherals, Supervisor Password, User Password y IDE HDD Auto Detection.
TZ:
cuando entro al grub y apreto "e", me salen estas opciones: root, kernel ./boot/vmlinuz-2.6.12-27-386.root=/dev/hdb2 ro quit splash, initrd ./boot/initrd.img-2.6.15-27-386, savedefault y boot. Booteando con esas, sigue todo igual. Apretando "c", sale la command-line, puse lo que vos me dijiste y me dice "error 27: unrecognized command", y vi que no está entre los comandos que se pueden usar, está sí initrd, pero ni idea que hacer con él. Quizá no te entendí y tendría que haber hecho otra cosa.
Gracias a los dos

---

### Post by Al_maverick on 2007-04-25
La opcion va a estar en Bios Features Setup o Chipset Features Setup. Dentro de alguna de esas dos esta el Boot order, para elegir bootear desde CD primero.

---

### Post by konstantin88 on 2007-04-25
Pude entrar con el LiveCD, pero no me deja montar la partición de Ubuntu; entrando a la carpeta system aparecen, las dos particiones (la de Windows y la de Ubuntu), CD, floppy, y file system. La partición de Ubuntu no me la deja montar, igual me pasa desde ubuntu cuando quiero montar la de Windows y, en file system, puedo hacer lo mismo que en el del disco, no me deja entrar ni a sudoers, ni a shadow.

---

### Post by konstantin88 on 2007-04-25
TZ decía "Lo de las contraseñas a mi me pasaba porque tenia mal configurado el ssh y se nota que alguien entraba/entro en mi sistema (se habia creado un user y todo)..." (no estoy nada canchero con el quote, jeje)

Eso creí desde el primer momento, pero después me pareció medio irreal, el clásico justo a mí se me van a venir a meter, pero ahora me parece que lo estoy confirmando, no sé que pensar...

---

### Post by jayflower on 2007-04-25
Probaste entrar con algún live CD? no tenes cuando arranca grub la opcion de entrar como root? muy raro...:|

---

### Post by konstantin88 on 2007-04-25
Entré con el Live CD ya, pero no me deja montar la partición de ubuntu del disco, me dice: "Imposible montar volumen seleccionado
error: el dispositivo /dev/hdb2 no es removible
error: no se puede ejecutar pmount"
Salvo que tenga que elegir otra de las opciones antes de entrar, son éstas: Start or install Ubuntu (con esa entré), Start Ubuntu in safe graphics mode, Check CD for defects, Memory test y Boot from first hard disk. También se puede apretar F6 para otras opciones y aparece la línea de comando, quizá ahí se pueda poner algo, pero creo que estoy entrando como root con la 1ra opción, el punto es que no sé porque no me deja montar esa partición.
Gracias

---

### Post by Al_maverick on 2007-04-25
> **konstantin88 said:**
> Entré con el Live CD ya, pero no me deja montar la partición de ubuntu del disco, me dice: "Imposible montar volumen seleccionado
error: el dispositivo /dev/hdb2 no es removible
error: no se puede ejecutar pmount"
Salvo que tenga que elegir otra de las opciones antes de entrar, son éstas: Start or install Ubuntu (con esa entré), Start Ubuntu in safe graphics mode, Check CD for defects, Memory test y Boot from first hard disk. También se puede apretar F6 para otras opciones y aparece la línea de comando, quizá ahí se pueda poner algo, pero creo que estoy entrando como root con la 1ra opción, el punto es que no sé porque no me deja montar esa partición.
Gracias

La opcion es la correcta. 
Como fue que intentaste montarlo? Desde linea de comando o por la GUI?

proba en una terminal:
```

mount /dev/hdb2
```

y tambien 
```
cat /etc/fstab
```
Esto es la forma en que esta intentando montar los discos. A ver que te dice.

---

### Post by konstantin88 on 2007-04-25
Poniendo en el terminal, sale
1) mount /dev/hdb2 
"mount can't find /dev/hdb2 in /etc/fstab or /etc/mtab"
2) cat /etc/fstab
"unionfs/unionfs rw o o
tmpfs/tmp tmpfs nosvid noved o o
/dev/hdb5 swap swap dafaults o o"

---

### Post by Al_maverick on 2007-04-25
> **konstantin88 said:**
> Poniendo en el terminal, sale
1) mount /dev/hdb2 
"mount can't find /dev/hdb2 in /etc/fstab or /etc/mtab"
2) cat /etc/fstab
"unionfs/unionfs rw o o
tmpfs/tmp tmpfs nosvid noved o o
/dev/hdb5 swap swap dafaults o o"


verifica si existe una carpeta /media/hdb2
si no existe, creala con:

```
cd /media
mkdir hdb2
```

y despues:

```
mount -t ext3 /dev/hdb2 /media/hdb2
```

Si te llega a dar error, pone el mensaje completo

---

### Post by tzulberti on 2007-04-25
> **konstantin88 said:**
> lavaramano:
soy muy nabo, pero no sé cómo configuro con que va a bootear; te digo lo que hice, apreté F2, entré a la pantalla de BIOS, pero ni idea en que opción meterme, tengo 11 y no sé cual es, te digo cuáles son por las dudas: Soyo Combo Setup, Standard Cmos Setup. Bios Features Setup, Chipset Features Setup, Power Management Setup, PNP/PCI Configuration, Load Setup Defaults, Integrated Peripherals, Supervisor Password, User Password y IDE HDD Auto Detection.
TZ:
cuando entro al grub y apreto "e", me salen estas opciones: root, kernel ./boot/vmlinuz-2.6.12-27-386.root=/dev/hdb2 ro quit splash, initrd ./boot/initrd.img-2.6.15-27-386, savedefault y boot. Booteando con esas, sigue todo igual. Apretando "c", sale la command-line, puse lo que vos me dijiste y me dice "error 27: unrecognized command", y vi que no está entre los comandos que se pueden usar, está sí initrd, pero ni idea que hacer con él. Quizá no te entendí y tendría que haber hecho otra cosa.
Gracias a los dos

Perdon, pasa que te di mal los datos...
En la linea donde que empieza con 
kernel .....
Ahi presiona "e"... borra "ro" y escribi rw... Al final del renglon escribi "init=/bin/bash"... Por ultimo, presiona Enter, y luego B...

Lo de la contraseña del root a mi me pasaba cada 3 meses... Cuando me la cambiaban, tambien me aparecia un nuevo usuario en el sistema (system, admin, Users and groups), asique fijate ese punto...

---

### Post by konstantin88 on 2007-04-26
Al_maverick
La carpeta no existía, la creé como vos me dijiste, y entré en la terminal "cat...". No salió ningún error, copió en la carpeta hdb2 lo que tenía la carpeta file system, pero sigue igual de inhabilitado para entrar a sudoers, decime qué querés que haga...

TZ
Hice lo que me dijiste, pero al bootearlo me aparece la línea de comando de root, qué hago?

Gracias

---

### Post by Al_maverick on 2007-04-26
> **konstantin88 said:**
> 
TZ
Hice lo que me dijiste, pero al bootearlo me aparece la línea de comando de root, qué hago?

Gracias

Si ya te aparece la linea de comando, entonces probaria utilizar el consejo de la otra thread, creando un usuario nuevo con permisos de admin. Con ese nuevo usuario ya podrias entrar a la GUI y arreglar el otro usuario y el root. (Rapidamente cambiales la contraseña a los dos)

> 
para crear el usuario y que no pierdas nada (eh permisos y gilada de sudo) lo haces con 'sudo adduser USUARIO admin'
el admin despues de USUARIO es el grupo donde va a ir a parar, el cual es ni mas ni menos que "admin", en ese grupo todos pueden sudear(?) (cualqueir cosa, 'sudo cat /etc/sudoers' y ahi van a ver, ******(?)).

ahora si ya agregaste al usuario y queres meterlo dentro del grupo "admin", hay que hacer lo siguiente.

Quote:
sudo nano /etc/group
ahi te va a aparecer eh.. justamente el archivo group que contiene a los usuarios dentro de los grupos.

si leiste al archivo /etc/sudoers vas a ver que todos los usuarios del grupo "admin" pueden sudear(?), entonces, agregas al usuario nuevo al grupo admin, el cual deberia quedarte masomenos asi:
Quote:
admin: x :666:usuario_actual,usuario_nuevo
notas:
* la x entre " : " es sin espacio, pero aca los tuve que poenr porque sino me clavaba un emoticon....
* el 666 es el gid del grupo "admin" y puede variar.
* lo que se hizo fue agregar al usuario nuevo, DESPUES de agregar una coma.


me explique como el ****, pero bueno.
cualquier cosa, man *problema* ... que no hace mal (?).

---

### Post by konstantin88 on 2007-04-26
Bueno, te cuento que pasa...
La línea de comando que aparece es 
> root@(none):/#
Si pongo 
> adduser gkp admin 
(gkp es el nombre de usuario que quiero crear)
Me sale 
> adduser: the user "gkp" does not exist 
Con
> cat /etc/sudoers 
Me sale 
> #This file MUST be edited with the 'visudo' command as root
#See the man page for details on how to edir sudoers file.
#Host alias specification
#User alias specification
#Cmnd alias specification
#Defaults
Defaults            !lecture, tty-tellets,!fqdm
#User privilege specification
root     ALL=(ALL) ALL
#Member of the admin group may gain root privilegies
Y con
> /etc/group 
Me sale 
> Permise denied


Estuve viendo en "man sudo_root" y dice, entre otras cosas:
> By  default, the password for the user "root" (the system administrator) is locked. This means you cannot login as root or use su. 
Instead, the installer will set up sudo to allow the user that is created during  install  to  run all administrative commands.
This  means  that  in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a password, it  needs  your  password, this means that a root password is not needed.
Lo que hace es pedirme justamente una password y cuando yo pongo la mía, como dice ahí que es la que te pide, me la rechaza.

En otra parte dice
> GOING BACK TO A TRADITIONAL ROOT ACCOUNT
       This is not recommended!
       To enable the root account (i.e. set a password) use:
           sudo passwd root
       Afterwards, edit /etc/sudoers and comment out the line
           %admin  ALL=(ALL) ALL
       to disable sudo access to members of the admin group.
Alguien lo pudo haber hecho? 

Gracias

---

### Post by Al_maverick on 2007-04-26
Por lo que puedo ver, el problema no esta en tu password, sino que por alguna razon sacaron al grupo admin del sudoers. Lo que quiere decir es que los usuarios del grupo admin no tienen permiso para ejecutar sudo, que es lo que te deja ejecutar tareas administrativas.

Me parece que en la ultima parte esta la indicacion del problema:

> En otra parte dice
GOING BACK TO A TRADITIONAL ROOT ACCOUNT
This is not recommended!
To enable the root account (i.e. set a password) use:
sudo passwd root
Afterwards, edit /etc/sudoers and comment out the line
%admin ALL=(ALL) ALL
to disable sudo access to members of the admin group.

En tu archivo sudoers aparece:
> #User privilege specification
root ALL=(ALL) ALL

podrias probar de comentar esa linea y agregar con:
> %admin ALL=(ALL) ALL

---

### Post by konstantin88 on 2007-04-26
Usando el command visudo y después edit, cambié en sudoers lo que me dijiste, guardé cambios y todavía no pasa nada.

Dos opciones tengo en mente:

1) quizá no te entendí bien, tengo que agregar en una nueva línea 
> %admin ALL=(ALL) ALL
O tengo que reemplazar el que ya está? me quedaría así
> #User privilege specification
root ALL=(ALL) ALL
%admin ALL=(ALL) ALL
Yo lo reemplacé, puede ser eso.

2) puede ser que me hayan sacado también de admin, entonces aunque habilite a ese grupo, como me sacaron, sigo sin poder realizar tareas administrativas. Tendría que entrar a /etc/gruop y ver si estoy en admin y si no estoy, usar el command que explican en la otra thread? ahora lo voy intentar hacer, me adelanto para que vayas respondiendo al 1) y a lo que te pregunto ahora: me explicás los command cat, man y nano? no entiendo demasiado las diferencias, cuando hay que usar cada uno (pesado era, no? jaja; el tema es que quiero saber para tener más libertad y no andar preguntando detalle por detalle, poder moverme solo un poco más)

Gracias

---

### Post by konstantin88 on 2007-04-26
Ya miré en group, sale un lista larga de la que solo veo el final. Entre otras cosas dice (konstantin es mi usuario)
> lpadmin:166:konstantin
konstantin: x :1000
admin: x :112
El primero significa que sí estoy en el grupo admin? si no es así, como uso el command de la otra thread?
> admin: x :666:usuario_actual,usuario_nuevo
Qué código pongo de los tres que aparecen en group? cuál es el usuario actual (el único para mi es konstantin, no hay uno actual y uno nuevo)?

De lo que te decía de los command, acá usé cat y me lo permitió, ya me voy a enterar que significa, jeje

Gracias

---

### Post by Al_maverick on 2007-04-26
"cat <archivo>" lista los contenidos del archivo
podes usar "cat <archivo> | more" para que te muestre de a una pantalla por vez
"man <comando>" te muestra el manual de algun comando o tema
"nano <archivo>" te permite editar un archivo
"sudo <comando>" te permite ejecutar tareas como root <--- este es el que no funciona

Lo que parece es que te sacaron del grupo admin, eso se resuelve editando el archivo group.

```
nano group
```

la linea de admin deberia quedar asi:
```
admin: x :112:konstantin
```

Espero que funcione! :)

---

### Post by konstantin88 on 2007-04-27
Vamos mejorando, ya me agregué a admin y aparecen las opciones de tareas administrativas en el menú aplicaciones y en sistema/administración;  igual no me deja entrar, me sigue dando como incorrecta mi contraseña. En qué archivo están las contraseñas?  

Estuve viendo por partes el archivo group y creo que sé quien es el otro usuario que hizo todo ésto
> haldaemon: x :108
Puede ser que sea él? Está junto con konstantin en varios grupos. Borrándolo de donde aparece ya lo eliminaría? 

Como se metió esta vez, se puede meter cuando quiera? igual dice en man sudo_root 
> * Every attacker trying to brute-force their way  into  your  box  will
         know  it has an account named root and will try that first. What they
         do not know is what the usernames of your other users are.
Entonces, por lo menos, entrar a mi sesión no puede teóricamente, lo que puede hacer es sacarme de admin, crearse un cuenta, bueno...lo que hizo.

Ya entendí los commands, re claro.

Gracias

---

### Post by konstantin88 on 2007-04-27
Entré a /etc/shadow y está también haldaemon, él tiene el mismo código que el root pero cambiando el * del root
> root: * : (código)
por
> haldaemon: ! : (mismo código)
konstantin, en cambio, tiene mil signos y números donde el root tiene * y haldaemon !, que tengo que hacer? ahí que iría? la contraseña? borro a haldaemon también de ahí?

---

### Post by Al_maverick on 2007-04-27
En cuanto a haldaemon, me parece que es un servicio, asi que en principio yo lo dejaria como esta. Despues que resolvamos esto podemos ver si tenes un package instalado con ese nombre.

Ahora, para cambiar la password de tu usuario, estando como root pone:

```
passwd konstantin
```

Ahi te va a pedir entrar la pwd nueva. Con eso creo que ya estarias. Despues intenta entrar con tu usuario, y ya deberias poder ejecutar las tareas administrativas. Tene en cuenta que cuando una tarea administrativa te pide el pwd, es el del usuario con el que estas logueado, no el de root.

---

### Post by jayflower on 2007-04-27
Viste necesitabas cambiar eso en shadow... yo te avise ! :p

---

### Post by Al_maverick on 2007-04-27
Yo no tocaria el user haldaemon por ahora. Por lo que vi, esta relacionado al DBUS de KDE.

[http://wiki.kde.org/tiki-index.php?page=DBUS+for+KDE+3.x]("D-BUS, HAL, KDE media:/ HOWTO")

---

### Post by konstantin88 on 2007-04-27
Sigo pensando que alguien hizo
> GOING BACK TO A TRADITIONAL ROOT ACCOUNT
       This is not recommended!
       To enable the root account (i.e. set a password) use:
           sudo passwd root
       Afterwards, edit /etc/sudoers and comment out the line
           %admin  ALL=(ALL) ALL
       to disable sudo access to members of the admin group.
Por eso, aunque cambié la contraseña de konstantin, sigue rechazándomela; para mi le pusieron al root una contraseña y por eso yo puedo entrar perfectamente a mi sesión pero a la hora de hacer tareas administrativas como root, me pide esa contraseña. En ese archivo no dice como volver al estado original ni tampoco en el vínculo que tiene al final.

---

### Post by Al_maverick on 2007-04-27
el problema ahora es que te deja loguear como konstantin, pero no te toma la contraseña cuando haces tareas administrativas, correcto?

Hace la siguiente prueba:
-entra como konstantin
-abri una terminal
-escribi:
```
sudo apt-get update
```
te va a pedir la contraseña. Pone la de konstantin y fijate si la acepta.

Si la acepta, el problema es otro. Si no, hay que seguir viendo por el lado del sudoers.

---

### Post by konstantin88 on 2007-04-28
No respondí antes porque tuve dos finales; ahora, después de haber aprobado, sigamos. 

Estuve probando y lo único que no me deja hacer es entrar en Usuarios y grupos, cuando intento entrar me dice que la contraseña es incorrecta. Pero ya puedo hacer todas las demás tareas administrativas, me pide la contraseña, pongo la de konstantin y me la acepta. Pude hacer lo que vos me dijiste también. 

Igual necesidad de entrar a Usuarios por ahora no tengo, pero ahí vería si hay un usuario más. Es medio raro, sabes qué puede ser?

Gracias

---

### Post by Al_maverick on 2007-04-29
Muy bien por los finales.

Me alegro que ya casi hayas resuelto el problema. La prueba te la hice hacer justamente porque podian ser dos cosas muy diferentes. Ya esta resuelto el tema de ejecutar tareas con sudo, pero a veces KDE se pira y tiene algunos problemas con el kdesu (similar al sudo, pero para kde).

Lo que voy a necesitar es el mensaje de error exacto que te da. A diferencia de Windows, en Linux los mensajes si significan algo. :D

---

### Post by konstantin88 on 2007-04-29
Ya puedo entrar a todoo; actualicé a Edgy y ahora me deja entrar a Usuarios y grupos, ahí aparece konstantin y root. No sé si tendría que aparecer root, además aparece con una contraseña.

Bueno, habiendo solucionado el problema:
1) muchísimas gracias Al_maverick por el aguante, tenés una paciencia increíble y muy buena onda que da gusto preguntarte y aprender cada día más, convenciéndome más aún de quedarme en Ubuntu. Gracias de vuelta
2) gracias a todos los que postearon: a Jayflower, a Tzualberti, a Lavaramano...
3) la verdad que me sorprendió este foro porque pensé que iba a tener el mismo resultado que cuando pregunté en Ubuntu-es (0 respuestas, se entiende, no?), pero, por suerte, acá hay gente que realmente quiere ayudar al resto. Los felicito, sigan así. 
4) obviamente los voy a seguir molestando con las preguntas y problemas que seguramente me van a ir surgiendo por ser todavía un novato en ésto, y espero algún día poder hacer lo que hacen ustedes, ya va llegar el día, jeje.

Graciaas

---

### Post by beuno on 2007-04-29
> **konstantin88 said:**
> 
4) obviamente los voy a seguir molestando con las preguntas y problemas que seguramente me van a ir surgiendo por ser todavía un novato en ésto, y espero algún día poder hacer lo que hacen ustedes, ya va llegar el día, jeje.

Y seguramente seran todas respondidas.
Bienvenido.

---

### Post by Al_maverick on 2007-04-30
> **konstantin88 said:**
> Ya puedo entrar a todoo; actualicé a Edgy y ahora me deja entrar a Usuarios y grupos, ahí aparece konstantin y root. No sé si tendría que aparecer root, además aparece con una contraseña.

Me alegro. Seguramente algun tema particular de esa funcion. Yo tuve algunos problemas similares hace mucho.
Por seguridad, se recomienda desactivarr el login de root, ahora que podes hacer tareas administrativas desde tu usuario.

> 
Bueno, habiendo solucionado el problema:
1) muchísimas gracias Al_maverick por el aguante, tenés una paciencia increíble y muy buena onda que da gusto preguntarte y aprender cada día más, convenciéndome más aún de quedarme en Ubuntu. Gracias de vuelta

jajaja de nada. A mi tambien me sirvio para aprender algunas cosas.

> 
3) la verdad que me sorprendió este foro porque pensé que iba a tener el mismo resultado que cuando pregunté en Ubuntu-es (0 respuestas, se entiende, no?), pero, por suerte, acá hay gente que realmente quiere ayudar al resto. Los felicito, sigan así. 
4) obviamente los voy a seguir molestando con las preguntas y problemas que seguramente me van a ir surgiendo por ser todavía un novato en ésto, y espero algún día poder hacer lo que hacen ustedes, ya va llegar el día, jeje.


Creo que todos empezamos igual. Y por suerte la buena onda de este foro (tanto el de argentina como el general) es contagiosa, asi que pasamos de preguntar a tratar de responder las preguntas de otros. :)

---

### Post by jayflower on 2007-04-30
Un gusto, esta vez pude tirar una pequeña data ya que una vez me pasó algo parecido con un equipo de la facultad y me volvi loca hasta encontrar como poder entrar. No podia entrar a ningun usuario. habian cambiado todos los passwords. Siempre es bueno tener algún live CD por ahi, y gente como Maverick que saben mucho, yo tambiñen aprendí. :)

---

