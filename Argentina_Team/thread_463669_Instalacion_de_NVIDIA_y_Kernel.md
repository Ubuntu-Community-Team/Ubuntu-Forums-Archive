---
title: "Instalacion de NVIDIA y Kernel"
date: 2007-06-03
forum: Argentina Team
---

### Post by ricardomanu on 2007-06-03
Hola, me a surgido un problema al instalar los driver de una tarjeta grafica NVIDIA 5200, dichos driver es la version 1.0-9755, ya que al haber  instalado no inica el modo grafico, me indica lo siguiente.
Error: API MISMATCH: THE NVIDIA KERNEL MODULE HAS THE VERSION 1.0-7184, BUT THIS X MODULE HAS THE VERSION 1.0-9755. PLEASE MAKE SURE THAT THE KERNEL.
MODULE AND ALL NVIDIA DRIVER COMPONENTS HAVE THE SAME VERSION.
Por lo que he desintalado todo lo que tiene que ver con NVIDIA como ser:" NVIDIA-KERNEL-COMMON", "LINUX-RESTRICTE-MODULES-2.6.20-15-GENERIC".
Al desintalar lo mensionado me baja de internet una version nueva del KERNEL 2.6.20-16-generic.
Y al iniciar da varias opciones de kernel a elegir la 2.6.20-15-generic y la 2.6.20-16-generic.
Esto es normal, con cual hay que inicia.
Al desintalar lo mensionado arriba funcionaron muy bien lo driver nuevos 1.0-9755, pero iniciando con el KERNEL 2.6.20.15-GENERIC.


Gracias.

---

### Post by elrengo79 on 2007-06-04
para iniciar con el kernel 2.6.20-16-generic usando el driver nvidia tenes que instalar el paquete LINUX-RESTRICTED-MODULES-2.6.20-16-GENERIC

---

### Post by ricardomanu on 2007-06-04
Si instalo LINUX-RESTRICTED-MODULES-2.6.20-16-GENERIC, no me funcionan los driver oficiales de nvidia 9755, ya que hay un conflicto con los driver que incluye UBUNTU 7.04, siendo que no he instalado nada manualmente, solo instalo los oficiales.
Tiene alguna solucion ya que cuando inicio la X con los driver oficiales (9755), el "GESTOR DE CONTROLADORES RESTRINGIDOS", me dice que necesita instalar el paquete,mensionado arriba para que funcione, si lo instalo no tengo grafica, que hago.



Gracias.

---

### Post by elrengo79 on 2007-06-04
hace un search nvidia en synaptic y postea que paquetes tenes instalados, asegurate que el xorg este cargando el driver nvidia y no el nv, fijate que en la seccion modulos del xorg no este cargando dri, que este similar a esta:
Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

tenes que tener instalado
linux-restricted-modules-2.6.20-15-generic
linux-restricted-modules-2.6.20-16-generic
nvidia-glx-new
nvidia-kernel-common
con esos paquetes yo lo tengo funcionando con mi geforce 5200 , asegurate de tener esos paquetes y que sean la ultima version.

---

### Post by netuntu on 2007-06-04
De donde puedo bajar el linux-restricted-modules-2.6.20-16-generic!!

Gracias

---

### Post by fetova on 2007-06-04
> **netuntu said:**
> De donde puedo bajar el linux-restricted-modules-2.6.20-16-generic!!

Gracias

Podes escribir en una terminal:

```
sudo aptitude install linux-restricted-modules-2.6.20-16-generic
```

te pide tu contraseña, se la das y le pones que si :)

Saludos

---

### Post by netuntu on 2007-06-04
Eso ya lo habia hecho y me sale lo siguiente:

sudo aptitude install linux-restricted-modules-2.6.20-16-genericPassword:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.20-16-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by guillermolisi on 2007-06-05
Hola Netuntu

Yo los tengo instalados y estan en un repositorio security de Feisty.

Te adjunto un par de screenshots para que veas que dice Synaptic.

Saludos

---

### Post by spg76 on 2007-06-05
> **netuntu said:**
> Eso ya lo habia hecho y me sale lo siguiente:

sudo aptitude install linux-restricted-modules-2.6.20-16-genericPassword:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linux-restricted-modules-2.6.20-16-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

¿Estás corriendo Feisty? Porque ese paquete está solo disponible para Feisty.
Podes ver los detalles del paquete (e incluso descargarlo) en [http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-generic)

---

### Post by netuntu on 2007-06-05
Si estoy corriendo Feisty, lo unico es que lo actualice de Edgy a Feisty.

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

De Antemano Gracias por sus respuestas.

---

### Post by ricardomanu on 2007-06-05
Lo he solucionado deshabilitando al driver NV con el comando, SUDO NANO ETC/DEFAULT/LINUX-RESTRICTED-MODULES-COMMON. Buscando la linea DISABLE_MODULES= "NV" y agregando "NV", sin desintalar los "LINUX-RESTRICTE-MODULES-2.6.20-15-GENERIC". El el XORG.CONF tengo todo bien en "Section "Module".
Y buscando en el SYNAPTIC, el unico que no tengo instalado es el linux-restricted-modules-2.6.20-16-generic, nvidia-glx-new, este ultimo esta en la version 1.0.9755+2.6.20.5-16.28, y el nvidia-kernel-common 20051028+1ubuntu7, este si esta instalado, tengo que instalar lo que no estas instaland.
El KERNEL version 2.6.20-16-generic, lo he desintalado.

---

### Post by netuntu on 2007-06-05
Ya quedo muchachos!

Segui algunas intrucciones de las que me dieron en sus posts y ya tengo trabajando mi NVIDIA, con TwinView activado, en lo general tuve que bajar el linux-restricted-modules-2.6.20-16-386_2.6.20.5-16.28_i386 e instalarlo (el generic no jalo con mi kernel),  lo baje de esta liga que me recomendaron:  [http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-386]("http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-386")

Luego instale los paquetes mas nuevos del nvidia con el synaptic:

nvidia-glx-new
nvidia-kernel-common

y utilice mi xorg.conf que ya tenia y listo.


Gracias por su ayuda!!!

Saludos desde Mexico

P.D. Adjunto una pantalla para que vean el grandioso resultado.

---

### Post by rumli on 2007-06-06
Sorry, I don't know the language, but if someone else does, maybe they can translate:

From your error message, you need to do the following.
```

sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable

```

nvidia kernel modue has version 1.0-7184 ==> nvidia-glx-legacy
nvidia kernel modue has version 1.0-9631 ==> nvidia-glx
nvidia kernel modue has version 1.0-9755 ==> nvidia-glx-new

---

### Post by el_itur on 2007-06-07
> **ricardomanu said:**
> Si instalo LINUX-RESTRICTED-MODULES-2.6.20-16-GENERIC, no me funcionan los driver oficiales de nvidia 9755, ya que hay un conflicto con los driver que incluye UBUNTU 7.04, siendo que no he instalado nada manualmente, solo instalo los oficiales.
Tiene alguna solucion ya que cuando inicio la X con los driver oficiales (9755), el "GESTOR DE CONTROLADORES RESTRINGIDOS", me dice que necesita instalar el paquete,mensionado arriba para que funcione, si lo instalo no tengo grafica, que hago.



Gracias.
Esto es mentira.
No hay ningún conflicto con los drives propietarios de nvidia y ubuntu 7.04. El único detalle es que el GESTOR DE CONTROLADORES RESTRINGIDOS no te los dá como una opción. La manera de instalarlo (teniendo en cuenta que tengas instalado el metapaquete linux (linux a secas o linux-generic no me acuerdo)) es buscar en el synaptic nvidia-glx-new, ese es un driver 9755 y anda joya. Yo recomiendo que si no instalaste nunca un driver propietario primero bajes el que te sugiere el gestor de controladores ya que él se va a encargar de configurarte el X.org como para dejarlo chiche bonbon, después bajás el nvidia-glx-new y todo de perlas, no le des pelota a cualquier mensaje del gestor de controladores, ya que este no va a manejar nada más.

se está trabajando en que el gestor de controladores te pueda dar más opciones (como esta de diferentes versiones de un driver), pero va a salir con suerte para gutsy.

---

### Post by ariel on 2007-06-10
Problema tipico :)

Por ejemplo, pasa siempre despues de un kernel update si instalaste a mano los drivers mas nuevos de nvidia (como mencionas 9755, asumo hiciste eso, por linea de comandos o usando alguna ayuda grafica como Envy).

Lo que sigue asume que el package linux-headers-generic esta instalado.

Mi receta para instalar los drivers de nvidia (a mano) y/o recompilar el modulo despues de un cambio de kernel es la siguiente:


Baja el driver directo desde nvidia a tu home directory: [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)
(por ejemplo, bajate el 9755; el archivo se llama NVIDIA-Linux-x86-1.0-9755-pkg1.run )

Abri un terminal y dale al archivo que bajo permiso de ejecucion 
```
chmod +x NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Cerra todas tus aplicaciones y abri una terminal virtual: Ctrl-Alt-F2; loggeate con tu user; y tira este comando:
```
sudo /etc/init.d/gdm stop
```
Con esto, se termina el proceso del servidor X (y todo el entorno grafico). Es necesario para poder compilar y cargar el nuevo modulo de nvidia

En la misma terminal, anda hasta el directorio en donde habias bajado el driver (tu home, por ejemplo), y ejecuta el instalador de Nvidia como root:
```
cd ~
sudo ./NVIDIA-Linux-x86-1.0-9755-pkg1.run

```

El instalador de Nvidia te pide que aceptes la licencia, y despues de eso aceptale todos los defaults: va a recompilar el modulo de Nvidia para que funcione con el nuevo kernel. Ojo: la opcion por default es no dejarle al instalador que modifique tu xorg.conf, lo cual esta perfecto, porque tu xorg.conf no tiene porque cambiar (ya estabas usando el driver de nvidia antes y te funcionaba).

Por ultimo, volve a cargar el servidor X y el entorno grafico:
```
sudo /etc/init.d/gdm start
```


Suerte!

ps. esto hay que hacerlo cada vez que Ubuntu actualiza el kernel. El motivo es que el driver que estas usando (9755) no es el oficial que se instala via Synaptics y el repositorio ubuntu oficial (que es un 96xx muy viejito). Si usas el driver propietario "oficial" de ubuntu entonces todo este proceso no hace falta, el nuevo modulo se instala junto con el kernel actualizado.

---

