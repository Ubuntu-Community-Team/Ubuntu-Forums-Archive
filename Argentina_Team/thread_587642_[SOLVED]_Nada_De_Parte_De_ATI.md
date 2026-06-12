---
title: "[SOLVED] Nada De Parte De ATI"
date: 2007-10-22
forum: Argentina Team
---

### Post by Timbis on 2007-10-22
Ya probe con 5.000.000 de tutos para hacerla andar, pero no logro hacerla funcionar en Gutsy, tengo una placa ATI Radeon 9250 AGP, y en Feisty si funcionaba.
Sorry por hacer un post igual a muchos, pero ya probe de todo, googlea hasta mas no poder. 
Y quiero probar el Compiz-Fusion, ya que espere mucho para que salga.

Gracias de ante mano.

---

### Post by Hernán-Amaya on 2007-10-23
yo postie como hacer para tener aceleracion 3d en una ati  yo uso mobility radeon 9200

[http://ubuntuforums.org/showthread.php?t=574250](http://ubuntuforums.org/showthread.php?t=574250)

el problema parece ser que no se puede usar compiz a resoluciones mayores de 1024X1024 proba de bajar la resolución. por lo menos eso es lo que me dice a mi

proba de ejecutar el compiz por consola para ver que error te tira

suerte!!

---

### Post by sajnox on 2007-10-23
Ok, no te preocupes. Creeme que es mas facil de lo que pensas.

En primer lugar, deshabilitaste los drivers propietarios no?? Es fundamental.

Para que te podamos dar una mano, copie estos dos resultados de la consola y postealos

```
 $ lspci
```

Para confirmar cual es tu placa de video

```
 $ compiz --help
```

Para ver que te dice compiz, y copia el contendido de tu xorg.conf aca

```
 gedti /etc/X11/xorg.conf
```

Y ahi vemos que podemos hacer, pero segun lo que vi tu placa lo soporta ampliamente.

Saludos,

---

### Post by Timbis on 2007-10-23
Aqui esta como la reconoce ubuntu...
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

Lo de compiz...
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
(aclaro que nunca intente instalarlo)

Y aca mi xorg ("todo desconfigurado a mano")

Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

	Section 	&#8220;Device&#8221;
	Identifier 	&#8220;ATI Technologies Inc RV280 [Radeon 9200 PRO]&#8221;
	Driver	 	&#8220;ati&#8221;
	Option 		&#8220;AGPMode&#8221; &#8220;4&#8221;
	Option 		&#8220;EnablePageFlip&#8221; &#8220;true&#8221;
	Option 		&#8220;ColorTiling&#8221; &#8220;on&#8221;
	Option 		&#8220;TripleBuffer&#8221; &#8220;true&#8221;
	BusID 		&#8220;PCI:1:0:0?
	EndSection
Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"800x600@85"	"800x600@60"	"800x600@75"	"832x624@75"	"800x600@72"	"1024x768@60"	"800x600@56"	"1024x768@43"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

El tema es que probe con tantas obciones, que esta todo cambiado...

aca les dejo lo que dice glxinfo...
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

 y aca glxgears...
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Gutsy tiene un servidor X de emergencia no? porque en el feisty se caia a cada rato cuando tocabas este tipo de configuracion.

---

### Post by Hernán-Amaya on 2007-10-23
tenes mal configurado el xorg.conf lo que a mí me funcionó fue poner 

en la sección device

Option          "XAANoOffscreenPixmaps"

en la sección  "ServerLayout"

Option		"AIGLX"	"true"


y al final de archivo agregar esto

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

esta mas explicado en el post que que linkié arriba

una vez que hayas modificado el xorg.conf 

mata las X con: alt + ctrl + backspace

y proba con glxinfo 

para ver si tenes direct rendering o no

suerte!!

---

### Post by sajnox on 2007-10-23
Coincido plenamente con las modifiaciones de Hernan

Saludos,

---

### Post by Hei Ku on 2007-10-23
Tambien coincido. De acuerdo a lo que posteaste de tu xorg.conf, no te va a andar. Con esos deberia.

Sino, fijate en este link que esta todo bien explicado paso a paso:

[https://wiki.ubuntu.com/RadeonDriverHowto](https://wiki.ubuntu.com/RadeonDriverHowto)

---

### Post by Timbis on 2007-10-24
Nop, agrege esas lineas en el xorg, lei y relei la guia, pero nada.
Cuando tenia feisty la placa la configure con el script ati.sh, pero esta vez no surge efecto.

---

### Post by sajnox on 2007-10-24
Si lo tocaste tanto como decis yo probaria con regarcar el xorg.conf que viene de inicio y reconfigurarlo

En el xorg.conf esta escrito el comando para reconfigurarlo como de inicio, era algo asi como 

```
 dpkg --reconfigure -xserver -phigh
```

Buscalo, ejecutalo y de nuevo reconfigura el xorg.conf

---

### Post by kk_furtiva on 2007-10-24
respuesta rapida porq no tengo mucho tiempo para leer este thread. por lo q vi, no tenes habilitado el DRI (aceleracion 3d).

hace:
```
sudo glxinfo | grep direct
```

si te dice algo como Direct Rendering: Yes, tenes aceleracion 3d, si dice no, no. :)

hay muchos tutoriales para habilitar la aceleracionn 3d. Googlea algo como "ubuntu ati enable 3d acceleration"

Saludos...me voy a laburar q si no me matan :S

---

### Post by Timbis on 2007-10-24
Nop, nosep, ya probe con casi todo y sige sin funcionar...

---

### Post by facundocorradini on 2007-10-24
Aún no los probé, pero [B]hoy salieron los nuevos drivers de ATI!!!!!!!!!!

CON SOPORTE AIXGL!!!!!!!!![/B] (lease "eso que necesitas pa' que te corra el compiz, viteh")

[http://www.phoronix.com/scan.php?page=article&item=887&num=1](http://www.phoronix.com/scan.php?page=article&item=887&num=1)

---

### Post by sajnox on 2007-10-24
Asi es Facundo, igual por algunos comentarios que lei habria que esperar un ratito mas (no mucho)

Saludos,

---

### Post by sdm_cacto on 2007-10-24
> **Timbis said:**
> Nop, nosep, ya probe con casi todo y sige sin funcionar...

Probaste [Envy]("http://albertomilone.com/nvidia_scripts1.html")??

---

### Post by sajnox on 2007-10-24
> **sdm_cacto said:**
> Probaste [Envy]("http://albertomilone.com/nvidia_scripts1.html")??

Envy le instala los drivers propietarios, y corrijanme si no estoy en lo cierto pero creo que de la pagina de ati, y en la pagina de ati los nuevos drivers todavia no estan = volves al fglrx sin soporte para AIGLX = No Compiz.

Timbis, no puedo soportar que no puedas configurar la placa, reconfigura el xorg con el comando que te pasamos y postealo que vemos que correcciones necesita

Saludos

---

### Post by Timbis on 2007-10-24
12714 frames in 5.0 seconds = 2535.204 FPS
13560 frames in 5.0 seconds = 2689.557 FPS
13469 frames in 5.0 seconds = 2682.775 FPS
19434 frames in 5.0 seconds = 3886.588 FPS
15466 frames in 5.0 seconds = 3082.968 FPS
13320 frames in 5.0 seconds = 2646.325 FPS
13504 frames in 5.0 seconds = 2687.419 FPS
13320 frames in 5.0 seconds = 2650.427 FPS
11880 frames in 5.0 seconds = 2368.925 FPS
12227 frames in 5.0 seconds = 2433.450 FPS
13200 frames in 5.0 seconds = 2639.432 FPS
12947 frames in 5.0 seconds = 2584.072 FPS

Muchachos... esto les dice algo????
 lo unico que hice fue poner: sudo dpkg-reconfigure -phigh xserver-xorg
y la reinicie...
gracias por todo...

---

### Post by sajnox on 2007-10-25
Dice mucho!!

Compiz Fusion te funciona?? en una consola

```
 $ compiz --help
```

Y postea el resultado

Saludos

---

### Post by facundocorradini on 2007-10-25
Cuales drivers usaste al final?

---

### Post by Hernán-Amaya on 2007-10-25
publica  como lo resolviste!!!!

---

### Post by Timbis on 2007-10-25
aca lo que devuelve compiz --help

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

Lo que no tengo es aceleracion... 

Lo unico que hice fue ejecutar: sudo dpkg-reconfigure -phigh xserver-xorg

ahh, tengo los drives libres.

---

### Post by sajnox on 2007-10-25
Ok, creeme que estas a un paso de hacer andar compiz.

en primer lugar hace un backup  de este xorg.conf que parece que va mejor

```
 $ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
```

Si tenes problemas lo reemplazas por el backup y no retrocedes conco casilleros

Ahora si!!! Segui el post (creo que de hernan-amaya) con las modificaciones a realizar al xorg.conf, si con eso no funciona compiz postea de nuevo el xorg que vemos que es.

(ya casi es una cruzada personal esto....)

Saludos,

---

### Post by Timbis on 2007-10-25
Esta todo como dice el tuto, pero sigue diciendo que NO
(lo que esta comentado lo agrege yop)

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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
#	Option 		"EnablePageFlip" "true" 
#	Option 		"ColorTiling" "true"
#	Option 		"EnableDepthMoves" "true"
#	Option		"BackingStore" "true"
#	Option 		"AccelMethod" "XAA"
#	Option		"AccelIDFS" "true"
#	Option 		"UseFBDev" "true"
	Option 		"XAANoOffscreenPixmaps" 
#	Option		"GARTSize" "256" 
#	Option 		"AGPMode" "4" 
EndSection

Section "Monitor"
	Identifier	"AOC"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"AOC"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"AIGLX" "true"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

#Section "Module"
#	Load 		"i2c"
#	Load 		"bitmap"
#	Load 		"ddc"
#	Load		"dri"	
#	Load 		"extmod"
#	Load 		"freetype"
#	Load 		"glx"
#	Load 		"int10"
#	Load 		"vbe"
#	Load 		"ati"
#EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option 		"Composite" "Enable"
EndSection

---

### Post by Hernán-Amaya on 2007-10-25
probaste con este driver es el ultimo que supuestamente soporta tu placa

[http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html)

si no te anda proba con alguno mas viejo, igual te cuento q a mi no me funciono
y ahora uso el driver libre

suerte

---

### Post by sajnox on 2007-10-26
> **Hernán-Amaya said:**
> probaste con este driver es el ultimo que supuestamente soporta tu placa

[http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html)

si no te anda proba con alguno mas viejo, igual te cuento q a mi no me funciono
y ahora uso el driver libre

suerte

Yo no usaria ese driver, vas a quedar seguro que peor que ahora (para usar los drivers oficiales de ATI hay que esperar un poco mas)

Timbis, descomenta las modificaciones que hiciste y de nuevo ejecuta compiz --help y postea el resultado

Saludos

---

### Post by Timbis on 2007-10-26
compiz --help
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

tengo que instalar algo del xgl?

2 horas despues...

instale con synaptic un paquete llamado xserver-xgl
y luego de reconfigurar xorg...

compiz --help
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
Usage: /usr/bin/compiz.real [--display DISPLAY] [--bg-image PNG] [--refresh-rate RATE]
       [--fast-filter] [--indirect-rendering] [--loose-binding] [--replace]
       [--sm-disable] [--sm-client-id ID] [--no-detection]
       [--ignore-desktop-hints] [--only-current-screen] [--use-root-window]
       [--version] [--help] [PLUGIN]...

aunque sigo sin aceleracion...
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

y los fps andan por el suelo...
 glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".

4320 frames in 5.0 seconds = 855.615 FPS
4320 frames in 5.1 seconds = 849.133 FPS
4320 frames in 5.1 seconds = 848.720 FPS
3836 frames in 5.0 seconds = 766.322 FPS
3838 frames in 5.1 seconds = 746.723 FPS

aparte solo anda la resolucion de 800x600 (con la de 1024x768 se achica la pantalla)
y el teclado se puso en ingles... chan!!

voy a desinstalarlo...

---

### Post by sajnox on 2007-10-27
Me llama poderosamente la atencion, esa placa es casi igual que la mia y con dos correcciones al xorg la tengo andando perfecto

Ademas el xgl-server solo te va enlentecer la maquina

Igual no te preocupes que en poco tiempo ATI ya larga oficlalmente los drivers de las placas con soporte para 3d.

Algo importante a destacar es que esto no es que Ubuntu ande mal, sino que los fabricantes no hacen drivers buenos para Linux ni liberan las especificaciones para que la comunidad del SL los haga.

Saludos

---

### Post by Timbis on 2007-10-27
sajnox: no te preocupes, se que no es problema de ubuntu, sino de los drivers... gracias por tu ayuda

---

