---
title: "2980 fps in ATI mobility radeon 9600, is this good?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by franestepona on 2006-06-08
Hi guys. I have an ATI mobility radeon 9600 graphic card (256 MB dedicated) and i get 2980 fps in glxgears, I consider that is pretty low. CPU usage is high for all the jobs running graphics and in the gxl session i get about half of the fps. Is this normal? should i have higher values? This is my info:

```
fran@fransmachine:~$ glxgears -printfps
14555 frames in 5.0 seconds = 2910.889 FPS
14911 frames in 5.0 seconds = 2982.011 FPS
14912 frames in 5.0 seconds = 2982.259 FPS
14911 frames in 5.0 seconds = 2982.060 FPS
fran@fransmachine:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)
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
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
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
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None

```
and my xorg file:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	RgbPath "/etc/X11/rgb"
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

Some of u have better values with the same card?

Thanks in advance.
Fran

---

### Post by franestepona on 2006-06-08
Sorry I forgot to say, the processor is Centrino 2 ghz, 1 GB ddram.

Thanks!

---

### Post by bruce89 on 2006-06-08
Are you using the fglrx driver?

---

### Post by tstadler on 2006-06-08
Using the 8.24 ati driver on my t42 1.8Ghz (1GB ram) with a 9600 64mb ram (1400x1050 24bit) I hit about 2200 so sounds fair to me. Better than my old Compaq n410c ~290 :D

---

### Post by aktiwers on 2006-06-08
Seams a bit low to me. Im getting 2 times as high FPS as you, and Im using a Radeon 9800 PRO.

```
aktiwers@ubuntu:~$ glxgears -printfps
23573 frames in 5.0 seconds = 4714.590 FPS
23536 frames in 5.0 seconds = 4707.170 FPS
23592 frames in 5.0 seconds = 4718.226 FPS
23607 frames in 5.0 seconds = 4721.306 FPS
23583 frames in 5.0 seconds = 4716.486 FPS
23527 frames in 5.0 seconds = 4705.399 FPS
aktiwers@ubuntu:~$

``` 
I simply followed this guide.
[http://www2.ati.com/drivers/linux/linux_8.25.18.html]("http://www2.ati.com/drivers/linux/linux_8.25.18.html")

After downloading these drivers:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")

---

### Post by u.b.u.n.t.u on 2006-06-08
Just for feedback purposes - 2.5Ghz CPU AMD, 1GB ram, Nvidia 6600GT 128MB video card.

I was averaging 6600+ FPS with nothing else running, other than firestarter.

I have a number of programs open now and it runs 6000+ FPS.

This is my gaming/movie box.


edit: screen res 1280x1024, the gears run at default size.

---

### Post by tstadler on 2006-06-08
Sure my home PC with a Nvidia 6600 128mb 3500+ 64bit Fedora hits 7800 or more, but with a laptop Mobility 9600 you don't get the same video performance. But it would be nice for that Dell XPS laptop :-) 3500$+ I would love to hear the fps on that

---

### Post by franestepona on 2006-06-08
[QUOTE=aktiwers]Seams a bit low to me. Im getting 2 times as high FPS as you, and Im using a Radeon 9800 PRO.

```
aktiwers@ubuntu:~$ glxgears -printfps
23573 frames in 5.0 seconds = 4714.590 FPS
23536 frames in 5.0 seconds = 4707.170 FPS
23592 frames in 5.0 seconds = 4718.226 FPS
23607 frames in 5.0 seconds = 4721.306 FPS
23583 frames in 5.0 seconds = 4716.486 FPS
23527 frames in 5.0 seconds = 4705.399 FPS
aktiwers@ubuntu:~$

``` 
I simply followed this guide.
[http://www2.ati.com/drivers/linux/linux_8.25.18.html]("http://www2.ati.com/drivers/linux/linux_8.25.18.html")

After downloading these drivers:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")[/QUOTE]

Thank you! I followed your guide, now my fps are:

```
fran@fransmachine:~$ glxgears -printfps
15193 frames in 5.0 seconds = 3038.548 FPS
15172 frames in 5.0 seconds = 3034.357 FPS
15174 frames in 5.0 seconds = 3034.619 FPS

```

Still a little bit low, look at this in the xorg file:
```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "ati"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```

i have never seen 3 sections device. Should i change the driver of some of these?

Thanks.
Fran

---

### Post by halfvolle melk on 2006-06-08
Hi,
glxgears is not considered to be a decent benchmark. Check this thread for GL benchmarking:
[http://www.ubuntuforums.org/showthread.php?t=157429&highlight=benchmark](http://www.ubuntuforums.org/showthread.php?t=157429&highlight=benchmark)

---

