---
title: "Radeon Mobility X1600 and Direct rendering using open source ATI drivers"
date: 2007-08-02
forum: Apple Intel Users
---

### Post by {{corona}} on 2007-08-02
Hi I have this setup working
fglrx ATI drivers + XGL + compiz
Now I don't have direct rendering working with that setup.

What I would like to have is compiz with direct rendering enabled, so that I can do some opengl based programming.
I have read that using the open source ATI drivers one can have direct rendering. Can someone please point me to thread where this is discussed?

Thanks
p.s logging into normal gnome session without XGL gives me DRI. What I want is DRI with XGL or AIXGL and compiz

---

### Post by benanzo on 2007-08-02
I can't help much with ATI problems, but I was under the impression that the Free *radeon* driver supports AIGLX out-of-the-box on certain GPUs.  This might not be true for the X1600 though.  I have a Radeon Mobility 7500 in my old Dell notebook and AIGLX, DRI, Compiz/Beryl work great with zero effort using the Free *radeon* driver which loads by default.

---

### Post by cyberdork33 on 2007-08-02
> **benanzo said:**
> I was under the impression that the Free *radeon* driver supports AIGLX out-of-the-box on certain GPUs.  This might not be true for the X1600 though.

That would be a no, it does not, at least not on these Macs.

I might be wrong, but I think that direct rendering works with fglrx. The problem is when you run XGL. This causes it to report that direct rendering is not enabled. Additionally, you have to use XGL because fglrx does not support compositing, nor does it work with AIGLX, so you are pretty much stuck with it the way it is unless you can convince ATI to fix their drivers.

As far as the open source drivers, none of them work on Macs that I know of.

---

### Post by {{corona}} on 2007-08-02
Thanks for the reply. Yes I haven't been able to find any help on sorting this problem. I guess sometime soon the updated drivers will work. I'll post back if i find something.

---

### Post by nlz on 2008-03-02
i don't have a macbook but an 'normal laptop' (asus s96j), but with the same video card. 

Did anyone try to install the new ATI driver ati-driver-installer-8-02-x86.x86_64.run from the ATI website?

I'm also hoping to get direct rendering working...

---

### Post by cyberdork33 on 2008-03-02
> **nlz said:**
> i don't have a macbook but an 'normal laptop' (asus s96j), but with the same video card. 

Did anyone try to install the new ATI driver ati-driver-installer-8-02-x86.x86_64.run from the ATI website?

I'm also hoping to get direct rendering working...

Yes, this thread is quite old. ATI drivers should work fine. Use [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by nlz on 2008-03-03
well, envy directs to a file that doesn't exist anymore (old driver). So is it okay to install it manually, and does direct rendering work then?

---

### Post by ronocdh on 2008-03-03
> **nlz said:**
> well, envy directs to a file that doesn't exist anymore (old driver). So is it okay to install it manually, and does direct rendering work then?
Give it a go and let us know your take on it. Worst case, you can always yank the new drivers you got from the site and then manually reinstall fglrx from the repos.

---

### Post by cyberdork33 on 2008-03-03
> **nlz said:**
> well, envy directs to a file that doesn't exist anymore (old driver). So is it okay to install it manually, and does direct rendering work then?I don't know what you mean... It should work fine. You need the legacy version if you are using Gutsy. 

Some output from envy would be helpful.

---

### Post by nlz on 2008-03-03
envy said something like:
couldn't fetch driver ati-driver-installer-8-01-x86 etc etc, download it yourself.
Then i went to the ati website and downloaded the driver for the radeon mobility x1600 and this was ati-driver-installer-8-02-x86 . That was why envy didn't work. 

I want to try it out, but this is also our only work laptop, and since we are working in rural ethiopia now, there are not so many resources. So my work partner will kill me if he cannot work for a day because of my nightly linux expiriments.

'Just download the old driver' takes about 6 hours... Sorry, for not being so expirimental, it are the circumstances..

these are my read outs BTW

fgrlxinfo
```
qnuf@mediaction:~$ fgrlxinfo
bash: fgrlxinfo: command not found
qnuf@mediaction:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```

fglrxinfo -display :1
```
qnuf@mediaction:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

glxinfo
```
name of display: :1.0
display: :1  screen: 0
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```



xorg.conf
```

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
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
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

Section "Extensions"
        Option          "Composite"     "Enable"
        Option          "Composite"     "0"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

To be clear: everything is working fine, except for direct rendering, which i just don't understand..

---

### Post by cyberdork33 on 2008-03-03
It's odd that fglrx is reporting on display 1 but not display 0. Are you running Gutsy? and the driver from the repos? 

If you really want to install manually, then you can follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually)

The "outdated" fglrx driver should still be a good link even though a newer version is out. I just tested it.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run)

---

### Post by tuwe on 2008-03-03
> **nlz said:**
> envy said something like:
couldn't fetch driver ati-driver-installer-8-01-x86 etc etc, download it yourself.
Then i went to the ati website and downloaded the driver for the radeon mobility x1600 and this was ati-driver-installer-8-02-x86 . That was why envy didn't work. 

I want to try it out, but this is also our only work laptop, and since we are working in rural ethiopia now, there are not so many resources. So my work partner will kill me if he cannot work for a day because of my nightly linux expiriments.

'Just download the old driver' takes about 6 hours... Sorry, for not being so expirimental, it are the circumstances..

these are my read outs BTW

fgrlxinfo
```
qnuf@mediaction:~$ fgrlxinfo
bash: fgrlxinfo: command not found

```
.

> **cyberdork33 said:**
> It's odd that fglrx is reporting on display 1 but not display 0. Are you running Gutsy? and the driver from the repos? 

If you really want to install manually, then you can follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually)

The "outdated" fglrx driver should still be a good link even though a newer version is out. I just tested it.
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-01-x86.x86_64.run)

it's not that odd if you see the typo: it says fgrlxinfo (instead of fglrxinfo)
i'd stick to the 8-01 driver, if possible. at least  for me (running gutsy) the 8.02 driver did not work at all.

---

### Post by cyberdork33 on 2008-03-03
> **tuwe said:**
> it's not that odd if you see the typo: it says fgrlxinfo (instead of fglrxinfo)I wasn't talking about the typo. He did the command correctly, and it reported Mesa... then he did the command specifying display 1 and it reported ATI correctly...

---

### Post by tuwe on 2008-03-04
> **cyberdork33 said:**
> I wasn't talking about the typo. He did the command correctly, and it reported Mesa... then he did the command specifying display 1 and it reported ATI correctly...

oh dear, i didn't seem to finish reading his post, sorry :)

as far as i can see, the first two lines of glxinfo report ```
name of display: :1.0
display: :1  screen: 0
```, which i think causes the problem with fglrxinfo. i don't know of any solution though.

furthermore, i think there's something wrong with the extensions section of xorg.conf, it says ```
Section "Extensions"
        Option          "Composite"     "Enable"
        Option          "Composite"     "0"
EndSection
```, i'd comment it out completely. the modules section below that looks quite short as well.

here's the corresponding part of my working xorg.conf (macbook pro 2,2, ati radeon mobility x1600):
```
Section "DRI"
    Mode 0666
EndSection

#Section "Extensions"
#     Option "Composite" "Disable"
#EndSection

Section "Module"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "dri"
    Load "extmod"
    Load "freetype"
    Load "glx"
    Load "int10"
    Load "vbe"
    Load "synaptics"
EndSection

```

hope this helps

---

