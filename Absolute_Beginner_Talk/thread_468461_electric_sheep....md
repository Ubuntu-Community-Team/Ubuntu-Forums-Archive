---
title: "electric sheep..."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-06-08
what is the issue with this thing. i tried to run it with the screensaver menu and nothing. so i tried to re-install it and the read-me file said :

> 
As usual, to configure, build, and install:

	./configure
	make
	sudo make install

This package depends on curl, xloadimage, and expat.  If you don't
have them already you can find them with [http://rpmfind.net](http://rpmfind.net).

After that you can test it by just running it from the commandline
without arguments, ie "electricsheep".  After several minutes of
downloading a window will appear and the first sheep will be drawn.



can someone please explain this to me...thanks in advance.

---

### Post by ryanVickers on 2007-06-08
Oh dear, I'm quite sure that's not normal - I mean to *get* the message, and the message itself :p

Are your video drivers installed?

---

### Post by freakavoid on 2007-06-08
It has to download a lot of stuff before the first run. Try running it from a terminal and you'll know when it has finished downloading. As far as the readme goes, you don't have to compile it yourself. It's in the repos. You can use apt-get or synaptic to install it.

---

### Post by thesonisshining on 2007-06-08
> **ryanVickers said:**
> Oh dear, I'm quite sure that's not normal - I mean to *get* the message, and the message itself :p

Are your video drivers installed?

video drivers? i'm a noob; please explain in noobian 
*this is where i do the robot to distract from my embarassment*

---

### Post by ryanVickers on 2007-06-08
Oh, ok!

You need a bit of special software to make your video card (second processor just for 3D) work.  It is also needed to make any 3D program work proporly.  Luckilly, this is all automatic:

step 1: click System > Administration > Restricted Drivers Manager
step 2: click the check box on
step 3: if any questions occur asking you "ok?", say yes
step 4: wait for download and install to complete (do nothing)
step 5: reboot (the first and last time you will reboot in ubuntu! (except for kernal upgrades))
try the thing again, and see if it doesn't work now!

---

### Post by handydan918 on 2007-06-08
> **thesonisshining said:**
> what is the issue with this thing. i tried to run it with the screensaver menu and nothing. so i tried to re-install it and the read-me file said :



can someone please explain this to me...thanks in advance.

README files typically cover either installing from source code, or installing from a tarball ( a compressed file with a .tar.gz or .tar.bz extension)
You will want to use synaptic for installing anything that is available in the software repositories. Synaptic makes it easy. It figures out what additionsl files are needed (dependencies) and, if possible, satisfies them.
I love micah 6:8.

---

### Post by thesonisshining on 2007-06-08
> **ryanVickers said:**
> Oh, ok!

You need a bit of special software to make your video card (second processor just for 3D) work.  It is also needed to make any 3D program work proporly.  Luckilly, this is all automatic:

step 1: click System > Administration > Restricted Drivers Manager
step 2: click the check box on
step 3: if any questions occur asking you "ok?", say yes
step 4: wait for download and install to complete (do nothing)
step 5: reboot (the first and last time you will reboot in ubuntu! (except for kernal upgrades))
try the thing again, and see if it doesn't work now!

it says "Your hardware does not need any restricted drivers."

---

### Post by ryanVickers on 2007-06-08
Weird.  I guess that means it would just work by default.  To test this, go in terminal and type "glxgears -info" and see if you get over about 4500 fps - if so, then it's probably OK.  I get ~11500 fps, but I've got a good processor and excellent video card, but I would think that even with a bad one, it would get about 4500.  without, expect hundreds or **under** 2000 for sure!  If it seems to run OK, and you've tried 3D games and they work, then I don't know what could be causing the electric sheep error :p

---

### Post by thesonisshining on 2007-06-08
> **ryanVickers said:**
> Weird.  I guess that means it would just work by default.  To test this, go in terminal and type "glxgears -info" and see if you get over about 4500 fps - if so, then it's probably OK.  I get ~11500 fps, but I've got a good processor and excellent video card, but I would think that even with a bad one, it would get about 4500.  without, expect hundreds or **under** 2000 for sure!  If it seems to run OK, and you've tried 3D games and they work, then I don't know what could be causing the electric sheep error :p

GL_RENDERER   = Mesa DRI Intel(R) 915G 20061017 x86/MMX/SSE2
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SUN_multi_draw_arrays
5577 frames in 5.0 seconds = 1115.365 FPS

---

### Post by Hibbelharry on 2007-07-04
Your score is quite normal. Since glxgears is no good 3D graphics benchmark results are neglible. 
To see if your Graphics Acceleration (that's not just 3D) works it's better to do a "glxinfo |grep direct" in a xterm/konsole/gnome-terminal or whatever. If it says "direct rendering:yes" everything is surely alright. 
Another fact: electricsheep doesn't use any 3D at all, instead the animations are movies which are downloaded from a server in the internet and played in a loop. Playing videos works with nearly every driver und every condition quite well nowadays. 
It seems common that electricsheep takes a really long while before it displays the first animations, depending on your connection speed and server load. Just wait a while. All dependencys to make it work should be installed by the packagesystem automatcially when you installed electricsheep from there.

Greetz
Hibbelharry

---

### Post by crispingatiesa on 2007-07-04
Dude, sorry for going off topic, but that nick name "thesonisshinning" is by any chance a tribute to the great Bobby Marley?  "Song is shinning, the weather is sweet ..."

---

### Post by ryanVickers on 2007-08-09
I just realized the other day that "electricsheep" is the name of a certain screensaver.  It's just unable to load for some reason, but I guess that's the point of this discussion! :)

---

### Post by dasbooter on 2007-08-13
does anybody know how to get this set up so that a bit torrent client azureus or possibly some other bit torrent client downloads the sheep. And I guess deletes the old ones or does the screensaver delete the old ones ?

---

