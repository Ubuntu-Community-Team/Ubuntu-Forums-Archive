---
title: "Canvi en la resolució de pantalla"
date: 2012-06-23
forum: Catalan Team
---

### Post by joaquimrubio on 2012-06-23
Ubuntu 12.04.
Al jugar a certs jocs (M'ha passat amb Open Arena i Trencaclosques de Einstein), es modifica la resolució de pantalla, la tinc per defecte a 1280 x 1024 i es canvia a molta menor resolució, veig les icones molt més grans. Si tanco el joc, em queda aquesta resolució de pantalla errònia i no puc treballar. Si apago l'ordinador i el torno a engegar, la resolució de pantalla s'arregla sola, per tant no és un problema greu, però si ho pogués arreglar, millor. 

He comprovat que al menú *Tots els paràmetres - Pantalles  *hi ha una pantalla que no és la meva, hi apareix la *Goldstar Company Ltd 17"*, quan la meva és una *Flatron L1718S*.
La opció de "Detecta les pantalles" no respon res, segueix havent-hi la pantalla Goldstar Company Ltd 17".

No sé si té res a veure amb no poder canviar el color de fons de l'escriptori, no ho he aconseguit i no sé si és error meu o hi ha quelcom que no funciona.

---

### Post by wgarcia on 2012-06-26
Sembla que aquests jocs tenen una opció de canvi de resolució de pantalla. Hauries de mirar en els menús de configuració del joc si trobes alguna cosa relacionada i intentar entrar la resolució que utilitzes al sistema, a veure si això arregla el problema.

---

### Post by joaquimrubio on 2012-06-26
No he sabut trobar aquest menú de configuració. Hi ha una entrada que posa options però només deixa triar si vols tota la pantalla o no i si vols en cursor normal o un d'especial. Si clico amb el botó dret del ratolí, per anar a un submenú de configuracions, el que succeeix és que s'engega el joc, amb el corresponent canvi de resolució de pantalla.
Amb la mateixa torre, el mateix Ubuntu 12.04 però des de l'escriptori KDE, curiosament, no hi ha aquest problema.

---

### Post by joaquimrubio on 2012-06-26
No sé si m'he explicat bé, volia dir que si situo el cursor sobre la icona del joc i clico sobre el botó dret del ratolí per anar a algun menú contextual, el resultat és que també s'engega el joc. (A l'escriptori Unity, que en contra d'opinions llegides al fòrum a mi sí que m'agrada, no he trobat menús amb el botó dret, no sé si és una nova característica d'aquest escriptori. Tampoc ho he esbrinat gaire).

---

### Post by wgarcia on 2012-06-27
No conec les configuracions d'openarena, però fent una cerca ràpida sembla que hi ha un error reportat a la distribució Debian, i per tant segurament també afecta a l'Ubuntu:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668771](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668771)

S'ho estan mirant i per tant si hi ha sort resoldran l'error en algun moment i s'actualitzarà a l'Ubuntu, però pot trigar una mica.

A un missatge d'aquest informe diu que l'usuari ha trobat una manera de solucionar-ho mentre que no es resolgui definitivament, però no diu exactament com ho fa, diu que llença l'openarena des d'una terminal i fa servir la comanda "xrandr":

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668771#44](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668771#44)

Per algun altre lloc he vist que la possible comanda pot ser:

```
openarena;xrandr -s 1 ; xrandr -s 0
```

És qüestió de provar a veure si corrent l'openarena així resol el problema de tornar a la resolució de pantalla original. Si funciona també es pot provar amb l'altre joc que menciones.

---

### Post by joaquimrubio on 2012-06-27
Moltes gràcies, wgarcia.

La comanda rep la següent resposta: 

can't open 

I la resolució no es rectifica.

Amb el Puzzle d'Einstein, el problema s'ha arreglat parcialment, ara no canvia la resolució de pantalla però queda de mida més petita. No en tinc cap prova però la intuició em diu que té a veure amb la instal·lació de l'escriptori KDE, ja que és l'única modificació del S.O. que he fet (no han arribat actualitzacions d'Ubuntu) i perquè al KDE l'Einstein funciona sense modificar la resolució de pantalla, funciona bé.

No és un problema greu ja que reiniciant la resolució s'arregla, m'esperaré que arribi l'actualització de kernel que correspongui. 
Wgarcia, et reitero l'agraïment per tot el temps i l'esforç que m'has dedicat.

---

### Post by wgarcia on 2012-06-27
Si sols entres "openarena" a la terminal, què surt?

---

### Post by joaquimrubio on 2012-06-29
Teclejo openarena al terminal i premo "enter".

El terminal va mostrant informació que no entenc i que aparentment es repeteix i a continuació, sense cap mes actuació meva, s'engega el joc, que puc jugar perfectament amb el so correcte. Quan voluntàriament tanco el joc, torno a l'escriptori amb el terminal obert i la resolució de pantalla ha canviat. Tancant i tornant a engegar, la resolució s'arregla.

A la terminal surt això (ho envio en diverses respostes ja que no m'ho admet en un de sol):

joaquim@joaquim-G31M-ES2L:~$ openarena
ioq3 1.36+svn2202-1/Ubuntu linux-x86_64 Dec 12 2011
Have SSE support
----- FS_Startup -----
Current search path:
/home/joaquim/.openarena/baseoa
/usr/lib/games/openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)

----------------------
4722 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
Trying to load "renderer_opengl1_x86_64.so" from "/usr/lib/ioquake3"...
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.250
...setting mode -1: 580 427
Using 8/8/8 Color bits, 24 depth, 8 stencil display.
Available modes: '1280x1024 640x480 800x600 832x624 1024x768 1152x864 720x400'
GL_RENDERER: Mesa DRI Intel(R) G33 
Initializing OpenGL extensions
...GL_EXT_texture_compression_s3tc not found
...GL_S3_s3tc not found
...using GL_EXT_texture_env_add
...using GL_ARB_multitexture
...using GL_EXT_compiled_vertex_array
...ignoring GL_EXT_texture_filter_anisotropic

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) G33 
GL_VERSION: 1.4 Mesa 8.0.2
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_rectangle GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_EXT_separate_shader_objects GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_robustness 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 580 x 427 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
------ Initializing Sound ------
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear

---

### Post by joaquimrubio on 2012-06-29
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Allocated 96 sources.
OpenAL default capture device is 'PulseAudio Default'
OpenAL capture device opened.
OpenAL info:
  Vendor:         OpenAL Community
  Version:        1.1 ALSOFT 1.13
  Renderer:       OpenAL Soft
  AL Extensions:  AL_EXT_DOUBLE AL_EXT_EXPONENT_DISTANCE AL_EXT_FLOAT32 AL_EXT_IMA4 AL_EXT_LINEAR_DISTANCE AL_EXT_MCFORMATS AL_EXT_MULAW AL_EXT_MULAW_MCFORMATS AL_EXT_OFFSET AL_EXT_source_distance_model AL_LOKI_quadriphonic AL_SOFT_buffer_sub_data AL_SOFT_loop_points
  ALC Extensions: ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_disconnect ALC_EXT_EFX ALC_EXT_thread_local_context
  Device:         PulseAudio Default
  Available Devices:
PulseAudio Default
So integrat Estèreo analògic via PulseAudio
ALSA Default
HDA Intel [ALC883 Analog] (hw:0,0) via ALSA
HDA Intel [ALC883 Digital] (hw:0,1) via ALSA
PortAudio Default
No Output
  Input Device:   PulseAudio Default
  Available Input Devices:
PulseAudio Default
Monitor of So integrat Estèreo analògic via PulseAudio
So integrat Estèreo analògic via PulseAudio
ALSA Default
HDA Intel [ALC883 Analog] (hw:0,0) via ALSA
HDA Intel [ALC883 Analog] (hw:0,2) via ALSA
PortAudio Default
Sound initialization successful.
--------------------------------
Loading vm file vm/ui.qvm...
File "vm/ui.qvm" found in "/usr/lib/games/openarena/baseoa/pak6-patch085.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch085/ui
... trying ui
Loading DLL file /usr/lib/games/openarena/baseoa/uix86_64.so instead.
Loading DLL file: /usr/lib/games/openarena/baseoa/uix86_64.so
Sys_LoadGameDll(/usr/lib/games/openarena/baseoa/uix86_64.so) found vmMain function at 0x7f81cb520b30
51 arenas parsed
1 arenas ignored to make count divisible by 4
24 bots parsed
^3WARNING: unknown blend mode 'gl_one_minus_dst_color' in shader 'menuback_blueish', substituting GL_ONE
--- Common Initialization Complete ---
IP: 127.0.0.1
IP: 192.168.1.130
IP6: ::1
IP6: fe80::21f:d0ff:fe12:4378%eth0
Opening IP6 socket: [::]:27960
Opening IP socket: 0.0.0.0:27960
------ Server Initialization ------
Server: oa_rpg3dm2
RE_Shutdown( 0 )
Hunk_Clear: reset the hunk ok
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) G33 
GL_VERSION: 1.4 Mesa 8.0.2
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_rectangle GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_EXT_separate_shader_objects GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_robustness 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 580 x 427 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
----- FS_Startup -----
Current search path:
/home/joaquim/.openarena/baseoa
/usr/lib/games/openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)

----------------------
4722 files in pk3 files
Loading vm file vm/qagame.qvm...
File "vm/qagame.qvm" found in "/usr/lib/games/openarena/baseoa/pak6-patch085.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch085/qagame
... trying qagame
Loading DLL file /usr/lib/games/openarena/baseoa/qagamex86_64.so instead.
Loading DLL file: /usr/lib/games/openarena/baseoa/qagamex86_64.so
Sys_LoadGameDll(/usr/lib/games/openarena/baseoa/qagamex86_64.so) found vmMain function at 0x7f81ca9e7480
------- Game Initialization -------
gamename: baseoa
gamedate: Aug  9 2011
Not logging to disk.
Gametype changed, clearing session data.
^3!readconfig: ^7could not open admin config file admin.dat
Sprees/Kills: loaded 1 killing sprees, 0 death sprees, and 0 multikills.
0 teams with 0 entities
16 items registered
-----------------------------------
------- BotLib Initialization -------
loaded weapons.c
loaded items.c
loaded syn.c
loaded rnd.c
loaded match.c
loaded rchat.c
------------ Map Loading ------------
trying to load maps/oa_rpg3dm2.aas
loaded maps/oa_rpg3dm2.aas
found 32 level items
-------------------------------------
24 bots parsed
51 arenas parsed
AAS initialized.
-----------------------------------
loaded skill 1 from bots/default_c.c
loaded skill 1 from bots/sarge_c.c
loaded bots/sarge_i.c
loaded bots/sarge_w.c
loaded sarge from bots/sarge_t.c
loaded cached skill 1.000000 from bots/default_c.c
loaded skill 1 from bots/ayumi_c.c
loaded bots/ayumi_i.c
loaded bots/ayumi_w.c
loaded Ayumi from bots/ayumi_t.c
loaded cached skill 1.000000 from bots/default_c.c
loaded skill 1 from bots/kyonshi_c.c
loaded bots/kyonshi_i.c
loaded bots/kyonshi_w.c
loaded kyonshi from bots/kyonshi_t.c
RE_Shutdown( 0 )
----- R_Init -----

GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) G33 
GL_VERSION: 1.4 Mesa 8.0.2
GL_EXTENSIONS: GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_shadow GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_half_float_pixel GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_rectangle GL_EXT_pixel_buffer_object GL_EXT_texture_rectangle GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_EXT_gpu_program_parameters GL_OES_EGL_image GL_ARB_copy_buffer GL_ARB_map_buffer_range GL_EXT_separate_shader_objects GL_ARB_ES2_compatibility GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_provoking_vertex GL_ARB_sampler_objects GL_EXT_provoking_vertex GL_ARB_robustness 
GL_MAX_TEXTURE_SIZE: 2048
GL_MAX_TEXTURE_UNITS_ARB: 8

PIXELFORMAT: color(24-bits) Z(24-bit) stencil(8-bits)
MODE: -1, 580 x 427 fullscreen hz:N/A
GAMMA: hardware w/ 0 overbright bits
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_NEAREST
picmip: 1
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: enabled
compressed textures: disabled
Initializing Shaders
----- finished R_Init -----
Loading vm file vm/ui.qvm...
File "vm/ui.qvm" found in "/usr/lib/games/openarena/baseoa/pak6-patch085.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch085/ui
... trying ui
Loading DLL file /usr/lib/games/openarena/baseoa/uix86_64.so instead.
Loading DLL file: /usr/lib/games/openarena/baseoa/uix86_64.so
Sys_LoadGameDll(/usr/lib/games/openarena/baseoa/uix86_64.so) found vmMain function at 0x7f81cb520b30
51 arenas parsed
1 arenas ignored to make count divisible by 4
24 bots parsed
^3WARNING: unknown blend mode 'gl_one_minus_dst_color' in shader 'menuback_blueish', substituting GL_ONE
Loading vm file vm/cgame.qvm...
File "vm/cgame.qvm" found in "/usr/lib/games/openarena/baseoa/pak6-patch085.pk3"
...which has vmMagic VM_MAGIC_USE_NATIVE.
... trying pak6-patch085/cgame
... trying cgame
Loading DLL file /usr/lib/games/openarena/baseoa/cgamex86_64.so instead.
Loading DLL file: /usr/lib/games/openarena/baseoa/cgamex86_64.so
Sys_LoadGameDll(/usr/lib/games/openarena/baseoa/cgamex86_64.so) found vmMain function at 0x7f81ca3b7af8
^3WARNING: Failed to load sound sound/items/invul_activate.wav!
^3WARNING: Using default sound for sound/items/invul_activate.wav
^3WARNING: Failed to load sound sound/items/invul_impact_01.wav!
^3WARNING: Using default sound for sound/items/invul_impact_01.wav
^3WARNING: Failed to load sound sound/items/invul_impact_02.wav!
^3WARNING: Using default sound for sound/items/invul_impact_02.wav
^3WARNING: Failed to load sound sound/items/invul_impact_03.wav!
^3WARNING: Using default sound for sound/items/invul_impact_03.wav
^3WARNING: Failed to load sound sound/items/invul_juiced.wav!
^3WARNING: Using default sound for sound/items/invul_juiced.wav
^3WARNING: Failed to load sound sound/items/cl_ammoregen.wav!
^3WARNING: Using default sound for sound/items/cl_ammoregen.wav
^3WARNING: Failed to load sound sound/weapons/nailgun/wnalimpd.wav!
^3WARNING: Using default sound for sound/weapons/nailgun/wnalimpd.wav
^3WARNING: Failed to load sound sound/weapons/vulcan/wvulimpd.wav!
^3WARNING: Using default sound for sound/weapons/vulcan/wvulimpd.wav
^3WARNING: Failed to load sound sound/weapons/vulcan/wvulimpl.wav!
^3WARNING: Using default sound for sound/weapons/vulcan/wvulimpl.wav
^3WARNING: Failed to load sound sound/weapons/vulcan/wvulimpm.wav!
^3WARNING: Using default sound for sound/weapons/vulcan/wvulimpm.wav
^3WARNING: Failed to load sound sound/misc/yousuck.wav!
^3WARNING: Using default sound for sound/misc/yousuck.wav
stitched 40 LoD cracks
...loaded 4106 faces, 90 meshes, 0 trisurfs, 0 flares
WARNING: reused image textures/flares/flarey.tga with mixed glWrapClampMode parm
^3WARNING: Failed to load sound sound/player/announce/UnnamedPlayer.wav!
^3WARNING: Using default sound for sound/player/announce/UnnamedPlayer.wav
^3WARNING: Failed to load sound sound/player/announce/Sarge.wav!
^3WARNING: Using default sound for sound/player/announce/Sarge.wav
^3WARNING: Failed to load sound sound/player/announce/Jenna.wav!
^3WARNING: Using default sound for sound/player/announce/Jenna.wav
Leg skin load failure: models/players/characters/ayumi/lower_jenna.skin
Torso skin load failure: models/players/characters/ayumi/upper_jenna.skin
Head skin load failure: models/players/heads/ayumi/head_jenna.skin
Failed to load skin file: ayumi : jenna, ayumi : jenna
^3WARNING: Failed to load sound sound/player/announce/Kyonshi.wav!
^3WARNING: Using default sound for sound/player/announce/Kyonshi.wav
CL_InitCGame:  3.64 seconds
13 msec to draw all images
Com_TouchMemory: 0 msec
UnnamedPlayer^7 entered the game
Kyonshi^7 entered the game
Jenna^7 entered the game
Sarge^7 entered the game
Sarge^7 was gunned down by UnnamedPlayer^7
Jenna^7 was gunned down by UnnamedPlayer^7
----- Server Shutdown (Server quit) -----
==== ShutdownGame ====
AAS shutdown.
---------------------------
----- FS_Startup -----
Current search path:
/home/joaquim/.openarena/baseoa
/usr/lib/games/openarena/baseoa
/usr/lib/games/openarena/baseoa/pak6-patch085.pk3 (559 files)
/usr/lib/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/lib/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/lib/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/lib/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/lib/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/lib/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/lib/games/openarena/baseoa/pak0.pk3 (1042 files)

handle 1: video/idlogo.roq
----------------------
4722 files in pk3 files
----- Client Shutdown (Client quit) -----
Wrote challenges.cfg
RE_Shutdown( 1 )
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3c00012
  Serial number of failed request:  210
  Current serial number in output stream:  212
joaquim@joaquim-G31M-ES2L:~$

---

### Post by wgarcia on 2012-07-01
Quan tens un resultat molt extens que vols enganxar, convé fer-ho amb alguns dels serveis lliures que hi ha, i aquí sols posar l'enllaç. 

Ubuntu té un servei propi, [http://paste.ubuntu.com/](http://paste.ubuntu.com/), sinó també pots fer servir [http://pastebin.com](http://pastebin.com) que és el més utilitzat. 

En quant al tema en concret, jo crec que el millor és esperar a veure com evoluciona l'error que citava més a baix de Debian, tampoc és un error greu, simplement empipa haver de sortir i tornar a entrar en tancar el joc.

---

### Post by joaquimrubio on 2012-07-01
Gràcies, wgarcia.

El resultat és en aquest enllaç:

[http://pastebin.com/embed_js.php?i=SRhkGrFp](http://pastebin.com/embed_js.php?i=SRhkGrFp)

(no he pogut comprovar que funcioni).

No sé com puc esborrar els 2 posts.

El tema de la resolució de pantalla quedarà en espera fins que es resolgui amb una actualització.

Ja he acabat les instal·lacions del 12.04 al fix i 1 portàtil. Un milió de gràcies al fòrum i en especial a wgarcia per tot l'esforç, temps i paciència que m'heu dedicat. Sou un exemple formidable d'altruisme.

Joaquim

---

### Post by wgarcia on 2012-07-01
Gràcies joaquimrubio, l'enllaç funciona perfectament. No fa falta esborrar els altres dos missatges, i en tot cas jo tampoc no ho puc fer (em sembla que sols els administradors ho poden fer). 

A veure si hi ha sort aviat amb la resolució d'aquest problema.

---

