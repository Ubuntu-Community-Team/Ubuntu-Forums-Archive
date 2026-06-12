---
title: "desktop effects and emerald"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ubunt22rock on 2007-10-28
hey i installed compizfusion in my ubuntu7.10

i checked the boxes in a few fields including cubes..but there's no difference

i also tried to install emerald theme manager following instructions from ubuntu documentations...but an error message comes...

please help me get cool effects and themes

---

### Post by Crafty Kisses on 2007-10-28
> **ubunt22rock said:**
> hey i installed compizfusion in my ubuntu7.10

i checked the boxes in a few fields including cubes..but there's no difference

i also tried to install emerald theme manager following instructions from ubuntu documentations...but an error message comes...

please help me get cool effects and themes

Post the following output:
```
glxinfo
```

---

### Post by ubunt22rock on 2007-10-28
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_shader_texture_lod, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

---

### Post by daimaru on 2007-10-28
first enable your restricted driver to get full 3D support.
then under preferences -- > advanced desktop effects settings enable all the stuff you want + if you want a rotating cube you have to set your workspaces to 4 not the default 2.
also make sure you installed the compizconfig-settings-manager

---

### Post by ubunt22rock on 2007-10-28
@daimaru

i have done everything u have instructed me to already...i have problems after all that

---

### Post by daimaru on 2007-10-28
sorry , i'm also guessing that the glx module is loaded in the xorg.conf right and that you have rebooted since you installed compiz ? when i first installed i only logged out and back in and after enabling all the stuff like cube and rotate nothing happend either for me until i rebooted

---

### Post by ubunt22rock on 2007-10-28
i just rebooted and did ctrl+alt+right arrow

no use

---

### Post by daimaru on 2007-10-28
ok last try otherwise i cant help you (to much of a noob too) did compiz load at all? 
```
ps aux |grep compiz
ap        8243  0.0  0.0   1752   536 ?        S    16:53   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
ap        8349  0.5  2.3  79416 47808 ?        SL   16:53   0:24 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 ccp
ap        8967  0.0  0.0   2976   752 pts/0    R+   18:13   0:00 grep compiz

```
thats what i get . if its not loaded do 
```
compiz --replace
``` 
and lastly where i got instructions to install from:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

sry i cant help out more:(

---

### Post by ubunt22rock on 2007-10-28
hey thats ok...
btw compiz --replace also showed errors...
thanks anyway


others pls give ur suggestions

---

### Post by llamakc on 2007-10-28
Share the errors.

---

### Post by ubunt22rock on 2007-10-28
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 





so i had to ctrl+z and stop it

---

### Post by llamakc on 2007-10-28
Ctrl-z stops the process but does not kill it. If you open a terminal and type "fg" you'll bring the process back to the foreground.

You may have wanted CTRL-c

---

### Post by ubunt22rock on 2007-10-28
oh thanks a lot


btw if u can help me wid desktop effects n emerald pls let me know...am all ears...
thanks

---

### Post by llamakc on 2007-10-28
Do Desktop Effects work without Emerald? Do you have them enabled yet?

---

### Post by ubunt22rock on 2007-10-28
apparently they do and i have enabled them in ccms

but in appearance preference wen i select normal or extra under visual effects an error dialogue reading "the composite extension not available" pops up

but the outcome::no cool effects[:(]

---

### Post by daimaru on 2007-10-28
did you try what the guy in this thread did to get his ati working with glx ? 
[http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+glx]("http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+glx")
cant miss it its halfway down with the big font saying "Before we begin -- supported hardware list"
EDIT: and just so we can get a better picture could you post your /etc/X11/xorg.conf file plz

---

### Post by ubunt22rock on 2007-10-28
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

---

### Post by ubunt22rock on 2007-10-28
and i cant make out wat that guy has done xactly from that link

---

### Post by daimaru on 2007-10-28
ok your composite extension is turned off "0" set it to "1" and also post your output from 
```
fglrxinfo
```

---

### Post by daimaru on 2007-10-28
> **ubunt22rock said:**
> and i cant make out wat that guy has done xactly from that link

in synaptic check that xserver-xgl is installed

---

### Post by llamakc on 2007-10-28
I have an ATI card and fglrx gives me fits every now and then. So much that I gave up on it and just use the radeon o/s driver instead.

Here's my relevant parts of my xorg.conf

My modules.

```

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
        Load            "dbe"
EndSection

```

My device.

```

Section "Device"
        Identifier        "ATI Technologies Inc Radeon rv370"
        Driver                "radeon"
        BusID                "PCI:5:0:0"
        Option          "XAANoOffscreenPixmaps"
#        Option "AGPMode" "4"
#        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

```

The end of my file. I don't have compositing enabled (because it breaks).

```

Section "DRI"
        Mode    0666
EndSection
#Section "Extensions"
#Option         "Composite"     "Enable"
#EndSection

```

If I run the command (in the terminal)

```

ps aux | grep compiz

```

I see this:

```


ken@llamakc 01:00:10:~$  ps aux |grep compiz
ken      29584  0.0  0.1   4408  1644 ?        S    11:35   0:00 /bin/sh /usr/bin/compiz --sm-client-id 117f000101000119352032100000066180000
ken      29770  0.1  1.2  18604 12588 ?        S    11:35   0:07 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id 117f000101000119352032100000066180000 ccp
ken      30621  0.0  0.0   2976   752 pts/0    R+   13:02   0:00 grep compiz

```

So, if YOU run "ps aux | grep compiz" what does it return?

---

### Post by daimaru on 2007-10-28
@ubunt22rock
you have your compiz extension disabled so it wont work enable it

---

### Post by ubunt22rock on 2007-10-28
fglrx gave


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)
 

and even after i changed my composite status to 1 in xorg.conf...its showing the same error...

do i need to reboot xserver??

---

### Post by daimaru on 2007-10-28
definately have to reboot xserver after changes to xorg.conf

---

### Post by ubunt22rock on 2007-10-28
ps aux | grep compiz returns



adhithya 18697  0.0  0.0   2976   744 pts/0    S+   23:44   0:00 grep compiz

---

### Post by daimaru on 2007-10-28
yeah compiz is not loaded 
also check if the module glx is loaded in your xorg.conf file as you can see in  llamakc  's conf file

```
Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
        Load            "dbe"
EndSection
```

---

### Post by ubunt22rock on 2007-10-28
hey guys luvz to u...its workin after i rebooted my xserver


i owe it to u

thanks a million..

codename  llamakc daimaru and all others


i ll check everything out and if i still have hiccups i ll get bak to u

thanks a lot

---

### Post by daimaru on 2007-10-28
i just remembered from my days with ATI and beryl that back then you had to disable composite extension with the fglrx driver, but i dont know if anything changed since then. why dont you try the radeon driver as illmas did just paste the relevant sections into your xorg.conf file make a backup of your xorg.conf before you do that because you might get xserver errors after reboot. 

make a backup :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-mybackup
```
then if you cant log into graphical desktop anymore and end up at the terminal or some error message you hit ctrl+alt+F2 to go to terminal login as your username and password then copy back your old xorg.conf file 

```
sudo cp /etc/X11/xorg.conf-mybackup /etc/X11/xorg.conf
```
and reboot

---

### Post by daimaru on 2007-10-28
oops then forget whtat i just posted , took me too long to write so i missed your posst

---

