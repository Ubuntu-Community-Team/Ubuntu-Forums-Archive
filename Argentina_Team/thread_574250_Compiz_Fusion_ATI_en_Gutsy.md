---
title: "Compiz Fusion ATI en Gutsy"
date: 2007-10-12
forum: Argentina Team
---

### Post by Hernán-Amaya on 2007-10-12
[FONT="Courier New"]hola gente! 
este es mi primer post y aprovecho para presentarme, mi nombre es Hernán
y estoy en la lista de correo pero nunca había entrado al foro, a partir de ahora voy a tratar de participar mas de esta noble comunidad

En este momento tengo un pequeño problema no puedo activar los efectos en Gutsy, no tengo instalado el driver propietario de ati

tengo una ATI Mobility Radeon  9200 

y tengo direct renderign: YES

por las dudas les paso el resultado de glxinfo y glxgears
también les mando mi xorg.conf lo que tengo al final donde esta la configuración de video

glxgears 

5203 frames in 5.0 seconds = 1040.443 FPS
5203 frames in 5.0 seconds = 1040.520 FPS

glxinfo

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample,
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution,
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square,
    GL_NV_light_max_exponent, GL_NV_texture_rectangle,
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix,
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x56 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

Xorg.conf 

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection[/FONT]

desde ya muchas gracias por su atención

---

### Post by nest on 2007-10-12
primero que el comando para las ATI es **fglrx**, no glxinfo


por otra parte, yo tengo ATI también y instalé todo sin problemas desde [este]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=fglrx") link.

---

### Post by Hernán-Amaya on 2007-10-12
ya había usado esa guía pero cuando usaba el aticonfig --initial 
me tira este error[1]. Aclaro que con feisty andaba con compiz fuision sin ningún problema 
había seguido varias guías y sin ningún buen resultado queria saber si hay alguien con mi misma placa que este usando gutsy y si pudieron hacerla andar

[1][FONT="Courier New"]Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-14
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf920af5 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d1392b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cbc050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 2460917    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 2460917    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c98000-b7c99000 rw-p b7c98000 00:00 0
b7c99000-b7c9b000 r-xp 00000000 08:01 5948422    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9b000-b7c9d000 rw-p 00001000 08:01 5948422    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c9d000-b7c9e000 rw-p b7c9d000 00:00 0
b7c9e000-b7ca2000 r-xp 00000000 08:01 2458926    /usr/lib/libXdmcp.so.6.0.0
b7ca2000-b7ca3000 rw-p 00003000 08:01 2458926    /usr/lib/libXdmcp.so.6.0.0
b7ca3000-b7ca5000 r-xp 00000000 08:01 2458915    /usr/lib/libXau.so.6.0.0
b7ca5000-b7ca6000 rw-p 00001000 08:01 2458915    /usr/lib/libXau.so.6.0.0
b7ca6000-b7dea000 r-xp 00000000 08:01 5948419    /lib/tls/i686/cmov/libc-2.6.1.so
b7dea000-b7deb000 r--p 00143000 08:01 5948419    /lib/tls/i686/cmov/libc-2.6.1.so
b7deb000-b7ded000 rw-p 00144000 08:01 5948419    /lib/tls/i686/cmov/libc-2.6.1.so
b7ded000-b7df0000 rw-p b7ded000 00:00 0
b7df0000-b7e13000 r-xp 00000000 08:01 5948423    /lib/tls/i686/cmov/libm-2.6.1.so
b7e13000-b7e15000 rw-p 00023000 08:01 5948423    /lib/tls/i686/cmov/libm-2.6.1.so
b7e15000-b7f02000 r-xp 00000000 08:01 2458165    /usr/lib/libX11.so.6.2.0
b7f02000-b7f06000 rw-p 000ed000 08:01 2458165    /usr/lib/libX11.so.6.2.0
b7f06000-b7f13000 r-xp 00000000 08:01 2458930    /usr/lib/libXext.so.6.4.0
b7f13000-b7f14000 rw-p 0000d000 08:01 2458930    /usr/lib/libXext.so.6.4.0
b7f14000-b7f15000 rw-p b7f14000 00:00 0
b7f15000-b7f1c000 r-xp 00000000 08:01 2458952    /usr/lib/libXrender.so.1.3.0
b7f1c000-b7f1d000 rw-p 00006000 08:01 2458952    /usr/lib/libXrender.so.1.3.0
b7f1d000-b7f22000 r-xp 00000000 08:01 2458950    /usr/lib/libXrandr.so.2.1.0
b7f22000-b7f23000 rw-p 00005000 08:01 2458950    /usr/lib/libXrandr.so.2.1.0
b7f2a000-b7f34000 r-xp 00000000 08:01 5914646    /lib/libgcc_s.so.1
b7f34000-b7f35000 rw-p 0000a000 08:01 5914646    /lib/libgcc_s.so.1
b7f35000-b7f38000 rw-p b7f35000 00:00 0
b7f38000-b7f52000 r-xp 00000000 08:01 5914644    /lib/ld-2.6.1.so
b7f52000-b7f54000 rw-p 00019000 08:01 5914644    /lib/ld-2.6.1.so
bf90c000-bf921000 rw-p bf90c000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Cancelado (core dumped)[/FONT]

---

### Post by Hernán-Amaya on 2007-10-15
SOLUCIONADO! (a medias jejeje) 

se soluciona instalando el driver libre, que está en los repositorios de gutsy. 

pero hay que hacer unas modificaciones en el xorg.conf para que ande,
hay modificar las siguientes secciones 

en la sección Device (ojo donde dice indentifier hay que dejar el que corresponde a cada uno)

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

```

en la sección ServerLayout (lo importante es agregar la opción Aiglx true)

```

Section "ServerLayout"
        Option		"AIGLX"	"true"
        Identifier	"Default Layout"
        Screen		"Default Screen"
        InputDevice	"Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

y al final de archivo agregar lo siguiente
```

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

después hay que reinciar las X 

con esto debería andar pero el compiz fusion solo anda en resoluciones de hasta 1024x1024

si quieren optimizar la aceleración (yo aumenté el 50 por ciento los fps )
instalando driconf, que también está en los repositorios de gutsy

espero que les sirva les dejo una de las fuentes el resto la verdad que vi tantos tutoriales que ya me olvidé
 
[http://wiki.compiz-fusion.org/ATI_with_AIGLX](http://wiki.compiz-fusion.org/ATI_with_AIGLX)

---

### Post by Hei Ku on 2007-10-15
yo tengo el compiz fusion andando en 1280x1024, con una ATI Radeon 9200, también con el driver libre.

---

### Post by Hernán-Amaya on 2007-10-16
podrías decirme como lo hiciste?

---

### Post by Hei Ku on 2007-10-16
Los drivers los instalo solos en la actualizacion a Feisty o Edgy, ya no recuerdo. En cuanto a la resolución, la puse a mano en el xorg.conf. Busque en la subsección display, y fijandome en las caracteristicas de la placa y del monitor le puse los modos soportados. Ahi también tenés para seleccionar el default. Después de eso, reinicié y listo. Obvio que hacete un backup del xorg.conf por las dudas.

Acá está como tengo yo esa parte del xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by Hernán-Amaya on 2007-10-16
mira esta es la salida de mi konsola cuando ejecuto compiz

```

hernan@hernan-laptop:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity
Not initializing the Gtk-Qt theme engine

```

lo raro es que en feisty andaba lo mas bien, igual en la pagina de compiz dice lo siguiente:

First generation radeons have a maximum 3D texture resolution of 1024x1024, so compiz will not work properly on displays larger than that.

tal vez sea por eso ?

gracias por tus respuestas

---

### Post by Hei Ku on 2007-10-17
yo arranco el compiz con --indirect-rendering

quizas eso funcione en tu caso, aunque puede ser q estes limitado por la version de tu placa nomas.

---

### Post by luchardi on 2007-10-17
Hola, tengo una ATI Radeon 9000 IGP Mobility.

Seguí los pasos que Hernán-Amaya comentó en su post, pero no logro iniciar la aceleración. En algunos foros comentaban que hace falta instalar xserver-xgl pero con xgl levanta la ventana de login y luego no inicia Gnome.

```
lucho@lucho-laptop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```
Cuando quiero arrancar compiz:

```
lucho@lucho-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by Hei Ku on 2007-10-17
probaste tambien con los drivers propietarios? cada modelo tiene sus vueltas. es el punto flojo de linux, que se esta resolviendo. Pero la verdad es que todavia es a pedal.

Tambien esta la wiki: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by luchardi on 2007-10-17
no encuentro los propietarios de mi ati.

Igualmente actualicé desde Feisty y con 7.04 tenía aceleración 10 puntos.
Es una placa medio chiquita 32mb compartidos de ram de la notebook pero aceleraba perfecto (aunque un poco lento) pero beryl con emerald funcionaba.

Lo demás 10 pts.

LO MEJOR DE 7.10 es que puede escribir en NTFS o sea las SDCards del celular las puedo cargar desde linux :):)

---

### Post by sajnox on 2007-10-17
Hei Ku, seguramente me podes ayudar.

Como puedo saber precisamente cual es el Driver que estoy utilizando? Tengo una Radeon 9600 que en Feisty anda diez puntos, pero en gutsy no hay forma.

Reemplaze el xorg de gutsy por el de fesity y aun asi no logro aceleracion.

Ya probe con todos los tutoriales y algunos otros mas y nada

Saludos

---

### Post by Hernán-Amaya on 2007-10-17
los driver propietarios son fglrx y los libres ati para ver cual estas usando 

abrí la consola y gedit /etc/X11/xorg.conf 

fijate cual de los dos tenes

luchardi: fijate con el driver libre de nuevo es raro por que vi casi mi misma configuracion en la pc de un amigo que tiene tu placa.

te fijaste con glxinfo | grep direct rendering  si te dice yes ? 
manda tu xorg.conf tambien

porque por lo que vi estas usando el driver propietario por que estas usando el fglrxinfo

---

### Post by Hernán-Amaya on 2007-10-28
hola sigo con el problema de no poder correr compiz fusion en gutsy, cosa que en  feisty andaba joya con --indirect-rendering pero ahora tira este error

hernan@hernan-laptop:~$ compiz --indirect-rendering
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 
metacity: Opción desconocida --indirect-rendering

alguien pudo activar el indirect-rendering??

---

### Post by sajnox on 2007-10-28
> **Hernán-Amaya said:**
> hola sigo con el problema de no poder correr compiz fusion en gutsy, cosa que en  feisty andaba joya con --indirect-rendering pero ahora tira este error

hernan@hernan-laptop:~$ compiz --indirect-rendering
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 
metacity: Opción desconocida --indirect-rendering

alguien pudo activar el indirect-rendering??

Te esta rebotando compiz por la resolucion y no por el soporte. La placa te dice que no soporta resolucion hasta 1024 y tenes la pantalla seteada en 1280 x 800.

Proba cambiar la resolucion a 1024 y ahi ejecuta compiz para ver si funciona

Saludos,

---

### Post by Hernán-Amaya on 2007-10-28
en 1024 anda pero la notebook es widescreen y se ve feo, en feisty con el indirect-rendering andaba joya en la resolución que tengo ahora, y me reconocía la opción indirect-rendering

---

