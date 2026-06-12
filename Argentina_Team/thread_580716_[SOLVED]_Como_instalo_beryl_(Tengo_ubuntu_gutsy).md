---
title: "[SOLVED] Como instalo beryl?? (Tengo ubuntu gutsy)"
date: 2007-10-19
forum: Argentina Team
---

### Post by sebadigri on 2007-10-19
Hola gente recien me acabo de dar cuenta que hay un foro argento por aca jaja...

Buen hace 1 semana toy en esto del linux no soy muy pro pero ya se "algo"...
Recien instale la 7.10 y recien acabo de instalar (creo q bien) los drivers de nvidia.com.

Tengo un par de dudas....

1) por q en el gutsy ya no tengo el cubo que tenia en festy...ahora es todo 2D cuando pasas por los Desktops...(Ya active los effects igual)
2) Como me andaba re mal...el repositorie de Argentina (al igual q casi todos los otros) puse buscar el mejor y me encontro uno  brazuca que me baja a 300kb/s osea re bien...pero igual mas haya de eso como hago para volver a tener el de argentina xq no me aparece el pais argentina en la lista (ese tmb me iba a full speed)...
3) Como instalo beryl? quiero instalarlo y ver q onda...

Saludos y gracias

---

### Post by tzulberti on 2007-10-19
> **sebadigri said:**
> Hola gente recien me acabo de dar cuenta que hay un foro argento por aca jaja...

Buen hace 1 semana toy en esto del linux no soy muy pro pero ya se "algo"...
Recien instale la 7.10 y recien acabo de instalar (creo q bien) los drivers de nvidia.com.

Tengo un par de dudas....

1) por q en el gutsy ya no tengo el cubo que tenia en festy...ahora es todo 2D cuando pasas por los Desktops...(Ya active los effects igual) 

Si instalastes los drivers bajandotelos de la pagina de nvidia entonces vamos mal.... Pero como todo tiene solucion: anda a System -> Administration -> Resitricted Drivers. Te va a aparecer una ventana para tildar el driver de nvidia. Tildala, y automaticamente te va a bajar el driver de nvidia y configurar para que uses compiz-fussion (despues de que reinicies la pc). 

Sobre las otras dos preguntas no se que constestarte... A beryl lo podes intentar de instalar usando:
sudo apt-get install beryl 
o
sudo apt-get install compiz-fussion (no me acuerdo si va con una s o con dos).

Como ahora estoy en debian, no te puedo ayudar pero mañana reinicio y veo como es el tema de beryl.

---

### Post by sebadigri on 2007-10-19
Okk una pregunta, por q decis q esta mal instalar los drivers de nvidia??
Pasa q tmb tengo una placa media complicada es 1 placa fisica con 2 gpu q igual ya es vieja para colmo ( q ovbiamente uso 1 solo xq no hay sli aca.. creo  o por lo menos q funcione bien )

A mi me andan perfecto....y les meti el xorg que hice con el "NVIDIA X Server Settings" y me lo tomo lo mas bien....onda con el nvidia-glx nose ni como poner q me use 75hertz..
En lo q me mejoro esto ultimo que meti es q antes el driver se ponia a buscar si era PCI:5:0:0 o PCI:4:0:0 el q daba video y el monitor me parpadeaba un par de veces y ahora ya no lo hace con este xorg q le meti....

En la 7.04 los drivers nvidia de ubuntu me funcionaban mal....no me booteaba y la unica chance q tenia era usar "vesa" o los originales de nvidia...(deshabilitando el restricted y blabla asi me los cargaba...) 

Ahora en la 7.10 me funcionan los de ubuntu pero igual preferi poner los de nvidia por el tema del open gl y todo eso (q igual ni lo uso)...

---

### Post by sebadigri on 2007-10-19
Ah ya voy entendiendo el Compizz fussion serian los efectos 3D del Ubuntu no?

Ahi me fije y ya lo tengo instalado ahora le meti para boludear a ver q es el "emerald"

Entonces q seria el "beryl"..? Lo que se parece a la Gadget Bar del w. vista?


EDIT: 
El emerald me tira esto:
-------
sebastian@sebastian-ubuntu:~$ sudo emerald
[sudo] password for sebastian:
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
sebastian@sebastian-ubuntu:~$ 
-------

Bueno fue mañana de ultima instalo de nuevo el driver nvidia-glx...decime como se hace bien para borrar el de nvidia y no mandarme cagadas jaja...y ya q estamos q tengo q hacer para q el driver ese me funcione a 75hertz y no a 60

saludos

---

### Post by tzulberti on 2007-10-19
> **sebadigri said:**
> Ah ya voy entendiendo el Compizz fussion serian los efectos 3D del Ubuntu no?

Ahi me fije y ya lo tengo instalado ahora le meti para boludear a ver q es el "emerald"

Entonces q seria el "beryl"..? Lo que se parece a la Gadget Bar del w. vista?

Hasta hace un par de meses (creo que 4) existian dos proyectos que agregaban efectos 3d al escritorio: beryl y compiz. Sin embargo, se unieron para crear lo que actualmente se llama compizz-fussion.

Por lo tanto no deberia de existir mas beryl y solo deberia de el compiz-fussion. El emeral te permite manejar que extensiones (algo similar a las extensiones del firefox) son las que queres usar, entre otras tantas cosas.

> **sebadigri said:**
> 
Okk una pregunta, por q decis q esta mal instalar los drivers de nvidia??
Pasa q tmb tengo una placa media complicada es 1 placa fisica con 2 gpu q igual ya es vieja para colmo ( q ovbiamente uso 1 solo xq no hay sli aca.. creo o por lo menos q funcione bien )

A mi me andan perfecto....y les meti el xorg que hice con el "NVIDIA X Server Settings" y me lo tomo lo mas bien....onda con el nvidia-glx nose ni como poner q me use 75hertz..
En lo q me mejoro esto ultimo que meti es q antes el driver se ponia a buscar si era PCI:5:0:0 o PCI:4:0:0 el q daba video y el monitor me parpadeaba un par de veces y ahora ya no lo hace con este xorg q le meti....

En la 7.04 los drivers nvidia de ubuntu me funcionaban mal....no me booteaba y la unica chance q tenia era usar "vesa" o los originales de nvidia...(deshabilitando el restricted y blabla asi me los cargaba...)

Ahora en la 7.10 me funcionan los de ubuntu pero igual preferi poner los de nvidia por el tema del open gl y todo eso (q igual ni lo uso)...


Si vas a usar los efectos 3d de gutsy, entonces vas a necesitar la aceleracion OpenGL. 
Cuando instalastes los drivers hicistes un "sudo dpkg-reconfigure xserver-xorg" o tocastes el archivo /etc/X11/xorg.conf a mano?

Fijate que en la parte de la placa de video decime que es lo que estas usando. 
Seria algo similar a lo de abajo.
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
EndSection

Si dice nvidia en vez de "vesa", entonces ya estas usando el driver propiertario de nvidia, y no habria ningun problema. Sino, es que solo instalastes el driver y no lo configurastes (si este es el caso, te recomiendo usar Restricted Drivers).

En cualquier caso, para activar los efectos de escritorio no tenes mas que ir a System -> Preferences -> Deskttop Effects (no me acuerdo si se llamaba asi la opcion). Mañana me fijo cual era la opcion en cuestion.

---

### Post by sebadigri on 2007-10-19
Lo q hice yo fue instalarlo con nvidia y dps ir a Apps --> System tools --> Nvidia

Y ahi le meti...q use 75 hertz para facilitar las cosas y como no podia xq no tenia acceso al xorg.conf el programa agarre y lo meti en cualquier ubicacion el "save" y dps hice "sudo cp" de esa q me grabo el programa este de nvidia al actual xorg y ahora el xorg lo tengo asi y funciona bien q digamos...
--------------------------------------------------------
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
    BusID          "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; nvidia-auto-select +0+0"
EndSection
------------------------------------

Los Effects me tan andando bien yo lo q queria es ver q onda el beryl pero si es el Compiz Fusion entonces ya lo tengo instalado (creo) y tendria q ver como configurarlo...

Segun esto q acabo de encontrar el OpenGL me esta funcionando...:


sebastian@sebastian-ubuntu:~$ glxinfo | egrep 'OpenGL|direct'
direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions:

---

### Post by sebadigri on 2007-10-19
YA estaaa tube q poner ALT F2 compiz --replace (aunque esta creo q fue al ****)

y la mas importante bajarme en el packet manager el compizconfig-settingmanager o algo similar! y dps encontre en el menu todo para configurar!

jaja esta terrible esto...

---

### Post by leo_rockway on 2007-10-19
> **sebadigri said:**
> 

Entonces q seria el "beryl"..? Lo que se parece a la Gadget Bar del w. vista?

yo habia escrito algo reee lindo... pero los malditos tubos que conforman la internets se llenaron y no llego el mensaje...

erase una vez compiz que iba todo contento por ahi... hasta que un dia... todo mal! a compiz le dio doble personalidad y para colmo sus personalidades se llevaban para el mismisimo demonio.

entonces fue cuando nacio beryl, fork de compiz.

por algun periodo compiz y beryl coexistieron como dos entidades separadas, hasta que un dia dijeron "esto no da para mas" y se volvieron a unir y formaron compiz fusion.

Fin :lolflag:

ps: esperemos que esta vez llegue y no muera en el limbo de la internet

---

### Post by sebadigri on 2007-10-19
jaja esta re bueno lo q si hay 1000 cosas q no se para q ****** estan jaja tengo q ponerme a leer q es cada efecto...
Quiero desactivar el q si haces doble click en la barra de arriba se contrae la ventana y se esconde en la barrita..por q a mi me gusta q cuando hagas doble click maximize y unmaximize

---

