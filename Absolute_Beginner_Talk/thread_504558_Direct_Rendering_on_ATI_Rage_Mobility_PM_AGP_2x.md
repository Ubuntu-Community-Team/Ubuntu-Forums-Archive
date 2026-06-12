---
title: "Direct Rendering on ATI Rage Mobility P/M AGP 2x"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-07-19
Hi there,

I have a  ATI Rage Mobility P/M AGP 2x card in my new laptop, which seemed to install fine (good resolution, etc) using a basic feisty install.

Trying to get a better driver installed to get direct rendering/desktop effects working, but all guides seem to be for Hoary/Breezy, and I know alot has changed since then.

Anyone point me in the right direction for what to do in a  Rage Mobility P/M AGP 2x?

glxinfo:
> matt@matt-laptop:~$ glxinfo
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Old Pink on 2007-07-19
Also,

Restricted Drivers Manager:
[IMG]http://www.filehive.com/files/0719/Screenshot-restricted-manager.png[/IMG]

lspci:
> 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

xorg.conf:
"ati" driver.

---

### Post by ageilers on 2007-07-19
This may be some help for you.

[[COLOR="DarkOrange"]http://ubuntuforums.org/showthread.php?t=406389[/COLOR]]("http://ubuntuforums.org/showthread.php?t=406389")

---

### Post by Old Pink on 2007-07-19
The information I've posted above is all I know about my Video/Graphics card. Is it a mach64 chipset, as required in the thread you posted? How am I to know?

---

### Post by ageilers on 2007-07-19
I looks like your card uses the Mach64 chipset. Here is another How To:

[[COLOR="DarkOrange"]http://ubuntuforums.org/showthread.php?t=7200[/COLOR]]("http://ubuntuforums.org/showthread.php?t=7200")

---

### Post by Old Pink on 2007-07-19
> **ageilers said:**
> I looks like your card uses the Mach64 chipset. Here is another How To:

[[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=7200[/COLOR]]("http://ubuntuforums.org/showthread.php?t=7200")


That hasn't been updated in over a year. 

> E: Couldn't find package linux-headers-2.6-686

Even the first stage is outdated and unable to install. 

I'm looking for something simple, and most importantly, Feisty friendly/recent.

---

### Post by Old Pink on 2007-07-19
> **ageilers said:**
> I looks like your card uses the Mach64 chipset. Here is another How To:

[[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=7200[/COLOR]]("http://ubuntuforums.org/showthread.php?t=7200")

Tried it anyway.
> The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

The first part worked, the second didn't. 

I just know when I restart X now, it won't start properly. Cheers. :( 

Anyway to fix this, preferably with direct rendering?

---

### Post by h4mx0r on 2007-07-19
"The script will now compile the DRM kernel modules for your machine."

wtf?

Also I am using an ATI 3d rage pro turbo 2x agp according to print out on my computer. It also is using ati under xorg.conf and glxinfo says its using mesa with no direct rendering. One thing I noticed about my computer is its got an odd number of ram not divisible by 2 so I'm thinking it is using shared video memory. I'm on a desktop not laptop so perhaps different. Any drivers for pre-radeon ATI cards would be extremely helpful!

---

### Post by Old Pink on 2007-07-19
> **h4mx0r said:**
> "The script will now compile the DRM kernel modules for your machine."

wtf?
How does that warrant a "what the ****" ?

Also, I rebooted successfully, but it still says > direct rendering: No

---

### Post by Old Pink on 2007-07-19
> **Old Pink said:**
> Also, I rebooted successfullyAfter the reboot, tried a recompile to this:> ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.again! 

Told you these old guides were ridiculous to even attempt, any chance you could save me?

---

### Post by Old Pink on 2007-07-19
dri.log says this:> make DRM_MODULES=mach64.o modules
make[1]: Entering directory `/home/matt/dri/mach64-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.20-16-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/matt/dri/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/matt/dri/mach64-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/home/matt/dri/mach64-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/matt/dri/mach64-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/matt/dri/mach64-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/matt/dri/mach64-20060403-linux.i386/drm/linux-core'
make: *** [mach64.o] Error 2

---

### Post by Old Pink on 2007-07-19
Been working on this for hours now and it's getting **** off annoying, tried god knows how many 16 page threads packed full of solutions, thousands of reboots, hundreds of X restarts, millions of guides, billions of terminal commands and no change, just a system full of crap that doesn't work.

Anyone got an **easy, RECENT, WORKING** guide?!

---

### Post by Old Pink on 2007-07-19
Anyone know where the 750MB of crap all these relevant "solutions" have created is so I can delete it?

---

### Post by Old Pink on 2007-07-19
Right, well I'll BUMP this for a different timezone, about to go to sleep, would appreciate any help at all. :)

---

### Post by Old Pink on 2007-07-21
... anyone at all?

---

### Post by Old Pink on 2007-07-22
> **ageilers said:**
> This may be some help for you.

[[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=406389[/COLOR]]("http://ubuntuforums.org/showthread.php?t=406389")Tried this, which is frankly the worst written, most misspelt guess-guide ever written. Got half way through and the guide stopped working, 404 error on the packages. Tried to find them myself and continue, used info in the first post to help, installer complained kernel DRM modules wouldn't compile, rebooted.

glxinfo now kills X on the spot. Why? I have no idea.

Tried to reverse the guide, deleting all changes done by it, still, no fix. **HELP, PLEASE.**

---

### Post by Old Pink on 2007-07-22
**sudo dpkg-reconfigure xserver-xorg** 

... didn't fix it. Now **sudo aptitude reinstall**ing the kernel, image, headers, everything. ageilers, don't you have a two year old guide to get me out of this? :(

---

### Post by Old Pink on 2007-07-22
And this has become one of those threads everyone ignores.

**I'll PayPal $10 to anyone who can get this working properly, meaning glxinfo working without crashing X, and displaying "direct rendering: yes" because the drivers and everything are installed correctly.**

---

### Post by Old Pink on 2007-07-22
Could someone at least confirm that this thread can be **seen**?!

I'm going to post it in Multimedia and Video now, see if those guys have any more help available.

---

### Post by DougieFresh4U on 2007-07-25
> **Old Pink said:**
> And this has become one of those threads everyone ignores.

**I'll PayPal $10 to anyone who can get this working properly, meaning glxinfo working without crashing X, and displaying "direct rendering: yes" because the drivers and everything are installed correctly.**

I got Direct Rendering to work by changing depth from 24 to 16 in x-file, it had me troubled for a long, long time :(

---

### Post by dougfractal on 2007-07-27
**[SIZE="4"]Direct Rendering on Mach64 (Feisty)[/SIZE]**
 
This script is OLD. dri.freedesktop.org have newer snapshots.
new script at
[http://ubuntuforums.org/showpost.php...69&postcount=6](http://ubuntuforums.org/showpost.php...69&postcount=6)
Challenge: help me get Rage Mobility P/M with mach64 chip set DRI Working.
[COLOR="Silver"]
This is a script to use as a last resort, when all other guides have failed!
It is meant to be easy but it does use snapshots that are over a year old so may cause problems later. 

Copy and paste into terminal
```

echo -e "You need sudo active for this script\nIf you need to enter the password, do so and run this script again\n"
sudo apt-get install linux-headers-generic build-essential
cd /usr/src/linux-headers-`uname -r`/include/linux
if [ -f 'config.h' ] ; then echo -n ''; else sudo ln -s autoconf.h config.h; fi
cd /usr/src
if ! [ -d 'mach64_dri' ] ; then sudo mkdir mach64_dri; sudo chown $UID mach64_dri; fi
cd mach64_dri
if ! [ -d 'common-20060403-linux.i386' ] ; then  \
   wget http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2 ;\
   tar xjvf common-20060403-linux.i386.tar.bz2 ; \
fi
if ! [ -d 'mach64-20060403-linux.i386' ] ; then  \
    wget http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2 ; \
    tar xjvf mach64-20060403-linux.i386.tar.bz2  ; \
    sed -i '87s\__put_page\put_page\'  /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c  ; \
    sed -i -e '51a\*/' -e   '51i\/*' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c ; \
fi
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    24\DefaultDepth    16\'  /etc/X11/xorg.conf
echo -n "sudo echo -e '\nYou must run this script as root.\n';
cd /usr/src/mach64_dri/common-20060403-linux.i386
sudo ./install.sh
cd  /usr/src/mach64_dri/mach64-20060403-linux.i386
sudo ./install.sh
echo -e '\nRestart X-Windows to activate driver\n'
echo -e 'type:    sudo /etc/init.d/gdm restart\n' " > ~/mach64driver.sh
sed -i '1i\#!/bin/bash' ~/mach64driver.sh
chmod 755 ~/mach64driver.sh
cat ~/mach64driver.sh
sudo ~/mach64driver.sh

```


You have a script called **~/mach64driver.sh** that you will need to run every kernel upgrade.


**_check with_**
```
glxinfo | grep direct
glxgears
```


**_FeedBack_**

Could you please list your working card model.
```
lspci | grep -i vga
```

I would really appreciate it if posts were concise, and what troubleshooting steps where made to get it working.


[B][U]
Troubleshooting[/U][/B]

linux-image-686|k7|386 has been obsoleted by: linux-image-generic
```
sudo apt-get install linux-image-generic
```

xorg and other packages have been so messed up you need to start a fresh before running the script
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri
```


```
export LIBGL_DEBUG=verbose
glxinfo
```
It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."
```
cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so
```

```
cat /var/log/Xorg.0.log | grep EE
```
If the output has this somewheres...:
> (EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least xxxxx kB of video memory needed at this resolution and depth.
Change your bit depth to 16 instead of the default 24...look for this line in your /etc/X11/xorg.conf file under the "Screen" section
```
DefaultDepth    16
```

I wanted 24 bit display not the 16bit you forced on me.
sorry I naively thought your card only had 8meg ram
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    16\DefaultDepth    24\'  /etc/X11/xorg.conf

```



*This howto has been put together off the backs of so many other members.*[/COLOR]

---

### Post by Old Pink on 2007-07-29
> **DougieFresh4U said:**
> I got Direct Rendering to work by changing depth from 24 to 16 in x-file, it had me troubled for a long, long time :(Tried it, did nothing besides making the colors look ugly.
> **dougfractal said:**
> **[SIZE=4]Direct Rendering on Mach64 (Feisty)[/SIZE]**
 
This is a script to use as a last resort, when all other guides have failed!
It is meant to be easy but it does use snapshots that are over a year old so may cause problems later. 

Copy and paste into terminal
```

echo -e "You need sudo active for this script\nIf you need to enter the password, do so and run this script again\n"
sudo apt-get install linux-headers-generic build-essential
cd /usr/src/linux-headers-`uname -r`/include/linux
if [ -f 'config.h' ] ; then echo -n ''; else sudo ln -s autoconf.h config.h; fi
cd /usr/src
if ! [ -d 'mach64_dri' ] ; then sudo mkdir mach64_dri; sudo chown $UID mach64_dri; fi
cd mach64_dri
if ! [ -d 'common-20060403-linux.i386' ] ; then  \
   wget http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2 ;\
   tar xjvf common-20060403-linux.i386.tar.bz2 ; \
fi
if ! [ -d 'mach64-20060403-linux.i386' ] ; then  \
    wget http://dri.freedesktop.org/snapshots/mach64-20060403-linux.i386.tar.bz2 ; \
    tar xjvf mach64-20060403-linux.i386.tar.bz2  ; \
    sed -i '87s\__put_page\put_page\'  /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/ati_pcigart.c  ; \
    sed -i -e '51a\*/' -e   '51i\/*' /usr/src/mach64_dri/mach64-20060403-linux.i386/drm/linux-core/drm_stub.c ; \
fi
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    24\DefaultDepth    16\'  /etc/X11/xorg.conf
echo -n "sudo echo -e '\nYou must run this script as root.\n';
cd /usr/src/mach64_dri/common-20060403-linux.i386
sudo ./install.sh
cd  /usr/src/mach64_dri/mach64-20060403-linux.i386
sudo ./install.sh
echo -e '\nRestart X-Windows to activate driver\n'
echo -e 'type:    sudo /etc/init.d/gdm restart\n' " > ~/mach64driver.sh
sed -i '1i\#!/bin/bash' ~/mach64driver.sh
chmod 755 ~/mach64driver.sh
cat ~/mach64driver.sh
sudo ~/mach64driver.sh

```You have a script called **~/mach64driver.sh** that you will need to run every kernel upgrade.


**_check with_**
```
glxinfo | grep direct
glxgears
```**_FeedBack_**

Could you please list your working card model.
```
lspci | grep -i vga
```I would really appreciate it if posts were concise, and what troubleshooting steps where made to get it working.


[B][U]
Troubleshooting[/U][/B]

linux-image-686|k7|386 has been obsoleted by: linux-image-generic
```
sudo apt-get install linux-image-generic
```xorg and other packages have been so messed up you need to start a fresh before running the script
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall libgl1-mesa-dri
``````
export LIBGL_DEBUG=verbose
glxinfo
```It told me that the library /usr/X11R6/lib/modules/dri/mach64_dri.so couldn't be found."
```
cd /usr/X11R6/lib/modules/dri
sudo ln -s /usr/lib/dri/mach64_dri.so mach64_dri.so
``````
cat /var/log/Xorg.0.log | grep EE
```If the output has this somewheres...:
Change your bit depth to 16 instead of the default 24...look for this line in your /etc/X11/xorg.conf file under the "Screen" section
```
DefaultDepth    16
```I wanted 24 bit display not the 16bit you forced on me.
sorry I naively thought your card only had 8meg ram
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
sudo sed -i 's\DefaultDepth    16\DefaultDepth    24\'  /etc/X11/xorg.conf

```*This howto has been put together off the backs of so many other members.*The less said about this the better, this screwed my system beyond recognition, it was only by sheer luck that I had a year's experience and another PC that led me to get this fixed.

Would **not** recommend this for use by anyone, especially if you don't think you'll be able to recover X after the even the backup drivers are borked.

---

### Post by dougfractal on 2007-07-29
**ATI-Technologies Inc Rage Mobility P/M 2x (rev64) SOVLED but not for Old Pink**

> **i386DX said:**
> @Dougfractal

Tested your script in Feisty (kernel 2.6.20-16-generic). It worked without any problems!

**Extra info**

_VGA-card_
ATI-Technologies Inc Rage Mobility P/M 2x (rev64) 
(Compaq Armada E500)

_Glxinfo_
LibGL warning:  3D driver claims to not support visual 0x4b
direct rendering: Yes

_Glxgears_
LibGL warning:  3D driver claims to not support visual 0x4b
Smooth and about 136 fps ;-)

Don't be put off by old pink's remarks, you will soon see by looking at the threads, who has the problem.
I guess you just can't help some people. ;)

He even thinks I broke his network connection. I think he forgot to turn his hub on#-o

---

### Post by ./confused on 2007-10-03
I see it. I'm having the same problems, but I've not once received a response on these forums. I know how you feel about not getting responses. These forums are notorious for this.

---

### Post by DioSonoIo on 2008-02-18
Same problem with same card... but just 4 Mb internal memory and Ubuntu 7.10 Gutsy! Some1 can help me? :confused:

---

### Post by Jay Jay on 2008-02-18
I was in the same boat as you guys, I couldn't get the script to work and no-one replied. I managed to solve the problem myself in the end. This is what you need to do: use Alex's [script]("http://ubuntuforums.org/showpost.php?p=3274249&postcount=172") and with these [corrections]("http://ubuntuforums.org/showpost.php?p=4289970&postcount=207") you should be in business as I am now :)

---

