---
title: "Molecules Screensaver locks up computer"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Mt Dew on 2007-07-05
I was scrolling thru the screensavers and come to the Molecules one.   It started to give me a preview and then froze.  I went to try and change it, but it freezes every time.  Now i can't leave the computer unattended for more than 10 minutes.  Is there a way I can change it back to default without actually going to the screensaver menu?  
And btw, I have only had Ubuntu for 3 days and still finding my way around.  :-)

Thanks!

---

### Post by Moop on 2007-07-05
What kind of video card do you have? Have you installed the restricted driver for it? Do the other 3d screensavers work?

---

### Post by Mt Dew on 2007-07-05
Not sure :o.  How can I tell? Everything worked ok when I installed Ubuntu so I didn't bother with drivers.  If there are 3D screensavers before you get to Molecules then yes.  If not, then no.

---

### Post by phizikal on 2007-07-05
Find out if you have accelerated rendering.

send your output on "glxinfo".

---

### Post by Mt Dew on 2007-07-05
> **phizikal said:**
> Find out if you have accelerated rendering.

send your output on "glxinfo".

How do I do that?

---

### Post by Moop on 2007-07-05
To install the driver for your video card go to System- Administration- Restricted Driver Manager.:)

---

### Post by Mt Dew on 2007-07-05
It says I don't have any restricted drivers to install.

---

### Post by pistcivet on 2007-07-05
Open a terminal and enter:  gconf-editor
Then browse to apps, gnome-screensaver
there you can change the screensaver from "Molecules" to something else.
Just make it blank.

Proper video drivers should fix the problem.

---

### Post by Moop on 2007-07-05
Ok. You didn't say what video card you have. To post the results of glxinfo open a terminal and type glxinfo and hit enter. Copy and paste the results.

---

### Post by Mt Dew on 2007-07-05
Here's the info.


xxxxx@xxxxxx-desktop:~$ glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 20051027 AGP 1x x86/MMX/SSE
OpenGL version string: 1.2 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_compression, GL_ARB_texture_env_add, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x26 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2b 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x2e 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x2f 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x32 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Mt Dew on 2007-07-05
Thanks **Pistcivet**, that worked.  I will leave it there until I find out if there is an underlying problem.

---

### Post by Mt Dew on 2007-07-05
**MOOP** Can you tell me what kind of Video Card I have?  Could that have been the problem?

Thanks for everyone's help!

---

