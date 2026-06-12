---
title: "ATI Radeon 9000 Graphics Card With 3D Desktop"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by will2273 on 2008-04-16
I really have no idea what I am doing with Ubuntu.  I am really just trying it out because I have an extra laptop which gives me that luxury.

However, I am having a huge problem setting up my 3d desktop which seems to be a common theme with ATI Radeon Graphics cards.

What I do know is that my card is supported but when I attempt to change my desktop effects I can't.

What I really need help with is the super dumb version of this.  I actually had to reinstall this OS three times because I messed up the xorg.conf.  I have a seriously hard time even altering that (probably because it took me twenty minutes to open a terminal).

Do I need to enable compiz?

How to I Install the driver because the only driver in my restricted drivers manager is an internet driver?

How do I enable the open source software?

Basically, I just reinstalled a fresh clean version of Ubuntu 7.10 and I would give my left leg for someone to show me how to enable this darn 3d desktop on this graphics card.

Start to finish walkthrough would be awesome.

CAN ANYONE HELP?  I m trying

---

### Post by Crafty Kisses on 2008-04-16
If the Restricted Drivers Manager doesn't have your driver, you might want to use Envy.

Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

See if that works.

This only supports nVidia and ATI.

---

### Post by qamelian on 2008-04-16
You should be able to just go to System > Preferences > Appearance and change the stting on the Visual Effects tab from "none: to one of the other settings. No additional drivers are needed with this card and compiz does not need to be installed because it already is by default. I have the same card here and it works out of the box.

What happens when you change to Normal or Extra on the Visual Effects tab?

---

### Post by Crafty Kisses on 2008-04-16
> **qamelian said:**
> You should be able to just go to System > Preferences > Appearance and change the stting on the Visual Effects tab from "none: to one of the other settings. No additional drivers are needed with this card and compiz does not need to be installed because it already is by default. I have the same card here and it works out of the box.

What happens when you change to Normal or Extra on the Visual Effects tab?

Yeah, that's what I was thinking too. My friend has a similar card and he doesn't have any issues with it, and it worked out of the box, and come to think of it I think it was this card.

That's really weird.

---

### Post by qamelian on 2008-04-16
> **Codename said:**
> If the Restricted Drivers Manager doesn't have your driver, you might want to use Envy.

Link: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

See if that works.

This only supports nVidia and ATI.
Don't bother. This card doesn't require the restricted driver, which is an old driver anyway since ATI no longer supports this card and hasn't for several driver releases now. Even on the last driver version that supported this card, the open-source driver out-performed the restricted driver.

---

### Post by Crafty Kisses on 2008-04-16
> **qamelian said:**
> Don't bother. This card doesn't require the restricted driver, which is an old driver anyway since ATI no longer supports this card and hasn't for several driver releases now. Even on the last driver version that supported this card, the open-source driver out-performed the restricted driver.

Yeah, I wasn't sure, thanks for the information.

---

### Post by will2273 on 2008-04-16
First off thank you guys so much for the help.  I guess you understand how hard this is without really knowing anything about programing.

When I try to change the effects I get the message

"desktop effects cannot be enabled"

---

### Post by will2273 on 2008-04-16
maybe I don't have the graphics card I think I do.

The laptop is hp pavilion zt3000

I looked it up and it should have this card can I test?

---

### Post by Crafty Kisses on 2008-04-16
> **will2273 said:**
> First off thank you guys so much for the help.  I guess you understand how hard this is without really knowing anything about programing.

When I try to change the effects I get the message

"desktop effects cannot be enabled"

Post the following output:
```
glxinfo
```

---

### Post by qamelian on 2008-04-16
> **Codename said:**
> Yeah, I wasn't sure, thanks for the information.
No problem. I did some real hair-pulling quite a while ago trying to get fglrx working before I realized it was unneeded. Actually, I've played a couple cross platform games on this card and was surprised to find that the open-source driver actually blew the doors of the native Windows driver bay a fairly noticeable margin as well!

---

### Post by will2273 on 2008-04-16
i put glxinfo into a blank terminal and got a bunch of information.  What am I looking for to make sure that this is supported because I am still getting "desktop effects cannot be enabled"

This is a brand new install nothing else on system.  Not even internet yet

Fortunately I figured out on my own how to turn on the wireless driver

---

### Post by qamelian on 2008-04-16
> **will2273 said:**
> i put glxinfo into a blank terminal and got a bunch of information.  What am I looking for to make sure that this is supported because I am still getting "desktop effects cannot be enabled"

This is a brand new install nothing else on system.  Not even internet yet

Fortunately I figured out on my own how to turn on the wireless driver
Congratulation on the wireless driver. I know they cause some users a lot of grief.

In a terminal, can you run:
```
glxinfo | grep "direct rendering"
```and post the result?

Repeat this for:
```
glxinfo | grep vendor
```

---

### Post by will2273 on 2008-04-16
direct rendering yes

server glx vendor string SGI
client glx vendor string SGI

Helpful?

---

### Post by will2273 on 2008-04-16
forgot the bottom was open gl vendor string tungsten graphics inc

---

### Post by qamelian on 2008-04-16
> **will2273 said:**
> direct rendering yes

server glx vendor string SGI
client glx vendor string SGI

Helpful?
Yep. This tells me that it should be fairly easy to fix you up.Let's make a backup of your xorg.conf file first.In the terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```Next, also in the terminal:
```
sudo nano /etc/X11/xorg.conf
```and make sure that there is a section in the file that says:
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection                      
```If this section is missing, add it to the end of the file. The best idea would be to copy it and paste it into the file using Shift-Insert.
Save the file by pressing Ctrl-O. When nano displays the path and filename to save to, just press enter. Then exit nano by pressing Ctrl-X.

Now, you need to restart your xserver. Close any applications and press Ctrl-Alt-Backspace. This will restart X and drop you back to the Gnome Login screen. Login and try again to activate the Visual Effects in the Appearance applet.

---

### Post by will2273 on 2008-04-16
OK.......

Everything went exactly to a T.  No hickups or errors at all, but after the restart I went into the appearance applet and selected extra and I got a message that has the Caution symbol with Desktop effects could not be enabled.

Any other thoughts because you have been very helpful?

I would have no idea where else to go.

Thanks again

---

### Post by qamelian on 2008-04-16
:confused: Very strange. Out of curiousity, what driver is showing in /etc/X11/xorg.conf in the device section? it should be either "ati" or "radeon". If it says "fglrx", which should only be the case if you tried installing the closed-source / restricted drivers, that may be the problem. Based on you previous responces, I doubt it will say "fglrx", but I want to be sure.

---

### Post by will2273 on 2008-04-16
Section "Device"
           Identifier          "ATI Technologies inc radeon r250 (mobility firegl 9000)"
           Driver                "ati"  [[[Lowercase letters}}
           Bus ID               "PCI:1:0:0"


Section "Monitor"
            Identifier           "Generic Monitor"
            Option                "DPMS"
EndSection

---

### Post by qamelian on 2008-04-16
I'm drawing a blank. I have this exact same card running in one of my test boxes and it "just works". I need to think about this some more. You may want to search the forum for say "ati radeon 9000 comipz" or something similar to see if you can find some helpful posts related to your issue. If I can think of anything, I'll post back ASAP. Sorry I'm at a loss right now.:(

---

### Post by will2273 on 2008-04-16
Is it possible that the ISO image I used may not have Compiz on it?

How can I check to see if it's installed because I was just thinking analytically (I know its scary) but I remember on one of my previous four tries once I got Compiz installed I had a fourth option in appearance that read custom.  I don't have that anymore.  

Can you help me make sure I have compiz.  For some reason I think thats the issue.

---

### Post by qamelian on 2008-04-16
> **will2273 said:**
> Is it possible that the ISO image I used may not have Compiz on it?

How can I check to see if it's installed because I was just thinking analytically (I know its scary) but I remember on one of my previous four tries once I got Compiz installed I had a fourth option in appearance that read custom.  I don't have that anymore.  

Can you help me make sure I have compiz.  For some reason I think thats the issue.
Unless you uninstalled it yourself, it is not the issue. It is part of the default install. In a terminal, run: ```
compiz --replace
``` and post the output.

---

### Post by will2273 on 2008-04-16
wills@wills-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity

---

### Post by will2273 on 2008-04-16
I actually have to get to bed I have a very early day tomorrow.  I wanted to thank you again very much and ask is there any way you could maybe think on this and post back tomorrow sometime when u get a chance?

I will have time to revisit at 6 tomorrow night eastern time

---

### Post by qamelian on 2008-04-16
> **will2273 said:**
> wills@wills-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity
The fact that you got that output confirms that you have compiz installed.I can only think of one other thing to try. First, let's make a backup of the compiz script:```
sudo cp /usr/bin/compiz /usr/bin/compiz_bak
```
Next, edit the compiz script and tell it to stop doing these steps:
```
sudo nano /usr/bin/compiz
```
The file starts with a block of comment lines several lines long, followed by several values being set. On a blank line below the comment block, but before the other values are set, enter: ```
SKIP_CHECKS="yes"
```
and save the file.
Now try enabling Visual effects. 
I need to crash now as I need to get up in a few hours to head in to my office, I'll check in later to see how you made out.

---

### Post by anewguy on 2008-04-17
Also note the error on resolution versus maximum 3D texture size - it fails on this and falls back to the metacity and hence no compiz.  You may need to find the specs for your card and monitor, then play with the resolutions (given the error the first thing I would do is lower the resolution to a maximum of 1024x768 - the message says the max 3D texture size is 1024).  You will need to get rid of that error before you will have compiz running.  Also worth noting - it helps a lot to install the compiz settings manager package.


I have a 9250 that I just did a clean install of Ubuntu Gutsy and it installed the driver and set up xorg.conf to "ati" and just worked "out of the box".  I needed to install the compiz settings manager, then went through advanced desktop effects settings (System/Preferences/Advanced Desktop Effects Settings) to set everything up.  Remember that compiz is just eye candy - it doesn't really do much for actually running anything.  But I get a kick out of showing my Vista buddies the shifted tabbing, the cube, etc., and then letting them know the whole thing was free and runs on an ancient machine that doesn't even come close to meeting the minimums for Vista.  I have the shading and reflections turned on and it just makes them drool.

Good luck!  :)

---

### Post by qamelian on 2008-04-17
> **anewguy said:**
> Also note the error on resolution versus maximum 3D texture size - it fails on this and falls back to the metacity and hence no compiz.  You may need to find the specs for your card and monitor, then play with the resolutions (given the error the first thing I would do is lower the resolution to a maximum of 1024x768 - the message says the max 3D texture size is 1024).  You will need to get rid of that error before you will have compiz running.  Also worth noting - it helps a lot to install the compiz settings manager package.


I have a 9250 that I just did a clean install of Ubuntu Gutsy and it installed the driver and set up xorg.conf to "ati" and just worked "out of the box".  I needed to install the compiz settings manager, then went through advanced desktop effects settings (System/Preferences/Advanced Desktop Effects Settings) to set everything up.  Remember that compiz is just eye candy - it doesn't really do much for actually running anything.  But I get a kick out of showing my Vista buddies the shifted tabbing, the cube, etc., and then letting them know the whole thing was free and runs on an ancient machine that doesn't even come close to meeting the minimums for Vista.  I have the shading and reflections turned on and it just makes them drool.

Good luck!  :)
Strange. I get that error too, but compiz runs just fine for me with the SKIP_CHECKS="yes" option.

Also, compiz is not just eye candy. Yes, there are some effect that are mostly eye-catching as opposed to functional, but there are a number of features that I find add real usability enhancements as well. Even features that to some seem like they are just attention-getters can make a real difference in your interactions with the desktop.

---

### Post by p0k3rch1p on 2008-06-18
I'm having the same error as well.  I just upgraded to Hardy Heron.

Here is my log of the glxinfo command:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
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
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 2x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2a 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2b 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x2c 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x2d 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x2e 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x2f 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x30 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x31 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x32 16 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x67 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
Segmentation fault

```

According to the lspci command, I have:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)

```

any help is appreciated! Thanks!

---

