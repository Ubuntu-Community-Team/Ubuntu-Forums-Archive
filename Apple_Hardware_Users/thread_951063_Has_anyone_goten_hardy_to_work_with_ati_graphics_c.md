---
title: "Has anyone goten hardy to work with ati graphics card."
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by crapple on 2008-10-17
I have a apple ppc with an ati radeon 7500. I know the graphics card driver is the problem. Does anyone know how to get this card to work. I have gotten it to work up to gutsy. In gutsy i used an older version of the drivers. In hardy however when I try this it will not work. 
Thanks

---

### Post by crapple on 2008-10-21
Anyone. It is also the radeon 7000 series not just my card

---

### Post by stevand on 2008-10-21
Hi there,
I have a similar problem,  I run 8.04 Hardy
the info from the glxinfo says

stevand@stevand-desktop:~/Desktop/tetgen$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.7412 Release
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_texgen_reflection, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, 
    GL_WIN_swap_hint, WGL_EXT_swap_control

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
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x48 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x49 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x4a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
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
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x67 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x68 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x69 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x70 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x71 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x72 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x85 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  8 1 Ncon



However, I can not use Paraview and a lot of other applications. Namely, when I click with the mouse on the application the figure shows and then it is gone .. so it is initialized only on mouse .... otherwise is just a one fuzzy color. Does anyone know can we fix this ... I have not had this problems with Drake ...
thanks

---

### Post by ppc_guy on 2008-10-22
Right there with ya guys, I've tried everything from 6.06 up on my G4/450pci and my Lombard/G3/333 and nothing yet, everything seems to go great until a stalled black screen, but I'll let you know if I find anything.

As always your mileage may vary,
----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
----------------------------------------------------------------------

---

### Post by mfox on 2008-10-22
I think that the issue is with the 7500 card, not Radeon cards in general.  My PowerBook G4 Al has a Radeon mobility 9700 card in it, and Ubuntu installs and runs OK on it.  I did have to invoke a video command when the install disk booted up at first, however.

---

### Post by crapple on 2008-10-26
The problem is with the new ati open source driver.  The last version that worked was 6.6.3-2.  If you install that version in 7.10 it works.  In 8.4 if you install it forcing all it works in low graphics.  The same with interpid which I heard was supposed to get a new driver.

Any ideas on how to fix the new driver?

---

### Post by oswaldkelso on 2008-10-26
I had problems with the new xorg on my Debian testing box. emac ppc ati radion 7500. I don't have it now but my posts are in these threads they may provide some pointers? 

[http://forums.debian.net/viewtopic.php?t=27139](http://forums.debian.net/viewtopic.php?t=27139)
[http://forums.debian.net/viewtopic.php?t=26577](http://forums.debian.net/viewtopic.php?t=26577)

---

### Post by wayne_n on 2008-10-27
It might be a PPC issue.  I am running 8.04 Hardy on a Mac Pro with ATI x1900 XT and it flickers from time to time, but it works.

---

### Post by paul_mcl on 2008-10-27
Yep, I have Radeon 7500 (PCI version) too. The following xorg.conf works fine for me (taken from Yellow Dog then modified):

```

# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
        Identifier      "XFree86 Configured"
        Screen          0 "Screen0" 0 0
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Keyboard0" "CoreKeyboard"
        Option          "OffTime" "10"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)

       RgbPath		"/usr/share/X11/rgb.txt"
      #FontPath		"/usr/share/X11/fonts/misc:unscaled"
      #FontPath		"/usr/share/X11/fonts/Type1/"
      #FontPath		"/usr/share/X11/fonts/Speedo/"
      #FontPath		"/usr/share/X11/fonts/75dpi:unscaled"
      #FontPath		"/usr/share/X11/fonts/100dpi:unscaled"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "freetype"
        Load            "type1"
        #Load           "dri"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:caps_toggle"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "ZAxisMapping"  "4 5"
        Option          "Protocol"      "IMPS/2"
        Option          "Device"        "/dev/input/mice"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        ModelName       "Monitor Model"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-60
EndSection

Section "Device"
        Identifier      "Card0"
        #Option         "ShadowFB"      "true"
        #Option         "fbdev"         "/dev/fb0"
        Driver          "fbdev"
        #BusID          "PCI:0:16:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection

```

---

### Post by crapple on 2008-10-30
It works in Hardy!!!!!!!!!!!!!!

But Intrepid gives error parsing file any idea why.

---

### Post by cyberdork33 on 2008-10-30
> **crapple said:**
> It works in Hardy!!!!!!!!!!!!!!

But Intrepid gives error parsing file any idea why.
Might have to give more info than that. When you boot and it fails, information should be found in /var/log/Xorg.0.log

---

### Post by crapple on 2008-11-01
Here is what the log said

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.15-51-powerpc64-smp ppc Ubuntu
Current Operating System: Linux biggie3linux 2.6.25-2-powerpc #1 Tue Sep 30 14:49:00 UTC 2008 ppc
Build Date: 24 October 2008  08:07:47AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@ross.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  1 11:14:54 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open APM successful
(II) Loader magic: 0x101d55e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 9

(--) PCI:*(0@0:16:0) ATI Technologies Inc Radeon RV200 QW [Radeon 7500] rev 0, Mem @ 0x0f9f0374/0, 0x0f9f0374/0, I/O @ 0x0f9f0374/0, BIOS @ 0x????????/262079348
(II) System resource ranges:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "fbdev"

(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:10:0
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"

(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 4.1
(**) FBDEV(0): claimed PCI slot 0@0:16:0
(II) FBDEV(0): using default device
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 8/8
(==) FBDEV(0): Depth 8, (==) framebuffer bpp 8
(==) FBDEV(0): Default visual is PseudoColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: ATI Radeon QW  (video memory: 32768kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
(**) FBDEV(0):  Built-in mode "current": 99.2 MHz, 72.1 kHz, 89.0 Hz
(II) FBDEV(0): Modeline "current"x0.0   99.20  1024 1072 1168 1376  768 769 772 810 +hsync +vsync -csync (72.1 kHz)
(==) FBDEV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(**) FBDEV(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	2	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[1] -1	2	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[2] -1	2	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[3] -1	2	0xffffffff - 0x00000000 (0x0) MX[B]
	[4] -1	1	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[5] -1	1	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[6] -1	1	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[7] -1	1	0xffffffff - 0x00000000 (0x0) MX[B]
	[8] -1	0	0xffffffff - 0x00000000 (0xffffffff) MX[B]
	[9] -1	0	0xffffffff - 0x00000000 (0xf0000) MX[B]
	[10] -1	0	0xffffffff - 0x00000000 (0xc0000) MX[B]
	[11] -1	0	0xffffffff - 0x00000000 (0x0) MX[B]
	[12] -1	2	0xffffffff - 0x00000000 (0xffff) IX[B]
	[13] -1	2	0xffffffff - 0x00000000 (0x0) IX[B]
	[14] -1	1	0xffffffff - 0x00000000 (0xffff) IX[B]
	[15] -1	1	0xffffffff - 0x00000000 (0x0) IX[B]
	[16] -1	0	0xffffffff - 0x00000000 (0xffff) IX[B]
	[17] -1	0	0xffffffff - 0x00000000 (0x0) IX[B]
(==) FBDEV(0): Backing store disabled
(II) FBDEV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Logitech Apple Optical USB Mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Logitech Apple Optical USB Mouse: always reports core events
(**) Logitech Apple Optical USB Mouse: Device: "/dev/input/event4"
(II) Logitech Apple Optical USB Mouse: Found x and y relative axes
(II) Logitech Apple Optical USB Mouse: Found 1 mouse buttons
(II) Logitech Apple Optical USB Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech Apple Optical USB Mouse" (type: MOUSE)
(**) Logitech Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device HID 047d:1009
(**) HID 047d:1009: always reports core events
(**) HID 047d:1009: Device: "/dev/input/event3"
(II) HID 047d:1009: Found x and y relative axes
(II) HID 047d:1009: Found 3 mouse buttons
(II) HID 047d:1009: Configuring as mouse
(II) XINPUT: Adding extended input device "HID 047d:1009" (type: MOUSE)
(**) HID 047d:1009: YAxisMapping: buttons 4 and 5
(**) HID 047d:1009: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Alps Electric M2452
(**) Alps Electric M2452: always reports core events
(**) Alps Electric M2452: Device: "/dev/input/event2"
(II) Alps Electric M2452: Found keys
(II) Alps Electric M2452: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric M2452" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Alps Electric M2452: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Alps Electric M2452: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Alps Electric M2452: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
AUDIT: Sat Nov  1 11:15:00 2008: 4752 X: client 4 rejected from local host ( uid=0 gid=0 pid=4769 )
AUDIT: Sat Nov  1 11:15:05 2008: 4752 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4773 )
AUDIT: Sat Nov  1 11:15:05 2008: 4752 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4774 )
AUDIT: Sat Nov  1 11:15:05 2008: 4752 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=4775 )
```

---

### Post by cyberdork33 on 2008-11-01
There doesn't seem to be any errors.

---

### Post by crapple on 2008-11-01
When I boot interpid it tells me error parsing xorg file Do you want to run in low graphics mode. Is there anyway to make it ignore the error and try and boot or a fix to this error

---

### Post by crapple on 2008-11-06
> **paul_mcl said:**
> Yep, I have Radeon 7500 (PCI version) too. The following xorg.conf works fine for me (taken from Yellow Dog then modified):

```

# xorg.conf (X.Org X Window System server configuration file)
#
# See the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.

Section "ServerLayout"
        Identifier      "XFree86 Configured"
        Screen          0 "Screen0" 0 0
        InputDevice     "Mouse0" "CorePointer"
        InputDevice     "Keyboard0" "CoreKeyboard"
        Option          "OffTime" "10"
EndSection

Section "Files"
# RgbPath is the location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)

       RgbPath		"/usr/share/X11/rgb.txt"
      #FontPath		"/usr/share/X11/fonts/misc:unscaled"
      #FontPath		"/usr/share/X11/fonts/Type1/"
      #FontPath		"/usr/share/X11/fonts/Speedo/"
      #FontPath		"/usr/share/X11/fonts/75dpi:unscaled"
      #FontPath		"/usr/share/X11/fonts/100dpi:unscaled"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "fbdevhw"
        Load            "freetype"
        Load            "type1"
        #Load           "dri"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
# Change "XkbModel" to "macintosh_old" if you are using
# the deprecated adb keycodes.
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:caps_toggle"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "ZAxisMapping"  "4 5"
        Option          "Protocol"      "IMPS/2"
        Option          "Device"        "/dev/input/mice"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        ModelName       "Monitor Model"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     50-60
EndSection

Section "Device"
        Identifier      "Card0"
        #Option         "ShadowFB"      "true"
        #Option         "fbdev"         "/dev/fb0"
        Driver          "fbdev"
        #BusID          "PCI:0:16:0"
        Option          "UseFBDev"      "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes   "1024x768"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes   "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Group           0
        Mode            0666
EndSection

```
This is a great xorg file. It fixed my problem. BUT when I install the x server xgl package to get desktop effects my graphics are so slow. I think i need to configure the xorg file but I am not sure. It might be because the driver isn't compatible with it but it did work in gutsy and feisty. Any ideas thanks

---

### Post by ash05 on 2008-11-07
Anyone. It is also the radeon 7000 series not just my card

[File sharing online,virtual file server storage,synchronize files offline]("http://www.nomadesk.com/")

---

