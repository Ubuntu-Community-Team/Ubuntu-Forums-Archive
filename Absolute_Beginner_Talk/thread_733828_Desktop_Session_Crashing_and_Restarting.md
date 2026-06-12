---
title: "Desktop Session Crashing and Restarting"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-03-24
Hi Community,

Long time Linux lover, but first time Linux user... :lolflag:

I've got my first Linux distro working on my Acer Extensa 5220 as I got sick of Vista and wanted to try a whole new Desktop environment as I was also sick of having to find cracks for Windows software and use them "illegally".

Ubuntu so far has been awesome, but I do have one problem.  My session always crashes when I run an app with 3D, such as;  Google Earth, 3D Tanks, etc.  But everything else runs perfect, "ESPECIALLY" my Compiz Fusion... I love that!!

Can someone enlighten me as to what I should do with this issue I'm having please.

Here are my specs;  [http://www.acer.com.au/acer/akc/portablepc.nsf/Page/RWPF2D97F75D3893C36CA2573620049801B?open&current=8.3&ms=expand&](http://www.acer.com.au/acer/akc/portablepc.nsf/Page/RWPF2D97F75D3893C36CA2573620049801B?open&current=8.3&ms=expand&)

---

### Post by jslman on 2008-03-24
Can you run one of these applications from a terminal and put the output here, if it generates errors they will be visible in the terminal.

Jeroen

---

### Post by kolisikepu on 2008-03-24
> Can you run one of these applications from a terminal and put the output here, if it generates errors they will be visible in the terminal.

Jeroen

Hi Jeroen,

I've just tried both and my session just crashes.... example;  with Google, as soon as it starts, my screen goes black and brings me to the login screen.  Likewise with my Scorched3D game...  I just noticed though with the game, it runs in a small screen, but as soon as it is maximised, HELLO LOGIN SCREEN.  :lolflag:  ... it's annoying me.

Regards,

Chris

---

### Post by jslman on 2008-03-24
And if you give the commmand glxgears?

```

glxgears -info

```

Jeroen

---

### Post by kolisikepu on 2008-03-24
> And if you give the commmand glxgears?

Code:

glxgears -info



Yeah... the killed my session and booted me out to the login screen again.  :confused::confused:

---

### Post by jslman on 2008-03-24
Well, that's working great! :twisted:
Other option, what is the output of:

```

glxinfo

```

Jeroen

---

### Post by kolisikepu on 2008-03-24
Sorry Jeroen... you're talking to a Linux newbie here.  How do I get the output for 'glxinfo' like you requested??

---

### Post by kolisikepu on 2008-03-24
> **kolisikepu said:**
> Sorry Jeroen... you're talking to a Linux newbie here.  How do I get the output for 'glxinfo' like you requested??

Sorry... my bad!!  Silly, of course I know how to do that!!  :lolflag:

Here you go.  I hope it makes sense to you.

name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

Regards,

Chris

---

### Post by jslman on 2008-03-24
```

jeroen@portable-pinguin:~$ glxinfo
name of display: :2.0
Xlib:  extension "XFree86-DRI" missing on display ":2.0".
display: :2  screen: 0
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
OpenGL renderer string: ATI Mobility Radeon X1600
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
jeroen@portable-pinguin:~$

```
This is what happens when I use the command, in a terminal.

No problemo, we all have to start at some point in time :-)

---

### Post by kolisikepu on 2008-03-24
Sorry J... I just posted my reply above yours after realising what you were asking.  hahaha...

---

### Post by jslman on 2008-03-24
please post you /etc/X11/xorg.conf. You can do that you giving the command:

```

cat /etc/X11/xorg.conf

```

Jeroen

---

### Post by jslman on 2008-03-24
My first question had to be, what type of videocard do you have? :-)

Jeroen

---

### Post by kolisikepu on 2008-03-24
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by kolisikepu on 2008-03-24
I forgot to mention... I also did this hack to get Compiz working with my video card.

[http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php](http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php)

I don't know if this hack is causing the issue, but I can't image so.

---

### Post by jslman on 2008-03-24
Does look fine, please try the following. Go the menu >>System >> Preferences >> Appearance and go to the final tab. There select No visual effects. No try to run glxgears again. Do you still have the same problem?

Jeroen

---

### Post by jslman on 2008-03-24
> **kolisikepu said:**
> I forgot to mention... I also did this hack to get Compiz working with my video card.

[http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php](http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php)

I don't know if this hack is causing the issue, but I can't image so.

Yeah, that is what I'm thinking, that since the X3100 is blacklisted it screws up all other acceleration... 

Jeroen

---

### Post by kolisikepu on 2008-03-24
Unfortunately J... I still do have the same problem with any visual affects. :(

---

### Post by jslman on 2008-03-24
Kolisi, 

I'm sorry to say that I ran out of options. I've searched the web for some solution but all I get is that the X3100 doesn't work well in Ubuntu 7.10 in combination with Compiz. Also I understand that these problems are resolved in Ubuntu 8.04 Hardy, but this is in Beta still. You could try the live cd for this beta to try it out though [Download]("http://releases.ubuntu.com/releases/8.04/ubuntu-8.04-beta-desktop-i386.iso"). 

Also I have read that PCLinuxOS Gnome works fine with the X3100 card. I hope you'll find a solution somewhere. 

Greetings Jeroen

---

### Post by kolisikepu on 2008-03-24
J,

You're the best for even trying.  I've Googled all over the place as well to try and fix this issue.

I might be patient anyways and wait for Hardy since it's only around the corner.  If I get impatient, I'll try the Beta version of it.

Dank u wel Jeroen.

---

### Post by jslman on 2008-03-24
No problem m8, waimaria

Jeroen

---

