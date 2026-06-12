---
title: "How to: VMware en Feisty"
date: 2007-03-30
forum: Argentina Team
---

### Post by Tinchio on 2007-03-30
Si te paso como a mi que estabas usando edgy y te actualizaste a feisty y te diste cuenta de que el vmware no funcaba mas segurmanente revisaste muchos foros y tutos pero tal vez ninguno te andubo, al menos a mi me paso. Afortunadamente revisando [Ubuntu Forums ](http://www.ubuntuforums.org/)(hay que hacerle un monumento a ese foro) encontre la solucion, [aqui](http://www.ubuntuforums.org/showthread.php?t=338305&page=2&highlight=vmware+feisty). Y por si no entendes ingles aca te dejo una traduccion lo mas fiel posible.

Paso 1 (Instalar los modulos)

Aclaración: en mi caso instale el player porque ya tenia creadas las maquinas entonces uso el player que es mas liviano, pero es valido para cualquiera de los 2, lo digo porque los probe a ambos

Antes que nada tienen que instalar “vmware-server-kernel-modules” o “vmware-player-kernel-module” y “vmware-tools-kernel-modules” desde los repositorios de feisty.

Nota: Fijense que les instale la version correspondiente a su kernel. Por ejemplo yo esoty usando el kernel “2.6.20-13-generic” (para saber usen “uname -r”) entonces necesito descargar los modulos que digan algo con “…..2.6.20-13&#8243;

$ sudo apt-get install vmware-server-kernel-modules o sudo apt-get install vmware-player-kernel-modules
$ sudo apt-get install vmware-tools-kernel-modules

Paso 2 (Instalar VMware Server)

Luego van a tener que bajar el programa desde [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) o [http://www.vmware.com/download/player](http://www.vmware.com/download/player)
Probablemente el archivo se va a llamar VMware-server-1.0.X-XXXXXX.tar.gz. (o VMware-player-1.0.X-XXXXXX.tar.gz.)

Descompriman e instalen:
$ tar -xzf VMware-server-1.0.1-29996.tar.gz
$ cd vmware-server-distrib/
$ ./vmware-install.pl

Step 3 (Configuración)
Despues de eso van a ver que vmware_config.pl no anda, entonces hay que editarlo
$ sudo kedit /usr/bin/vmware_config.pl

(usen su editor preferido, el mio kedit)

y cambiar la función (busquen esta linea en el archivo y reemplazen TODO lo que encierran las llaves y dejen nada mas que “return ‘yes’;”):

sub build_module {
…
}

lo reemplazan por

sub build_module {
return ‘yes’;
}

Este paso lo que hace es decirle al script de configuracion que ignore la construccion de un nuevo modulo para el kernel ya que los instalamos antes desde los repositorios.

Paso 4 (Hacer que VMware Server o Player trabajen con los modulos de Feisty)
El script en init.d esta configurado para que cargue los modulos ya construidos no los que bajamos nosotros asi que vamos a tener que cambiar una linea en el archivo /etc/init.d/vmware

$ sudo kedit /etc/init.d/vmware

y buscan la siguiente linea
/sbin/insmod -s -f “/lib/modules/`uname -r`/misc/$1.o” || exit 1
y la reemplazan por
modprobe -s -f $1 || exit 1

Paso 5 (Borrar la bandera de no configurado)
Y luego borar el archivo “not_configured” y arrancar el demonio.

$ sudo rm /etc/vmware/not_configured

Paso 6 (Start the daemon)
$ sudo /etc/init.d/vmware restart

Y listo ya podemos ejecutar el server o el player segun hayamos instalado

vmplayer o vmware

---

### Post by nachotronics on 2007-05-14
Otra alternativa:

1- Agregar el repositorio comercial de Canonical haciendo
```
sudo gedit /etc/apt/sources.list
```
Y agregar la siguiente linea:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Entonces hacemos (gracias a Nemesis Teufel)
```
sudo apt-get update
```

2- Instalar:
```
sudo apt-get install vmware-server
```

---

### Post by lugonesjoaquin on 2007-05-14
¿VMware no era de pago o era no-libre o algo de eso?

Mucho mejor es VirtualBox, libre, gratuito, rapido, facil de instalar.

---

### Post by jpmorelli on 2007-05-14
La versión VMWare workstation es paga.
La versión VMWare server es gratuita, solo hay que registrarse para que te den el número de serie a tu nombre.
Ninguna versión de VMWare es Open source ( código abierto )

Sé que generalmente uno no tiene otra opción porque trabaja con imágenes pre-hechas pero recomiendo fervientemente el programa VirtualBox que funciona per-fec-to y tiene las misma opciones !!!
Super fácil de instalar y para mi gusto, más lindo.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by fetova on 2007-05-14
> **jmorelli said:**
> La versión VMWare workstation es paga.
La versión VMWare server es gratuita, solo hay que registrarse para que te den el número de serie a tu nombre.
Ninguna versión de VMWare es Open source ( código abierto )

Sé que generalmente uno no tiene otra opción porque trabaja con imágenes pre-hechas pero recomiendo fervientemente el programa VirtualBox que funciona per-fec-to y tiene las misma opciones !!!
Super fácil de instalar y para mi gusto, más lindo.
[http://www.virtualbox.org/]("http://www.virtualbox.org/")

ya he visto la edicion no open source, y esta muuuy bonito, aunque... como le hago para instalar la open source ? no le entiendo:) 

Gracias :D

---

### Post by nachotronics on 2007-05-14
Estoy de acuerdo, VirtualBox es mejor en muchas cosas, es mas rapido que VMWare y QEmu(incluso con aceleracion), por lo menos corriendo un xp que tengo para probar cosas. Pero VMWare es mas completo, podes emular maquinas virtuales Mac y tambien correr instalaciones que ya existen en el disco rigido, esto es, por ejemplo correr el xp que tengo en dualboot desde linux, cambiandole el perfil de hardware.

---

### Post by manzuk on 2007-05-14
Yo habia usado VMware; después dejé de necesitarlo. Pero ahora estaba en la duda si instalar de nuevo el VMware o probar con VirtualBox. Que me recomiendan? Tengo una Laptop relativamente nueva, pero no es ningun camion.
Y otra pregunta, Nachotronics, me podes explicar un poco más lo de correr el Xp que tenes en dual boot? Algo he leído por los foros de Ubuntu, pero nunca entendí del todo bien cómo hay que hacer y que problemas puede traer.

---

### Post by lugonesjoaquin on 2007-05-14
Proba con VirtualBox, si te sirve usalo sino vete por VMware.

Siempre es mejor usar software OpenSource :D

---

### Post by marianom on 2007-05-14
La solución al tema es sencilla: en la medida de nuestras posibilidades todos deberíamos optar por software libre. En tal caso, y hasta donde mi entendimiento alcanza en este tema en particular, la respuesta es que, de ser posible, le demos preferencia a QEMU - ú otros virtualizadores LGPL/GPL- por sobre los de código cerrado, por más gratis que sean.

---

### Post by nachotronics on 2007-05-15
**_[VirtualBox]("http://www.virtualbox.org/")_** es de código abierto, distribuido bajo licencia GNU/GPL yo lo uso para correr un xp virtual y anda mas rápido y mejor que QEMU(con KQEMU) y VMware. No lo he probado para Linux virtuales pero debe andar bien, no podes correr un SO Mac ni una instalación previa.


Este es el articulo original sobre correr una instalación de winxp ya instalada en el disco:
**_[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)_**
Los problemas que tuve fueron:

1- Que la carpeta /.vmware no era mía, sino del usuario root, entonces:
```
sudo chown usuario -hR ~/.vmware
```
(en usuario el nombre de usuario :) )

2- Con el vmware player en XGL/Beryl podes tener el clásico problema "*Xlib:  extensión "XFree86-VidModeExtension" missing on display ":1.0"*". o quizas el programa "anda" pero no ves nada. Solución: o instalas vmware server o inicias sesión normal, sin XGL, o lo corres así:
```
DISPLAY=:1 vmplayer
```
Lo cual es una solución a medias porque el administrador de ventanas no lo agarra y no podes cambiar de tamaño ni mover la ventana(este método es el mismo que se usa para correr googleearth bajo XGL)

3- En mi caso cuando instale Feisty ni me preguntó y metió GRUB en la partición de windows, entonces cuando corro la maquina virtual siempre se carga el GRUB, y a veces si no me doy cuenta rápido bootea el mismo linux que ya estoy usando, el único problema que esto me ha ocasionado es que una vez cuando inicie linux me dijo que habían errores de disco, me pedía que corra "fsck" y eso resolvió el problema. Igual yo recomendaría sacarle el timeout al GRUB por las dudas.

4- Cada vez que cambias de perfil de hardware tenés que revalidar windows, pero como me da fiaca dar vuelta la notebook para ver la licencia pongo que me avise mas adelante, en cualquier momento busco un crack para que no moleste mas. Leí en un foro que después de un determinado numero de revalidaciones deja de funcionar y tenés que llamar a microsoft para que te reactiven el numero de serie, no me consta.


De paso les recomiendo si van a correr windows xp virtuales que usen [**_"Suricata OS"_**]("http://www.phpbbcity.com/forum/viewtopic.php?t=230&mforum=suricataos") es un windows xp pro service pack 2, pero totalmente limado, apenas instalado ocupa 700MB y es mucho mas liviano que el normal, al principio tiene demasiados servicios desactivados pero agregando sólo los que necesitamos anda muy bien :wink:


Saludos

---

### Post by Nemesis Teufel on 2007-05-16
> **nachotronics said:**
> Otra alternativa:

1- Agregar el repositorio comercial de Canonical haciendo
```
sudo gedit /etc/apt/sources.list
```
Y agregar la siguiente linea:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

2- Instalar:
```
sudo apt-get install vmware-server
```

Antes de instalar hay que hacer un

```

sudo apt-get update

```

Asi encuentra el directorio

---

### Post by nachotronics on 2007-05-16
Gracias, ya lo corregi me habia olvidado

---

### Post by lugonesjoaquin on 2007-05-16
> De paso les recomiendo si van a correr windows xp virtuales que usen "Suricata OS" es un windows xp pro service pack 2, pero totalmente limado, apenas instalado ocupa 700MB y es mucho mas liviano que el normal, al principio tiene demasiados servicios desactivados pero agregando sólo los que necesitamos anda muy bien


Seamos legales che!
Muchos de aqui tambien no solo usamos Ubuntu por que es mejor seguro y todas esas cosas sino tambien por el hecho de que es gratuito.

Es bien sabido que es "distribucion" de Windows es ilegal..xD

---

### Post by Nemesis Teufel on 2007-05-17
> **lugonesjoaquin said:**
> Seamos legales che!
Muchos de aqui tambien no solo usamos Ubuntu por que es mejor seguro y todas esas cosas sino tambien por el hecho de que es gratuito.

Es bien sabido que es "distribucion" de Windows es ilegal..xD

que home user tiene win xp con licencia pagada?

---

### Post by nachotronics on 2007-05-17
Yo tengo win xp con licencia(me vino de clavo)
SuricataOS es ilegal si no tenés una licencia de un win xp pro, no trae ningún otro programa que haya que pagar. En el caso de que quieras estar 100% en regla solo le cambias el numero de llave por el tuyo y listo.

Que quede claro, nunca he usado software pirata ni lo voy a volver a hacer :)

---

### Post by lugonesjoaquin on 2007-05-17
> que home user tiene win xp con licencia pagada?

Muy pocos, pero no deja de ser pirateria por eso :D

> Yo tengo win xp con licencia(me vino de clavo)
SuricataOS es ilegal si no tenés una licencia de un win xp pro, no trae ningún otro programa que haya que pagar. En el caso de que quieras estar 100% en regla solo le cambias el numero de llave por el tuyo y listo.

Que quede claro, nunca he usado software pirata ni lo voy a volver a hacer 

;) 

Ta bien!;) Suerte che!

---

### Post by undiaperfecto on 2007-07-12
hoy instale vmware server, es la primera vez que me meto en esto de virtualizar.
la verdad esta bueno, pero todavia tengo mucho camino por recorrer, por ejemplo no se como hacer para que el xp virtualizado me detecte mi lectora de tarjetas de memoria o algunos otros dispositivos que una instalacion normal de xp si me reconoce.
incluso recien lei que se puede virtualizar una instalacion previa de winxp, por ejemplo la que tengo en hda1
vi que pusieron un tutorial, pero esta en ingles y la verdad no cazo una.
seria ideal poder usarlo de esta manera y ya no necesitaria mas bootear en xp sino que las pocas tareas que tengo ahi, hacerlas desde vmware. 
si alguien conoce un howto en español lo podria postear?

---

