---
title: "Configurar 6200 - Compiz-Fussion"
date: 2007-10-19
forum: Argentina Team
---

### Post by DavidRnR on 2007-10-19
Bueno estoy en el laburo, ya tengo internet en la pc con UBuntu 7.10. Recien instalado, esta pelado el SO.

Tengo una Geforce 6200 y cuando le doy de habilitar la aceleracion por hardware me tira el error siguiente:

The software source for package
nvidia-glx-new
is not enabled

Quiero habilitar el Compiz-Fussion.

AH! otra pregunta, como bajo los codec de audio y video?

PD: EL que me ayude que diga los comando y eso, porque no se nada de nada en Ubuntu/linux.

---

### Post by facundocorradini on 2007-10-19
Lo bueno de Ubuntu, a mi entender, es justamente que lo podés usar sin saber nada de Linux, ni usar comandos.

Para instalar los códecs simplemente tratá de reproducir el archivo, te va a salir un asistente que descarga e instala automáticamente los códecs necesarios. 

Para habilitar el driver, usá el gestor de controladores restringuidos.

slds

---

### Post by Mauro22 on 2007-10-19
el nvidia glx new da ese error. dale una y otra vez habilitar hasta que te lo baje!

:popcorn:

---

### Post by Hernán-Amaya on 2007-10-19
fijate de instalarte el driver propietario, esto lo podés hacer desde el gestor de de controladores restringidos. Lo encontrás en:

Sistema/Adiministración/Gestor de controladores restringidos 

y ahora proba de habilitar los efectos

---

### Post by DavidRnR on 2007-10-19
No pasa nada...el reproductor Totem me pide que instale el paquete Gstreamer pero no me deja...intenta y actualiza la lista...pero no instlaa.

En cuanto a lo de la 6200 no hace nada...sigue con el mismo error. Hice lo de lo restringido.

---

### Post by Mauro22 on 2007-10-19
abri la consola y pone

```
sudo apt-get install nvidia-glx
```

pone tu password.


cuando lo baje, Vas a activar driver propietario y (segun como me lo hizo a mi) te va a desinstalar el que bajaste e instalar el nvidia-glx-new

---

### Post by GGsalas on 2007-10-19
A mi me sucedió que luego de que se instaló Ubuntu, reinicio y :

[B][FONT="System"]Error al iniciar el servidor X.

etc/gdm/failsafeXServer:line 47: [: demasiados argumentos

Warning: Could not retrive EDID because get-edit is not installed[/FONT][/B]

luego de aceptar esto...
[FONT="System"][B]
El servidor X está deshabilitado. Reinicie GDM cuando esté configurado correctamente.[/B][/FONT]

Luego de esto aparece la pantalla negra sin nada.

Claro que puedo instalar de nuevo, pero voy a querer configurar el driver de video ¿como evito que me suceda lo mismo, o como lo soluciono?

Gracias.

---

### Post by steve_ignorant on 2007-10-19
sabes que a mi me acaba de pasar lo mismo.... pero ami ya me venia pasando desde que baje el beryl con los drivers de Nvidia.... me parece que hay algo que hace que entre en conflicto... 


[http://george2002.obolog.com/p/instalar-controladores-nvidia-en-ubuntu-kubuntu-xubuntu-26821]("http://george2002.obolog.com/p/instalar-controladores-nvidia-en-ubuntu-kubuntu-xubuntu-26821")



en esta pagina que puse ahi arrba hay un how to para instalar los drivers de Nvidia en el ubuntu, a mi no se porq no me entro... pero bueno sera cuestion de que pruebes. por el momento voy a instalar el 7.10 lo bajo por torrent y listo... borro todo y se acabo...

---

### Post by DavidRnR on 2007-10-19
> **Mauro22 said:**
> abri la consola y pone

```
sudo apt-get install nvidia-glx
```

pone tu password.


cuando lo baje, Vas a activar driver propietario y (segun como me lo hizo a mi) te va a desinstalar el que bajaste e instalar el nvidia-glx-new


Gracias ante todo pero no me andubo.

Puse el comando y me dice que el paquete no esta disponible.

Toy sin el pan y sin la torta :(

---

### Post by Hernán-Amaya on 2007-10-19
proba de cambiando los repositorios, entra al synaptic y después entrá al menú configuración/repositorios, después en la solapa software ubuntu en donde dice descargar desde  elegí otro y después dale a Seleccionar el mejor servidor

espero que te sirva! contanos como te fue

---

### Post by DavidRnR on 2007-10-19
> **Hernán-Amaya said:**
> proba de cambiando los repositorios, entra al synaptic y después entrá al menú configuración/repositorios, después en la solapa software ubuntu en donde dice descargar desde  elegí otro y después dale a Seleccionar el mejor servidor

espero que te sirva! contanos como te fue

Muchas gracias...cambie el servidor...intente otra vez bajar el nvidia, o actualizar los codec y no anda.

Estonya me esta impcientando :(:(:(:(:(:(:(

---

### Post by ariel on 2007-10-21
yo tengo una placa 6200 tb. y estoy usando 

nvidia-glx-new

se instalo solito al activar desktop-effects.

Se me hace que por algun motivo tu maquina no esta pudiendo conectarse con los repositorios.

proba: sudo apt-get update

deberia conectarse y bajarse las listas de packages, si todo esta bien.


> **DavidRnR said:**
> Gracias ante todo pero no me andubo.

Puse el comando y me dice que el paquete no esta disponible.

Toy sin el pan y sin la torta :(

---

### Post by DavidRnR on 2007-10-22
Bien, muchas gracias por las respuestas. Ya tengo andando los mp3 y los videos.

Me falta el tema del compiz. Baje el compiz manager....ahora me desaparecio el gestor de hardware bloqueado.

Cuando bootea el Ubuntu puedo elegir entre 3 tipos...la version 14...15...y 16..porque? como hago para dejar una sola?

Pego el xconf.org

[PHP]# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Driver		"nvidia"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"E40-3"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"E40-3"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection[/PHP]

---

### Post by Hei Ku on 2007-10-22
lo que paso es que instalaste actualizaciones de kernel. En principio, no te preocupes por eso. Pero si realmente queres sacarlos, tendrias que desinstalar las versiones viejas (poco recomendable porque puede haber algo con las dependencias)
Si lo que te molesta es que aparezcan las opciones en el booteo, podes editar el menu.lst. Busca esto en los foros y vas a encontrar ayuda mas puntual.

---

### Post by DavidRnR on 2007-10-23
Bueno gracias a todos por las respuestas.

Les cuento que formatie...instale todo de cero con internet..se actualizo todo solo y salio andando todo solo. Salvo eso de que hay que hay que activar a la placa en hardware bloqueado. Despues Nada Mas!

Algunas cosas voy entendiendo jaja.

Saludos! :lolflag:

---

### Post by Cripton on 2007-10-23
hola!!

tuve tu mismo problema al instalar el 7.10 de cero en amd64,

lo que tenés que hacer es ir a Sistema\Administración\Orígenes del software

y habilitar donde dice controladores privativos,

poné cerrar y reintenta en gestor de controladores restringidos

y WALAA

espero haber sido de utilidad, me debés una

---

