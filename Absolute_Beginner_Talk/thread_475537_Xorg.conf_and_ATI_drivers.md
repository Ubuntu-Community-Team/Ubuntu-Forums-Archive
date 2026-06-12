---
title: "Xorg.conf and ATI drivers"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by raynard79 on 2007-06-16
Hi All, 

I am new to Linux / Ubuntu, and wanted to ask about the various drivers and codes I have read up on relevant to an ATI graphics card.

I have Ubuntu Feisty 7.04 installed, and an ATI Radeon 9600, RV350 card.

My understanding is that ATI have open sourced drivers (XGL??), and also closed source drivers (FGLRX).
   
I tried to unsuccessfully install both drivers, and in doing so, and much time on google, I have come across some terms which i have no idea about. 

     - AiGLX
     - Composite Extension Enabled/Disabled (in the Xorg.conf) ... what does this do?
     - DRI Enabled / Disabled (in the Xorg.conf) ... what does this do?

Thankyou in advance..

Raynard.

---

### Post by starcraft.man on 2007-06-16
> **raynard79 said:**
> 
     - [AiGLX]("http://en.wikipedia.org/wiki/AIGLX")
     - [Composite Extension]("http://en.wikipedia.org/wiki/Compositing_window_manager") Enabled/Disabled (in the Xorg.conf) ... what does this do?
     -[ DRI Enabled ]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure")/ Disabled (in the Xorg.conf) ... what does this do?


Questions answered I believe. AIGLX doesn't work with ATI for the most part, and you want composite extension always enabled, I think the DRI it depends...

As for installing drivers, have you tried [Envy?]("http://albertomilone.com/nvidia_scripts1.html") It always works for me (admittedly I'm 100% nvidia) and it worked for lots of ATI users. Download (stable version), install it, run it from Applications > System tools > Envy and then select install automatically ATI drivers and wait for it to finish answering yes as you go.

---

### Post by raynard79 on 2007-06-16
Thanks for your answer.

I will try out envy, and let you know what happens. 

I am still confused on what DRI and Composite blah blah actually means...

I am trying to get Beryl working on my computer, and have read mixed opinions on it all. 

ie, does not work with closed sourced drivers, will only work if composite rendering is off, 

will only work if dri is enabled, etc...

Just trying to understand it all..

Cheers,,.

R

---

### Post by Kubunteando on 2007-06-17
Some more hints:

- DRI is Direct Rendering provided by the 3D HW acceleration. So it allows you to make use of your Graphics card 3D HW acceleration capabilities. Direct Rendering "No" means you are not using HW acceleration is 3D effect will be slow or they will not work

- AIGLX, is an extension used by Beryl to access the OpenGL (HW acceleration routines)

- Composite is an extension used also by Beryl, I don't know much about this one

But the important thing is the following:

if you want to install Beryl you have to use:

Open Source drivers for ATI (ati) + AIGLX + Beryl

or

ATI proprietary drivers (fglrx) + XGL + Beryl

In both cases you should have DRI enabled (Direct Rendring as "Yes" when you issue a "glxinfo" command)

There are guides available for Feisty how to install Beryl.

---

### Post by raynard79 on 2007-06-18
Ah many thanks!

Have you managed to get it working?

I heard you can do it on dual monitors too, by editing the xorg.conf.

I guess getting it to work on one would be a start.

Cheers.

---

### Post by Kubunteando on 2007-06-18
Yes, I have it working.

But I am using the Open Source drivers, and was really easy in Feisty.
I did not manage to make it work with Edgy. Probably what helped the most is that Feisty is having Xorg version 7.2 which much better support of AIGLX.

But this is not relevant if you plan to use XGL with the ATI proprietary drivers.

---

### Post by videocheez on 2007-06-18
Hey guys.   Sorry to hijack your post but since I also have an ATI Radeo x1900xtx video card,I was wondering if you could take at the results when I typed **glxinfo** and let me know if I'm using ATI proprietary or Open source drivers.  I'm also tryoing to play with Beryl and although it seem to be installed properly, I can't figure out how to make all of the cool stuff happen.  Please review the info below and give me a summary of my set up.  I'm trying to get things working properly but i still need a lot of help interpreting the data.

Thanks in advance,

VC

don@don-ubuntu:~$ glxinfo
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
OpenGL renderer string: Radeon X1900 Series
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
don@don-ubuntu:~$

---

### Post by machoo02 on 2007-06-18
> OpenGL vendor string: ATI Technologies Inc.You are using Ati's binary driver(fglrx).  If you were using the open source driver it would say Tungsten Graphics.  In order to use Beryl with your video card, you will need to install a special composite X-server called Xgl...the instructions are [here]("https://help.ubuntu.com/community/CompositeManager/Xgl").  Then check out [this page]("https://help.ubuntu.com/community/CompositeManager/Beryl") for info on installing beryl.

---

### Post by videocheez on 2007-06-18
Thanks.  It likes a little bit of work but at least the instructions are straight forward.
Before I get started, please comment on the following:

When I tried to make the sript which gives the xgl session at start-up, the following message appeared  in my terminal:

don@don-ubuntu:~$ gksudo gedit /usr/bin/startxgl.sh
(gedit:8928): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Also, will this modification affect the dual boot set up that I'm currently using?  Right now  I have modified menu.lst to boot to windows by default and ubuntu 2nd.

If this doesn't work, how easy will it be to go back to my current configuration?  Will it be as simple as just replacing my xorg.conf file with a backup?

Finally, If it matters, direct rendering is currently working:

don@don-ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes
don@don-ubuntu:~$ 

Does this mean that Beryl should automatically work?  I already have Beryl installed and I can't tell if it is working or not.  I will be working on this script trying to understand and hopefully you will reply before I finish and begin to run it. ;)

Thanks in advance,

VC




glxinfo | grep rendering

---

### Post by videocheez on 2007-06-19
I gotta another question.  That guide at the following URL :

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

said, "Now we'll add an option to the gnome login manager so that we can choose to log into our new Xgl-gnome session. Create an Xsession file like so:"

What is and how do I find the gnome login manager?

---

### Post by NS2-10 on 2007-06-19
Hey!

I'm also going to hijack this a bit. I have a X1400 ATI card that I finally got to work with XGL sessions and Beryl but now I the **maximum resolution is stuck on 1024x768 instead of 1280x800** as my screen should be able to run...

I use the fglrx drivers and all the info and greps show that I have full 3D support and Beryl runs perfectly... I am a bit of a noob though so I might have missed something obvious...

How do I solve this!??

---

### Post by videocheez on 2007-06-19
> **NS2-10 said:**
> Hey!

I'm also going to hijack this a bit. I have a X1400 ATI card that I finally got to work with XGL sessions and Beryl but now I the **maximum resolution is stuck on 1024x768 instead of 1280x800** as my screen should be able to run...

I use the fglrx drivers and all the info and greps show that I have full 3D support and Beryl runs perfectly... I am a bit of a noob though so I might have missed something obvious...

How do I solve this!??

Which method did you choose when setting up xgl?  A, B or C
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

And to ansoer your question, I had this same problem when using x-server and when I came to screen that listed allof thre screen resolution sizes, I simple pressesd space bar at each resolution option and this allowed my gui several resolution choices.

---

### Post by raynard79 on 2007-06-22
Hey, 

No probs, for hijacking my query! haha..

I had a similar problem with my wide screen 22" monitor. The resolution basically sucked.

So I looked up the native screen resolution for my monitor (BenQ FP222W).  

This was 1680 X 1050.

Next I had to edit my xorg.conf file, which was done by typing this:

    "gksu gedit /etc/X11/xorg.conf"

++This was NOT done in root, but in my login name for the computer.

Then i plugged in the new figures in my xorg.conf file, saved, and rebooted.

One lesson i have learnt when playing with the xorg.conf file, is to ALWAYS make a backup.

This is done by typing..

touch /etc/X11/xorg.conf_backup22June07 (this creates the file)

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup22June07 (this copies the file)

If you reboot and you get a black screen, and jsut a big *** screen with a terminal

type in:
cp /etc/X11/xorg.conf_backup22June07 /etc/X11/xorg.conf (this copies your backup into the original..

then type 

"reboot'

and you back to where you began.

If it worked, then go into system, preferences, screen resolution, and your new resolution should be there...

good luck!

---

### Post by videocheez on 2007-06-22
Thanks man.  I followed this guide with good luck finally:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

---

