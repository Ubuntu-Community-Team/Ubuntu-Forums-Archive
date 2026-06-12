---
title: "Problemas con gutsy"
date: 2007-10-24
forum: Argentina Team
---

### Post by rigatuso on 2007-10-24
Upgradie mi el ubuntu 7.04 a 7.10 y tengo un problema que cuando inicia la maquina no me da el login o sea se ve girar el puntero del mouse y cuando quiere poner la pantalla del login se abre y se cierra y sigue girando el puntero del mouse intente de desinstalar el gdm y volverlo a instalar pero no funciona
, lo que hice fue stopear el gdm y desde una consola poner startx , me levanto pero me anda lento.Si me pueden ayudar se los agradeceria muchisimo.

Muchas gracias.
Saludos

Rigatuso

---

### Post by Hernán-Amaya on 2007-10-24
pude ser un problema de video, fijate el xorg.conf.
pero primero probá con:

```

sudo dpkg-reconfigure xserver-xorg

```

si no te anda con eso decinos que placa de video tenes?
Y si podes postear el xorg.conf que esta en la carpeta /etc/X11/

suerte!

---

### Post by rigatuso on 2007-10-25
lo de la placa funciona con eso ya puedo bajar la resolucion sin problemas pero sigue sin darme el login cuando inicia, tengo que bajar el gdm y correr el startx les paso el xorg que tengo confiugrado ahora.

Section "Files"
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
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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
EndSection


muchas gracias por su ayuda.

rigatuso.

---

