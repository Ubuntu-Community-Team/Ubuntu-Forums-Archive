---
title: "Games are too dark?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-28
When ever I try to play a good 3D game like Planeshift or TCE, the game is way too dark!

The brightness is on 100 % on my monitor. I have a Radeon 9800 Pro video card, and I have installed the ATI drivers.

I still do suspect it has something to do with those drivers though.

Here is the output of  glxgears -printfps
```

aktiwers@ubuntu:~$ glxgears -printfps
23151 frames in 5.0 seconds = 4630.024 FPS
24100 frames in 5.0 seconds = 4819.990 FPS
24100 frames in 5.0 seconds = 4819.821 FPS
24103 frames in 5.0 seconds = 4820.435 FPS
24100 frames in 5.0 seconds = 4819.968 FPS
aktiwers@ubuntu:~$
```

And here is the output of  sudo glxinfo :

```
aktiwers@ubuntu:~$ sudo glxinfo
Password:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
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
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
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
aktiwers@ubuntu:~$

```

Anyone has any idea why I have these dark game experiance? And how to fix it?

Thansk a lot!

---

### Post by erniewinner on 2006-05-28
hi,

what kind of monitor? is it an lcd? i have all the settings on 11 and somethings are still too dark. some games have their own "gamma" adjustment for such a problem. look in the games display settings...

---

### Post by aktiwers on 2006-05-28
Thanks for your reply.

The problem only happends in Big 3d games. The Gamma is on 100 % both on my monitor and in the game, but still the games are way to dark!

I have a Samsung SyncMaster 959NF 19" Monitor, and it is CRT not LCD.

Thanks again for your reply.

Any other suggestions?

---

### Post by aktiwers on 2006-05-28
Bump

---

### Post by IYY on 2006-05-28
Some cards support gamma correction, which can be done using the command:

**xgamma -gamma *num***

where ***num*** is a number between 0.1 and 1

---

### Post by aktiwers on 2006-05-28
[quote=IYY]Some cards support gamma correction, which can be done using the command:

**xgamma -gamma *num***

where ***num*** is a number between 0.1 and 1[/quote]

Thanks a lot for your reply!

Can you explain what this actually does? And how I use it?

For an example, I just tried this:

```
aktiwers@ubuntu:~$ xgamma -gamma 100
Gamma values must be between  0.100 and 10.000
aktiwers@ubuntu:~$ xgamma -gamma 1
-> Red  1.000, Green  1.000, Blue  1.000
<- Red  1.000, Green  1.000, Blue  1.000
aktiwers@ubuntu:~$

```

But what does it do?

Thanks a lot!

---

### Post by IYY on 2006-05-29
Well, on my machine it changes the brightness. When I set the gamma to 0.1, I get a very dark screen. 1 is norma. 10 is very bright. If these numbers don't change anything for you, it's not supported by your driver.

---

### Post by aktiwers on 2006-05-29
Thanks now I get it!
It worked! Thanks a lot :)

---

### Post by Lord Illidan on 2006-10-02
I have something further to say on this.

On Edgy, it appears that Tremulous is extremely dark unless you set the xgamma value in the terminal to 2. I dunno what to make about this, as the game worked perfectly in Dapper and FC 5 on the same hardware.

It could be a bug in SDL..or it could be not..I dunno what to make about it.

---

### Post by minisori on 2006-10-02
> **Lord Illidan said:**
> I have something further to say on this.

On Edgy, it appears that Tremulous is extremely dark unless you set the xgamma value in the terminal to 2. I dunno what to make about this, as the game worked perfectly in Dapper and FC 5 on the same hardware.

It could be a bug in SDL..or it could be not..I dunno what to make about it.

Yes I agree, i got the same problem since I updated to edgy last night ](*,) . I have to check if it happend with more games, but i think is opengl related.

---

### Post by Lord Illidan on 2006-10-02
> **minisori said:**
> Yes I agree, i got the same problem since I updated to edgy last night ](*,) . I have to check if it happend with more games, but i think is opengl related.

Somehow, Quake 4 played well...I have to check more games.

---

### Post by Lord Illidan on 2006-10-03
It is a bug, reported in Launchpad here : [https://launchpad.net/distros/ubuntu/+source/libsdl1.2/+bug/61389](https://launchpad.net/distros/ubuntu/+source/libsdl1.2/+bug/61389)

There's supposed to be a patch here, I dunno how to apply it, does anyone know?

[http://www.libsdl.org/pipermail/sdl/2006-June/074812.html](http://www.libsdl.org/pipermail/sdl/2006-June/074812.html)

---

### Post by minisori on 2006-10-03
> **Lord Illidan said:**
> It is a bug, reported in Launchpad here : [https://launchpad.net/distros/ubuntu/+source/libsdl1.2/+bug/61389](https://launchpad.net/distros/ubuntu/+source/libsdl1.2/+bug/61389)

There's supposed to be a patch here, I dunno how to apply it, does anyone know?

[http://www.libsdl.org/pipermail/sdl/2006-June/074812.html](http://www.libsdl.org/pipermail/sdl/2006-June/074812.html)

First thx for the patch it worked flawless :D

Note this patch is for edgy, i didnt have this problem in dapper, and i don't know if it would work in dapper :-s

1. > cd /usr/src

2. Get the source files from repository
> sudo apt-get source libsdl1.2debian

3. Install build dependences
> sudo apt-get build-dep libsdl1.2debian

4. Download the patch you mentioned early and put it in /usr/src if you want.

5. Apply the patch, the sudo is cause you probably dont have rights in the src folder mentioned...
> sudo patch -i patch_file_name

6. If when you do the thing before you get asked what file to patch you may say 
> libsdl1.2-1.2.10/src/video/SDL_gamma.c

7. After build the package
> cd libsdl1.2-1.2.10
sudo dpkg-buildpackage -rfakeroot -uc -b


8. After a long wait you will get it compiled now to install it. For example if you use the alsa one install libsdl1.2debian-alsa_1.2.10-3ubuntu1_i386.deb
> cd ..
sudo dpkg -i libsdl1.2debian-alsa_1.2.10-3ubuntu1_i386.deb

NOTE: you dont really need to do all this in /usr/src, you can do it from any folder you choose, for example in your home one, so most of the sudo will not be needed.

I hope it helps :D

Edit: I forgot after you can delete all the stuff you downloaded plus the dependeces.

---

### Post by minisori on 2006-10-03
Sorry there is a mistake up, i corrected it now.

Edit: And here i leave the alsa working package for edgy wich i just compiled, just if anyone want to get it.

Note: After you have installed the one i atached or the one you compiled by yourself, update manger will jump saying there is an update.. dont install it or again the darkness will come :P

---

### Post by Lord Illidan on 2006-10-04
Thanks mate. I installed the deb and it works fine.. will add this thread to launchpad, then.

Just a note : build-dep didn't work for me...why? Do I have to install something first?

---

### Post by minisori on 2006-10-04
Hum no idea, I thought it was a default option for apt-get :-s

---

### Post by Lord Illidan on 2006-10-04
> **minisori said:**
> Hum no idea, I thought it was a default option for apt-get :-s

Ok - got it.

You have to change this line : ```
sudo build-dep libsdl1.2debian
```

to```
 sudo apt-get build-dep libsdl1.2debian
```

---

### Post by minisori on 2006-10-04
ohhh sorry was that the error lol, i didn't notice i didn't write apt-get before.

Sorry, ](*,) , fixed now.

---

### Post by Lord Illidan on 2006-10-18
This still hasn't been fixed..shame

---

### Post by aktiwers on 2006-10-18
Maybe we should sendt it to the developers?

---

### Post by minisori on 2006-10-21
Yes i saw they updated the package to ubuntu2 but still there is the bug.

---

### Post by Lord Illidan on 2006-10-22
Damn, I upgraded by mistake, and now not only does Tremulous play as dark as possible, but when I downgrade, I cannot install anything from the repos without running sudo apt-get -f install which upgrades again to the faulty version.

EDIT : this is damn near unforgivable, imho.

---

### Post by minisori on 2006-10-22
Yes, that is cause the dummy package. You can compile it again with the new version or just install the dummy package of the patched one.

Here you have the old one in case u dont want to compile all again :P

---

### Post by sefs on 2006-12-15
In point number 8 below I am lost what do you mean by the alsa one...is there a number of packages that i can choose from that are made? How do I know which one to use if its alsa or something else.

When deleteting stuff after applying the patch  what should i delete. from what I get in what you say ... they are about 3 things to delete?

1) /usr/src/libsdl1.2-1.2.10 directory
2) the directory that i created the path in
3) the dependacies...this part i don't get...where are they and how can i delete them?

Thanks.

> **minisori said:**
> First thx for the patch it worked flawless :D



8. After a long wait you will get it compiled now to install it. For example if you use the alsa one install libsdl1.2debian-alsa_1.2.10-3ubuntu1_i386.deb




Edit: I forgot after you can delete all the stuff you downloaded plus the dependeces.

---

### Post by Lord Illidan on 2007-01-02
This still hasn't been fixed in the upgrades of libsdl. I really hope it won't continue into Feisty.

---

