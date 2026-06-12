---
title: "Dudas varias sobre Xgl, beryl y chipset."
date: 2007-06-22
forum: Argentina Team
---

### Post by faktorqm on 2007-06-22
Hola a todos, escribo este post por que tengo algunas dudas, que no se si llegan a ser problemas, para ver si alguien me puede ayudar a resolverlas.
Tengo un mother MSI-K7N2G-L, con micro AMD Athlon XP 2600+, 512mb de RAM, 400 gb de disco, integrada viene una placa Nvidia Gforce 4, tengo ubuntu feisty fawn (7.04), chipset Nforce 2.
Bueno, el ubuntu me va perfecto, no tengo ningun problema, salvo por el driver de nvidia. Luego de varios intentos de instalacion, fallidos por cierto, logre instalar el bendito driver. El tema estaba en que a partir de la serie 97XX del driver no soportaba mas mi placa, que ubuntu me la reconoce como Gforce4 Integrated GPU.
Entonces instale la serie legacy de drivers (71XX), pero el X me tiraba una excepcion de memoria, y me sacaba la roja.  Luego instale la version 9631 y me decia que la version del modulo del kernel era la 7184 que no lo podia cargar, y me dejaba con la consola. Asi que me baje el "envy", que es un programa que te instala el driver de nvidia, y me compilo ese modulo que necesitaba y ahora tengo el driver de nvidia 9631 andando perfectamente. probe el glxgears y a pantalla completa me tira 90fps. No le puedo pedir mas a una integrada gforce4 asi que no me quejo.
La primera duda viene a que el glxgears se ve bien, pero me baje el quake I y el super maryo chronicles, para ver que tal andaba la aceleracion 3D, y resulta que el quake I la ventana se ve todo negro, y de vez en cuando cuando el demo dispara se ve una lucesita timida, y no pasa de ahi. El maryo feo ese ([www.getdeb.com](www.getdeb.com)) se ve todo amarillo, y lo mismo, no puedo hacer nada. 
Alguno se le ocurre alguna sugerencia? si quieren ver mi xorg.conf lo agrego al final del post.

La segunda duda es que instale beryl desde el synaptic, (fui a buscar, puse beryl e instale todo lo que vi), lo inicie, y anda, pero no se ven los iconos del escritorio y algunas ventanas! los efectos de minimizar/maximizar la pantalla se ven perfecto, y el cubo tb anda, las vistas en miniatura tb, otros efectos no conozco, ya los explorare. pero por ejemplo, el audacious (clon del winamp/xmms/beep media player) se
ve normal, pero abro un terminal y no se ve nada, o sea, yo tenia antes fondo negro, luego del beryl, tengo todo negro menos las barras. Bueno, sugerencias?

La tercera duda tiene que ver con mi chipset. Al ser nforce2 me parece (lo cual no significa nada) que no me lo reconoce bien, por que por ejemplo, no tengo instalada ninguna optimizacion en cuanto al manejador IDE, y no tengo las opciones hibernar/suspender, y en el guindos las tengo, o sea que tema de BIOS no es, por ke el APIC/ACPI anda bien. (o en teoria...), asi que me baje el driver del chipset de la pagina de nvidia, pero se me ocurrio antes mirar el readme, y menos mal, por ke pedia encarecidamente que no sea instalado en las distribuciones que no estaban listadas a continuacion, y ubuntu no aparecia ni cerca. asi ke no instale nada. como hago para suspender/hibernar el sistema? existira algun paquete de gestion de energia?

La cuarta duda es mas bien de ********** que de otra cosa, como saco el splash con el coso de nvidia? me rompe las ***** y no lo quiero. intente desactivarlo por xorg.conf pero no se fue :(

aca va el xorg.conf:

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dri"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	VendorName	"NVIDIA Corporation"
	BoardName	"GeForce4 MX Integrated GPU"
	BusID		"PCI:2:0:0"
	VideoRam	65535
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Samsung"
	ModelName      "SyncMaster 997MB"
	HorizSync       30.0 - 96.0
	VertRefresh     50.0 - 160.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Videocard0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option	       "NoLogo" "FALSE"
	Option	       "AllowGLXWithComposite" "TRUE"
	Option         "TVStandard" "PAL-NC"
	Option         "TVOutFormat" "AUTOSELECT"
	Option         "metamodes" "CRT: 1600x1200_70 +0+0"
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024"
	EndSubSection	
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Layout0"
	Screen		"Screen0"
	InputDevice	"Keyboard0"
	InputDevice	"Mouse0"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "DRI"
	Mode	0666
EndSection

el nvidia-settings sobre glx dice que esta todo ok, que estoy usando la version de nvidia y etcetc y me muestra las extensiones. 
Desde ya, perdonen por el post largo, mil gracias de antemano, y salu2 4 all!

---

### Post by wordgf on 2007-06-22
Para seguir esos problemas con Berly! debes seguir lo que dice este enlace::
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631)

y más precisamente debes agregar estasdos linieas en tu xorg.conf:, en Section "Device"



Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"

debes chequear que esto sea similar a 

DefaultDepth 24  

en la sección de screen

en cuanto a tu tarjeta de video...
pudes tener suerte siguiendo los pasos en ::: (tu nvidia es targeta integrada?)

[http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica](http://www.guia-ubuntu.org/index.php?title=Aceleraci%C3%B3n_gr%C3%A1fica)

o 

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28videocard%29](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia?highlight=%28videocard%29)

saludos.
:popcorn:

---

### Post by faktorqm on 2007-06-22
MUCHAS GRACIAS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 

ya solucione casi todo, ahora falta "tunear" un pokito para ke todo ande ""normal"". 
estuve leyendo lo que me pasaste, mas links que estaban ahi, asi que ya active xgl, puse beryl, se veia todo
negro, le puse algo de renderizacion por copia, que decia ahi que el driver de nvidia tenia un problema y que haciendo eso se solucionaba, y lo hace realmente, y bueno, ya no mas me falta resolver el tema de la hibernacion/suspension del sistema y no me van a tener ke soportar mas. GRACIAS OTRA VEZ!!!! :D:D:D

---

### Post by jpmorelli on 2007-06-23
Acá tenés varias respuestas oficiales también, incluso como sacar el logo de Nvidia.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by faktorqm on 2007-06-27
Hola, bueno muchas gracias por los links! me los lei todos, y ahora anda todo, pero (siempre hay un pero! :( ) ocurre lo siguiente. 
En aplicaciones -> herramientas del sistema -> nvidia settings me aparece el configurador de nvidia, y me dice que la memoria de la tarjeta de video es de 32MB. cuando la tengo a 64MB puesta. Despues de pasearme por varios lugares vi que cuando arranca, linux hace como una comprobacion del hardware que tiene y ahi me detecta la placa "bien" pero con 32mb. en el xorg.conf que puse arriba dice 65535, aunque parece que mucha bola a esto no le da. Ahora bien, vayamos a la practica, activo el beryl manager y anda, pero tiene un problema, algunas ventanas me las muestra en negro, y otras no, entonces a pasear otra vez guiado por el tio google y encontre en muchas paginas que si la placa de video se queda sin memoria fisica, no puede mostrar el contenido, por lo tanto es como que se da cuenta y muestra negro. La solucion propuesta era poner el modo de renderizacion (no recuerdo exactamente si es renderizacion) en "copiar". Este modo segun tengo entendido usa el frame buffer, que no se que es, pero que me muestra todas las ventanas, pero a una velocidad semejante a una tortuga. (lo unico que vi del frame buffer es cuando haces "dpkg-reconfigure xserver-xorg" que en un momento te pregunta si lo queres o no).

Resumiendo, anda super lento, bien, o rapido, pero mal. solucion? hacer que detecte bien los 64mb de la placa. como se hace eso? no tengo la menor idea. si a alguno le paso por favor tire un cable, yo estoy investigando de todas maneras.

Otra cosa al margen, el nvidia settings no modifica los cambios que le haces por que no tiene permisos para escribir el archivo xorg.conf. como se soluciona esto? yo quiero poner "gksudo" adelante del comando de ejecucion del acceso directo, pero no se como se hace, y encima, si tiene poder de sudo, no sera peligroso? :(

Otra: escribi "aptitude" en un terminal, y al final dice "Este apt no tiene poderes de super vaca". Escribi "apt-get" y al final dice "Este apt tiene poderes de super vaca".  WTF?!? :D

Muchas gracias a todos!! :D

---

### Post by clasificado on 2007-06-27
> y al final dice "Este apt tiene poderes de super vaca"

¡¡¡Tu pc es una granja!!! :D

Y si le anteponés el comando SUDO?
algo asi:
```
sudo apt-get update
```

¿sigue teniendo problemas con las vacas?

Clasificado

---

### Post by Hex_Mandos on 2007-06-27
Probá diciéndoles moo a las vacas (son vacas angloparlantes)

---

### Post by faktorqm on 2007-06-28
> ¡¡¡Tu pc es una granja!!!

Y si, el que la maneja es un animal............ cuac!

si, proba en un terminal 

```
apt-get
```

y te dice que tiene poderes de super vaca.

pone ahora (aclaracion, pongo fruta para que me muestre la ayuda, sino te lo abre)

```
aptitude qwqw
```

y te dice que no tiene poderes de super vaca.

y si pones 

```
sudo aptitude qwqw
```

te dice lo mismo. 

de lo nvidia y del nvidia-settings ni idea no? :(:(

---

