---
title: "Nvidia GeForce 6200 256MB AGP"
date: 2007-08-28
forum: Argentina Team
---

### Post by MatoGroso on 2007-08-28
Hola linuxeros, de nuevo yo por aqui. En esta ocacion les cuento que me pasa: Me compré esta placa en cuestion (no es turbocache) y cuando quiero configurarla solo me detectó 1024 x 768 a 65 Mhz. Edité el xorg.conf en forma manual, agregando otras resoluciones, pero la tasa de refresco me queda en 50MHz en 1280 x 1024 y en 51MHz en 1280 x 960. Tengo un monitor Philips 17" CRT 107S6 y deberia llegar a estas resoluciones. Segun lo que Philips dice en el manual lo soporta (La función Autoscan cubre frecuencias horizontales de hasta 71 KHz y ofrece una resolución máxima de 1280 x 1024 con visualización sin parpadeo de 1024 x 768 a frecuencias de hasta 89 Hz) . Ademas de esto, ahora cuando arranco Ubuntu se queda congelado en la pantalla de inicio, antes de pedirme el nombre de usuario y password, para poder entrar lo unico que "encontré" fué reiniciar X con ctrl + alt + backspace.

Las preguntas son:

1) Como hago para cambiar la taza de refresco?
2) Alguien sabe por que se queda congelada la pantalla de inicio?

Les paso en detalle mi pc:

AMD Athlon 1700+, 512MB RAM, mother PCChips M810LR, GeForce 6200 256MB ddr.

Muchas gracias

 
Mato

PD: Este thread está posteado originalmente en Ubuntu.es.

---

### Post by por100pre1 on 2007-08-28
Intentaste reconfigurar xorg.conf mirando las opciones que te puede ofrecer?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_respaldo
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Y al terminar:

```
startx
```

---

### Post by por100pre1 on 2007-08-28
Si no te funciona dejalo como estaba:

```
sudo cp /etc/X11/xorg.conf_respaldo /etc/X11/xorg.conf
```

---

### Post by faktorqm on 2007-08-29
[http://ubuntuforums.org/showthread.php?t=536855](http://ubuntuforums.org/showthread.php?t=536855)

---

### Post by MatoGroso on 2007-08-29
> **por100pre1 said:**
> Intentaste reconfigurar xorg.conf mirando las opciones que te puede ofrecer?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_respaldo
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Y al terminar:

```
startx
```



si, ya lo intenté pero siempre me pasa lo mismo.

Te detallo mi xorg.conf
Muchas gracias por la ayuda!

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	Identifier	"GeForce6200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"GeForce6200"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by ariel on 2007-08-29
yo estoy usando la misma placa con el driver propietario 9755 (los mas nuevos tienen problemas con compiz-fusion). todo anda joya incluso compiz-fusion. 

refresh rate puede cambiarse usando el utilitario de nvidia:  System Tools > NVIDIA X Server Settings 

(se instala junto con el driver, creo).



> **MatoGroso said:**
> Hola linuxeros, de nuevo yo por aqui. En esta ocacion les cuento que me pasa: Me compré esta placa en cuestion (no es turbocache) y cuando quiero configurarla solo me detectó 1024 x 768 a 65 Mhz. Edité el xorg.conf en forma manual, agregando otras resoluciones, pero la tasa de refresco me queda en 50MHz en 1280 x 1024 y en 51MHz en 1280 x 960. Tengo un monitor Philips 17" CRT 107S6 y deberia llegar a estas resoluciones. Segun lo que Philips dice en el manual lo soporta (La función Autoscan cubre frecuencias horizontales de hasta 71 KHz y ofrece una resolución máxima de 1280 x 1024 con visualización sin parpadeo de 1024 x 768 a frecuencias de hasta 89 Hz) . Ademas de esto, ahora cuando arranco Ubuntu se queda congelado en la pantalla de inicio, antes de pedirme el nombre de usuario y password, para poder entrar lo unico que "encontré" fué reiniciar X con ctrl + alt + backspace.

Las preguntas son:

1) Como hago para cambiar la taza de refresco?
2) Alguien sabe por que se queda congelada la pantalla de inicio?

Les paso en detalle mi pc:

AMD Athlon 1700+, 512MB RAM, mother PCChips M810LR, GeForce 6200 256MB ddr.

Muchas gracias

 
Mato

PD: Este thread está posteado originalmente en Ubuntu.es.

---

### Post by MatoGroso on 2007-08-30
Muchas gracias por la ayuda! Igual ya lo solucioné!!
Lo que hice fue volver a instalar la version 6.06 y me reconoció la placa enseugida, sin ningun problema a 1280 x 1024 50Hz. 
No probé la aceleracion grafica, pero supongo que debe andar bien. Hoy a la mañana llegué tarde al trabajo por hacer la instalacion en casa asi que no pude probar nada :P 

Gracias de nuevo!

[mato]

---

