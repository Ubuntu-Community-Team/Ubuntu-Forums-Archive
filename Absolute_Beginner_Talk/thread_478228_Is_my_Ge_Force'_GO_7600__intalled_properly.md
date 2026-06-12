---
title: "Is my Ge Force' GO 7600  intalled properly?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Doc.Frosty on 2007-06-19
:popcorn:
Dear friends i'd like to know what the hell i have to do to know if my Grahphics Card is well installed or not...

Before i was using Microsoft Xp so when i needed to check something about my hardware i was used to to the control panel but since i started to use ubuntu i didn't noticed anything similar, so if i want to check about hardware where i have to go or what line command am i supposed to write?

Thanks a lot guys.

---

### Post by Doc.Frosty on 2007-06-19
please tell me something......

---

### Post by mjwhitfield on 2007-06-19
Do you have problems with the screen?
What is it you want to check?
If it's working now, what makes you think you need to check it?

---

### Post by firetux on 2007-06-19
Post the output from glxgears and glxinfo.

---

### Post by Doc.Frosty on 2007-06-19
3757 frames in 5.0 seconds = 750.432 FPS
3842 frames in 5.1 seconds = 750.460 FPS
3894 frames in 5.2 seconds = 755.674 FPS
3840 frames in 5.1 seconds = 756.104 FPS
3720 frames in 5.0 seconds = 742.224 FPS
4302 frames in 5.1 seconds = 842.875 FPS
4478 frames in 5.1 seconds = 880.775 FPS
4477 frames in 5.1 seconds = 874.353 FPS
4237 frames in 5.0 seconds = 846.546 FPS
4440 frames in 5.1 seconds = 878.107 FPS
4440 frames in 5.0 seconds = 881.735 FPS
4440 frames in 5.1 seconds = 873.578 FPS
4440 frames in 5.1 seconds = 872.748 FPS
4440 frames in 5.1 seconds = 871.599 FPS
4320 frames in 5.2 seconds = 837.808 FPS
4266 frames in 5.0 seconds = 852.567 FPS
4126 frames in 5.1 seconds = 806.579 FPS
4068 frames in 5.0 seconds = 805.974 FPS
4407 frames in 5.1 seconds = 871.960 FPS

this is what shows after the command GLXGEARS

frosty@frosty-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


This is glxinfo command result...

---

### Post by rajeev1204 on 2007-06-19
TYPE nvidia-settings in terminal

this is what u will get   .


I have created a custom launcher for this command under menu/system tools so i just click on it to display info

---

### Post by jd65pl on 2007-06-19
The graphics card is not rendering 3D, this suggests you haven't installed the driver for it.

---

### Post by Doc.Frosty on 2007-06-19
> **jd65pl said:**
> The graphics card is not rendering 3D, this suggests you haven't installed the driver for it.

Probably i have no idea how to install my card here....
What should i do?!?!?

---

### Post by mjwhitfield on 2007-06-19
> **jd65pl said:**
> The graphics card is not rendering 3D, this suggests you haven't installed the driver for it.Explain to a newbie (me) which part of the info he posted says it's not renderng 3d?

---

### Post by Doc.Frosty on 2007-06-19
> **mjwhitfield said:**
> Explain to a newbie (me) which part of the info he posted says it's not renderng 3d?


i'm a newbie too but my intuition tell me that could be this line that let him understand...


direct rendering: No




Anyway i tried to use the command nvidia-settings but it fails...


this is the report..

frosty@frosty-laptop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

but it open a wind with a few controls...

---

### Post by anaconda on 2007-06-19
You havn't installed the restricted drivers. It wont work before you do!

Go to System>Administration>Restricted drivers manager
and select the NVIDIA driver.
It will install the drivers automatically..

---

### Post by rajeev1204 on 2007-06-19
oops sorry  i missed that . U have not installed nvidia drivers

install  nvidia drivers through the restricted drivers manager 

Configures everything automatically .

Or through synaptic  install nvidia-glx-new

---

### Post by Doc.Frosty on 2007-06-19
> **rajeev1204 said:**
> oops sorry  i missed that . U have not installed nvidia drivers

install  nvidia drivers through the restricted drivers manager 

Configures everything automatically .

Or through synaptic  install nvidia-glx-new


Restricted drivers manager....?!?!?!?
I heard about him but i forgot where he is located...

Sorry, but i'm really a noob...

---

### Post by Doc.Frosty on 2007-06-19
> **rajeev1204 said:**
> oops sorry  i missed that . U have not installed nvidia drivers

install  nvidia drivers through the restricted drivers manager 

Configures everything automatically .

Or through synaptic  install nvidia-glx-new



i was installing the drivers when i lost the connection and this is what appeared when i tried to install the second time...,.


E: /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.28_i386.deb: tentata sovrascrittura di `/usr/bin/nvidia-settings', che si trova anche nel pacchetto nvidia-settings



that mean the pc try to rewrite the file "/usr/bin/nvidia-settings" but it failed...


Any idea on what i have to do?


thanks again!


th

---

### Post by rajeev1204 on 2007-06-19
> **Doc.Frosty said:**
> Restricted drivers manager....?!?!?!?
I heard about him but i forgot where he is located...

Sorry, but i'm really a noob...


Go to main menu > system > administration > restricted driver manager

---

### Post by Doc.Frosty on 2007-06-19
> **rajeev1204 said:**
> Go to main menu > system > administration > restricted driver manager


yeah i got what i have to do but the point now is that after i lost the connection the first time if i try install those driver another time it says i can't write them again.
Probably i should delete the incomplete one but i do not know how to do that.

---

### Post by Doc.Frosty on 2007-06-20
guy, i'm freaking out....i spent  a lot of time to try to understand what i have to do to delete the filese that i downloaded just till the half....
When i try to re-install those "nvida-glx-new" it says that he can't write cause there already is an incomplete version of them....
Should i format?



:popcorn::(

---

### Post by rajeev1204 on 2007-06-20
Hi

try this 

         sudo apt-get --purge remove nvidia-glx-new nvidia-kernel-common nvidia-settings

Will clean out all nvidia configuration files .  and drivers 

Now try installing nvidia-glx  ( instead of glx-new )  from synaptic

---

### Post by Doc.Frosty on 2007-06-20
> **rajeev1204 said:**
> Hi

try this 

         sudo apt-get --purge remove nvidia-glx-new nvidia-kernel-common nvidia-settings

Will clean out all nvidia configuration files .  and drivers 

Now try installing nvidia-glx  ( instead of glx-new )  from synaptic


I am trying that command.....i let you know what will happen...


Thanks a lot...

---

### Post by Doc.Frosty on 2007-06-20
> **rajeev1204 said:**
> Hi

try this 

         sudo apt-get --purge remove nvidia-glx-new nvidia-kernel-common nvidia-settings

Will clean out all nvidia configuration files .  and drivers 

Now try installing nvidia-glx  ( instead of glx-new )  from synaptic



Bad news i did what you suggested but another error show up: 


E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb: il sottoprocesso pre-installation script ha restituito un codice di errore 2



what can i do?

---

### Post by Doc.Frosty on 2007-06-20
please help me...

---

### Post by rajeev1204 on 2007-06-20
hi

come stai .

Sorry i dont understand that error message . 

Could u translate that into english so maybe me can help . :)

Check if the package nvidia-settings is installed  . If it is installed then remove it completely  including configuration files ( through synaptic )

Also try this in terminal  sudo apt-get clean


regards

rajeev


P.S  .   Have to upgraded from edgy to feisty or is this a fresh install ??

---

### Post by Doc.Frosty on 2007-06-20
> **rajeev1204 said:**
> hi

come stai .

Sorry i dont understand that error message . 

Could u translate that into english so maybe me can help . :)

Check if the package nvidia-settings is installed  . If it is installed then remove it completely  including configuration files ( through synaptic )


regards

rajeev


P.S  .   Have to upgraded from edgy to feisty or is this a fresh install ??


The error means moreless : the process of inferior level resulted in error code lvl 2

the nvidia-settings is installed cause i replaced after i tried your first solution and didn't solve the problem.

So now what am i supposed to delete exactly?

It's a fresh install, just left windows.

Comunque sto bene. Grazie

Do you speak italian?

---

### Post by rajeev1204 on 2007-06-20
> **Doc.Frosty said:**
> The error means moreless : the process of inferior level resulted in error code lvl 2

the nvidia-settings is installed cause i replaced after i tried your first solution and didn't solve the problem.

So now what am i supposed to delete exactly?

It's a fresh install, just left windows.

Comunque sto bene. Grazie

Do you speak italian?



The package nvidia-settings is included in the nvidia-glx package so that package should not be installed separately  .When u install nvidia-glx package , nvidia-settings is contained within that package itself .  I think that is why the problem is happening cos u have nvidia-settings package installed .

Ok before a reinstalling do this ........ sudo apt-get clean

then install nvidia-glx 
 


I dont speak much italian :) just hello

---

### Post by Doc.Frosty on 2007-06-20
how can i delete the configuration files?
i know how to take out nvidia-settings but no idea about the configuration files...

---

### Post by rajeev1204 on 2007-06-20
> **Doc.Frosty said:**
> how can i delete the configuration files?
i know how to take out nvidia-settings but no idea about the configuration files...



Go to synaptic Right click on nvidia-settings and select remove completely

---

### Post by Doc.Frosty on 2007-06-20
i tried the apt-get clean , i deleted nvidia-settings but i couldn't nvidia-glx anyway.

After apt-get clean was i supposed to reboot the system?

---

### Post by Doc.Frosty on 2007-06-20
i tried to use apt to install nvidia-glx

this is the result...


frosty@frosty-laptop:~$ sudo apt-get install nvidia-glx
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Pacchetti suggeriti:
  nvidia-kernel-source
I seguenti pacchetti NUOVI (NEW) saranno installati:
  nvidia-glx
0 aggiornati, 1 installati, 0 da rimuovere e 27 non aggiornati.
È necessario prendere 4492kB di archivi. 
Dopo l'estrazione, verranno occupati 13,7MB di spazio su disco.
ATTENZIONE: i seguenti pacchetti non possono essere autenticati!
  nvidia-glx
Installare questi pacchetti senza la verifica [s/N]? s
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted nvidia-glx 1:1.0.9631+2.6.20.5-16.28 [4492kB]
Scaricato 4492kB in 5m31s (13,5kB/s)                                           
(Lettura del database ... 96276 file e directory attualmente installati.)
Spacchetto nvidia-glx (da .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' è in conflitto con `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: errore processando /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb (--unpack):
 il sottoprocesso pre-installation script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


it doesn't say anything special except this line...


Spacchetto nvidia-glx (da .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' è in conflitto con `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: errore processando /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.28_i386.deb 

That means this file "diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx" in conflict with the following file "diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new".


i thought it could be usfull...

---

### Post by Doc.Frosty on 2007-06-20
should i start to consider Format: C a solution?

---

### Post by rajeev1204 on 2007-06-20
Hi

It seems the error is different this time about conflict between nvidia glx and glx new 

Before u format , maybe u can try to reinstall nvidia-glx-new again  so it will overwrite the old nvidia-glx configuration .

Iam sorry iam unable to help any further.:(


Please let me know how it goes .



regards

rajeev

---

### Post by Doc.Frosty on 2007-06-21
> **rajeev1204 said:**
> Hi

It seems the error is different this time about conflict between nvidia glx and glx new 

Before u format , maybe u can try to reinstall nvidia-glx-new again  so it will overwrite the old nvidia-glx configuration .

Iam sorry iam unable to help any further.:(


Please let me know how it goes .



regards

rajeev

i'm out now, but as soon as possbile i'll try your solution but i don't think is gonna work because  it already told me the system cann'ot override the old files....

thanks a lot anyway

---

### Post by Motoxrdude on 2007-06-21
Eh, screw it. Just reinstall ubuntu. It always works for me ;)

---

### Post by Doc.Frosty on 2007-06-21
> **Motoxrdude said:**
> Eh, screw it. Just reinstall ubuntu. It always works for me ;)


I'll do if it doesn't work now...anyway it seems that the nvidia-glf-new are working...
it should be fixed...

---

### Post by Doc.Frosty on 2007-06-21
it's seems ok now..

i installed the driver nvidia-glx  but when i ask glxinfo or glxgears this is what appears:



frosty@frosty-laptop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
frosty@frosty-laptop:~$ 



and



frosty@frosty-laptop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 16 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
frosty@frosty-laptop:~$ 



Any idea?

---

### Post by firetux on 2007-06-21
The nvidia driver needs a reboot  to work.
If it still doesn't work after reboot, post your xorg.conf.

---

### Post by meborc on 2007-06-21
usually, if you have problems with packages incomplete, you can fix it with> sudo apt-get update
sudo apt-get -f installat least i always can :D

---

### Post by rajeev1204 on 2007-06-21
There is one step u need to do after installing nvidia driver


type in terminal  sudo nvidia-glx-config enable

Now it should work properly

---

