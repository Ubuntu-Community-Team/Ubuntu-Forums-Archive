---
title: "Controladors privatius ATI R9550"
date: 2007-10-23
forum: Catalan Team
---

### Post by raukonak on 2007-10-23
Hola a tothom,

He instal·lat el driver privatiu d'ati9 amb una ati radeon 9550 utilitzant el gestor de controladors restringits. No m'ha donat cap error i al tornar a entrar he pogut activar el compizfusion sens cap problema. Però després li he donat un glxinfo i em surt això:

:~$ glxinfo
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


O com jo he entès, que no tinc l'acceleració gràfica activada. Com que m'ha semblat estrany he fet un glxgears i m'ha donat això:

:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
19976 frames in 5.0 seconds = 3989.381 FPS
19980 frames in 5.0 seconds = 3995.998 FPS
20039 frames in 5.0 seconds = 3991.939 FPS
19787 frames in 5.0 seconds = 3955.167 FPS
19667 frames in 5.0 seconds = 3919.125 FPS


I que jo recordi, quan feia servir el driver lliure amb Feisty (No vaig arribar mai a ser capaç de configurar el privatiu sense que em petessin les X) com a molt m'anava a 1000FPS, He instal·lat el xserver-xgl, hi ha alguna cosa que em manqui per instalar? Que vol dir Xlib: extension....? Ho he mirat una mica pel google però no ho he acabat d'entendre, a cada pagina donen una solució diferent.

Moltes gràcies

---

