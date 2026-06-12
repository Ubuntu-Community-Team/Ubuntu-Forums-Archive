---
title: "Mejorar performance de nvidia fx5200"
date: 2007-04-08
forum: Argentina Team
---

### Post by martin_legion on 2007-04-08
Hola gente. Recién descubro el grupo de Argentina así que aprovecho para dejarles mi pregunta en mi primera lengua.

Tengo configurada mi placa de video, una nvidia fx5200 (128M), funcionando correctamente, con aceleración y todo, pero me da la impresión de que el rendimiento no es óptimo.
Cuando miro algunas películas, la imagen se traba un poco, como si la velocidad de refresco no fuera suficiente, especialmente en las escenas en donde la cámara va girando de a poco o cuando hay muchos cambios en la imagen.
La aceleración está activada, eso es seguro, porque cuando recién instalé el ubuntu tuve que configurar la aceleración, y hasta entonces tuve la oportunidad de usarla sin aceleración y la diferencia es enorme.

¿Alguien se anima a darme algunos consejos sobre qué puedo cambiar/agregar/sacar de mi xorg.conf?
Si alguien tiene alguna idea, le estaré más que agradecido.

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Driver		"nvidia"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Option		"TVStandard" "PAL-NC"
	Option		"TVOutFormat" "SVIDEO"
	Option		"RenderAccel" "True"
	Option		"ConnectedMonitor" "CRT,TV"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Noc"
	HorizSync 	30-65
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Noc"
	DefaultDepth	24
	Option 		"AddARGBGLXVisuals" "True"
	Option		"TwinView" "on"
	Option		"TwinViewOrientation" "Clone"
	Option		"MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
	Option		"SecondMonitorHorizSync" "30 - 96.0"
	Option		"SeconfMonitorVertRefresh" "50 - 120"
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by gabrielsaman on 2007-04-09
zbzxcv

---

### Post by marianom on 2007-04-09
gabrielsaman, ¿podrías clarificar tu mensaje?

---

### Post by martin_legion on 2007-04-10
Gracias gabrielsaman!! Ahora anda mucho... ah no, anda igual. ¿Alguien más?

---

### Post by felipelerena on 2007-04-10
gabrielsaman, sos un guru...
martin... esa pregunta es como ir al supermercado, mostrarles una foto de la heladera y decir "que me falta?"
consejo: lee la guia de "como ayudarte a vos mismo" que esta en [www.uluga.com.ar](www.uluga.com.ar)

---

### Post by martin_legion on 2007-04-10
Casualmente tengo un problemita con la heladera...¿en qué sección del foro me conviene preguntar?

---

### Post by MeduZa on 2007-04-10
bueno te lo lei y dentro de todo, me parece q tiene todo lo que necesita para ir rapido :P

yo le agregue ademas estas cosas:

> Section "Device"
	Identifier	"NVIDIA Corporation G71 [GeForce 7900 GS]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "NvAGP" "2"
 	VendorName 	"NVIDIA Corporation"
	BoardName 	"NVIDIA GeForce 7900 GS"
	Option 		"NoLogo" "1"
	Option 		"RenderAccel" "1"
	Option 		"CursorShadow" "1"
	Option 		"Coolbits" "1"
	Option 		"ConnectedMonitor" "dfp, TV"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"NoPowerConnectorCheck"
	Option 		"TwinView" "1"
	Option 		"TwinViewOrientation" "RightOf"
	Option 		"TVStandard" "NTSC-M"
	Option 		"TVOutFormat" "SVIDEO"
	Option          "TripleBuffer" "true"
	Option 		"Metamodes" "1024x768,1024x768; 800x600,800x600; 800x600,NULL; 1024x768,NULL"
	Option 		"SecondMonitorHorizSync" "31-60"
	Option 		"SecondMonitorVertRefresh" "56-60"
	# Option "NoTwinViewXineramaInfo"
# Enable 32-bit ARGB GLX Visuals
	Option		"AddARGBGLXVisuals" "True"

EndSection

el coolbits calculo que si lo apagas te tendria q dar mas velocidad pero generaria mas calor el gpu, otra q podes hacer es overclockiar el gpu desde el panel de control de nvidia

una seccion para que el monitor no se me apague a los 10 o 20 mins solo:
> 
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

---

### Post by jpmorelli on 2007-04-11
El problema que describís me suena a un problema muy típico de Win y no se refiere a la placa de video sino a la habilitación del DMA para la unidad de CD. Me parece que tendrías que buscar por ese lado, no me acuerdo el comando exacto para ver y/o habilitar el DMA en la unidad pero buscando un poco seguro que lo podés encontrar enseguida.
Suerte !

---

### Post by Tinchio on 2007-04-11
> **jmorelli said:**
> El problema que describís me suena a un problema muy típico de Win y no se refiere a la placa de video sino a la habilitación del DMA para la unidad de CD. Me parece que tendrías que buscar por ese lado, no me acuerdo el comando exacto para ver y/o habilitar el DMA en la unidad pero buscando un poco seguro que lo podés encontrar enseguida.
Suerte !


sudo hdparm <dispositivo>   

ese? :KS

---

### Post by jpmorelli on 2007-04-11
> **Tinchio said:**
> sudo hdparm <dispositivo>   

ese? :KS

ese mismo !!! Gracias Tinchio ! Probá con eso martin_legion.

---

### Post by martin_legion on 2007-04-12
> **jmorelli said:**
> El problema que describís me suena a un problema muy típico de Win y no se refiere a la placa de video sino a la habilitación del DMA para la unidad de CD. Me parece que tendrías que buscar por ese lado, no me acuerdo el comando exacto para ver y/o habilitar el DMA en la unidad pero buscando un poco seguro que lo podés encontrar enseguida.
Suerte !

En realidad las películas las estoy viendo en linux y desde el rígido, así que la lectura de CD (si bien también puede ser un factor a la hora de ver dvds) no creo que sea el factor que yo estaba buscando arreglar. Igualmente voy a hacer lo del hdparm. Recuerdo haberlo hecho en otras ocasiones que tuve linux instalado.
Y gracias por las demás opciones para el xorg,conf voy a darles una mirada a ver si cambia algo.

Gracias, aunque me quedo esperando que me digan qué puedo hacer con la heladera...

---

