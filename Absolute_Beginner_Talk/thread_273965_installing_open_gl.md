---
title: "installing open gl"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by blkdragon on 2006-10-09
i was wondering what you would need (hardware, software etc) to installl open gl. most of the games i play use it and i have no idea on how to install it, or what you need for it.

---

### Post by Rhubarb on 2006-10-09
Software wise, Open GL should already be working for you, in Ubuntu / Kubuntu / Xubuntu.  An easy way to find out is buy opening the terminal and typing:
```
glxgears
```
You'll see some Open GL rendered gears on the screen.
If you want to play some games, then you'll need a good video card.
What games would you be playing?
What spec PC are you currently running?

---

### Post by amo-ej1 on 2006-10-09
hardware won't be any issue, almost any video card supports it, and those lacking support will fall back to software rendering (which is offcourse way slower).

try providing us the output of 'glxinfo' and 'lspci'

---

### Post by blkdragon on 2006-10-09
> **Rhubarb said:**
> 
If you want to play some games, then you'll need a good video card.
What games would you be playing?
What spec PC are you currently running?

im currently running a 366Mhz P2 with 128mb ram, and as for a good video card, well...it has 256kb of memory. then again, the game i had in mind was only [Xmoto]("http://xmoto.sourceforge.net/"), so i think its okay...

---

### Post by amo-ej1 on 2006-10-09
can you paste the output you get when you run xmoto from commandline ?

---

### Post by blkdragon on 2006-10-09
> **amo-ej1 said:**
> 
try providing us the output of 'glxinfo' and 'lspci'

glxinfo outputs:

```
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
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x2e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x31  8 pc  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  0 0 None
0x32  8 gs  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  0 0 None
0x33  8 sc  0 24  0 c  y  .  3  3  2  0  0 16  0  0  0  0  0  0 0 None
0x34  8 tc  0  8  0 r  y  .  3  3  2  0  0 16  0  0  0  0  0  0 0 None
0x35  8 tc  0  8  0 r  y  .  3  3  2  0  0 16  8 16 16 16  0  0 0 None
0x36  8 tc  0 16  0 r  y  .  3  3  2  8  0 16  8 16 16 16 16  0 0 None
0x37  8 tc  0 16  0 r  .  .  3  3  2  8  0 16  8 16 16 16 16  0 0 None
0x38  8 dc  0  8  0 r  y  .  3  3  2  0  0 16  0  0  0  0  0  0 0 None
0x39  8 dc  0  8  0 r  y  .  3  3  2  0  0 16  8 16 16 16  0  0 0 None
0x3a  8 dc  0 16  0 r  y  .  3  3  2  8  0 16  8 16 16 16 16  0 0 None
0x3b  8 dc  0 16  0 r  .  .  3  3  2  8  0 16  8 16 16 16 16  0 0 None
0x3c  8 sg  0 24  0 c  y  .  0  0  0  0  0 16  0  0  0  0  0  0 0 None


```

lspci outputs:

```
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
0000:00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
0000:00:0c.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
0000:00:0d.0 Multimedia controller: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder (rev 02)

```

thx for the help.

---

### Post by blkdragon on 2006-10-09
> **amo-ej1 said:**
> can you paste the output you get when you run xmoto from commandline ?

it dosent work... i need to fix the dependencies first, one of them being OpenGL.

---

### Post by oskarloko on 2006-10-09
But if you can run glxgears I think you have installed opengl...
Maybe you'll need SDL and OpenGL to Linux games.

DSL it's 'like' DirectX, for every system, build on GLP

[http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
[http://www.opengl.org/](http://www.opengl.org/)

---

### Post by amo-ej1 on 2006-10-09
What dependencies ? Simply pull it from apt ?

```

root@lap:/tmp# apt-get install xmoto
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libode0c2 libsdl-mixer1.2 libsmpeg0 xmoto-data
The following NEW packages will be installed:
  libode0c2 libsdl-mixer1.2 libsmpeg0 xmoto xmoto-data
0 upgraded, 5 newly installed, 0 to remove and 27 not upgraded.
Need to get 6242kB of archives.
After unpacking 8667kB of additional disk space will be used.
Do you want to continue [Y/n]? 


```

And indeed it's SDL based. It shouldn't give you any issues pulling this from apt and running it. (altough speed might be an issue :p)

---

### Post by oskarloko on 2006-10-09
Well, if SDL is not needed, just better... ( I'm at work, using a heretic xp :oops: ). I really don't know if xmoto uses SDL or OpenGL...

Using ```
apt-get,apitude,synaptic
``` to install a new game is the safe way... it install whatever it needs.

If you install a game from source or from an installer (downloaded from webpage ) just chek install requeriments... and make a apt-get with the names of the packages. 99% will work


Also, can look at
[http://www.ubuntuforums.org/showthread.php?t=80367&highlight=opengl](http://www.ubuntuforums.org/showthread.php?t=80367&highlight=opengl)


And for games...
[http://gaming.gwos.org/](http://gaming.gwos.org/)

Open your system, gates no needed ;)

---

### Post by blkdragon on 2006-10-09
hey thx guys.

im not a hoome right now but when i get home ill try

```

sudo apt-get install xmoto
```

thx for the help.

---

### Post by blkdragon on 2006-10-10
would you believe, it works

albeit very,very slowly.

would there be any way to fix the speed?

a friend said something about editing xorg.conf for dri.

im in the dark here.

---

### Post by Weedman on 2006-10-13
Your friend is here.

Now what happened was, I got a copy of his xorg.conf, and checked for DRI having been enabled as a module, for which it was.

However, thanks to his *lspci* output, I was able to pinpoint the problem. His graphics card, which is one that utilises the 'neomagic' driver, cannot & never has worked with DRI.

So, blkdragon, you are stuck with mesa-based 3D with that laptop.

weed

---

### Post by blkdragon on 2006-10-15
yeh. i understand it.

oh well.

thats what you get for having a ~crappy laptop.

---

