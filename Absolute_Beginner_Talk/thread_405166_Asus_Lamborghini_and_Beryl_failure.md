---
title: "Asus Lamborghini and Beryl failure"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Cetic on 2007-04-09
Hello,
After reading this forum for some time I have managed to download and install NVIDIA drivers for my Asus Lamborghini, however yet still in 'xorg' my monitor, video card are displeyed as generic, high resolution modes are not available. 
Another issue deals with installation of Beril, again I have followed the recommended instuctions, it starts up but the movement of windows is unavailable and there is a general feeling that it was installed incorrectly.
Looking forward for your help
Thanks in advance
Andriy

---

### Post by mand0 on 2007-04-09
Can you post some more information? Like, for example, which tutorial did you follow? What is the error message you see?

Type in the Terminal:

```
glxinfo
```

and post the outcome.

---

### Post by Cetic on 2007-04-09
Unfortunatly (feeling silly to admit it) I do not remember which particular guide I have used, because I was searching through forum and in several posts found guides to do that.
Just to be brief: I have downloaded from NVIDIA site required drivers after failure to use ENVY script, that I have downloaded beryl. It seems to me that the problem is in my video card NVIDIA GE Force Go 7400 because several people complained on problems with it
The output you asked for is

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_clear_tag, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x31 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x33 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x34 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x35 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x3f 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  2 1 Ncon
0x40 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  4 1 Ncon
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x43 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  2 1 Ncon
0x44 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  4 1 Ncon
0x45 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x46 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x47 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  2 1 Ncon
0x48 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  4 1 Ncon
0x10c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by Cetic on 2007-04-09
After adding the string with resolution into xorg.conf I have managed to come up with first issue - dealing with resolution. It is now 1400x1050 :)
But beryl simply runs with problems eg not moving window etc.
I can attach my xorg.conf if that helps

---

### Post by mand0 on 2007-04-09
> **Cetic said:**
> After adding the string with resolution into xorg.conf I have managed to come up with first issue - dealing with resolution. It is now 1400x1050 :)
But beryl simply runs with problems eg not moving window etc.
I can attach my xorg.conf if that helps

Yes, post that next if you wouldn't mind.

---

### Post by Cetic on 2007-04-09
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
#Load "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by mand0 on 2007-04-09
> **Cetic said:**
> Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    **16**
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Try changing the bolded 16 to 24.  Can you post what the error is when you run:

```
beryl-manager
```

---

### Post by Cetic on 2007-04-09
After changing to 24 it finally works fine
I am very gratefull for help :)
Thanks!

---

### Post by maxim1 on 2007-04-09
CEtic how you finding the new laptop, I was going to get one but could not get the spec I wanted in black , opted for the G1 instead. Ive still got to install beryl, what guide did you use ?

---

### Post by Cetic on 2007-04-09
I find laptop great :)
Ive got VX1 in yellow and really enjoy it
The guide... The problem here is that I simply used search on forum and dont remember which particular topic I used :(
Another page that I used is [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)
Hope that helps

---

