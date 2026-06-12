---
title: "Need help with graphics"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by kulotzy on 2008-04-15
Here's my problem. I seem to be having problems with graphics. My screensaver crashes(i uninstalled it completely), my desktop effects wont work at all, i cant run games such as Tibia etc... im new to this and i have no idea what the problem nor the solution to this is?

Any help would be appreciated, thanks.

Edit: Btw, my screensavers worked fine even  after upgrading to Hardy.... one of the updates messed it up... I dont know exactly what Open GL is but i think it doesnt work or is malfunctioning

---

### Post by Crafty Kisses on 2008-04-15
We need more info, what kind of video card do you have? Also post the following output:
```
glxinfo
```

---

### Post by mevets on 2008-04-15
We need to know more about your hardware. What graphics card does your computer have?

---

### Post by kulotzy on 2008-04-15
It appears i use VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01). I just copy pasted that, i have no idea what it means nor do i know if thats the correct on from typing lspci in the terminal(?).

---

### Post by kulotzy on 2008-04-15
My PC crashed when i typed in that code, Codename.

---

### Post by Crafty Kisses on 2008-04-15
> **kulotzy said:**
> My PC crashed when i typed in that code, Codename.

All that command does is tell me if your video card is working or not, so I don't see why it crashed, did it go to a black screen, or what?

---

### Post by kulotzy on 2008-04-15
> **Codename said:**
> All that command does is tell me if your video card is working or not, so I don't see why it crashed, did it go to a black screen, or what?

I tried once more and it was the same result. My PC froze and then went back to the login screen. Perhaps, since it reacts this way, it means its not working correctly?

---

### Post by mister_pink on 2008-04-15
I had this before (crashing on glxinfo). I ended up just reinstalling. Have you done anything to get to this state, because I only ended up there after an attempt to get 3D graphics working involving a combination of restricted driver manager, envy and manually installing from the ati website resulting in things being massively messed up.

---

### Post by kulotzy on 2008-04-15
> **mister_pink said:**
> I had this before (crashing on glxinfo). I ended up just reinstalling. Have you done anything to get to this state, because I only ended up there after an attempt to get 3D graphics working involving a combination of restricted driver manager, envy and manually installing from the ati website resulting in things being massively messed up.

I havent done anything i can think of except the updates. Also, i have yet to get the graphics working right (ie. desktop effects) since my first install... (i had to try to install Ubuntu 3 times before it worked.)

---

### Post by kulotzy on 2008-04-15
Any suggestions?

---

### Post by kulotzy on 2008-04-15
Darn... i did something stupid... i removed WINE, and then i deleted the wine folder from the main menu (system > preferences > main menu), now that i reinstalled wine, it wont appear on the menu anymore.... ugh... am i screwed? I removed it because when yet another update messed it up, it was fine before that, everytime i click on configure wine, it takes up my whole screen and its super zoomed in, the letters are half the size of the screen.

---

### Post by Crafty Kisses on 2008-04-15
> **kulotzy said:**
> I tried once more and it was the same result. My PC froze and then went back to the login screen. Perhaps, since it reacts this way, it means its not working correctly?

Sounds like your X is restarting for some reason, mind posting some Xorg logs?

---

### Post by kulotzy on 2008-04-15
> **Codename said:**
> Sounds like your X is restarting for some reason, mind posting some Xorg logs?

Err... what is that, sir?:confused:

---

### Post by kulotzy on 2008-04-15
> **kulotzy said:**
> Darn... i did something stupid... i removed WINE, and then i deleted the wine folder from the main menu (system > preferences > main menu), now that i reinstalled wine, it wont appear on the menu anymore.... ugh... am i screwed? I removed it because when yet another update messed it up, it was fine before that, everytime i click on configure wine, it takes up my whole screen and its super zoomed in, the letters are half the size of the screen.

Nevermind all this. I was able to fix it, whew.

---

### Post by kulotzy on 2008-04-15
> **Codename said:**
> We need more info, what kind of video card do you have? Also post the following output:
```
glxinfo
```

Im on LIve CD right now.... i messed up Ubuntu and now im planning to make a complete reinstallation..

i got this from that code:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome (KM400) 20060710 x86/MMX+/3DNow!+/SSE
OpenGL version string: 1.2 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod
Segmentation fault (core dumped)



However, since im going to make a complete reinstall, i dont think it matters anymore, or does it? What does it mean anyway?

---

### Post by kulotzy on 2008-04-16
Ok errr.... i tried installing Linux Mandriva just to test it out... im reverting back to Ubuntu. However, i wonder why my 3d effects worked with that but not with my old Ubuntu...

---

