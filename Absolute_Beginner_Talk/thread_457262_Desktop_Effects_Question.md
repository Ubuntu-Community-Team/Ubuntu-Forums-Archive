---
title: "Desktop Effects Question"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by kimcheefreak17 on 2007-05-28
I've got a question about whether or not it is possible to have Desktop Effects with my graphics card. I've got an ATI Radeon 9600. I assume it's possible, but for some reason when I try to enable them, I get a message saying I can't enable desktop effects. 

Any insight/help would be greatly appreciated. Thanks!

---

### Post by Hobo Joe on 2007-05-28
Yes you can, but you may not have drivers properly installed. 

Paste the output of:
```

glxinfo

```

---

### Post by kimcheefreak17 on 2007-05-28
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by DJ Wings on 2007-05-28
Add "Load dri" to the modules section of /etc/X11/xorg.conf.

---

### Post by kimcheefreak17 on 2007-05-28
Sorry about this completely newbie question, but how do you open that? (/etc/x11/xorg.conf)
Is the command *Xorg -configure* ? Because if it is, I get this error message: Fatal server error:

Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by notquitemichael on 2007-05-28
you just need to open /etc/X11/xorg.conf as a root user, I'd reccomend you make a back up first,

i.e.: from terminal assuming your using ubuntu

sudo cp /etc/X11/xorg.conf xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

when the text editor appears find the section that starts with Modules, copy, paste the line, and save and close.

Then logout and press CTRL - ALT - BACKSPACE at the same time (this restarts the X-server) if any problems arise just ok through the blue error screen, press CTRL - ALT - F1 (opens a kinda terminal.) login and type:

sudo cp /etc/X11/xorg.conf.backup xorg.conf

(i.e. replace with the backup) restart your computer and try to figure out what's wrong.

hope that was some help :)

---

### Post by den benne on 2007-05-28
you have to open the "xorg.conf" file with a text editor
if you're using gnome, you can use gedit
to edit the xorg-file you will need root priviliges. the easiest way to do this, is the "sudo" command

try typing this in a terminal:
sudo gedit /etc/X11/xorg.conf

EDIT: appears I was a little bit slow; use the advise above, especially the backup isn't a bad idea ;)

---

### Post by kimcheefreak17 on 2007-05-28
Hmm... I did just that, but it still says I can't use desktop effects...

Do you think it would hurt to reinstall Feisty and start from scratch?

---

### Post by notquitemichael on 2007-05-28
before you do that, go to the restricted driver bit (somewhere in the system area) and check you don't need to install a restricted driver to get the effects (like most nvidia cards.)

also i suggest you read this:
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)

i know it's for nvidia, but if your at the point of reinstalling feisty, it's worth a try. personally, if you want some desktop effects, i would reccomend you have at look at the beryl project in any case.

good luck. :)

---

### Post by kimcheefreak17 on 2007-05-28
I just reinstalled Feisty... That didn't help much. Now when I try to turn on the Background Effects, well, the menu doesn't even open. It says "The Composite Extension is Not Available". :(

---

