---
title: "notebook freezes -&gt; can reproduce it"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by ivo_second on 2006-07-18
Hardware:  Fujitsu p2120
Distro:    ubuntu dapper

hi folk,

before I installed dapper I used libranet, a commercial distribution.
Because libranet does not exist anymore, I decided to try ubuntu. 
Suspend to disk and so on works very well. I have only one problem, my notebook freezes sometimes.

When does it freeze:

If I work for a longer time (randomly).
While Installing dapper and playing around with some tools.
If I open the adobe acrobat reader.

What I have tried out so far:

check the memory -> all ok;
googled half a day -> was not able to grep the key information

What happens if it freezes:

No user input is possible.
Even the power off button (Hardware, controlled by acpi) does not work.
Display is freezed, mouse does not move nor does anything else.

Can I somehow check what happens if I start adobe acrobat reader?

thx for any help

Ivo

---

### Post by Paerez on 2006-07-18
I got this when I was running the radeon driver for my ati video card and it was not doing direct rendering. What kind of video card do you have?

---

### Post by ivo_second on 2006-07-18
I use the following card

0000:00:14.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

I have loaded the radeon driver in the xorg.conf. I changed it back 
to the ATI one -> but still crashes.

How do you got DRI working? Played around with it but had no luck.

Thx for your answer

---

### Post by Paerez on 2006-07-18
I just enabled it in the xorg.conf. I am using mesalibgl1 from the compiz repos, but I don't know if that is what helped.

---

### Post by ivo_second on 2006-07-19
I do not know why, but my system seems to work stable since I copied
your xorg.conf into my /etc/X11 folder. I simply had to change the bus
ID and your config file worked great. 

But the dri still does still not work. XFree86-DRI is missing. 
Do I have to install an other Xorg server?

name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

Thx a lot for your help

Ivo

---

### Post by Paerez on 2006-07-19
search in synaptic for "mesa" and there is something that is like "mesalibgl1-dri". The important thing is that it has "mesa" "lib" and "dri" in the name. I had to install that, and also I had to uninstall xorg's fglrx driver.

But, make sure you install the mesa before uninstalling the fglrx driver. I had some apt trouble when I removed fglrx and then tried to re-install mesa. Hopefully it was just me.

---

### Post by MiniZiper on 2006-07-19
> **Paerez said:**
> I got this when I was running the radeon driver for my ati video card and it was not doing direct rendering. What kind of video card do you have?

I have the same video card, DRI is enale, and sometimes LInux freezes out of nowhere. It freezes when I use normal firefox (not with swiftfox or opera or konqueror) it froze like 3 times upon startup, until I reformated and change CPU... So, how do I fix this?? I'm kinda of a newbie ](*,)  

Help!!! PLz :)

---

### Post by Paerez on 2006-07-19
post this for me please:
```
grep Device /etc/X11/xorg.conf
glxinfo | grep Rendering
lsmod | grep radeon
lsmod | grep fglrx

```
thanks

---

### Post by MiniZiper on 2006-07-19
> **Paerez said:**
> post this for me please:
```
grep Device /etc/X11/xorg.conf
glxinfo | grep Rendering
lsmod | grep radeon
lsmod | grep fglrx

```
thanks

[COLOR="DarkOrange"]Section "InputDevice"
Section "InputDevice"
        Option          "Device"                "/dev/input/mice"
Section "InputDevice"
  Option        "Device"        "/dev/wacom"          # Change to
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
Section "InputDevice"
  Option        "Device"        "/dev/wacom"          # Change to
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
Section "InputDevice"
  Option        "Device"        "/dev/wacom"          # Change to
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
Section "Device"
        Device          "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
miniziper@miniziper-kubuntu:~$ glxinfo | grep Rendering
miniziper@miniziper-kubuntu:~$ lsmod | grep radeon
radeon                116000  0
drm                    73236  1 radeon
miniziper@miniziper-kubuntu:~$ lsmod | grep fglrx
miniziper@miniziper-kubuntu:~$   [/COLOR]        

Two of the codes didn't show anything. Your xorg.conf has the radeon  driver enabled. I have the "ati" driver enabled. I haven't changed it, to avoid screwing up ^^

---

### Post by MiniZiper on 2006-07-19
I did glxinfo, just in case:
[COLOR="DarkOrange"]name of display: :0.0
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
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None[/COLOR]

---

### Post by Paerez on 2006-07-19
I'm sorry I messed those up, but you gave me what I needed. The only problems I saw was when someone used "radeon" for their drier, so I don't know whats wrong with yours. Sorry.

---

### Post by MiniZiper on 2006-07-19
Well, My Laptop is much more stable than before. So it's not even critical. I have googled this for a while now... How do I enable DRI on this? I love google earth, but it runs at 1/2 frames per second because of Indirect Rendering... and glxgears barely move...

---

### Post by Paerez on 2006-07-19
you will have to switch to the radeon driver instead of ati, and you need the "mesalibgl1-dri" package (i think thats the name, just search for mesa)

---

### Post by MiniZiper on 2006-07-19
I have libgl1-mesa-dri already installed.... acording to adept. and thats the only thing with "DRI". so, should I change drivers now? or im still missign something?

---

### Post by MiniZiper on 2006-07-20
I changed from "Ati" to "radeon" on xorg.conf... I did glxinfo, and still... no direct rendering...

---

### Post by Paerez on 2006-07-20
i have the compiz repositories enabled, maybe that is how I am getting direct rendering...

Is there a DRI section in your xorg.conf? Mine looks like this and its at the end:
```
Section "DRI"
	Mode	0666
EndSection
```

---

### Post by ivo_second on 2006-07-20
Thx for your help, my system works great.

What I also had to do was to remove the unused input devices.
My system had a problem with the wacom stuff in xorg.conf.
The wacom entry was always the last before my system crashed.

The goal for the DRI stuff was to remove the fglrx drivers, as 
you said.

Can use google earth now!!!!!!   :-D

---

### Post by Paerez on 2006-07-20
sweet! I am gonna try google earth, since last time I tried it, I was on the ATI non-DRI drivers. Glad you got it going!

---

### Post by MiniZiper on 2006-07-20
Oh, so you have to delete the flgx or w/e drivers to get "DRI" ?? and yes i do have the DRI section on xorg.conf... its just like yours... So how do I remove the flgx or w/e drivers??

---

### Post by Paerez on 2006-07-21
to remove fglrx:
```
sudo aptitude remove xorg-driver-fglrx
```

---

### Post by MiniZiper on 2006-07-21
and.. how do u make sure ur using mesa?? so when i uninstall it, x will start up...

---

### Post by MiniZiper on 2006-07-21
this is weird, this si what i got:
[COLOR="DarkOrange"]miniziper@miniziper-kubuntu:~$ sudo aptitude remove xorg-driver-fglrx
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
miniziper@miniziper-kubuntu:~$[/COLOR]

---

### Post by MiniZiper on 2006-07-21
wait a minute... i don't have fglrx installed! or the control thing. thats what adept reports. so why am i still unable to have DRI???

---

### Post by Paerez on 2006-07-21
you need to install mesalibgl1-dri, then switch your xorg to the radeon driver.

---

### Post by MiniZiper on 2006-07-21
I do have libgl1-mesa-dri.... and my xorg.conf does have radeon driver on... My control setting reports that my graphics card and the driver are called radeon. I uploaded my xorg.conf so you can see if i'm missing something...

sorry to bother, but I really want DRI :mrgreen: 

THanks for the help so far!

---

### Post by Paerez on 2006-07-21
I just wrote a howto for xgl/compiz on the mobility 9x00 cards. If you follow step 1, that gets you dri. Then you can ignore step 2, which is the xgl compiz stuff.
[http://www.ubuntuforums.org/showthread.php?p=1277210#post1277210](http://www.ubuntuforums.org/showthread.php?p=1277210#post1277210)

---

### Post by ivo_second on 2006-07-22
thx for spending so much time writing this tutorial. 
will try it out soon.

Ivo

---

