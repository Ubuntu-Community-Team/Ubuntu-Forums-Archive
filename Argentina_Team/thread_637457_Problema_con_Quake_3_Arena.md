---
title: "Problema con Quake 3 Arena"
date: 2007-12-11
forum: Argentina Team
---

### Post by faktorqm on 2007-12-11
Hola a todos, les comento un pequeño problema:

Instale el Quake 3 Arena para linux, encontre 150 tutos, agarre y armé uno para mi. Ahora bien, cuando lo ejecuto, el tipo me cambia la resolucion a 640x480, hasta ahi normal, pero se me ve todo negro Y SE ESCUCHA PERFECTO. Me cansé de leer millones de posts diciendo que no tenian sonido, y ninguno se le queda en negro la pantalla. :(

Las instrucciones que basicamente segui son estas:

- Insertar el CD del q3a.
- Escribir en una terminal "sudo mkdir -p /usr/local/games/quake3/baseq3"
- Luego "sudo cp /media/cdrom/baseq3/pak0.pak /usr/local/games/quake3/baseq3/pak0.pak"
- Luego copiamos el linuxq3apoint-1.32b-3.x86.run a /usr/local/games/quake3
- Luego escribimos "sudo sh /usr/local/games/quake3/linuxq3apoint-1.32b-3.x86.run"
- Luego hacemos "unzip -x quake3-1.32c.zip" y copiamos EL CONTENIDO DE la carpeta "linux" en /usr/local/games/quake3/
- Ejecutamos con "quake3".

Hasta ahi vamos barbaro, obvio hasta que ejecuto "quake3" y pierdo el control sobre el escritorio.

Aca les pongo la salida de la terminal (aca intente reinstalarlo, cuando termina le pongo "run")

```

faktorqm@theship:~$ sudo sh /usr/local/games/quake3/linuxq3apoint-1.32b-3.x86.run
Password:
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b.................................................................................................................................................
Removing existing quake3 symlink
Installing symlink /usr/local/bin/quake3 -> /usr/local/games/quake3/quake3
Removing existing quake3-smp symlink
Installing symlink /usr/local/bin/quake3-smp -> /usr/local/games/quake3/quake3-smp
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/faktorqm/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.01
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xb1e3e000 dma buffer
No background file.
----------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: theship
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
Received signal 15, exiting...
Shutdown tty console
faktorqm@theship:~$ 

```

aca dice que sale por que hice ctrl+alt+F2 y me loguie y le hice kill al proceso.

Yo lo unico que veo de "raro" aca es que en una parte dice "shaders", usa pixel shaders? por que mi placa no lo banca eso. de todas maneras, en windows anda de pm este juego, asi que no tendria por que pensar en ke no ande.

Otra cosa, tengo copmiz-fusion activado, eso generara problemas? como hago para desactivarlo? no instale el compiz-fusion-icon (aviso). 
y si no lo kiero desactivar, no puedo levantar otra sesion de X en otro lado con metacity pelado y correr ahi el q3a? eso seria una solucion? o no tendria la aceleracon? perdonen pero jamas entendi como es que funciona el driver, opengl, el X, gnome, y emerald :S es como que son capas no?

Bueno, escucho sugerencias!!! Mil gracias de antemano. ^_^

---

### Post by faktorqm on 2007-12-11
de vuelta: encontre que si haciendo ```
metacity --replace
``` podia desactivar compiz-fusion.
no se si es cierto pero al menos las ventanas se ven muy feas.

resultado de la corrida: todo mal. sigue negra la pantalla. lo bueno es que aprete "enter-enter-enter" y entre al escenario digamos. aqui la salida de la terminal:

```
faktorqm@theship:~$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/faktorqm/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
Initializing OpenGL extensions
...ignoring GL_S3_s3tc
...ignoring GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
XF86 Gamma extension initialized

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.01
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
----- finished R_Init -----

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xb1f9c000 dma buffer
No background file.
----------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: theship
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
------ Server Initialization ------
Server: q3dm0
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- FS_Startup -----
Current search path:
/home/faktorqm/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
8146 files in pk3 files
Loading vm file vm/qagame.qvm.
VM file qagame compiled to 1137840 bytes of code
qagame loaded in 3821696 bytes on the hunk
------- Game Initialization -------
gamename: baseq3
gamedate: Sep 30 2002
Not logging to disk.
Gametype changed, clearing session data.
1 teams with 2 entities
11 items registered
-----------------------------------
^1Error: can't open the log file botlib.log
------- BotLib Initialization -------
loaded weapons.c
loaded items.c
loaded syn.c
loaded rnd.c
loaded match.c
loaded rchat.c
------------ Map Loading ------------
trying to load maps/q3dm0.aas
loaded maps/q3dm0.aas
found 19 level items
-------------------------------------
32 bots parsed
35 arenas parsed
AAS initialized.
-----------------------------------
loaded skill 1 from bots/default_c.c
loaded skill 1 from bots/crash_c.c
loaded skill 4 from bots/default_c.c
loaded skill 4 from bots/crash_c.c
loaded bots/crash_i.c
loaded bots/crash_w.c
loaded crash from bots/crash_t.c
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce4 MX Integrated GPU/AGP/SSE/3DNOW!
GL_VERSION: 1.5.8 NVIDIA 96.43.01
GL_EXTENSIONS: GL_ARB_imaging GL_ARB_multitexture GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shared_texture_palette GL_EXT_stencil_wrap GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_fence GL_NV_fog_distance GL_NV_light_max_exponent GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_register_combiners GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_NV_texture_rectangle GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_SGIS_generate_mipmap GL_SGIS_multitexture GL_SGIS_texture_lod GL_SUN_slice_accum 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_ACTIVE_TEXTURES_ARB: 2

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 3, 640 x 480 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: disabled
Initializing Shaders
...loading 'scripts/lightningnew.shader'
...loading 'scripts/explode1.shader'
...loading 'scripts/gfx.shader'
...loading 'scripts/tim.shader'
...loading 'scripts/base.shader'
...loading 'scripts/base_button.shader'
...loading 'scripts/base_floor.shader'
...loading 'scripts/base_light.shader'
...loading 'scripts/base_object.shader'
...loading 'scripts/base_support.shader'
...loading 'scripts/base_trim.shader'
...loading 'scripts/base_wall.shader'
...loading 'scripts/common.shader'
...loading 'scripts/ctf.shader'
...loading 'scripts/eerie.shader'
...loading 'scripts/gothic_block.shader'
...loading 'scripts/gothic_floor.shader'
...loading 'scripts/gothic_light.shader'
...loading 'scripts/gothic_trim.shader'
...loading 'scripts/gothic_wall.shader'
...loading 'scripts/hell.shader'
...loading 'scripts/liquid.shader'
...loading 'scripts/menu.shader'
...loading 'scripts/models.shader'
...loading 'scripts/organics.shader'
...loading 'scripts/sfx.shader'
...loading 'scripts/shrine.shader'
...loading 'scripts/skin.shader'
...loading 'scripts/sky.shader'
...loading 'scripts/test.shader'
----- finished R_Init -----
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
Loading vm file vm/cgame.qvm.
VM file cgame compiled to 786818 bytes of code
cgame loaded in 5380768 bytes on the hunk
stitched 0 LoD cracks
...loaded 4806 faces, 46 meshes, 43 trisurfs, 128 flares
^3WARNING: could not find sound/player/announce/UnnamedPlayer.wav - using default
^3WARNING: could not find sound/player/crash/taunt.wav - using default
CL_InitCGame:  4.53 seconds
11 msec to draw all images
Com_TouchMemory: 0 msec
UnnamedPlayer^7 entered the game
Crash^7 entered the game
Crash^7: ^2Feel my shrieking rocket blast in your gibs!
Received signal 15, exiting...
Shutdown tty console
faktorqm@theship:~$ 

```

Crash me disparo........:(:( ok. 

Sigo con sonido ok. Tambien aclaro que no tengo xgl, y/o si lo tengo no lo se. :confused: como puedo saber eso?

Gracias again!!

---

### Post by faktorqm on 2007-12-12
Hola, bueno, me lei media internet mas o menos...... lo unico que encontre, que puede ser factible que este pasando, es que me falta un archivo, en ambos post se repite

```
couldn't exec autoexec.cfg
```

alguien que juegue quake 3 arena seria tan amable de facilitarme el archivo ese y su ubicacion? o decirme de donde lo puedo inventar/generar?

Desde ya mil gracias!!!!!!!!!! :D

---

### Post by facundocorradini on 2007-12-12
Instalate Open Arena man...

---

### Post by faktorqm on 2007-12-12
Claro, pero como muy bien dice el titulo del post, yo quiero Quake 3 Arena. Salu2!

---

### Post by Mr.Linc on 2007-12-12
Lo que me parece extraño es esto que veo en tu proceso de instalación:
> - Luego hacemos "unzip -x quake3-1.32c.zip" y copiamos EL CONTENIDO DE la carpeta "linux" en /usr/local/games/quake3/
¿Qué es eso? ¿Algún add-on, algún hack, alguna cosa rara? Porque por lo que veo en los pasos previos, estás instalando el Point Release 1.32b que es el correspondiente, y estás compiando el archivo pak0.pk3 como corresponde. Y así debería andar lo más bien. Pero toda esa parte entera que acabo de citar no debería existir.

No me parece que sea incompatible la placa de video, sino no te dejaría siquiera entrar al juego.
Aceleración gráfica tenés, porque sino no podrías usar el compiz.
La placa de video es la misma que yo tengo, y aparentemente los drivers son los que corresponden.

El mensaje de *"couldn't exec autoexec.cfg"* es la respuesta que te da por una gran variedad de posibles problemas, pero todos esos problemas tienen en común que no se ha hecho bien la instalación, por eso no puede llevar a cabo ese paso.

Por las dudas, antes de intentar la instalación de nuevo, borrá toda la carpeta quake3 de /usr/local/games, y en tu /home, poné la opción para que se vean los archivos ocultos y borrá la carpeta .q3a, así después iniciás una instalación limpia.

Y te diría que primero instales el linuxq3apoint-1.32b-3.x86.run, dejando que el instalador cree todas las carpetas, y después copiá el pak0.pk3. Y nada más, ningún .zip; y probá.

Te comento cómo lo instalé yo, en cada una de las versiones desde el Ubuntu 6.10 hasta ahora; probablemente los fundamentalistas del foro se burlen como se burlan de todos los que no hacen las cosas como ellos, pero acá va. Sirve igual si usás un CD original o trucho, yo lo tengo original.

[LIST]
[*]Pongo el linuxq3apoint-1.32b-3.x86.run en la carpeta /home, o da lo mismo en cualquier lado.
[*]Abro la consola, hago *gksudo nautilus*.
[*]A través del Nautilus que se abre voy hasta donde está el linuxq3apoint-1.32b-3.x86.run y vía botón derecho del mouse, propiedades, permisos, le chequeo la casilla para permitir ejecutar el archivo como programa.
[*]Doble click en el archivo y le doy a la opción de ejecutar.
[*]Ahí se me instala en /usr/local/games/quake3
[*]Ahora meto el CD del Q3A y desde el mismo Nautilus abierto de antes, copio el pak0.p3 a /usr/local/games/quake3/baseq3
[*]Listo.
[/LIST]

---

### Post by faktorqm on 2007-12-13
> **Mr.Linc said:**
> Lo que me parece extraño es esto que veo en tu proceso de instalación:

¿Qué es eso? ¿Algún add-on, algún hack, alguna cosa rara? Porque por lo que veo en los pasos previos, estás instalando el Point Release 1.32b que es el correspondiente, y estás compiando el archivo pak0.pk3 como corresponde. Y así debería andar lo más bien. Pero toda esa parte entera que acabo de citar no debería existir.


No es nada mas ni nada menos que el parche 1.32c. Son 3 binarios precompilados, para linux, mac y windows. Este parche es oficial y esta en el ftp de id software, es la ultima version digamos del q3a. lo que pasa es que me parece que los tipos no querian sacar un ".run" mas para que no les rompan las bo**s con la compatibilidad, pero en windows la ultima es la 1.32c.
Como veras lo unico que quiero es jugar al juego clásico digamos. (no a mods baratos que usen el motor.................................. ¬¬)

> **Mr.Linc said:**
> No me parece que sea incompatible la placa de video, sino no te dejaría siquiera entrar al juego.
Aceleración gráfica tenés, porque sino no podrías usar el compiz.
La placa de video es la misma que yo tengo, y aparentemente los drivers son los que corresponden.

Coincidimos. El driver es el propietario, instalado a traves del envy. Te comento por las dudas si no te habias fijado en nvidia, que el driver es ultima version tambien, y se ha discontinuado. Asi que para nuestras placas "legacy" ya no va a haber mas actualizaciones de drivers. (hora de actualizar?)


> **Mr.Linc said:**
> 
Y te diría que primero instales el linuxq3apoint-1.32b-3.x86.run, dejando que el instalador cree todas las carpetas, y después copiá el pak0.pk3. Y nada más, ningún .zip; y probá.

Te comento cómo lo instalé yo, en cada una de las versiones desde el Ubuntu 6.10 hasta ahora; probablemente los fundamentalistas del foro se burlen como se burlan de todos los que no hacen las cosas como ellos, pero acá va. Sirve igual si usás un CD original o trucho, yo lo tengo original.

[LIST]
[*]Pongo el linuxq3apoint-1.32b-3.x86.run en la carpeta /home, o da lo mismo en cualquier lado.
[*]Abro la consola, hago *gksudo nautilus*.
[*]A través del Nautilus que se abre voy hasta donde está el linuxq3apoint-1.32b-3.x86.run y vía botón derecho del mouse, propiedades, permisos, le chequeo la casilla para permitir ejecutar el archivo como programa.
[*]Doble click en el archivo y le doy a la opción de ejecutar.
[*]Ahí se me instala en /usr/local/games/quake3
[*]Ahora meto el CD del Q3A y desde el mismo Nautilus abierto de antes, copio el pak0.p3 a /usr/local/games/quake3/baseq3
[*]Listo.
[/LIST]


Bueno, hasta aca, una sola consulta antes de hacer lo que me dijiste, cuando te sale el instalador, supuestamente necesita del pak0.pk3 para descomprimir los archivos en las carpetas. Como es que lo instala igual? En todos los tutoriales que vi siempre antes creaban todo y luego copiaban el pak0.pk3 y recien ahi le daban al instalador.... igual obvio que voy a hacer lo que me dijiste.
Desde ya mil gracias por responder, lo pruebo y te digo. :KS Salu2!

---

### Post by Mr.Linc on 2007-12-13
El instalador no necesita nada, hacé la prueba y vas a ver, crea las carpetas por sí mismo.
Creo que el instalador tiene la opción de copiar el pak0.pk3 durante la instalación (ya no me acuerdo, creo que es un casillero para marcar o desmarcar), pero él mismo crea las carpetas.
Probá instalando primero el PR 1.32b y después copiando el pak0.pk3, con la línea de comandos o como quieras.

El otro parche (1.32c) no es necesario ni para el funcionamiento offline ni para jugar online, así que podés obviarlo.

No es necesario que sigas las instrucciones detalladas que puse... hacelo a tu manera a través de comandos, pero en el orden de poner primero el PR y después copiar el pak0. Lo demás, por ridículo que parezca mi "método de instalación", lo puse porque a veces de ahí sale algo útil o le funciona a alguien.

Saludos. :)

---

### Post by Mister X on 2007-12-14
Me hiciste dar ganas de jugar al viejo y querido Quake 3 en linux, jaja, asi que me puse a instalarlo.
Por el error "couldn't exec autoexec.cfg" no te preocupes, no creo que tenga algo que ver con tu problema, a mi tambien me aparece el error.
Proba editando el archivo de configuracion ~/.q3a/baseq3/q3config.cfg
y pone el valor 0 en la linea :
```
 seta r_fullscreen "0"
```
y fijate si en modo windowed tenes el mismo problema.

---

### Post by faktorqm on 2007-12-15
Bueno, parece que tengo malas noticias.... Instale de todas formas el q3, como root, como user, etcetcetc y sigue pasando exactamente lo mismo. Puse lo del modo windowed y pasa lo mismo, solo que me muestra negra una ventania no mas xDxD gracias igual.

Ahora bien, aqui LA RAREZA: Lo instale en Windows para ver como andaba..... Y PASA LO MISMO QUE EN LINUX!! yo la verdad que no lo puedo creer, pero bueno. Asi que mire con bastante seriedad los drivers de nvidia, que las versiones anteriores tanto en win como en lin andaban perfectamente y ahora parece que no. Voy a buscar por internet a ver si alguien dice algo de los drivers nuevos.

Ahora ni siquiera en win me anda :(:(:(:( salu2!!

---

### Post by SLA_leandrin on 2007-12-15
Pregunta medio tonta,

probaste instalarlo en otra PC desde el mismo DVD? No será problema del pak0.pak o algo así???? Digo, para descartar eso...

---

### Post by Mister X on 2007-12-15
Sep, coincido con SLA_leandrin, parece mas algun archivo corrupto del Quake mas que otra cosa, trata de conseguir otro pak0.pak

saludos

---

### Post by faktorqm on 2007-12-16
Hola, no no eso no es por que anda josha. Les cuento como detecte el problema:
Me fui a guin y no andaba, entonces me acorde del viejo y querido "dxdiag". Bueno, fui haciendo todas las pruebas, y cuando hago las de direct 3D, me tira, primera prueba interfaces 7, josha, la segunda interfaces 8, se veia cualquier cosa, la tercera, interfaces 9, cualquier cosa.
Fui al solucionador de problemas, y me recomendaba que baje la frecuencia de actualizacion del monitor, ya me di cuenta de antemano que eso no era, pero lo hice igual por que con m$ nunca se sabe. y no resulto.
Me fui a la pagina de nvidia, me baje la version 91.31 del driver, desintale la otra, reinicie, etc y seguia lo mismo. entonces me di cuenta de que le problema era algo mas importante, asi que instale la version 77.71. Y ahi anduvo perfecto el dxdiag y el quake 3 arena. :D

Ahora bien, como veo que es un problema del driver de nvidia, en linux pasa algo parecido entonces. Como hago para desinstalar el driver este que tengo e instalar la version vieja? Vale la pena instalar la version vieja solo por un juego? Que pierdo? Voy a ver el envy si me puede ayudar.

Mil gracias y saludos!!

p.d.: Cada vez que compro un cd original, automaticamente le saco una iso, y anoto el serial en un txt y con algun iso manager lo agrego a la iso en la raiz del cd. Si le pasa algo al cd original, lo tiro y grabo otro. Por eso les decia que no era el tema del pak0.pak. salu2!!

---

### Post by SLA_leandrin on 2007-12-16
> **faktorqm said:**
> 

p.d.: Cada vez que compro un cd original, automaticamente le saco una iso, y anoto el serial en un txt y con algun iso manager lo agrego a la iso en la raiz del cd. Si le pasa algo al cd original, lo tiro y grabo otro. Por eso les decia que no era el tema del pak0.pak. salu2!!

OK... es la falta de costumbre sobre CDs originales, los únicos que tengo son los del Ubuntu :rolleyes:

---

### Post by faktorqm on 2007-12-17
desde el envy me deja instalar el driver 71.XX pero dice instalacion manual..... yo lo quiero es que me lo instale el envy :S alguien uso esa opcion o voy a experimentar? salu2!

---

### Post by faktorqm on 2007-12-19
Hola, comento acá cómo solucioné el problema:

Agarré y con el envy instalé el driver version 71.XX. Y como no podia ser de otra manera, se me cayó el escritorio. Al parecer, no soporta compiz o algo por el estilo. Arranqué con el metacity y de ahi instale XGL para acelerar. Reinicié y no andaba, al parecer el xorg.conf se había roto. Le puse mi copia de backup (el que anda) y lo mismo, me tiraba error. Asi que fusioné el posta con el nuevo y ahora tengo un nuevo xorg.conf posta v2. Todo se activo de maravillas y volvió a ser como era antes.
El Quake 3 Arena, anda perfecto. 

Varias cosas al respecto: Los efectos me andan igual de bien que antes, pero el AWN anda super lentisimo, al igual que el 90% de las aplicaciones. Hasta el Amsn tarda una banda en redibujar la ventana, lo cual es un problema gravisimo.
Será que estoy usando el frame buffer y no lo sé? como lo puedo averiguar?
Otra: el Quake 3 es IMPOSIBLE jugarlo con los efectos activados. tengo entendido que es normal. Tengo un AMD Athlon XP 2600+ Barton con 512MB de RAM DDR 400mhz, GeForce 4 MX de 128MB, juego a 1280x1024@32, 75hz. En guin anda perfecto, en linux ANDA MAS RAPIDO. Con los efectos activados parece que lo estoy corriendo en una 486...... :mad:

Me parece que lo que voy a hacer es volver al driver 94.XX y jugar en otro lado..... con wine andara? no tengo ganas de reinstalar este ubuntu, e instalar otro pelado solo para jugar q3a, Salu2!!!!!!!

---

