---
title: "how can i see if i have have 3d acceleration?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-22
hello, can someone tell me if my ATI video drivers are all up to date and can handle games like Savage?


the reason im asking is when I launch savage it sends me back after 3 seconds to the place i launched it from.

this is the code 

admin@admin-desktop:~$ cd /home/admin/games/Savage
admin@admin-desktop:~/games/Savage$ ./savage
System_Init()
Unknown command: '/home/admin/games/Savage'
admin@admin-desktop:~/games/Savage$

somone one help?

---

### Post by orb9220 on 2006-09-22
type in a term

glxinfo

---

### Post by crunchystrike on 2006-09-22
i typed that in, this is what it tells me:

admin@admin-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
admin@admin-desktop:~$

---

### Post by YeahBuntu on 2006-09-22
forum prowling here sorry to interupt... what is savage and .. if I type that command in my terminal .. it shoots a bunch of stuff out.  What am I looking for that tells me if I have game capabilities?

---

### Post by crunchystrike on 2006-09-22
savage is a video game, now can somone help me out with my problem? kind of annoying when only one person posts, and no one else posts after.

---

### Post by crunchystrike on 2006-09-22
bump

---

### Post by orb9220 on 2006-09-22
Just read down and you will see the line that says

direct rendering: No

So you most likely you cannot play the game.

"kind of annoying when only one person posts, and no one else posts after."

I think if you want help in the future you need to curb your desire for instant satifacation. People here are quite helpful when they know the answer to your problem.

If you want to learn how to play games, Then my advice would be for you to learn enough to understand how linux works first.

Sorry I couldn't be more help,

---

