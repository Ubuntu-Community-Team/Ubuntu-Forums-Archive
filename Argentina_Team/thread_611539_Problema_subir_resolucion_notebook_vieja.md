---
title: "Problema subir resolucion notebook vieja"
date: 2007-11-13
forum: Argentina Team
---

### Post by katon on 2007-11-13
Hola tengo un problema con my laptop un poco vieja que tiene Xubuntu, no puedo subir la resolucion a mas de 800x600 cuando en realidad antes esta maquina tenia winxp y se veia 1024x768
Que se puede hacer ya cabie el DEPTH en la parte de display a 16 como decia en otros post pero nada...
pense que algo pasa con el driver...nose que hacer ya que por ejemplo hay programas como el DC-connect que no puedo ver lo que dice en la parte inferior de la pantalla al ser tan grande.

la placa es  ATI Technologies Inc Rage Mobility P/M AGP 2x 
y la laptop es Ibm Celeron 500 thinkpad 
este es el xorg.conf:
gracias desde ya!

Section "Device"
Identifier "ATI Technologies Inc Rage Mobility P/M AGP 2x"
Driver "ati"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Rage Mobility P/M AGP 2x"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by katon on 2007-11-13
alguien no me daria una mano?  muchas graciasss

---

### Post by sajnox on 2007-11-13
Shalom Javer!!!

A ver si esto sirve, yo nunca lo use pero recuerdo que a varios les sirvio.

1)  Backup del xorg

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back
```

2) edita el xorg.conf y borrale todas las resoluciones que no sean 1024 x 768, para editar el xorg.conf

```
 sudo gedit /etc/X11/xorg.conf
```

lo guardas y reincias las X con "control + alt + backspace"

Lo peor que te puede pasar es que no funcione y no levante la grafica, si no lo hace en una consola escribis

```
 sudo mv /etc/X11/xorg.back /etc/X11/xorg.conf
```

Y reinicias la parte grafica nuevamente

Contanos si funciona

Saludos

---

### Post by katon on 2007-11-13
no che la verdad no funca eso
nose si sera porque no tengo instalada la aceleracion 3d render 
o algo del monitor
gracias desde ya

---

### Post by Hernán-Amaya on 2007-11-13
te paso mi parte del xorg donde esta configurado el monitor y la placa por ahí te ayuda a configurar el tuyo.

```

Section "Monitor"
	Identifier	"Monitor genérico"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
        modeline  "1024x768@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Monitor genérico"
	Option		"AIGLX"	"true"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection


```

suerte!

---

### Post by katon on 2007-11-15
Deberia ver la opcion de 1024*768 en el menu de resoluciones en display? porque yo hasta ahora solo veo como maximo 800 * 600

---

