---
title: "Serious system lag Ubuntu 6.10"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-03-25
Forgive me if this issue turns out to be beryl related, and therefore "off topic" however I could really use some feedback from the experienced Ubuntu users here.

I installed Ubuntu edgy around 3 weeks ago, and have been amazed by linux ever since, as an ex legacy OS user, breaking free from the aforementioned legacy os has brought a new breeze of life into my computing world.

Up until now I have had very limited Ubuntu issues, a real credit to the development team, however at the moment I am experiencing serious system lag, akin to legacy os "gunge" issues.

I am not blessed with the greatest or most powerful pc, however she's always done me alright...my issues started when I installed Beryl, my graphics card (only having an available 64mb of memory bless his cotton socks:) ) simply cannot cope with beryl (or at least I think this is the problem), and whilst loading an xgl/beryl session my system simply falls over and freezes X (I think its called :confused: ).

I decided to give beryl a miss, after all its cool but unnecessary; and reverted back to the standard GNOME desktop, however my system is now super s l o w.....I have conkey installed and decided to take a look, it seems that "something" is using over half of my RAM, and thats whilst the OS is sat looking pretty but not actually doing anything! I currently only have 256mb RAM on board... therefore 160mb of already committed RAM means disaster to my sys, and has already caused issues with system freezes (currently on 2-3 per day) and subsequent restarts.

The recently available Ubuntu updates were also downloaded, and I wondered if perhaps these were the culprit...however I seem unable to find anyone else complaining about this so I presume the updates and my sys issues are unrelated.

My system details are as follows:

2.4ghz P4
256mb RAM
ATI Radeon 7500 64mb memory.

Perhaps my poor system is to blame, although quite honestly it isn't the worst sys config you will see....

Ive seen xubuntu and was wondering what all that was about, I read that it doesn't demand too much from your system, however what are the exact differences between Ubuntu, and Xubuntu??

I am able to supply further info if anyone is kind enough to assist, I am about to remove beryl hope that this helps, otherwise it seems I am doomed by the legacy is style pc gunge which wil forever slow down my sys until I have the time and energy for a fresh install!! :mad: 

thanks in advance to readers, and anyone who is able to assist here.

---

### Post by rodrigo juarez on 2007-03-25
First you have to know that setting up Beryl is not easy at all there are many guides for many hardware setups, however you should try here first: [http://ubuntuforums.org/showthread.php?t=263851]("http://ubuntuforums.org/showthread.php?t=263851")
There are many links in the page, follow each one to see the different methods.
Also, you can see the help at Beryl forums [here]("http://forum.beryl-project.org/viewforum.php?f=36&sid=613872b07bc17267bab5c31d1ea87b9c")
As for the differences between Ubuntu editions, look at ubuntu.com (I did't give you the link as I'm not having response from ubuntu.com servers)

---

### Post by WakkiTabakki on 2007-03-25
Hi
Just to get the ball rolling, lets see if the graphics side of your config is the problem...
What's the output of running ```
glxinfo
``` in a terminal?

Only the top part is interesting (tell's you whether you've got hardware rendered 3D or not). Mine looks like this:
> name of display: :0.0
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
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6600 GT/AGP/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 96.31


Also, try running ```
glxgears -info
``` to get an idea of how fast 3D-rendering is on your system (but remember, it's not a benchmark :) )
Hmmm, since you're on 6.10, the command may be ```
glxgears -iacknowledgethatthistoolisnotabenchmark
```


Have you got wireless network? Any network? Is it properly configured, I mean, does it work...

/N

---

### Post by TURNER on 2007-03-25
Hi, thanks for getting back so quickly...

Here are the results of 

```
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_logic_op, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_
```

Glxgear's seems to run ok, fairly quickly and smoothly....

However my main issues at the moment, centre around my system whilst not running an xgl session, my system has slowed up to stopping point, does Beryl (running in the background) really take up so much RAM?

---

### Post by TURNER on 2007-03-25
anymore help advice ref this issue would be appreciated....don't be shy :)

---

### Post by WakkiTabakki on 2007-03-25
Sorry, I'm at a loss... 
But a few things you could check out:
* Do you have a wireless network? I noticed (don't remember which distro) if net is a bit dodgy, the comp could seem to hang waiting for timeouts...
* Have you run memtest86 to verify that the memory you've got actually works properly. Well, if this was the prob, it would've caused regular hard lockups, not just sluggish behaviour....
* Run gnome-system-monitor and see if you can spot which process/application it is thats hogging the resources (if any). Make sure you show 'CPU Time' which tells the total amount of time a process has spent actively running

But, apart from being a bit low on memory, you rig should definitely not have any performance issues... 
<edit>The fact that you've got 160-something Mb of mem commited, doesn't necessarly mean it's tied up and not available for use. There are caches and different types of virtual memory that can be released if needed, so it's actually really hard to tell how much is in use. On my system, with 1Gb, there's about 400Mb of "commited" mem when I've just logged in... The best sign of running out of memory is monitoring how much of the swap file is being used (you can see that in the gnome-system-monitor as well</edit>
If you're looking to reinstall anyway, I'd suggest you take a look at Xubuntu, which comes with the Xfce desktop environment (instead of Gnome). It'll perform a lot better on a lower end machine, and you still can run anything that the standard Ubuntu setup would...

And also, Feisty (the upcoming version, only a week or two from release) is a lot better than Edgy. I've been running Feisty since January, and granted, it's an adventure running an OS that's in its test stages, it still has always felt a lot more stable than Edgy did.

/N

---

### Post by TURNER on 2007-03-25
WakkiTabakki thanks for taking the time and effort to look into this!

Gnome sys monitor indicates that 74% of my RAM is being used, and a total of 2 % of my cpu, the biggest RAM eater is apparently firefox, but I am working with 2 windows and numerous tabs...

I am still a little concerned, as I previously specified my sys did previous work much better.....now everything has a time delay, and ubuntu seems to be really strained.

I've heard X org mentioned a few times, is X the desktop manager?? How can I look into my X settings via the terminal?

Thanks again...

---

### Post by WakkiTabakki on 2007-03-26
Hi again
When checking the system monitor, look at the 'CPU Time' column, which shows the accumulated time a process has spent actively running. The '% CPU' column is just a momentary value. Use you comp normally for 15 minutes or so, and then check which processes has the highest 'CPU Time' (and again, the reported memory usage doesn't tell the full story).
Also, having the monitor running and sorting the columns on '% CPU', you can check which process jumps on top when the comp drops to a crawl...

Yup, firefox is a memory hog, but there may be some tweaks you can do to get firefox to be a bit more conservative (you can access its settings by surfing to the address 'about:config'). Check the Mozilla forums for that.
And maybe there are less resource hungry browsers, check out Opera and Epiphany (well LYNX would be the ideal one, but surfing in text-mode does take some of the fun out of the web...). [http://en.wikipedia.org/wiki/Comparison_of_web_browsers]("http://en.wikipedia.org/wiki/Comparison_of_web_browsers") is a start.


X is the underlying graphic system (among other things, it handles drivers for the graphics card, keyboard, mouse etc), the desktop manager runs on top of X. Regardless of which desktop manager you use, X is always the "foundation". There are two flavours of X, XFree and Xorg. Ubuntu switched from XFree to XOrg som time ago, since XFree changed its licensing, making it less free (!).
X is configured through the file /etc/X11/xorg.conf but there isn't much you can do with it, apart from just making sure the correct drivers are used. You may want to check the forum for instructions on how to make sure your graphics card is using the correct driver (ati, radeon or fglrx depending on your card). I've got a nvidia so I can't help you, but there should be roughly 6 billion pages out there dealing with that...
I don't believe this is your problem, though...

The desktop manager runs on top of X, Gnome (Ubuntu), KDE (Kubuntu) and Xfce (Xubuntu) are examples... KDE and Gnome are generally more resource intense than Xfce, so you could try that and see if it helps... You may be able to install Xfce without a complete reinstall simply by installing the 'xubuntu-desktop' package together with all it's dependencies. 
I have never tried this myself, and it feels like it could lead up to one of those classic 'doh!'-moments, so DO CHECK THE FORUM IF THIS IS POSSIBLE BEFORE TRYING!!!


/N

---

### Post by cowlip on 2007-03-26
easy performance tweak that might help [http://beuno.com.ar/?p=4](http://beuno.com.ar/?p=4)

---

### Post by TURNER on 2007-03-26
I also posted [[COLOR="Blue"]in this thread[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=322846") and after adding some swap mem things seem to have gotten better, although I am still going to reinstall and get rid of legacy os next door :) , and format my hard drive...on that note has anyone any recommendations in that area, FAT32 or a differing format??

I am also going to keep Edgy, and prob upgrade to Feisty after the release.....I am hooked on linux, I've managed to find a replacement for all of my software needs, and it feels good to be free from windows, especially when you have to earn your money working for MS where the average worker is treated worse than the average end user! :( 

 Thanks for all your time and effort with this!!:)

---

### Post by WakkiTabakki on 2007-03-27
Go for EXT3 instead of FAT, it's faster, safer and more secure. 
If you need to access it from a Windows install on the same computer, you can install an IFS in Windows ([http://www.fs-driver.org](http://www.fs-driver.org)).

/N

---

