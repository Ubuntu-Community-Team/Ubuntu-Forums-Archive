---
title: "[SOLVED] Dudas antes de instalar"
date: 2008-04-15
forum: Argentina Team
---

### Post by El_canaya on 2008-04-15
hola, quiero empezar a usar Linux... el tema es q no me moleta usar windows sino que quiero aprender y como estuve leyendo parece ser muchisimo mejor que windows...

la compu q tengo es esta:
Procesador Dual Core AMD Athlon 64 x2, 2100 MHz
Memoria 512 MB DDR2 SDRAM

ya me baje el CD de Ubunte 7.10 y lo corri una vez al livecd, pero me iba muy lento (debe ser por la lectora) bah, a cada rato se ponia a leer y entonces iba lento :P asi q iba a instalarlo para q corra mas rapido... aparte quise conectarme a internet pero me aparecia la pagina de q no estaba conectado :S no se si tendre q configurar algo... (tengo cablemodem) y el adaptador de red es Encore 10/100Mbps Fast Ethernet PCI Adapter

Tengo un Disco rigido con dos particiones:
C: 93.7 Gb (40 Gb usados) donde esta windows, los programas, musica, fotos, etc...
D: 140 Gb (8 bg ocupados) lo unico q hay es la pelicula Sicko y Supercool

como tendria q hacer la particion esa de linux?? cuando use linux voy a poder usar los archivos q estan en el C??

Gracias :P

---

### Post by PatoDB on 2008-04-15
Bienvenido al mundo de Linux amigo!!


Mira, yo tengo:

Un disco de 80 Gb

Un procesador Intel(R) Celeron(R) CPU 2.26GHz

512 de Ram

Y me anda a la perfeccion!!!

Las particiones mias son asi:

10 Gb en una Particion para Windows (ntfs)

10 GB en otra Particion para Ubuntu 7.10 (ext3)

1 Gb en otra Particion para memoria swap

y Los 49 Gb restantes, en una particion **ntfs**. De este modo puedo ver los archivos que estan ahi, tanto en Windows como en Ubuntu, y es donde tengo toda la musica, series, archivos de la facu, imagentes y demas cosas...


Espero que pueda darte una idea...

Exitos!!!

---

### Post by El_canaya on 2008-04-15
pero puedo hacer la particion por ejemplo:

la particion de 93.7 Gb donde esta windows, los programas, musica, fotos, etc... q es ntfs dejarla como esta
y la otra (la de 140 gb) q tambien es ntfs dividirla en 10 gb para Ubuntu 7.10 (ext3) y 1 Gb en otra Particion para memoria swap y aparte dejar 129 Gb en otra particion mas?

y otra cosa: si "subparticiono" la de 140 Gb tengo q borrar lo q tiene?

---

### Post by sajnox on 2008-04-15
Basicamente podes hacer todo lo que decis, aunque dijiste tanto que me maree.

Mi consejo (por el momento) move todos tus archivos (musica, fotos, etc) a la particion de 140GB y en la que tenes instalado windows le das un poco de espacio a Ubuntu.

Dentro del Live CD de ubuntu tenes un editor de particiones muy simple de usar y parecido al partition magic. Ojo, siempre hace backup de los datos, con las particiones esta todo bien hasta que no esta todo bien y ahi te empezas a agarrar la cabeza

Leete la guia ubuntu ([www.guia-ubuntu.org](www.guia-ubuntu.org)) que es una muy buena manera de aprender de las instalaciones.

Para saber si el modem va andar bien arranca el live cd y fijate si tenes internet, lo que haces con el live cd lo tenes en la instalacion

Tomate tu tiempo para hacerte amigo de Linux y escribinos con las dudas que tengas

---

### Post by El_canaya on 2008-04-16
> Mi consejo (por el momento) move todos tus archivos (musica, fotos, etc) a la particion de 140GB y en la que tenes instalado windows le das un poco de espacio a Ubuntu.

eso no lo puedo hacer porq complicaria a las otras personas q usan la compu q no cazan una de computacion, porq el mas minimo cambio ya los pierde :S

por eso queria particional el de 140 para q para los otros usuarios de la pc no noten ninguna diferencia...
se puede hacer lo q puse antes: la de 140 gb, q es ntfs, dividirla en 10 gb para Ubuntu 7.10 (ext3) y 1 Gb en otra Particion para memoria swap y aparte dejar 129 Gb en otra particion mas??

> Para saber si el modem va andar bien arranca el live cd y fijate si tenes internet, lo que haces con el live cd lo tenes en la instalacion 

ese es el problema :P cuando arranque desde el live cd no me funciono internet... :s

---

### Post by oktubrer on 2008-04-16
Yo tengo ubuntu instalado en una particion de 9 gb, 1gb aparte para la swap, y el resto en ntfs.
Como poder, podés.  No es lo "óptimo" pero funciona y bien.
Con respecto a la conexión, fijate que hay un thread abierto en el foro al respecto, si es por adsl leelo y comentanos las dudas.

---

### Post by PatoDB on 2008-04-16
> **El_canaya said:**
> eso no lo puedo hacer porq complicaria a las otras personas q usan la compu q no cazan una de computacion, porq el mas minimo cambio ya los pierde :S

por eso queria particional el de 140 para q para los otros usuarios de la pc no noten ninguna diferencia...
se puede hacer lo q puse antes: la de 140 gb, q es ntfs, dividirla en 10 gb para Ubuntu 7.10 (ext3) y 1 Gb en otra Particion para memoria swap y aparte dejar 129 Gb en otra particion mas??


Supuestamente si se puede, lo que te recomendo sajnox es que, antes de particionar, o tocar algo del disco de 140 gb, saques todo momentaneamente, por las dudas. Moves todo al otro Disco a una carpeta que se llame "BackUp" o "Disco de 140".

Una vez que el disco de 140 esta vacio, recien ahi particionalo, separa el espacio que le vallas a dar a Ubuntu. (si tenes 140 te recomiendo que le des 15 gb o 20 gb), separas 1gb para swap y el resto lo pones en ntfs.

Una vez que tengas el disco particionado, volves a Windows y volves a copiar todos los datos que antes tenias en el disco de 140. Para evitar asi, posibles perdidas.



Fijate que tal te va y comenta!!!!


Exitos!!

---

### Post by El_canaya on 2008-04-16
ok, ahora lo instalo... mientra otra duda :P

si por X razon no me gusta o no me adapto a linux... se puede eliminar la particion y volver todo como estaba antes??

---

### Post by facundocorradini on 2008-04-16
> ok, ahora lo instalo... mientra otra duda :P

si por X razon no me gusta o no me adapto a linux... se puede eliminar la particion y volver todo como estaba antes?? 

Ajá. Simplemente desde windows borrás las particiones de linux y redimensionas la de win. 

Luego si querés sacar el grub, ponés el disco de XP en modo recuperación y reinstala el gestor de arranque de windows. 


Te recomiendo instales Ubuntu 8.04. Mañana sale la RC y la semana que viene la versión final.  Pero la RC ya es una versión más que estable. 


Por otra parte, no te apures a juzgar... puede que tome un tiempo entender las ventajas reales de usar gnu/linux.  (más si -dios no quiera- llegás a tener algún problemita de compatibilidad o algo así)

Pero con buena voluntad, y preguntando en el foro, todo se arrregla

saludos y éxito con la instalación!

---

### Post by El_canaya on 2008-04-16
> Luego si querés sacar el grub, ponés el disco de XP en modo recuperación y reinstala el gestor de arranque de windows. 

ahi tengo un gran poblema gran!!, no tengo el cd de win xp :S

y otra cosa...  el grub se puede configurar q si en 2 o 3 segundos no elijo q SO usar abra directamente Windows??

---

### Post by sajnox on 2008-04-16
Se puede hacer, y ademas es demasiado facil hacerlo. Tenes un programa grafico para hacerlo

---

### Post by El_canaya on 2008-04-16
como se hace??

y vuelvo a preguntar: si por X razon no me gusta o no me adapto a linux... como saco el grub si no tengo el disco de Win XP??

gracias :P

Edit: ah, ya pude hacer andar internet :P

---

### Post by faktorqm on 2008-04-16
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by El_canaya on 2008-04-16
gracias :P

en español no hay nada?? :(

---

### Post by faktorqm on 2008-04-16
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
[http://www.google.com.ar/](http://www.google.com.ar/)

---

### Post by oktubrer on 2008-04-16
si no tenés el cd del xp, un diskette de inicio de windows 98 (por decir alguno) también te sirve.
Inicias con el diskette, te carga las herramientas en una unidad virtual, y desde ahí ejecutas fdisk /mbr
Eso te restaura el master boot record de windows

---

### Post by El_canaya on 2008-04-17
hola, estaba haciendo la particion del disco desde el cd live de ubunto  asi ya lo instalaba y no estoy seguro como hacerlo.

porq me aparecen las 2 particiones de windows, entonces elimine la ntfs de 140 gb y en ese espacio libre puse:

Device----------Type...Moint point ............ format?.......size
- /dev/hda1...ntfc..../media/hda1...........no.............100660
- /dev/hda2...ext3.../.............................si..............10240
- /dev/hda5...swap..(nada)....................si...............1024

y el resto queria dejarlo todo para Windows en ntfs, pero no se puede con este programa :S cual tendria q poner?? Fat32??

conviene hacer otra particion ext3 de 10 gb para /home y el resto si dejarlo para windows??

y por ultimo... cual de las particiones tienen q ser logicas y cuales primarias??

gracias a todos por la ayuda q me estan brindando... espero poder devolver ese favor a la comunidad :P

---

### Post by sajnox on 2008-04-17
Para poner a Windows que arranque por default, en mi opnion la forma mas facil es usar el administrador de arranque (no viene instalado asi que tenes que agregarlo), los programas los podes instalar en forma grafica o desde una terminal (al principio parece mas facil en forma grafica y despues te acostumbras a la terminal)

En forma grafica:

Sistema/Administracion/Gestor de Paquetes Synaptic

Elegis buscar y escribis startupmanager y lo marcas para instalar

Desde una terminal

sudo apt-get install startupmanager

En ambos casos el programa lo encontras en Sistema/Administracion/Administrador de Arranque

Desde ahi podes elegir muchas opciones para el Grub, no solo cual es el sistema que bootea

Saludos

---

### Post by El_canaya on 2008-04-18
> En forma grafica:

Sistema/Administracion/Gestor de Paquetes Synaptic

Elegis buscar y escribis startupmanager y lo marcas para instalar


bueno, al fin instale el Ubunto :p

cuando quise hacer eso q me decis, no me aparece nada en la busqueda :S

y lo de la terminal no se como se usa... creo q se entra con alt+ctrl+f1 no?? y dps como se sale?

gracias :P

---

### Post by oktubrer on 2008-04-18
> **El_canaya said:**
> y lo de la terminal no se como se usa... creo q se entra con alt+ctrl+f1 no?? y dps como se sale?
gracias :P

Más simple, en el menú Aplicaciones / Accesorios / Terminal

---

### Post by angelsguitar on 2008-04-18
deleted

---

### Post by El_canaya on 2008-04-18
y para salir??

ya la reinicie a la compu 4 veces :S

edit: ya ta :P Alt+Ctrl+F7

---

### Post by El_canaya on 2008-04-18
> 
Quote:
y otra cosa... el grub se puede configurar q si en 2 o 3 segundos no elijo q SO usar abra directamente Windows??
Es posible configurar estas opciones en un archivo de configuracion del GRUB o utilizando una interface grafica que viene para eso (yo prefiero editar el archivo directamente). Un dato: cuando instales Ubuntu, por defecto te dara 10 segundos , luego de los cuales iniciara la particion de Ubuntu automaticamente

y como hago para q espere esos 10 seg y depues cargue windows en vez de Ubuntu?

---

### Post by sajnox on 2008-04-18
Lo podes hacer con el programa que te comente, si no lo encontraste

Abri una terminal/consola y escribis

```
sudo apt-get install startupmanager

```
Si te dice que no lo encuentra, en la misma terminal escribi

```
cat /etc/apt/sources.list
```

Copia y pega el resultado aca (para copiar desde la terminal tenes que pintar y copiar o usar ctrl + shift + c y con ctrl + v pegas en el firefox

---

### Post by El_canaya on 2008-04-18
> Copia y pega el resultado aca (para copiar desde la terminal tenes que pintar y copiar o usar ctrl + shift + c y con ctrl + v pegas en el firefox

con ctrl + shift + c no hace nada :S

y no se a que te referis con pintar y copiar :P

con el "impr pant" no se si sera eso, pero igual no se donde pegar la imagen :S

---

### Post by sajnox on 2008-04-18
A pintar me refiero a que con el mouse selecciones el texto.

---

### Post by El_canaya on 2008-04-19
hola, ya le estoy agarrando un poco la mano al Ubuntu :P no entendia como copiar eso de cat /etc/apt/sources.list porq lo estaba haciendo desde el alt+ctrl+f1 y no desde la terminal...

igual, inevestigando en otro foro me recomendaron hacer esto:

> Prueba: Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories.. dale click para que acepte todo.

entonces a partir de ahi se puso a bajar 212 actualizaciones y tambien me permitio bajar el startupmanager :P

este es el informe del sources.list:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

tiene algun problema o tengo q configutar algo??

por ahora no tengo mas dudas, pero en cualquier momento vuelvo a bombardearlos con nuevas preguntas :P

Por ultimo, quiero agradecer a todo uds que me estuvieron ayudando a aprender a usar este SO y tambien quiero agradecer la paciencia que tuvieron para conmigo.

Saludos desde Rosario... el_canaya

---

### Post by faktorqm on 2008-04-19
No lo hace por que no es ctrl + shift + c sino es shift + ctrl + c.
En el menu Editar de la terminal te dice las teclas....

---

