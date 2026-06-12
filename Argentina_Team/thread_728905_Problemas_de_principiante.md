---
title: "Problemas de principiante"
date: 2008-03-19
forum: Argentina Team
---

### Post by MaReaDo^ on 2008-03-19
Yo hara 1 año o dos usaba Ubuntu, pero lo use por 2 meses nomas y tuve que volver a Windows por un problema con un soft, como ya no necesito ese Soft, decidi probar de nuevo y experimentar. Me encontre con varios problemas que no tuve antes o que ya no recordaba como resolver.
Estuve buscando en este foro, en otros y en google; y pude resolver varios problemas pero de esos surgieron otros o algunos otros no los pude resolver.
Espero que ninguno de estos problemas hayan estado posteado antes y molestar con eso; y espero que esto les pueda servir a otros.
Desde ya muchas gracias a todos los que me puedan ayudar o a los que por lo menos me leyeron para ver si podian.

**1)**El primer problema que tuve fue con los drivers de NVIDIA, tipico. Busque en foros y recomendaban dos cosas: la primera era usar el gestor de controladores restringidos, y el segundo era usar el envy. Probe con las dos cosas y ninguna me dio resultado. Me pedian reiniciar, al reiniciar me decia que el driver no era compatible y que tenia que usar baja resolucion. Despues encontre una tercera solucion que era bajar los drivers de la pagina de NVIDIA e instalarlos por modo texto. Lo hice. Pero ahora el problema que tengo es que no me deja poner 1024x768 con 32 bits y 85 hercios. Los hercios me los deja en 60, y los bits en 24, aunque ahora los pude poner en 32. En todos lados decia que para solucionar eso habia que modificar el archivo xorg.conf, me fije y no se bien que modificar porque sale: "modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync" que supongo que eso me lo tendria que habilitar; asi que no se que otra linea agregar o modificar. Posteo aca el xorg.conf. Otro drama que tuve con el video que puede estar relacionado es con el compiz fusion, tengo bajados todos los paquetes, y cuando quiero poner en Apariencia, los efectos visuales extra me dice "Desktop effects could not be enabled" despues de refrescar la pantalla; ya tengo instalados los paquetes que te pide para habilitar el extra. Mi placa de video es una NVIDIA GEForce 8400 GS y mi monitor un Samsung SyncMaster 753DFX.

**2)**No se como compartir internet. Mi pc es server de mi red hogareña, tengo la conexion pppoe configurada y se ejectua al iniciar Ubuntu(no se si por defecto reconecta ante una desconexion, pero si no lo tiene tambien me gustaria saber como ponerlo). Busque en google y encontre dos formas: una con script del iptables que no me funciono, y otra con el Firestarter que tampoco me funciono. El firestarter no se inicia solo al iniciar Ubuntu asi que tampoco me sirve. Se que en sesiones puedo poner que inicie solo, pero para iniciar tiene que ser con 'sudo', y me pediria pass, asi que no se bien como hacer eso, y creo que me serviria en otros casos. En fin. el firestarter me tira error desconocido :S. Ninguna PC tiene internet salvo esta. El cableado y eso esta todo bien, porque con Windows me anda perfecto. No se si alguien sabe de algun script simple para hacer funcionar esto u otro metodo. Tambien me gustiar saber lo de reconexion automatica si es que existe.

**3)**Ni bien me aparecieron las actualizaciones automaticas al iniciar Ubuntu por primera vez, en la mayoria de las actualizaciones me tiro un error con el kernel.xxxx.restrictedpackpages o algo asi, seguro todos saben cual es. Busque en internet y con unos comandos me salia que estaba roto o no instalado correctamente. Lo reinstale con Synaptic y nunca mas aparecio el error, ni siguio diciendo que estaba roto; pero queria saber si las cosas que se instalaron antes y los problemas que tengo arriba podrian estar originados en esto, o si habra influenciado en algo.

**4)**Tambien queria saber si haber tenido estos problemas, haber insistido mucho, reinstalar, etc; me puede llegar a traer problemas a futuros para saber si me reinstalo ya o sigo como estoy.

*(Las dos preguntas que siguen son re tontas, pero no sabia bien como buscarlas, me salia cualquier resultado)*

**5)**Como hago con archivos ejecutables que se abran de una y no me pregunte "'mostrar' 'ejecutar en terminal' 'etc'". O para hacer archivos que ejecuten un comando, osea un script, y que se abra al hacerle doble click sin preguntar nada. [COLOR="Red"]**[Resuelto]**[/COLOR] **Nautilus dentro de sus opciones tiene para elegir si los archivos de texto ejecutables se abran, se muestren, etc.**

**6)**Tengo unas dudas sobre montar, yo la particion de Windows la comente en el fstab y en el mtab porque la quiero montar manualmente con algun script, pero no se que atributos debo mantener de los que aparecian en fstab, queria saber si me podian ayudar con eso, como seria la sintaxis del mount para que quede montado igual a como si lo montara el fstab. (Ya probe copiar y pegar y no funciono)
UUID=10D8500DD84FF010 /windows        ntfs    defaults,umask=007,gid=46 0       1
[COLOR="Red"]**[Resuelto]**[/COLOR] **Lo monte con el mount /windows /hd1, asi a secas, no se que quieren decir los otros parametros que tiene el comando en el fstab, espero que no sean importantes o me saquen la escritura o algo**

Espero no hayan jodido las consultas y no haber hecho preguntas tontas o que otra gente ya ha hecho. Muchas gracias a todos.

*[I]P.D.*: Pido perdon de nuevo si molesto o estuvo mal un thread que hice hace una semana sobre Windows, no queria hacer nada mal, solo queria saber de algun Windows tipo el Lite, no desatendido, si no liviano, para tener de respaldo para situaciones como ahora que necesito compartir internet y no puedo de Ubuntu. No era mi intencion hablar de Windows, ni pedir software propietario de manera ilegal, ni nada; solo queria saber si alguien estabae en mi situacion y habia usado un Windows liviano. Mil disculpas.[/I]

**Saludos**.

**edit:** No se si es normal o no, pero me tarda 6 segundos cronometrados con reloj en abrir el home o una terminal. En uso de CPU no llego ni al 5%. Es normal? esta algo mal configurado?

---

### Post by tzulberti on 2008-03-19
> **MaReaDo^ said:**
> 

1)El primer problema que tuve fue con los drivers de NVIDIA, tipico. Busque en foros y recomendaban dos cosas: la primera era usar el gestor de controladores restringidos, y el segundo era usar el envy. Probe con las dos cosas y ninguna me dio resultado. Me pedian reiniciar, al reiniciar me decia que el driver no era compatible y que tenia que usar baja resolucion. Despues encontre una tercera solucion que era bajar los drivers de la pagina de NVIDIA e instalarlos por modo texto. Lo hice. Pero ahora el problema que tengo es que no me deja poner 1024x768 con 32 bits y 85 hercios. Los hercios me los deja en 60, y los bits en 24, aunque ahora los pude poner en 32. En todos lados decia que para solucionar eso habia que modificar el archivo xorg.conf, me fije y no se bien que modificar porque sale: "modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync" que supongo que eso me lo tendria que habilitar; asi que no se que otra linea agregar o modificar. Posteo aca el xorg.conf. Otro drama que tuve con el video que puede estar relacionado es con el compiz fusion, tengo bajados todos los paquetes, y cuando quiero poner en Apariencia, los efectos visuales extra me dice "Desktop effects could not be enabled" despues de refrescar la pantalla; ya tengo instalados los paquetes que te pide para habilitar el extra. Mi placa de video es una NVIDIA GEForce 8400 GS y mi monitor un Samsung SyncMaster 753DFX.


Fijate si lo podes configurar usando "sudo dpkg-reconfigure xserver-xorg" desde una consulta. Cuando te pida configurar el montir elegi intermedia. Luego "sudo /etc/init.d/gdm restart".


 > **MaReaDo^ said:**
> 
3)Ni bien me aparecieron las actualizaciones automaticas al iniciar Ubuntu por primera vez, en la mayoria de las actualizaciones me tiro un error con el kernel.xxxx.restrictedpackpages o algo asi, seguro todos saben cual es. Busque en internet y con unos comandos me salia que estaba roto o no instalado correctamente. Lo reinstale con Synaptic y nunca mas aparecio el error, ni siguio diciendo que estaba roto; pero queria saber si las cosas que se instalaron antes y los problemas que tengo arriba podrian estar originados en esto, o si habra influenciado en algo.


Si seguis teniendo algun problema con el apt-get proba apt-get -f install.

> **MaReaDo^ said:**
> 
4)Tambien queria saber si haber tenido estos problemas, haber insistido mucho, reinstalar, etc; me puede llegar a traer problemas a futuros para saber si me reinstalo ya o sigo como estoy.
(Las dos preguntas que siguen son re tontas, pero no sabia bien como buscarlas, me salia cualquier resultado)


Seria raro que no te ocurra cuando vuelvas a formatear. Esto no es MS. Sin embargo, lo que haria es chequear que el cd con el que instalastes sea correcto (usando una opcion que el cd tiene al momento de bootear).

> **MaReaDo^ said:**
> 
6)Tengo unas dudas sobre montar, yo la particion de Windows la comente en el fstab y en el mtab porque la quiero montar manualmente con algun script, pero no se que atributos debo mantener de los que aparecian en fstab, queria saber si me podian ayudar con eso, como seria la sintaxis del mount para que quede montado igual a como si lo montara el fstab. (Ya probe copiar y pegar y no funciono)
UUID=10D8500DD84FF010 /windows        ntfs    defaults,umask=007,gid=46 0       1


Sacale defaults y ponele noauto,users 

Nunca me acuerdo si es user o users...

Saludos,
TZ

---

### Post by MaReaDo^ on 2008-03-19
yo a mi cd le pase ese chequeo de integridad y salio bien
yo pensaba si arreglo todo o no, reinstalar ubuntu, capaz el tema ese de los paquetes que me tiraban error ****Le varias instalaciones, ya no da mas el error, pero no se. a eso me refiero con lo de reinstalacion, capaz se crean conflictos por el toqueteo que hice.
el error del paquete ese ya no me lo da mas por suerte. se arreglo cuando lo reinstale.
ahora estoy en win ¬¬ porque necesitan usar interent en otra pc, pero despues pruebo el tema del sudo dpkg-reconfigure xserver-xorg
y lo del montado
muchas gracias por contestar :D:D

hice lo que me dijiste del xserver bla bla y no funciono, ante stenia 60 hercios y ahora 50 hercios xd, no se si abre hecho cualquiera, en un paso me pidio poner manualmente los ratios de refresco de mi monitor y yo puse los reales, asi que nose, si hace falta despeus adjuntos el xorg actual

---

### Post by MaReaDo^ on 2008-03-20
reinstale y no tengo mas dramas, pude compartir internet y todo
no me tiro el error en la primera actualizacion que me tiro antes y ahora anda todo bien
pero sigo teniendo un problema
no me deja ponerle 85 hercios de refresco a la pantalla
y mi monitor lo soporta
me lo deja en 52 :S
probe con el reconfigure
con nvidia settings
con todo :S

---

### Post by Hei Ku on 2008-03-21
eso debería arreglarse en el xorg.conf.

Postea el contenido de /etc/X11/xorg.conf asi lo vemos y te podemos dar una mano.

---

### Post by MaReaDo^ on 2008-03-21
despues de mucho buscar encontre que si le agregaba:
    Option         "UseEdidFreqs" "no"
    Option         "DPMS"
a la seccion de monitor me dejaba poner mas frecuencias, y funciono, me dejo hasta 75, despues le agregue otro modo con 85 en una parte donde parecia que faltaba, le puse "1024x768@85 +0+0
hasta 75 funciono bien, le modifique eso de arriba y no reinicie
instale compiz fusion
y ahi reinicie y ahora se puso loco todo
primero no tengo las barritas para cerrar y toda esa historia, le agregue:
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
en dos lugares, pero capaz los puse mal porque no funciona
ahora el programa de nvidia no me deja poner ni 75 hercios, me deja hasta 60, asi que atrase de nuevo y no se dodne poner las options de arriba
en un lugar del xorg, dice:
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
no se si el auto-select ese esta bien :S
y tambien dice:
    Option         "TwinView" "0"
en un foro decia que eso podia traer problemas. yo no tengo twinview ni nada :P
encima a mi cuando tenia 75 hercios con nvidia, me fije en las opciones de ubuntu y salia 43 hz, lei que es normal y que es bug arreglable, pero no se, no entendi bien porque estaba en ingles :P
ah, y otra cosa, mi xorg.conf dice:
Section "Monitor"
    Identifier     "Monitor genérico"
y yo cuando busque mi problema, a todo el mundo le salia:
   Identifier      "SynMaster"
no se si tendra que ver.
bueno desde ya muchas gracias
aca les dejo el xorg.conf completo

---

### Post by MaReaDo^ on 2008-03-21
resolvi un par de problemas
adjunto el xorg nuevo
ya veo las barras, me funciona compiz, tengo 1024, pero no puedo poner 85 hercios, todo lo demas funciona bien

edit: le puse dynamic twin view false asi ahora me reconoce los hercioes reales el configurador de gnome
pero sigo sin poder poner 85 hercios
el configurador de gnome me los deja poner pero se ve todo mal con lineas y titileando :S

---

### Post by faktorqm on 2008-03-24
No te deja poner los 85 hertz por que tenes mal en el xorg.conf la frecuencia de actualizacion horizontal y vertical.
Las frecuencias de tu monitor son: 

- Frecuencia Horizontal : 30 ~ 70KHz 
- Frecuencia Vertical : 50 ~ 160Hz

y las cambias directamente del xorg.conf, pero aca te dejo el tuyo (el ultimo que posteaste que te andaba todo) ya modificado:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Gamma           1
    ModeLine       "640x480@60" 25.0 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.0 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.0 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.0 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.0 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.0 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.0 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.0 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.0 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x960@60" 102.0 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.0 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    Option         "UseEdidFreqs" "false"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768 +0+0; 832x624@75 +0+0; 800x600@60 +0+0; 1024x768@60 +0+0; 800x600@85 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 800x600@56 +0+0; 640x480@85 +0+0; 640x480@75 +0+0; 640x480@72 +0+0; 640x480@60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Como tu xorg.conf no me gusta ni un poquito, te dejo el mio modificado para vos digamos, cosa de que si lo queres probar y te anda tenes un xorg.conf como la gente:

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	RgbPath	"/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
	Load	"extmod"
	Load          "type1"
	Load	"freetype"
	Load	"glx"
	Load          "v4l"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Device"
	Identifier		"nVIDIA GEForce 8400 GS"
	Driver		"nvidia"
	VendorName	"nVIDIA Corporation"
	BoardName	"GEForce 8400 GS"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Monitor"
	Identifier		"Monitor generico"
	VendorName 	"Samsung"
	ModelName	"SyncMaster 753DFX"
	HorizSync		30.0 - 70.0
	VertRefresh	50.0 - 160.0
	Gamma		1
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier		"Default Screen"
	Device		"nVIDIA GEForce 8400 GS"
	Monitor		"Monitor generico"
	DefaultDepth	24
	Option		"metamodes" "1024x768_85 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier		"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "0"
EndSection

```

Salu2!!

---

### Post by MaReaDo^ on 2008-03-25
copie y pegue tu xorg modificado para mi y no me dejo poner mas de 60 hz, encima me **** el compiz creo xd ya no anda mas xd, voy a probar con el mio que modificaste
pasa que ni bien entre me empezo a decir que el teclado, el mouse, y no se que mas seleccionado en el xorg no tenian nada que ver con los mios o algo asi
despeus cualquie rcosa edito y agrego si me fue bien con el mio modificado

edit: con el mio que me modificaste me dejo poner hasta 75 hercios, es un avance :D, gracias :D, capaz nunca voy a poder poenr 85 xD
  no tiene nada que ver que diga:     Option         "metamodes" "1024x768_75 +0+0; 1024x768 +0+0"
no tendria que decir _85?

---

### Post by faktorqm on 2008-03-25
Vamos por partes. si te anda tu xorg.conf, bueno, el tema de la prolijidad lo veras despues. Te quedo el mio como ejemplo de ultima. 
Con el tema de los 85, vos en los metamodes no tenes especificado para 1024x768 nada, asi que ponele @85 como estan los otros, si sigue sin andar, andate al nvidia settings y hacelo a mano. Vas a ver que te deberia dejar elegir frecuencias altas, luego le decis que te lo guarde en el xorg.conf. Si te tira error, vas hasta sistema -> preferencias -> menu principal, te vas hasta el nvidia settings, le agregas "gksudo" adelante del comando que sea, guardas todo y volves a abrir. Salu2!

---

### Post by MaReaDo^ on 2008-03-27
puse en el xorg el @85 y no paso nada :P
no se bien a que te referis con modificarlo manualmente con el nvidia-settings
pero en el combo de frecuencias del nvidia-settings me deja hasta 75 :P
no se si eso es manualmente
me deja escribir en el xorg.conf y todo pero no puedo poner mas hercios
igual ya fue, no hay drama, no hay tanta diferencia supongo entre 75 y 85

---

