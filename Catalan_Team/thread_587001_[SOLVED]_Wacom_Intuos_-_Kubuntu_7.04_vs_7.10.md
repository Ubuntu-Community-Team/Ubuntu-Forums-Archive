---
title: "[SOLVED] Wacom Intuos - Kubuntu 7.04 vs 7.10"
date: 2007-10-22
forum: Catalan Team
---

### Post by rajoar on 2007-10-22
A veure si algú en sap alguna cosa:
En l'Ubuntu i Kubuntu 7.04 la Tauleta Wacom em funcionava fantásticament.... Casi, casi a la perfeccció. En canvi amb les versions 7.10 té alguns problemes... De funcionar funciona, però el punter va d'una forma erràtica i moltes vegades no va cap on vols que vagi...
Creieu que hauria de buscar algún driver nou? O és que és necessari un kernel nou adequat al de les versions 7.10?...
No sé ben bé que és el que puc fer per solucionar-ho...

---

### Post by papapep on 2007-10-22
No tinc idea de tabletes gràfiques, però si ens dius el model exacte (crec que d'Intuos ni ha de diferents) i ens enganxes el contingut del /etc/X11/xorg.conf tindrem algun lloc per on començar a pensar.

---

### Post by rajoar on 2007-10-23
papapep,
Gràcies pel teu interès...
La tauleta gràfica es un Wacom Intuos 2.
El contingut del meu /etc/X11/xorg.conf és:

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"DELL 1800FP"
	Vendorname	"Dell"
	Modelname	"Dell 1800FP (Digital)"
	Horizsync	30.0-70.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"DELL 1800FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x960@60"	"800x600@72"	"1280x1024@60"	"800x600@56"	"1400x1050@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by papapep on 2007-10-23
Sense més coneixement de causa, cap al final del fitxer posa:
> # **Uncomment if you have a wacom tablet**
[COLOR="Red"](Descomentar si teniu una tableta wacom)[/COLOR]
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"

Aquesta pot ser una possible causa del problema.

Hauries de treure el caràcter # de les tres línies que comencen per InputDevice...

Un cop ho hagis fet, reinicia el servidor gràfic amb Ctrl+Alt+Backspace i a veure què tal.

---

### Post by rajoar on 2007-10-23
papapep,
Que passarell que he estat !!!
Efectivament, descomentant les tres línies tot funciona a la perfeccció..., apareixen i es poden configurar els dipositius d'entrada estesos (Gimp, Inskape, etc).
Moltes gràcies...

---

### Post by papapep on 2007-10-23
Me'n alegro de que hagi estat tan fàcil :-D

---

### Post by CarlesOriol on 2007-10-23
> **rajoar said:**
> papapep,
Que passarell que he estat !!!
Efectivament, descomentant les tres línies tot funciona a la perfeccció..., apareixen i es poden configurar els dipositius d'entrada estesos (Gimp, Inskape, etc).
Moltes gràcies...

A l'inkscape recorda d'activar específicament el dispositiu a File > dispositius d'entrada.Sino sols funcionarà com un ratolí xulo.

Un cop ho hagis fet tindràs a més del posicionament absolut (i no sols la diferencia de posició) control de pressió que és genial en eines com la ploma de dibuix cal·ligràfic.

---

### Post by xabierurra on 2007-11-04
Hola, una pregunta:
cuando descomento las 3 líneas de la última parte de /etc/X11/xorg.conf se me cuelga el ordenador y tengo que volver a comentarlas para que se cargue de nuevo el servidor gráfico. 
Sabéis por qué puede ser?
Gracies

Xabi

---

### Post by papapep on 2007-11-04
Xabieurra, _hauries de crear un fil nou_ i enganxar-hi el teu xorg.conf

---

### Post by xabierurra on 2007-11-04
Ok, [_ya ho he fet_]("http://ubuntuforums.org/showthread.php?p=3705761#post3705761"). A veure si teniu alguna idea. 

Xabi

---

