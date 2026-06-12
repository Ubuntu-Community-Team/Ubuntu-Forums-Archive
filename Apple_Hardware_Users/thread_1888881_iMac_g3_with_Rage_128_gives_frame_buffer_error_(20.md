---
title: "iMac g3 with Rage 128 gives frame buffer error (2011)"
date: 2011-11-30
forum: Apple Hardware Users
---

### Post by narcisgarcia on 2011-11-30
This comes from the original thread:
[http://ubuntuforums.org/showthread.php?t=1096448](http://ubuntuforums.org/showthread.php?t=1096448)

rsavage user made me a question, and I don't know why overdrank user closed the forum thread.

rsavage, yo can see the complete sheet for this computer here:
[http://wiki.lapipaplena.org/index.php/AppleImacG3350-ubuntu1104](http://wiki.lapipaplena.org/index.php/AppleImacG3350-ubuntu1104)

But I also copy the xorg.conf content:
```
# xorg.conf optimized for Apple iMac G3 350 (Summer 2000) with Ubuntu GNU/Linux 11.04
# Display device: ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS
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
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier "ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"
	# BusID	"PCI:0:16:0"
	# Driver "ati"
	Driver "r128"
	Option "NoInt10" "true"
	Option "CCEusecTimeout" "100000"
	Option "UseFBDev" "false"
	Option "XAANoOffscreenPixmaps"
	Option "SWcursor" "true"
	# Option "ForcePCIMode" "true"
EndSection

Section "Module"
	Load "i2c"
	# Load "bitmap"
	Load "ddc"
	Load "dri"
	# Disable "dri"
	Load "dri2"
	Load "record"
	Load "extmod"
	Load "freetype"
	# Load "dbe"
	# Load "glx"
	# Load "int10"
	Load "type1"
	# Load "vbe"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection 

Section "DRI"
	Mode 0666
EndSection

Section "Monitor"
	# Supports 1024x768@75, 800x600@94, 640x480@116
	Identifier	"iMac"
	VendorName	"iMac"
	ModelName	"Monitor Model"
	Option "DPMS"
	HorizSync 58-62
	VertRefresh 75-117
	# ModeLine "1024x768" 78.75 1024 1044 1140 1328 768 781 784 820 +hsync +vsync
	# ModeLine "800x600" 62.40 800 821 901 1040 600 609 612 644 +hsync +vsync
	# Modeline "640x480" 49.90 640 657 721 832 480 481 484 514 +hsync +vsync
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies Inc Rage 128 PR/PRO AGP 4x TMDS"
	Monitor "iMac"
	# Ubuntu 11.04 doesn't work in 16bit colour depth mode here
	DefaultDepth 24
	SubSection "Display"
		Depth 1
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600" "640x480"
		#Virtual 1024 768
	EndSubSection
EndSection
```
I don't know how to check if the X-Window session is working with 2D or 3D acceleration. I tested "glxgears -info" and gave me up to 10fps, but I don't know if it's the maximum for that graphics chip.

---

### Post by rsavage on 2011-11-30
Hi Narcis Garcia,
 
Thanks for getting back to me with this. I don't know why overdrank closed that other thread either! I did complain to the mods that it was an overuse of power, but they didn't reopen it! 
 
I did see your link that you posted later on another thread so thanks for that too! It's been on my list of things to do to reply to that thread. I've been very busy at the moment with limited amount of time to write on the forum and many threads I just haven't been able to answer.
 
I haven't got a r128 card, but my interest is due to this guide that I wrote [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) . I wanted to make sure I was advising people correctly. Somebody on askubuntu.com was trying to follow an early version of the guide and totally failed with the r128!
 
The user 'axion' did post an interesting answer though [http://askubuntu.com/questions/58488/x-does-not-want-to-start-at-all-no-screens-have-a-usable-configuration/62789#62789](http://askubuntu.com/questions/58488/x-does-not-want-to-start-at-all-no-screens-have-a-usable-configuration/62789#62789) .
 
Compiling a kernel seems a bit extreme (and I'm not sure whether the answer by axion is 100% accurate), particularly after I read the post by 'walterav' on the MintPPC forum [http://mintppc.org/forums/viewtopic.php?f=9&t=321&p=2673#p2673](http://mintppc.org/forums/viewtopic.php?f=9&t=321&p=2673#p2673) . He says his method works on Ubuntu 11.04 too:
 
> 
[noparse].... Even switching virtual consoles "ttys" that have a lower resolution is working fine! I haven't tried the mintppc versions yet, but only pure debian 5 and ubuntu 11.04 mini. .....
 
Second, the real problem is that with new kernel versions "offb" (openfirmware framebuffer) always gets loaded first. Therefor "aty128fb" will not load (memory reserved error etc), and is probably blacklisted, check syslog/dmesg and it will report something about framebuffer. This was fixed by adding "video=offb:off" to yaboot.conf in the append section, btw this file resides in the boot partition not in /etc/. When you restart you have no framebuffer at all and won't see a thing on your screen, unless you can login via ssh. So before you restart, uncomment aty128fb in /etc/modprobe/blacklist-framebuffer.conf. This will give you a framebuffer halfway past the bootstrap as soon as the modules get loaded. So don't panic if you see the Openfirmware/yaboot screen freezing when the system is booting, just wait and you have your picture back.
 
The third thing that fixed this was using a "xorg.conf" I found on this website with only adding (Option "UseFBDev" "true"), because you gonna use the framebuffer "aty128fb" and selecting "r128" as the Driver. Therefor all the other maybe conflicting options "NoInt10" etc are not necessary, but these well found Options might be necessary as a workaround if you have no or conflicting framebuffers.
.....
[/noparse]
I should point out he has got the thing about the yaboot.conf wrong. You should edit the file in /etc and then use the command ybin to copy it across to the boot partition. Alternatively, if you just want to test it you could use at the second yaboot prompt:
```

Linux video=offb:off

```
It might be best to check first you haven't got anything like video=ofonly in your yaboot.conf as I don't know how that would react with the new yaboot parameter. 
 
Another thing he has got wrong is that you actually want to comment the line (by adding a #) in /etc/modprobe/blacklist-framebuffer.conf rather than uncommenting it like he says.
 
If after a reboot things are successful, you could possibly load the aty128fb framebuffer earlier in the boot process by running the command "update-initramfs -u"?
 
You could possibly test all these things at the second yaboot prompt by typing:
 
```

Linux video=offb:off modprobe aty128fb

``` 
 
Option "UseFBDev" "true" is the default setting on PowerPC so you shouldn't have to state it in a xorg.conf.
 
It would be interesting if any of these things make a difference to your experience of the r128. When you run "glxgears -info", if you don't see "Software Rasterizer" written then you have 3D working I think (but I am no expert on this). When you run "glxinfo" check that you have at the start of the output "direct rendering: Yes". 
 
Finally, it is great to see your enthusiasm for ubuntu and the iMac. Keep up the good work!
 
rsavage
 
EDIT: I've just seen your comment at the bottom of the askubuntu thread so you know most of this stuff already!!!

---

### Post by new to ubutnu on 2011-12-08
ok so this is new to ubutnu and i am having a similar problem

i tried to do the Linux video= fixes but when entering them in the Linux video=offb:off caused the white screen to freeze up

---

### Post by rsavage on 2011-12-09
Okay let's focus on getting a working system by an xorg.conf......
 
I'll use the xorg.0.log from the askubuntu page as a guide. I suspect you have something similar. The relevant snippet from the bottom is here:
 
```

[  1902.318] (**) R128(0): Using framebuffer device
[  1902.318] (II) Loading sub module "fbdevhw"
[  1902.318] (II) LoadModule: "fbdevhw"
[  1902.319] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1902.325] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1902.325]    compiled for 1.10.1, module version = 0.0.2
[  1902.326]    ABI class: X.Org Video Driver, version 10.0
[  1902.326] (EE) Unable to find a valid framebuffer device
[  1902.327] (EE) R128(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
    (you may have to look at the server log to see warnings)
[  1902.327] (II) UnloadModule: "r128"
[  1902.327] (II) Unloading r128
[  1902.327] (II) UnloadModule: "fbdevhw"
[  1902.327] (II) Unloading fbdevhw
[  1902.327] (EE) Screen(s) found, but none have a usable configuration.
[  1902.332] 
Fatal server error:
[  1902.332] no screens found
[  1902.332] 

```
There is no shame in not understanding this as first glance. The people trying to help on the askubuntu page literally answer 1000s of problems so they are not novices to linux. However, none of them properly read the log, instead, they all focused on the last error message "EE) Screen(s) found, but none have a usable configuration".
 
If you trace further back up you'll see there are other error messages, the first being "(EE) Unable to find a valid framebuffer device". It is trying to use a framebuffer device. We know this because it tells us "(**) R128(0): Using framebuffer device". This is in line with what the r128 manual says for PowerPC:
 
> 
**Option** **"UseFBDev"** **"**_boolean_**"**
Enable or disable use of an OS-specific framebuffer device
interface (which is not supported on all OSs). See [fbdevhw]("http://manpages.ubuntu.com/manpages/natty/en/man4/fbdevhw.4.html")(4)
for further information. Default: **on** for PowerPC, **off** for other
architectures.

 
If we set this value to false in your xorg.conf it won't now look for a framebuffer and so you won't have the error. 
 
Now, what I am not sure about is the NoInt10. This is described in the "Screen" section of the manual, although it seems you can put it in the "Device" section too:
 
> 
**Option** **"NoInt10"** **"**_boolean_**"**
Disables the Int10 module, a module that uses the int10 call to
the BIOS of the graphics card to initialize it. Default: false.

 
Whether you get another error relating to Int10 I can only speculate. A lot of people seem to set this to true so it is worth trying if you still have a problem.
 
The users 'axion' and 'walterav' are trying to fix the framebuffer error in a different way. I suspect there is a better way than they both describe, but let's cross that bridge after you at least get a working system.

---

### Post by new to ubutnu on 2011-12-09
couple of questions

first how do i set useFBdev to false i am going to try putting false in the bool parantheses but i don't know if i need to uncomment the line

second how can i send the output on my screen in an email or something to another computer so i can post it here (im in cli so its kind of hard)

third i dont remember how to run that xorg file or whatever to get that screen with the no screen found but i did get that same screen

---

### Post by new to ubutnu on 2011-12-09
oh also i dont see the noint10 in my xorg.conf file so i dont know what to do to edit that if the framebuffer fix doesn't work

---

### Post by new to ubutnu on 2011-12-09
i tried the framebuffer=false option and the framebuffer was bypassed but it still ran to cli

then i added the noint10 line since i couldn't find it so i thought that would be good except now it goes to a blank screen like its thinking but it isn't responding and i cant get into the cli anymore

---

### Post by rsavage on 2011-12-10
> **new to ubutnu said:**
> 
second how can i send the output on my screen in an email or something to another computer so i can post it here (im in cli so its kind of hard)


No idea I'm afraid as I have never needed to look into it.  You can use google probably better than me!

All your other questions are answered in the lubuntu instructions.  You are asking questions when I am sound asleep so if you want answers then you'll get a quicker answer by re-reading the instructions.  To get back to the command line you can boot into single user mode.  At the second yaboot prompt type:

Linux single

When you are logged in, I suggest you do the following:
[I]
(I think this is the right file for your mac)[/I]
wget [http://mac.linux.be/files/xorg/imac5.txt](http://mac.linux.be/files/xorg/imac5.txt)
sudo mv imac5.txt /etc/X11/xorg.conf

Then open the file

sudo nano /etc/X11/xorg.conf

Change UseFBDev to false.

Save, exit and reboot with the command "sudo reboot".

This should hopefully work.  If it doesn't try adding NoInt10 like in post #1 of this thread.

I've been looking into what you need to do to get UseFBDev True working.  There are some basic-ish instructions in the lubuntu instructions at the moment, but I'll refine them this afternoon when I listen to the football (if it is a dull match!).

---

### Post by new to ubutnu on 2011-12-10
worked after noint10 this time so im happy also is there any cleaning up i need to do/can do to make startup time faster or is my computer so old it just wont go faster

secondly how can i uninstall some files like bluetooth and wireless that i dont need since my computer is a desktop

third thanks a ton

---

### Post by rsavage on 2011-12-10
> **new to ubutnu said:**
> worked after noint10 this time so im happy
Excellent! I thought we were never going to get there! I think maybe you needed to add some modelines before? That xorg.conf does it a different way with the HorizSync and VertRefresh lines. Have you got all the resolutions you need as I notice 1024x768 is not listed in the file? Have you tried to change resolutions to check it is all working?
 
> 
secondly how can i uninstall some files like bluetooth and wireless that i dont need since my computer is a desktop

Uninstall bluetooth with "sudo apt-get remove gnome-bluetooth" or use the application Synaptic. You can stop the Network Applet from starting by removing it from the startup list? Any other changes you'll have to ask on a different forum because I don't know the answer!
 
> 
also is there any cleaning up i need to do/can do to make startup time faster or is my computer so old it just wont go faster

How fast is the boot up time at the moment?
 
You should get a faster system if we can get UseFBDev to work when set to true. Sorry didn't get around to writing those instructions! Here is some....
 
First lets check what speed you have at the moment. 
 
Close any running applications like Firefox so they don't affect the result.
```

sudo apt-get install mesa-utils
glxinfo

```
What does the direct rendering line at the top of the output say? Is it yes or no?
 
Then run "glxgears -info"
 
What does the OpenGL render string line say? 
Then what FPS do you get?
 
Right now we've got to make some changes!!!! This is experimental!!!!
 
sudo nano /etc/X11/xorg.conf
 
Comment out the UseFBDev and NoInt10 lines by putting a # at the start.
```

      # [COLOR=#222222]Option "UseFBDev" "False"[/COLOR]
      # [COLOR=#222222][COLOR=#222222]O[/COLOR][/COLOR][COLOR=#000000]ption "NoInt10" "True"[/COLOR]

```
Save.
 
Then open yaboot.conf with "sudo nano /etc/yaboot.conf" and remove "video=ofonly" if it is in the 'append' lines. Save and run the command "sudo ybin -v". Laugh at the funny message.
 
Then run the command "sudo nano /etc/initramfs-tools/modules" and add 
```

aty128fb

```
on a new line. Save and then run the command "sudo update-initramfs -u".
 
Reboot and see if it loads. If it doesn't try [noparse]"Linux video=offb:off"[/noparse] at the second yaboot prompt. If you get to a cli login then you'll have to make more changes:
 
Type the command "sudo nano /etc/modules" and add to the file on a new line
```

aty128fb

```
Save and then run the command "sudo update-initramfs -u" again. Reboot and see if it loads. If it doesn't try [noparse]"Linux video=offb:off"[/noparse] at the second yaboot prompt. If you get to a cli login then you'll have to make try even more changes:
 
sudo nano /etc/modprobe/blacklist-framebuffer.conf
 
Remove the # from in front of the "aty128fb" line.
 
Save and re-run the "sudo update-initramfs -u" command.
 
Reboot ("sudo reboot"). If that doesn't work then try try [noparse]"Linux video=offb:off"[/noparse] again. If that doesn't work try uncommenting the NoInt10 line in the xorg.conf.
 
If that doesn't work then reverse all the changes and re-run the "sudo update-initramfs -u" command.
 
If you do get it working then redo all the tests with glxgears and glxinfo and see if things have changed.
 
If you just keep getting a blank frozen screen and can't return to a cli or graphical login then you may have to boot using "old" at the second yaboot prompt. Reverse all the changes again but the update-intramfs command will be slightly different. Type "man update-intramfs" to see if you can work it out.

---

### Post by new to ubutnu on 2011-12-10
for the first output i get yes
the second is Software Rasterizer and approx. 25 FPS then 28 and 29 eventually it declines to around 16 and goes up to 28 again

it worked after changing everything and running the 'Linux video=offb:oof'
and it comes to 30 fps so not a big difference

how do i make the Linux video line permanent unless you have other suggestions and also the computer is slow but i expect that with a 400 mhz processor and 512 mb of ram but the start up time takes at least 5 min. if im there to press l for linux and Linux at the second screen so i dont think it should be so bad especially for ubuntu

---

### Post by rsavage on 2011-12-11
> **new to ubutnu said:**
> it worked after changing everything and running the 'Linux video=offb:oof'
Sorry to be a bore, but can you expand on what everything is? Everything as in NoInt10 too? If that is the case can you reverse some of the other things like removing the # in blacklist-framebuffer.conf and retrying. Keep running the command "sudo update-initramfs -u" after any changes. It is only by experimentation that you actually find out what was the precise change that makes it works. Then you can give clearer instructions to future people.
 
> and it comes to 30 fps so not a big differenceWell that is disappointing. What about the open GL string line? Can we have the full output message? What about direct rendering yes/no? Can we have the full output of "LIBGL_DEBUG=verbose glxinfo" too?
 
It seems 'axion' may have been correct. I've re-read his answer and he says he built in the "r128 driver". Maybe 'walterav' miss led us slightly with the talk of framebuffers?
 
Is it possible for you to post the xorg.0.log file?
 
Also can you install fbset "sudo apt-get install fbset" and give the output of "sudo fbset -i"? Thanks
 
>  
how do i make the Linux video line permanent unless you have other suggestions 
Instructions in lubuntu instructions section 3.7b. Only make it permanent when you have finished testing. I need your logs before I can suggest things. 
 
> 
and also the computer is slow but i expect that with a 400 mhz processor and 512 mb of ram but the start up time takes at least 5 min. if im there to press l for linux and Linux at the second screen so i dont think it should be so bad especially for ubuntu5 mins is too long I would of thought. What are you running? Ubuntu/xubuntu/lubuntu? My ibook 1.2GHz takes around 30 secs from the yaboot prompt running lubuntu natty. 512mb is plenty for lubuntu. You'll have to look at your logs to see what is taking the time.

---

### Post by new to ubutnu on 2011-12-11
```
adminubuntu@iMacUbuntu:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_paletted_texture, GL_EXT_polygon_offset, 
    GL_EXT_subtexture, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_EXT_compiled_vertex_array, GL_EXT_texture, GL_EXT_texture3D, 
    GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_3DFX_texture_compression_FXT1, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_MESA_resize_buffers, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_SUN_multi_draw_arrays, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_EXT_framebuffer_object, GL_EXT_shared_texture_palette, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_fragment_program, GL_NV_point_sprite, GL_NV_vertex_program1_1, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_depth_bounds_test, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, GL_ARB_fragment_program_shadow, 
    GL_ARB_half_float_pixel, GL_ARB_occlusion_query2, GL_ARB_point_sprite, 
    GL_ARB_shading_language_100, GL_ARB_sync, GL_ARB_texture_non_power_of_two, 
    GL_ARB_vertex_buffer_object, GL_ATI_blend_equation_separate, 
    GL_EXT_blend_equation_separate, GL_OES_read_format, 
    GL_ARB_pixel_buffer_object, GL_ARB_texture_compression_rgtc, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_shared_exponent, 
    GL_ARB_framebuffer_object, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_packed_depth_stencil, 
    GL_NV_fragment_program_option, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_MESA_texture_array, GL_ARB_copy_buffer, 
    GL_ARB_draw_instanced, GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, 
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_EXT_provoking_vertex, GL_ARB_robustness

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0cc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d0 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0de 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0e0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ea 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0eb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ec 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ed 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ee 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ef 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0fa 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fe 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ff 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x100 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x043 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x044  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x045  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x046  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x047  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x048  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x049  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x04a  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x04b  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x04c  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x04d  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x04e  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x04f  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x050  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x051  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x052  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x053  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x054  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x055  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x056  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x057  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x058  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x059  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x05a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x05b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x05c  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x05e  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x060  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x076 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x077 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x078 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x079 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x07a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x07c 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x07e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x080 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x082 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x083 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x084  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x085  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x086  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x087  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x088  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x089  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x08a  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x08b  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x08c  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x08d  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x08e  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x08f  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x090  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x091  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x092  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x093  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x094  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x095  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x096  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x097  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x098  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x099  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x09a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x09b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x09c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x09e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x09f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0a1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0a3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ae 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0b0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b4 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0b8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0ba 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0bc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0be 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0bf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c0 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c2 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

adminubuntu@iMacUbuntu:~$ glxgears -info
GL_RENDERER   = Software Rasterizer
GL_VERSION    = 2.1 Mesa 7.11
GL_VENDOR     = Mesa Project
GL_EXTENSIONS = GL_ARB_multisample GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_logic_op GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_copy_texture GL_EXT_paletted_texture GL_EXT_polygon_offset GL_EXT_subtexture GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_compiled_vertex_array GL_EXT_texture GL_EXT_texture3D GL_IBM_rasterpos_clip GL_ARB_point_parameters GL_EXT_draw_range_elements GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_separate_specular_color GL_EXT_texture_edge_clamp GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_ARB_multitexture GL_IBM_multimode_draw_arrays GL_IBM_texture_mirrored_repeat GL_3DFX_texture_compression_FXT1 GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_transpose_matrix GL_EXT_blend_func_separate GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_secondary_color GL_EXT_texture_env_add GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_INGR_blend_func_separate GL_MESA_resize_buffers GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texgen_reflection GL_NV_texture_env_combine4 GL_SUN_multi_draw_arrays GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_EXT_framebuffer_object GL_EXT_shared_texture_palette GL_EXT_texture_env_dot3 GL_MESA_window_pos GL_NV_packed_depth_stencil GL_NV_texture_rectangle GL_NV_vertex_program GL_ARB_depth_texture GL_ARB_occlusion_query GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_EXT_stencil_two_side GL_EXT_texture_cube_map GL_NV_depth_clamp GL_NV_fragment_program GL_NV_point_sprite GL_NV_vertex_program1_1 GL_APPLE_packed_pixels GL_APPLE_vertex_array_object GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_shader GL_ARB_shader_objects GL_ARB_vertex_program GL_ARB_vertex_shader GL_ATI_draw_buffers GL_ATI_texture_env_combine3 GL_EXT_depth_bounds_test GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_ARB_depth_clamp GL_ARB_fragment_program_shadow GL_ARB_half_float_pixel GL_ARB_occlusion_query2 GL_ARB_point_sprite GL_ARB_shading_language_100 GL_ARB_sync GL_ARB_texture_non_power_of_two GL_ARB_vertex_buffer_object GL_ATI_blend_equation_separate GL_EXT_blend_equation_separate GL_OES_read_format GL_ARB_pixel_buffer_object GL_ARB_texture_compression_rgtc GL_ARB_texture_rectangle GL_ATI_texture_compression_3dc GL_EXT_pixel_buffer_object GL_EXT_texture_compression_rgtc GL_EXT_texture_mirror_clamp GL_EXT_texture_rectangle GL_EXT_texture_sRGB GL_EXT_texture_shared_exponent GL_ARB_framebuffer_object GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_packed_depth_stencil GL_NV_fragment_program_option GL_APPLE_object_purgeable GL_ARB_vertex_array_object GL_ATI_separate_stencil GL_ATI_texture_mirror_once GL_EXT_draw_buffers2 GL_EXT_draw_instanced GL_EXT_gpu_program_parameters GL_EXT_texture_array GL_EXT_texture_compression_latc GL_EXT_texture_env_combine GL_EXT_texture_sRGB_decode GL_MESA_texture_array GL_ARB_copy_buffer GL_ARB_draw_instanced GL_ARB_half_float_vertex GL_ARB_map_buffer_range GL_ARB_texture_rg GL_ARB_texture_swizzle GL_ARB_vertex_array_bgra GL_EXT_separate_shader_objects GL_EXT_texture_swizzle GL_EXT_vertex_array_bgra GL_NV_conditional_render GL_ARB_draw_elements_base_vertex GL_ARB_explicit_attrib_location GL_ARB_fragment_coord_conventions GL_ARB_provoking_vertex GL_EXT_provoking_vertex GL_ARB_robustness 
103 frames in 5.1 seconds = 20.339 FPS
98 frames in 5.0 seconds = 19.547 FPS
127 frames in 5.0 seconds = 25.313 FPS
149 frames in 5.0 seconds = 29.745 FPS
148 frames in 5.1 seconds = 29.242 FPS
131 frames in 5.0 seconds = 26.056 FPS
172 frames in 5.0 seconds = 34.384 FPS
179 frames in 5.0 seconds = 35.698 FPS
130 frames in 5.1 seconds = 25.721 FPS
91 frames in 5.0 seconds = 18.079 FPS
82 frames in 5.0 seconds = 16.352 FPS
61 frames in 5.0 seconds = 12.160 FPS
84 frames in 5.1 seconds = 16.630 FPS
86 frames in 5.0 seconds = 17.136 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 3414 requests (3370 known processed) with 0 events remaining.

```

this is my glxinfo and glxgears -info lines after i did everything you said and with firefox up

so these are the steps i went through after i had my gui
1. ran glxinfo then glxgears -info to answer your questions see post #11
2. second i commented out both "UseFBDev" "false" and "NoInt10" "true"
3. i tried to take out the video=ofonly but there wasn't a line in yaboot.conf so i ran the ybin -v command and saw the funny :D
4. added aty128fb to initramfs-tools/modules dir and ran sudo update-initramfs -u
5. when i restarted it went into a command line so i added aty128fb to /etc/modules directory
6. didn't work so i restarted and ran Linux video=offb:off it worked yeah!!!!! but now when i start up thats the only way it will run
7. ran glxinfo then glxgears -info to answer your questions see post #11 again

i might have exaggerated with 5 min but its at least 2-3 and i think it can go faster because it seems to need to think a lot for my startup also where can i find the log of what the computer was doing at startup (i think the xorg.0.log you were talking about which i dont know where it is )

this is the fbset -i command output
```
mode "1024x768-75"
    # D: 78.753 MHz, H: 60.025 kHz, V: 75.031 Hz
    geometry 1024 768 1024 768 32
    timings 12698 176 16 28 1 96 3
    hsync high
    vsync high
    rgba 8/16,8/8,8/0,8/24
endmode

Frame buffer device information:
    Name        : ATY Rage128
    Address     : 0x94000000
    Size        : 8388608
    Type        : PACKED PIXELS
    Visual      : DIRECTCOLOR
    XPanStep    : 8
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 4096
    MMIO Address: 0x90000000
    MMIO Size   : 8192
    Accelerator : ATI Rage128 family

```

---

### Post by new to ubutnu on 2011-12-11
looked up on the internet where the Xorg.0.log file is and i found so here it is
```
[    33.507]
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    33.507] X Protocol Version 11, Revision 0
[    33.507] Build Operating System: Linux 2.6.35-30-powerpc64-smp ppc Ubuntu
[    33.507] Current Operating System: Linux iMacUbuntu 3.0.0-14-powerpc #23-Ub$
[    33.507] Kernel command line: root=UUID=31740f50-8a45-4e99-8708-ba6661d768f$
[    33.512] Build Date: 19 October 2011  06:30:26AM
[    33.512] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see $
[    33.512] Current version of pixman: 0.22.2
[    33.512]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    33.512] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.513] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 12:57:06 20$
[    33.657] (==) Using config file: "/etc/X11/xorg.conf"
[    33.658] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.891] (==) ServerLayout "Default Layout"

```

---

### Post by rsavage on 2011-12-11
Thanks for the info, but the log seems short? Where is the rest of it?!
 
Oh, and I said to close Fiefox!

---

### Post by rsavage on 2011-12-11
I've finally found something that goes along with what 'axion' has been saying [http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg0Mg) .  However, those changes don't come in until Mesa 7.12 (January release) and you have Mesa 7.11.  So Natty and Oneiric shouldn't be affected by this.  So I still don't get it!
 
You could try adding "r128" to the /etc/modules and /etc/initramfs-tools/modules files and re-running the "sudo update-initramfs -u" command.
 
What is causing the low values in glxgears is the Software Rasterizer.  I think it should still be possible to get hardware acceleration.  It is just how????!!!  The last resort to try would be to compile a new kernel......
 
Back to logs.... there should be a whole load of them in the directory /var/log/ .  Look at syslog or dmesg or something to check out your startup times.  The Xorg.0.log you printed is definitly too short!

---

### Post by new to ubutnu on 2011-12-11
first off i had to have firefox open to copy and paste into the post

second the reason i didnt get the whole is that it wasnt scrollable and so i dont know how to copy it and post it here can you help

---

### Post by rsavage on 2011-12-11
leafpad /var/log/Xorg.0.log

(if you have installed lubuntu)

---

### Post by new to ubutnu on 2011-12-11
```
  33.507] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    33.507] X Protocol Version 11, Revision 0
[    33.507] Build Operating System: Linux 2.6.35-30-powerpc64-smp ppc Ubuntu
[    33.507] Current Operating System: Linux iMacUbuntu 3.0.0-14-powerpc #23-Ubuntu Mon Nov 21 22:30:24 UTC 2011 ppc
[    33.507] Kernel command line: root=UUID=31740f50-8a45-4e99-8708-ba6661d768f3 ro quiet splash video=offb:off
[    33.512] Build Date: 19 October 2011  06:30:26AM
[    33.512] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    33.512] Current version of pixman: 0.22.2
[    33.512]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    33.512] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    33.513] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 12:57:06 2011
[    33.657] (==) Using config file: "/etc/X11/xorg.conf"
[    33.658] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    33.891] (==) ServerLayout "Default Layout"
[    33.891] (**) |-->Screen "Default Screen" (0)
[    33.891] (**) |   |-->Monitor "iMac"
[    33.913] (**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
[    33.913] (**) |-->Input Device "Generic Keyboard"
[    33.913] (**) |-->Input Device "Configured Mouse"
[    33.913] (==) Automatically adding devices
[    33.913] (==) Automatically enabling devices
[    33.914] (WW) The directory "/usr/share/X11/fonts/misc" does not exist.
[    33.914]     Entry deleted from font path.
[    33.914] (WW) The directory "/usr/share/X11/cyrillic" does not exist.
[    33.914]     Entry deleted from font path.
[    33.914] (WW) The directory "/usr/share/X11/100dpi/" does not exist.
[    33.914]     Entry deleted from font path.
[    33.914] (WW) The directory "/usr/share/X11/75dpi/" does not exist.
[    33.914]     Entry deleted from font path.
[    33.914] (WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
[    33.915]     Entry deleted from font path.
[    33.915] (WW) The directory "/usr/share/X11/fonts/CID" does not exist.
[    33.915]     Entry deleted from font path.
[    33.915] (WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
[    33.915]     Entry deleted from font path.
[    33.915] (WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
[    33.915]     Entry deleted from font path.
[    33.941] (WW) The directory "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType" does not exist.
[    33.941]     Entry deleted from font path.
[    33.942] (WW) `fonts.dir' not found (or not valid) in "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID".
[    33.942]     Entry deleted from font path.
[    33.942]     (Run 'mkfontdir' on "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID").
[    33.963] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    33.964]     Entry deleted from font path.
[    34.033] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.034]     Entry deleted from font path.
[    34.037] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.037]     Entry deleted from font path.
[    34.057] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    34.057] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.058] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.058] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    34.058] (WW) Disabling Generic Keyboard
[    34.058] (WW) Disabling Configured Mouse
[    34.058] (II) Loader magic: 0x101ddbf0
[    34.058] (II) Module ABI versions:
[    34.058]     X.Org ANSI C Emulation: 0.4
[    34.058]     X.Org Video Driver: 10.0
[    34.058]     X.Org XInput driver : 12.3
[    34.058]     X.Org Server Extension : 5.0
[    34.062] (--) PCI:*(0:0:16:0) 1002:524c:1002:524c rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    34.062] (II) Open APM successful
[    34.062] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    34.063] (II) "dbe" will be loaded by default.
[    34.063] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    34.063] (II) "record" will be loaded by default.
[    34.063] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    34.063] (II) "dri2" will be loaded by default.
[    34.063] (II) LoadModule: "i2c"
[    34.068] (II) Module "i2c" already built-in
[    34.068] (II) LoadModule: "ddc"
[    34.068] (II) Module "ddc" already built-in
[    34.069] (II) LoadModule: "dri"
[    34.167] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    34.189] (II) Module dri: vendor="X.Org Foundation"
[    34.190]     compiled for 1.10.4, module version = 1.0.0
[    34.190]     ABI class: X.Org Server Extension, version 5.0
[    34.190] (II) Loading extension XFree86-DRI
[    34.190] (II) LoadModule: "extmod"
[    34.195] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    34.226] (II) Module extmod: vendor="X.Org Foundation"
[    34.227]     compiled for 1.10.4, module version = 1.0.0
[    34.227]     Module class: X.Org Server Extension
[    34.227]     ABI class: X.Org Server Extension, version 5.0
[    34.227] (II) Loading extension MIT-SCREEN-SAVER
[    34.227] (II) Loading extension XFree86-VidModeExtension
[    34.227] (II) Loading extension XFree86-DGA
[    34.227] (II) Loading extension DPMS
[    34.227] (II) Loading extension XVideo
[    34.228] (II) Loading extension XVideo-MotionCompensation
[    34.228] (II) Loading extension X-Resource
[    34.228] (II) LoadModule: "glx"
[    34.230] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.285] (II) Module glx: vendor="X.Org Foundation"
[    34.285]     compiled for 1.10.4, module version = 1.0.0
[    34.285]     ABI class: X.Org Server Extension, version 5.0
[    34.286] (==) AIGLX enabled
[    34.286] (II) Loading extension GLX
[    34.286] (II) LoadModule: "int10"
[    34.288] (II) Loading /usr/lib/xorg/modules/libint10.so
[    34.311] (II) Module int10: vendor="X.Org Foundation"
[    34.311]     compiled for 1.10.4, module version = 1.0.0
[    34.311]     ABI class: X.Org Video Driver, version 10.0
[    34.311] (II) LoadModule: "vbe"
[    34.327] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    34.350] (II) Module vbe: vendor="X.Org Foundation"
[    34.350]     compiled for 1.10.4, module version = 1.1.0
[    34.350]     ABI class: X.Org Video Driver, version 10.0
[    34.350] (II) LoadModule: "dbe"
[    34.352] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    34.355] (II) Module dbe: vendor="X.Org Foundation"
[    34.355]     compiled for 1.10.4, module version = 1.0.0
[    34.355]     Module class: X.Org Server Extension
[    34.355]     ABI class: X.Org Server Extension, version 5.0
[    34.355] (II) Loading extension DOUBLE-BUFFER
[    34.355] (II) LoadModule: "record"
[    34.362] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    34.365] (II) Module record: vendor="X.Org Foundation"
[    34.365]     compiled for 1.10.4, module version = 1.13.0
[    34.365]     Module class: X.Org Server Extension
[    34.365]     ABI class: X.Org Server Extension, version 5.0
[    34.365] (II) Loading extension RECORD
[    34.365] (II) LoadModule: "dri2"
[    34.367] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    34.373] (II) Module dri2: vendor="X.Org Foundation"
[    34.373]     compiled for 1.10.4, module version = 1.2.0
[    34.373]     ABI class: X.Org Server Extension, version 5.0
[    34.374] (II) Loading extension DRI2
[    34.374] (II) LoadModule: "ati"
[    34.375] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    34.393] (II) Module ati: vendor="X.Org Foundation"
[    34.394]     compiled for 1.10.2.902, module version = 6.14.99
[    34.394]     Module class: X.Org Video Driver
[    34.394]     ABI class: X.Org Video Driver, version 10.0
[    34.394] (II) LoadModule: "r128"
[    34.400] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    34.422] (II) Module r128: vendor="X.Org Foundation"
[    34.422]     compiled for 1.10.1, module version = 6.8.1
[    34.422]     Module class: X.Org Video Driver
[    34.422]     ABI class: X.Org Video Driver, version 10.0
[    34.422] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    34.426] (++) using VT number 7

[    34.443] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    34.444] (II) R128(0): PCI bus 0 card 16 func 0
[    34.444] (**) R128(0): Depth 24, (--) framebuffer bpp 32
[    34.445] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    34.445] (==) R128(0): Default visual is TrueColor
[    34.445] (II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
[    34.445] (==) R128(0): RGB weight 888
[    34.445] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    34.445] (**) R128(0): Using framebuffer device
[    34.445] (II) Loading sub module "fbdevhw"
[    34.445] (II) LoadModule: "fbdevhw"
[    34.447] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.469] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.469]     compiled for 1.10.4, module version = 0.0.2
[    34.469]     ABI class: X.Org Video Driver, version 10.0
[    34.470] (--) R128(0): Chipset: "ATI Rage 128 VR RL (AGP)" (ChipID = 0x524c)
[    34.470] (--) R128(0): Linear framebuffer at 0x94000000
[    34.470] (--) R128(0): MMIO registers at 0x90000000
[    34.470] (--) R128(0): VideoRAM: 8192 kByte (64-bit SDR SGRAM 2:1)
[    34.470] (**) R128(0): Using external CRT for display
[    34.471] (WW) R128(0): Failed to read PCI ROM!
[    34.471] (WW) R128(0): Video BIOS not found!
[    34.471] (II) R128(0): Primary Display == Type 1
[    34.471] (WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
[    34.471] (II) R128(0): PLL parameters: rf=2950 rd=56 min=12500 max=25000; xclk=5010
[    34.471] (II) Loading sub module "ddc"
[    34.476] (II) LoadModule: "ddc"
[    34.476] (II) Module "ddc" already built-in
[    34.476] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    34.476] (II) R128(0): iMac: Using hsync value of 60.00 kHz
[    34.477] (II) R128(0): iMac: Using vrefresh range of 75.00-117.00 Hz
[    34.477] (II) R128(0): Clock range:  12.50 to 250.00 MHz
[    34.477] (II) R128(0): Not using default mode "640x350" (hsync out of range)
[    34.477] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.478] (II) R128(0): Not using default mode "320x175" (unknown reason)
[    34.478] (II) R128(0): Not using default mode "640x400" (hsync out of range)
[    34.478] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.478] (II) R128(0): Not using default mode "320x200" (unknown reason)
[    34.478] (II) R128(0): Not using default mode "720x400" (hsync out of range)
[    34.478] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.479] (II) R128(0): Not using default mode "360x200" (unknown reason)
[    34.479] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    34.479] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.479] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    34.479] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    34.479] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.484] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    34.484] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    34.484] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.485] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    34.485] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    34.485] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.485] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    34.485] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    34.485] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.486] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    34.486] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    34.486] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.486] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    34.486] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    34.486] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.487] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    34.487] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    34.487] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.487] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    34.487] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    34.487] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.492] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    34.492] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.492] (II) R128(0): Not using default mode "1024x768i" (unknown reason)
[    34.492] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.492] (II) R128(0): Not using default mode "512x384i" (unknown reason)
[    34.493] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    34.493] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.493] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    34.493] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    34.493] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.493] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    34.494] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.494] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    34.494] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    34.494] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.494] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    34.494] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.495] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.495] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.495] (II) R128(0): Not using default mode "1280x960" (vrefresh out of range)
[    34.495] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.495] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    34.495] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    34.500] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.500] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    34.500] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    34.500] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.500] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    34.501] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    34.501] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.501] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    34.501] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    34.501] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.501] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    34.502] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    34.502] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.502] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    34.502] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    34.502] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.502] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    34.503] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    34.503] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.503] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    34.503] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    34.503] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.503] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    34.508] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.508] (II) R128(0): Not using default mode "1600x1200" (unknown reason)
[    34.509] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.509] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    34.509] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    34.509] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.509] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    34.509] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    34.509] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.509] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    34.509] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    34.510] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.510] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    34.510] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    34.510] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.510] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    34.510] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    34.510] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.510] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    34.510] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    34.511] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.511] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    34.511] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[    34.511] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.511] (II) R128(0): Not using default mode "416x312" (unknown reason)
[    34.511] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.516] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.516] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.516] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.516] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.516] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.517] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.517] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.517] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.517] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.517] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.517] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.518] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.518] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.518] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.518] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    34.518] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.518] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    34.519] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    34.519] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.519] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    34.519] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    34.519] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.519] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    34.524] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    34.524] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.524] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    34.524] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    34.524] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.524] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    34.525] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    34.525] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.525] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    34.525] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    34.525] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.525] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    34.526] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[    34.526] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.526] (II) R128(0): Not using default mode "720x450" (unknown reason)
[    34.526] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    34.526] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.526] (II) R128(0): Not using default mode "800x512" (unknown reason)
[    34.527] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    34.527] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.527] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    34.527] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    34.527] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.527] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    34.532] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    34.532] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.532] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    34.532] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    34.533] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.533] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    34.533] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    34.533] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.533] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    34.533] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    34.534] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.534] (II) R128(0): Not using default mode "960x540" (unknown reason)
[    34.534] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    34.534] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.534] (II) R128(0): Not using default mode "960x600" (unknown reason)
[    34.534] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    34.534] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.534] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    34.535] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    34.535] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.535] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    34.535] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    34.535] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.535] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    34.535] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    34.535] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    34.535] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    34.535] (II) R128(0): Not using mode "800x600" (no mode of this name)
[    34.540] (II) R128(0): Not using mode "640x480" (no mode of this name)
[    34.540] (--) R128(0): Virtual size is 1024x768 (pitch 1024)
[    34.540] (**) R128(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    34.540] (II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    34.541] (==) R128(0): DPI set to (96, 96)
[    34.541] (II) Loading sub module "fb"
[    34.541] (II) LoadModule: "fb"
[    34.543] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.572] (II) Module fb: vendor="X.Org Foundation"
[    34.572]     compiled for 1.10.4, module version = 1.0.0
[    34.572]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.572] (II) Loading sub module "ramdac"
[    34.572] (II) LoadModule: "ramdac"
[    34.573] (II) Module "ramdac" already built-in
[    34.573] (II) Loading sub module "xaa"
[    34.573] (II) LoadModule: "xaa"
[    34.575] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    34.614] (II) Module xaa: vendor="X.Org Foundation"
[    34.614]     compiled for 1.10.4, module version = 1.2.1
[    34.615]     ABI class: X.Org Video Driver, version 10.0
[    34.615] (II) Loading sub module "shadowfb"
[    34.615] (II) LoadModule: "shadowfb"
[    34.617] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    34.648] (II) Module shadowfb: vendor="X.Org Foundation"
[    34.648]     compiled for 1.10.4, module version = 1.0.0
[    34.649]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.649] (II) R128(0): Page flipping disabled
[    34.649] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    34.649] (--) Depth 24 pixmap format is 32 bpp
[    34.650] (WW) R128(0): Static buffer allocation failed -- need at least 9216 kB video memory
[    34.875] (II) R128(0): Memory manager initialized to (0,0) (1024,2048)
[    34.875] (II) R128(0): Reserved area from (0,768) to (1024,770)
[    34.875] (II) R128(0): Largest offscreen area available: 1024 x 1278
[    34.876] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    34.876]     Screen to screen bit blits
[    34.876]     Solid filled rectangles
[    34.876]     8x8 mono pattern filled rectangles
[    34.876]     Indirect CPU to Screen color expansion
[    34.876]     Solid Lines
[    34.876]     Dashed Lines
[    34.877]     Scanline Image Writes
[    34.877]     Setting up tile and stipple cache:
[    34.877]         32 128x128 slots
[    34.877]         10 256x256 slots
[    34.877] (II) R128(0): Acceleration enabled
[    34.877] (==) R128(0): Backing store disabled
[    34.878] (==) R128(0): Silken mouse enabled
[    34.934] (II) R128(0): Using hardware cursor (scanline 3080)
[    34.935] (II) R128(0): Largest offscreen area available: 1024 x 1276
[    34.937] (**) R128(0): DPMS enabled
[    34.938] (WW) R128(0): Direct rendering disabled
[    34.938] (==) RandR enabled
[    34.938] (II) Initializing built-in extension Generic Event Extension
[    34.938] (II) Initializing built-in extension SHAPE
[    34.938] (II) Initializing built-in extension MIT-SHM
[    34.938] (II) Initializing built-in extension XInputExtension
[    34.938] (II) Initializing built-in extension XTEST
[    34.938] (II) Initializing built-in extension BIG-REQUESTS
[    34.939] (II) Initializing built-in extension SYNC
[    34.939] (II) Initializing built-in extension XKEYBOARD
[    34.939] (II) Initializing built-in extension XC-MISC
[    34.939] (II) Initializing built-in extension SECURITY
[    34.939] (II) Initializing built-in extension XINERAMA
[    34.939] (II) Initializing built-in extension XFIXES
[    34.939] (II) Initializing built-in extension RENDER
[    34.939] (II) Initializing built-in extension RANDR
[    34.939] (II) Initializing built-in extension COMPOSITE
[    34.939] (II) Initializing built-in extension DAMAGE
[    34.939] (II) Initializing built-in extension GESTURE
[    35.071] (II) AIGLX: Screen 0 is not DRI2 capable
[    35.072] (II) AIGLX: Screen 0 is not DRI capable
[    35.073] (II) AIGLX: Trying DRI driver /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
[    35.670] (II) AIGLX: Loaded and initialized swrast
[    35.671] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    36.656] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.753] (II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
[    36.753] (II) No input driver/identifier specified (ignoring)
[    36.764] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event1)
[    36.764] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    36.764] (II) LoadModule: "evdev"
[    36.766] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.661] (II) Module evdev: vendor="X.Org Foundation"
[    37.662]     compiled for 1.10.2, module version = 2.6.0
[    37.662]     Module class: X.Org XInput Driver
[    37.662]     ABI class: X.Org XInput driver, version 12.3
[    37.662] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    37.662] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.662] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    37.662] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event1"
[    37.663] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    37.663] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    37.664] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input1/event1"
[    37.664] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    37.664] (**) Option "xkb_rules" "evdev"
[    37.664] (**) Option "xkb_model" "pc105"
[    37.664] (**) Option "xkb_layout" "us"
[    37.672] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[    37.672] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    37.672] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    37.673] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.673] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    37.673] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[    37.674] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[    37.674] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    37.674] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[    37.674] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    37.674] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[    37.674] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.674] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input2/event2"
[    37.675] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    37.675] (**) Option "xkb_rules" "evdev"
[    37.675] (**) Option "xkb_model" "pc105"
[    37.675] (**) Option "xkb_layout" "us"
[    37.684] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/event3)
[    37.684] (**) HID 1241:1111: Applying InputClass "evdev pointer catchall"
[    37.685] (II) Using input driver 'evdev' for 'HID 1241:1111'
[    37.685] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.685] (**) HID 1241:1111: always reports core events
[    37.685] (**) HID 1241:1111: Device: "/dev/input/event3"
[    37.686] (--) HID 1241:1111: Found 3 mouse buttons
[    37.686] (--) HID 1241:1111: Found scroll wheel(s)
[    37.686] (--) HID 1241:1111: Found relative axes
[    37.686] (--) HID 1241:1111: Found x and y relative axes
[    37.686] (II) HID 1241:1111: Configuring as mouse
[    37.686] (II) HID 1241:1111: Adding scrollwheel support
[    37.686] (**) HID 1241:1111: YAxisMapping: buttons 4 and 5
[    37.686] (**) HID 1241:1111: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.687] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:19.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3/event3"
[    37.687] (II) XINPUT: Adding extended input device "HID 1241:1111" (type: MOUSE)
[    37.687] (II) HID 1241:1111: initialized for relative axes.
[    37.688] (**) HID 1241:1111: (accel) keeping acceleration scheme 1
[    37.688] (**) HID 1241:1111: (accel) acceleration profile 0
[    37.688] (**) HID 1241:1111: (accel) acceleration factor: 2.000
[    37.688] (**) HID 1241:1111: (accel) acceleration threshold: 4
[    37.691] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/mouse0)
[    37.691] (II) No input driver/identifier specified (ignoring)
[    37.746] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    37.746] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    37.746] (II) Using input driver 'evdev' for 'PMU'
[    37.746] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.747] (**) PMU: always reports core events
[    37.747] (**) PMU: Device: "/dev/input/event0"
[    37.747] (--) PMU: Found keys
[    37.752] (II) PMU: Configuring as keyboard
[    37.752] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    37.752] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
[    37.752] (**) Option "xkb_rules" "evdev"
[    37.752] (**) Option "xkb_model" "pc105"
[    37.752] (**) Option "xkb_layout" "us"
[    37.767] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
[    37.767] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    37.767] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    37.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.772] (**) Macintosh mouse button emulation: always reports core events
[    37.772] (**) Macintosh mouse button emulation: Device: "/dev/input/event4"
[    37.773] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    37.773] (--) Macintosh mouse button emulation: Found relative axes
[    37.773] (--) Macintosh mouse button emulation: Found x and y relative axes
[    37.773] (II) Macintosh mouse button emulation: Configuring as mouse
[    37.773] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    37.773] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.773] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    37.773] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    37.774] (II) Macintosh mouse button emulation: initialized for relative axes.
[    37.774] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    37.774] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    37.775] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    37.775] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    37.781] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse1)
[    37.782] (II) No input driver/identifier specified (ignoring)
[    58.168] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
[    58.168] (II) No input driver/identifier specified (ignoring)
[    58.835] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event6)
[    58.835] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    58.835] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    58.835] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    58.836] (**) Mouseemu virtual keyboard: always reports core events
[    58.836] (**) Mouseemu virtual keyboard: Device: "/dev/input/event6"
[    58.836] (--) Mouseemu virtual keyboard: Found keys
[    58.836] (II) Mouseemu virtual keyboard: Configuring as keyboard
[    58.837] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    58.837] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
[    58.837] (**) Option "xkb_rules" "evdev"
[    58.837] (**) Option "xkb_model" "pc105"
[    58.837] (**) Option "xkb_layout" "us"
[    58.954] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event7)
[    58.954] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    58.954] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    58.954] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    58.955] (**) Mouseemu virtual mouse: always reports core events
[    58.955] (**) Mouseemu virtual mouse: Device: "/dev/input/event7"
[    58.955] (--) Mouseemu virtual mouse: Found 15 mouse buttons
[    58.959] (--) Mouseemu virtual mouse: Found scroll wheel(s)
[    58.959] (--) Mouseemu virtual mouse: Found relative axes
[    58.959] (--) Mouseemu virtual mouse: Found x and y relative axes
[    58.959] (II) Mouseemu virtual mouse: Configuring as mouse
[    58.963] (II) Mouseemu virtual mouse: Adding scrollwheel support
[    58.963] (**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    58.963] (**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    58.964] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    58.965] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
[    58.965] (II) Mouseemu virtual mouse: initialized for relative axes.
[    58.965] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    58.965] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    58.966] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    58.966] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4

```

real Xorg.0.log sorry:(

---

### Post by rsavage on 2011-12-12
A few things that leap out at me are:
 
```

[    34.650] (WW) R128(0): Static buffer allocation failed -- need at least 9216 kB video memory
 
.......
 
[    34.938] (WW) R128(0): Direct rendering disabled
 
....
 
[    35.071] (II) AIGLX: Screen 0 is not DRI2 capable
[    35.072] (II) AIGLX: Screen 0 is not DRI capable
[    35.073] (II) AIGLX: Trying DRI driver /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
[    35.670] (II) AIGLX: Loaded and initialized swrast
[    35.671] (II) GLX: Initialized DRISWRAST GL provider for screen 0
```For some reason your direct rendering has been disabled. This appears to have the knock on effect that you are using the software rasterizer - the swrast_dri.so.
 
What does 
 
```

dmesg | grep drm

```produce?

Can you give the output of "lspci -v" please?
 
Can you give the output of "lsmod" please?

Can you add uninorth-agp, agpgart and r128 to the /etc/modules file (one per line) and reboot? From section 1.8 of [http://dri.freedesktop.org/wiki/Building](http://dri.freedesktop.org/wiki/Building) . The order is important:
```

uninorth-agp
agpgart
r128

```See if that changes the output of "dmesg | grep drm"?
 
If you take the first warning about the static buffer then this page [http://dri.freedesktop.org/wiki/DriTroubleshooting#X_server_setup](http://dri.freedesktop.org/wiki/DriTroubleshooting#X_server_setup) mentions a static buffer error as a possible cause for lack of DRI. Try reducing the resolution. You can do this in the xorg.conf file by removing the references to 1024x768 from the Depth 24 subsection. If there are no references to 1024x768 in the xorg.conf, then you'll have to add a PreferredMode line into your Monitor section? See lubuntu instructions. 
 
If adjusting the resolution/default depth doesn't give you DRI, then can you try adding "r128" to the /etc/initramfs-tools/modules files and re-run the "sudo update-initramfs -u" command please?
 
When you reboot with the r128 added can you give the output of "dmesg | grep drm" again? Also the new Xorg.0.log please?
 
Btw, you can make the [noparse]video=offb:off[/noparse] permanent now. Open the file /etc/yaboot.conf ("gksudo leafpad /etc/yaboot.conf") and add it into the two append lines. Save and type command "sudo ybin -v".

---

### Post by rsavage on 2011-12-12
This is the kind of thing you want to see in your Xorg.0.log:

```


........

(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmGetBusid returned ''
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0xc0000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x1f000201 [AGP 0x1039/0x0735; Card 0x1002/0x5246]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0xd0000000
(II) R128(0): [agp] Ring mapped at 0xb78a9000
(II) R128(0): [agp] ring read ptr handle = 0xd0101000
(II) R128(0): [agp] Ring read ptr mapped at 0xb80c2000
(II) R128(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0xb55ba000
(II) R128(0): [agp] AGP texture map handle = 0xd0302000
(II) R128(0): [agp] AGP Texture map mapped at 0xb50da000
(II) R128(0): [drm] register handle = 0xcfefc000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (1024,3840)
(II) R128(0): Reserved area from (0,768) to (1024,770)
(II) R128(0): Largest offscreen area available: 1024 x 3070
(II) R128(0): Reserved back buffer from (0,770) to (1024,1538)
(II) R128(0): Reserved depth buffer from (0,1538) to (1024,2307)
(II) R128(0): Reserved depth span from (0,2306) offset 0x902000
(II) R128(0): Reserved 17408 kb for textures at offset 0xf00000
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Dashed Lines
    Setting up tile and stipple cache:
        32 128x128 slots
        14 256x256 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 9228)
(II) R128(0): Largest offscreen area available: 1024 x 1531
(II) R128(0): DPMS enabled
(WW) R128(0): Option "TVOutput" is not used
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 5
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

........

```

---

### Post by new to ubutnu on 2011-12-13
lspci output
```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
    Flags: bus master, 66MHz, medium devsel, latency 16
    Capabilities: <access denied>
    Kernel driver in use: agpgart-uninorth
    Kernel modules: uninorth-agp

0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 RL/VR AGP
    Subsystem: ATI Technologies Inc Rage 128 RL/VR AGP
    Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 48
    Memory at 94000000 (32-bit, prefetchable) [size=64M]
    I/O ports at 0400 [size=256]
    Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
    Expansion ROM at 90020000 [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: aty128fb
    Kernel modules: aty128fb

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
    Flags: bus master, 66MHz, medium devsel, latency 16
    Kernel modules: uninorth-agp

0001:10:12.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller (prog-if 10 [OHCI])
    Flags: bus master, medium devsel, latency 16, IRQ 52
    Memory at 80082000 (32-bit, non-prefetchable) [size=2K]
    Memory at 80084000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
    Flags: bus master, medium devsel, latency 16
    Memory at 80000000 (32-bit, non-prefetchable) [size=512K]
    Kernel driver in use: macio

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10 [OHCI])
    Flags: bus master, medium devsel, latency 16, IRQ 27
    Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB (prog-if 10 [OHCI])
    Flags: bus master, medium devsel, latency 16, IRQ 28
    Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
    Flags: bus master, 66MHz, medium devsel, latency 16
    Kernel modules: uninorth-agp

0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)
    Flags: bus master, 66MHz, slow devsel, latency 16, IRQ 41
    Memory at f5200000 (32-bit, non-prefetchable) [size=2M]
    Expansion ROM at f5000000 [disabled] [size=1M]
    Kernel driver in use: gem
    Kernel modules: sungem


```
lsmod output
```
Module                  Size  Used by
bnep                   12519  2 
rfcomm                 41682  0 
bluetooth             159934  10 bnep,rfcomm
iptable_filter          1702  0 
ip_tables              13622  1 iptable_filter
x_tables               19030  2 iptable_filter,ip_tables
parport_pc             38344  0 
ppdev                   7821  0 
lp                      9035  0 
parport                37094  3 parport_pc,ppdev,lp
rtc_generic             1347  0 
binfmt_misc             8063  1 
uninorth_agp            7630  1 
snd_powermac           66118  1 
snd_pcm                85118  1 snd_powermac
snd_seq_midi            5428  0 
snd_rawmidi            21931  1 snd_seq_midi
snd_seq_midi_event      7107  1 snd_seq_midi
snd_seq                58103  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23217  2 snd_pcm,snd_seq
snd_seq_device          6903  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61951  8 snd_powermac,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1108  1 snd
snd_page_alloc          7364  1 snd_pcm
apm_emu                 1408  0 
apm_emulation           6914  2 apm_emu
r128                   41035  0 
drm                   210131  1 r128
sg                     30773  0 
sd_mod                 36108  3 
sr_mod                 15170  0 
cdrom                  43827  1 sr_mod
crc_t10dif              1335  1 sd_mod
usbhid                 41754  0 
hid                    83349  1 usbhid
sungem                 32452  0 
sungem_phy             12036  1 sungem
firewire_ohci          33933  0 
firewire_core          60255  1 firewire_ohci
crc_itu_t               1467  1 firewire_core
aty128fb               21061  2 
pata_macio             13824  2 

```
ok so i forgot to submit the dmesg before i restarted so i lost it after i added the three modules so here is after i added them and it didn't change really at all
```
[    5.680453] [drm] Initialized drm 1.1.0 20060810
[    5.700389] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.710507] [drm] No driver support for vblank timestamp query.
[    5.720332] [drm] Initialized r128 2.5.0 20030725 for 0000:00:10.0 on minor 0

```

---

### Post by new to ubutnu on 2011-12-13
also in initramfs-tools/modules i had already added r128 before so i dont know what to do
here is the Xorg.0.log just for the fun of it
```
[    39.672] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    39.673] X Protocol Version 11, Revision 0
[    39.673] Build Operating System: Linux 2.6.35-30-powerpc64-smp ppc Ubuntu
[    39.673] Current Operating System: Linux iMacUbuntu 3.0.0-14-powerpc #23-Ubuntu Mon Nov 21 22:30:24 UTC 2011 ppc
[    39.673] Kernel command line: root=UUID=31740f50-8a45-4e99-8708-ba6661d768f3 ro video=offb:off 
[    39.673] Build Date: 19 October 2011  06:30:26AM
[    39.674] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    39.674] Current version of pixman: 0.22.2
[    39.674]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    39.674] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    39.675] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 14 00:18:19 2011
[    39.701] (==) Using config file: "/etc/X11/xorg.conf"
[    39.701] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    39.724] (==) ServerLayout "Default Layout"
[    39.724] (**) |-->Screen "Default Screen" (0)
[    39.725] (**) |   |-->Monitor "iMac"
[    39.726] (**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
[    39.727] (**) |-->Input Device "Generic Keyboard"
[    39.727] (**) |-->Input Device "Configured Mouse"
[    39.727] (==) Automatically adding devices
[    39.727] (==) Automatically enabling devices
[    39.727] (WW) The directory "/usr/share/X11/fonts/misc" does not exist.
[    39.727]     Entry deleted from font path.
[    39.751] (WW) The directory "/usr/share/X11/cyrillic" does not exist.
[    39.751]     Entry deleted from font path.
[    39.751] (WW) The directory "/usr/share/X11/100dpi/" does not exist.
[    39.752]     Entry deleted from font path.
[    39.752] (WW) The directory "/usr/share/X11/75dpi/" does not exist.
[    39.752]     Entry deleted from font path.
[    39.752] (WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
[    39.752]     Entry deleted from font path.
[    39.752] (WW) The directory "/usr/share/X11/fonts/CID" does not exist.
[    39.752]     Entry deleted from font path.
[    39.752] (WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
[    39.752]     Entry deleted from font path.
[    39.753] (WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
[    39.753]     Entry deleted from font path.
[    39.753] (WW) The directory "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType" does not exist.
[    39.753]     Entry deleted from font path.
[    39.763] (WW) `fonts.dir' not found (or not valid) in "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID".
[    39.764]     Entry deleted from font path.
[    39.764]     (Run 'mkfontdir' on "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID").
[    39.764] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    39.764]     Entry deleted from font path.
[    39.765] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    39.765]     Entry deleted from font path.
[    39.765] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    39.765]     Entry deleted from font path.
[    39.765] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    39.765] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    39.765] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    39.765] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    39.765] (WW) Disabling Generic Keyboard
[    39.766] (WW) Disabling Configured Mouse
[    39.766] (II) Loader magic: 0x101ddbf0
[    39.766] (II) Module ABI versions:
[    39.766]     X.Org ANSI C Emulation: 0.4
[    39.766]     X.Org Video Driver: 10.0
[    39.766]     X.Org XInput driver : 12.3
[    39.766]     X.Org Server Extension : 5.0
[    39.785] (--) PCI:*(0:0:16:0) 1002:524c:1002:524c rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    39.786] (II) Open APM successful
[    39.786] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    39.786] (II) "dbe" will be loaded by default.
[    39.786] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    39.786] (II) "record" will be loaded by default.
[    39.787] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    39.787] (II) "dri2" will be loaded by default.
[    39.787] (II) LoadModule: "i2c"
[    39.806] (II) Module "i2c" already built-in
[    39.807] (II) LoadModule: "ddc"
[    39.807] (II) Module "ddc" already built-in
[    39.807] (II) LoadModule: "dri"
[    39.830] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    39.848] (II) Module dri: vendor="X.Org Foundation"
[    39.848]     compiled for 1.10.4, module version = 1.0.0
[    39.848]     ABI class: X.Org Server Extension, version 5.0
[    39.848] (II) Loading extension XFree86-DRI
[    39.848] (II) LoadModule: "extmod"
[    39.850] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    39.851] (II) Module extmod: vendor="X.Org Foundation"
[    39.868]     compiled for 1.10.4, module version = 1.0.0
[    39.868]     Module class: X.Org Server Extension
[    39.868]     ABI class: X.Org Server Extension, version 5.0
[    39.868] (II) Loading extension MIT-SCREEN-SAVER
[    39.868] (II) Loading extension XFree86-VidModeExtension
[    39.868] (II) Loading extension XFree86-DGA
[    39.868] (II) Loading extension DPMS
[    39.869] (II) Loading extension XVideo
[    39.869] (II) Loading extension XVideo-MotionCompensation
[    39.869] (II) Loading extension X-Resource
[    39.869] (II) LoadModule: "glx"
[    39.871] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.889] (II) Module glx: vendor="X.Org Foundation"
[    39.890]     compiled for 1.10.4, module version = 1.0.0
[    39.890]     ABI class: X.Org Server Extension, version 5.0
[    39.890] (==) AIGLX enabled
[    39.890] (II) Loading extension GLX
[    39.890] (II) LoadModule: "int10"
[    39.912] (II) Loading /usr/lib/xorg/modules/libint10.so
[    39.915] (II) Module int10: vendor="X.Org Foundation"
[    39.915]     compiled for 1.10.4, module version = 1.0.0
[    39.915]     ABI class: X.Org Video Driver, version 10.0
[    39.915] (II) LoadModule: "vbe"
[    39.948] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    39.949] (II) Module vbe: vendor="X.Org Foundation"
[    39.949]     compiled for 1.10.4, module version = 1.1.0
[    39.949]     ABI class: X.Org Video Driver, version 10.0
[    39.950] (II) LoadModule: "dbe"
[    39.951] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    39.966] (II) Module dbe: vendor="X.Org Foundation"
[    39.967]     compiled for 1.10.4, module version = 1.0.0
[    39.967]     Module class: X.Org Server Extension
[    39.967]     ABI class: X.Org Server Extension, version 5.0
[    39.967] (II) Loading extension DOUBLE-BUFFER
[    39.967] (II) LoadModule: "record"
[    39.973] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    39.974] (II) Module record: vendor="X.Org Foundation"
[    39.974]     compiled for 1.10.4, module version = 1.13.0
[    39.974]     Module class: X.Org Server Extension
[    39.974]     ABI class: X.Org Server Extension, version 5.0
[    39.974] (II) Loading extension RECORD
[    39.974] (II) LoadModule: "dri2"
[    40.009] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    40.011] (II) Module dri2: vendor="X.Org Foundation"
[    40.011]     compiled for 1.10.4, module version = 1.2.0
[    40.011]     ABI class: X.Org Server Extension, version 5.0
[    40.011] (II) Loading extension DRI2
[    40.011] (II) LoadModule: "ati"
[    40.033] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    40.034] (II) Module ati: vendor="X.Org Foundation"
[    40.034]     compiled for 1.10.2.902, module version = 6.14.99
[    40.034]     Module class: X.Org Video Driver
[    40.034]     ABI class: X.Org Video Driver, version 10.0
[    40.035] (II) LoadModule: "r128"
[    40.051] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    40.060] (II) Module r128: vendor="X.Org Foundation"
[    40.060]     compiled for 1.10.1, module version = 6.8.1
[    40.061]     Module class: X.Org Video Driver
[    40.061]     ABI class: X.Org Video Driver, version 10.0
[    40.061] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    40.081] (++) using VT number 7

[    40.098] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    40.099] (II) R128(0): PCI bus 0 card 16 func 0
[    40.099] (**) R128(0): Depth 24, (--) framebuffer bpp 32
[    40.099] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    40.099] (==) R128(0): Default visual is TrueColor
[    40.099] (II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
[    40.100] (==) R128(0): RGB weight 888
[    40.100] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    40.100] (**) R128(0): Using framebuffer device
[    40.100] (II) Loading sub module "fbdevhw"
[    40.101] (II) LoadModule: "fbdevhw"
[    40.102] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    40.103] (II) Module fbdevhw: vendor="X.Org Foundation"
[    40.103]     compiled for 1.10.4, module version = 0.0.2
[    40.103]     ABI class: X.Org Video Driver, version 10.0
[    40.115] (--) R128(0): Chipset: "ATI Rage 128 VR RL (AGP)" (ChipID = 0x524c)
[    40.115] (--) R128(0): Linear framebuffer at 0x94000000
[    40.115] (--) R128(0): MMIO registers at 0x90000000
[    40.116] (--) R128(0): VideoRAM: 8192 kByte (64-bit SDR SGRAM 2:1)
[    40.116] (**) R128(0): Using external CRT for display
[    40.117] (WW) R128(0): Failed to read PCI ROM!
[    40.117] (WW) R128(0): Video BIOS not found!
[    40.117] (II) R128(0): Primary Display == Type 1
[    40.117] (WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
[    40.117] (II) R128(0): PLL parameters: rf=2950 rd=56 min=12500 max=25000; xclk=5010
[    40.117] (II) Loading sub module "ddc"
[    40.117] (II) LoadModule: "ddc"
[    40.117] (II) Module "ddc" already built-in
[    40.118] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    40.118] (II) R128(0): iMac: Using hsync value of 60.00 kHz
[    40.118] (II) R128(0): iMac: Using vrefresh range of 75.00-117.00 Hz
[    40.118] (II) R128(0): Clock range:  12.50 to 250.00 MHz
[    40.119] (II) R128(0): Not using default mode "640x350" (hsync out of range)
[    40.119] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.119] (II) R128(0): Not using default mode "320x175" (unknown reason)
[    40.119] (II) R128(0): Not using default mode "640x400" (hsync out of range)
[    40.119] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.119] (II) R128(0): Not using default mode "320x200" (unknown reason)
[    40.142] (II) R128(0): Not using default mode "720x400" (hsync out of range)
[    40.143] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.143] (II) R128(0): Not using default mode "360x200" (unknown reason)
[    40.143] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    40.143] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.143] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    40.153] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    40.154] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.154] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    40.154] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    40.154] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.154] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    40.155] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    40.155] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.155] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    40.155] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    40.155] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.155] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    40.161] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    40.169] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.169] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    40.169] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    40.169] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.170] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    40.170] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    40.170] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.170] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    40.170] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    40.170] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.171] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    40.171] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.171] (II) R128(0): Not using default mode "1024x768i" (unknown reason)
[    40.171] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.171] (II) R128(0): Not using default mode "512x384i" (unknown reason)
[    40.171] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    40.171] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.192] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    40.192] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    40.192] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.192] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    40.193] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.193] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    40.193] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    40.193] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.193] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    40.194] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.194] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.194] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.194] (II) R128(0): Not using default mode "1280x960" (vrefresh out of range)
[    40.194] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.194] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    40.195] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    40.195] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.195] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    40.195] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    40.195] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.195] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    40.210] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    40.210] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.211] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    40.211] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    40.211] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.211] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    40.211] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    40.211] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.224] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    40.224] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    40.224] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.224] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    40.225] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    40.225] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.225] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    40.225] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    40.225] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.225] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    40.226] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.226] (II) R128(0): Not using default mode "1600x1200" (unknown reason)
[    40.226] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.226] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    40.226] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    40.226] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.226] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    40.226] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    40.226] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.227] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    40.227] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    40.227] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.227] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    40.227] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    40.227] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.227] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    40.227] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    40.227] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.244] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    40.244] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    40.244] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.244] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    40.245] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[    40.245] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.245] (II) R128(0): Not using default mode "416x312" (unknown reason)
[    40.245] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.245] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.245] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.246] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.246] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.246] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.246] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.246] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.246] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.247] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.247] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.247] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.247] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.247] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.247] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.268] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    40.268] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.268] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    40.268] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    40.269] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.269] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    40.269] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    40.269] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.269] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    40.269] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    40.270] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.270] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    40.270] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    40.270] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.270] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    40.270] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    40.271] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.271] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    40.271] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    40.271] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.271] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    40.271] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[    40.288] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.288] (II) R128(0): Not using default mode "720x450" (unknown reason)
[    40.288] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    40.288] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.289] (II) R128(0): Not using default mode "800x512" (unknown reason)
[    40.289] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    40.289] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.289] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    40.289] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    40.289] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.289] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    40.290] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    40.290] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.290] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    40.290] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    40.290] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.290] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    40.291] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    40.291] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.291] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    40.291] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    40.291] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.308] (II) R128(0): Not using default mode "960x540" (unknown reason)
[    40.308] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    40.308] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.308] (II) R128(0): Not using default mode "960x600" (unknown reason)
[    40.308] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    40.309] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.309] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    40.309] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    40.309] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.309] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    40.309] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    40.309] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.309] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    40.310] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    40.310] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    40.310] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    40.310] (II) R128(0): Not using mode "800x600" (no mode of this name)
[    40.310] (II) R128(0): Not using mode "640x480" (no mode of this name)
[    40.310] (--) R128(0): Virtual size is 1024x768 (pitch 1024)
[    40.310] (**) R128(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    40.311] (II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    40.311] (==) R128(0): DPI set to (96, 96)
[    40.311] (II) Loading sub module "fb"
[    40.311] (II) LoadModule: "fb"
[    40.337] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.338] (II) Module fb: vendor="X.Org Foundation"
[    40.338]     compiled for 1.10.4, module version = 1.0.0
[    40.338]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.338] (II) Loading sub module "ramdac"
[    40.338] (II) LoadModule: "ramdac"
[    40.339] (II) Module "ramdac" already built-in
[    40.339] (II) Loading sub module "xaa"
[    40.339] (II) LoadModule: "xaa"
[    40.364] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    40.366] (II) Module xaa: vendor="X.Org Foundation"
[    40.366]     compiled for 1.10.4, module version = 1.2.1
[    40.366]     ABI class: X.Org Video Driver, version 10.0
[    40.366] (II) Loading sub module "shadowfb"
[    40.366] (II) LoadModule: "shadowfb"
[    40.385] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    40.386] (II) Module shadowfb: vendor="X.Org Foundation"
[    40.386]     compiled for 1.10.4, module version = 1.0.0
[    40.386]     ABI class: X.Org ANSI C Emulation, version 0.4
[    40.386] (II) R128(0): Page flipping disabled
[    40.386] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    40.386] (--) Depth 24 pixmap format is 32 bpp
[    40.387] (WW) R128(0): Static buffer allocation failed -- need at least 9216 kB video memory
[    40.414] (II) R128(0): Memory manager initialized to (0,0) (1024,2048)
[    40.415] (II) R128(0): Reserved area from (0,768) to (1024,770)
[    40.415] (II) R128(0): Largest offscreen area available: 1024 x 1278
[    40.415] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    40.416]     Screen to screen bit blits
[    40.416]     Solid filled rectangles
[    40.416]     8x8 mono pattern filled rectangles
[    40.416]     Indirect CPU to Screen color expansion
[    40.416]     Solid Lines
[    40.416]     Dashed Lines
[    40.416]     Scanline Image Writes
[    40.417]     Setting up tile and stipple cache:
[    40.417]         32 128x128 slots
[    40.417]         10 256x256 slots
[    40.417] (II) R128(0): Acceleration enabled
[    40.417] (==) R128(0): Backing store disabled
[    40.417] (==) R128(0): Silken mouse enabled
[    40.418] (II) R128(0): Using hardware cursor (scanline 3080)
[    40.418] (II) R128(0): Largest offscreen area available: 1024 x 1276
[    40.444] (**) R128(0): DPMS enabled
[    40.444] (WW) R128(0): Direct rendering disabled
[    40.445] (==) RandR enabled
[    40.445] (II) Initializing built-in extension Generic Event Extension
[    40.445] (II) Initializing built-in extension SHAPE
[    40.445] (II) Initializing built-in extension MIT-SHM
[    40.445] (II) Initializing built-in extension XInputExtension
[    40.445] (II) Initializing built-in extension XTEST
[    40.445] (II) Initializing built-in extension BIG-REQUESTS
[    40.445] (II) Initializing built-in extension SYNC
[    40.445] (II) Initializing built-in extension XKEYBOARD
[    40.445] (II) Initializing built-in extension XC-MISC
[    40.445] (II) Initializing built-in extension SECURITY
[    40.446] (II) Initializing built-in extension XINERAMA
[    40.446] (II) Initializing built-in extension XFIXES
[    40.446] (II) Initializing built-in extension RENDER
[    40.446] (II) Initializing built-in extension RANDR
[    40.446] (II) Initializing built-in extension COMPOSITE
[    40.446] (II) Initializing built-in extension DAMAGE
[    40.446] (II) Initializing built-in extension GESTURE
[    40.840] (II) AIGLX: Screen 0 is not DRI2 capable
[    40.840] (II) AIGLX: Screen 0 is not DRI capable
[    40.840] (II) AIGLX: Trying DRI driver /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
[    40.985] (II) AIGLX: Loaded and initialized swrast
[    40.985] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    41.914] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    42.185] (II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
[    42.185] (II) No input driver/identifier specified (ignoring)
[    42.225] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event1)
[    42.226] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    42.226] (II) LoadModule: "evdev"
[    42.227] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.287] (II) Module evdev: vendor="X.Org Foundation"
[    42.287]     compiled for 1.10.2, module version = 2.6.0
[    42.287]     Module class: X.Org XInput Driver
[    42.287]     ABI class: X.Org XInput driver, version 12.3
[    42.287] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    42.287] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.287] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    42.305] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event1"
[    42.306] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    42.306] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    42.307] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input1/event1"
[    42.307] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    42.307] (**) Option "xkb_rules" "evdev"
[    42.307] (**) Option "xkb_model" "pc105"
[    42.307] (**) Option "xkb_layout" "us"
[    42.373] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[    42.374] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    42.374] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    42.374] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.374] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    42.374] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[    42.375] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[    42.375] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    42.375] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[    42.375] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    42.375] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[    42.395] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.395] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input2/event2"
[    42.395] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    42.395] (**) Option "xkb_rules" "evdev"
[    42.395] (**) Option "xkb_model" "pc105"
[    42.404] (**) Option "xkb_layout" "us"
[    42.482] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/event3)
[    42.483] (**) HID 1241:1111: Applying InputClass "evdev pointer catchall"
[    42.483] (II) Using input driver 'evdev' for 'HID 1241:1111'
[    42.483] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.483] (**) HID 1241:1111: always reports core events
[    42.483] (**) HID 1241:1111: Device: "/dev/input/event3"
[    42.492] (--) HID 1241:1111: Found 3 mouse buttons
[    42.492] (--) HID 1241:1111: Found scroll wheel(s)
[    42.493] (--) HID 1241:1111: Found relative axes
[    42.493] (--) HID 1241:1111: Found x and y relative axes
[    42.493] (II) HID 1241:1111: Configuring as mouse
[    42.493] (II) HID 1241:1111: Adding scrollwheel support
[    42.493] (**) HID 1241:1111: YAxisMapping: buttons 4 and 5
[    42.493] (**) HID 1241:1111: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.493] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    42.493] (II) XINPUT: Adding extended input device "HID 1241:1111" (type: MOUSE)
[    42.494] (II) HID 1241:1111: initialized for relative axes.
[    42.494] (**) HID 1241:1111: (accel) keeping acceleration scheme 1
[    42.495] (**) HID 1241:1111: (accel) acceleration profile 0
[    42.495] (**) HID 1241:1111: (accel) acceleration factor: 2.000
[    42.495] (**) HID 1241:1111: (accel) acceleration threshold: 4
[    42.531] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/mouse0)
[    42.541] (II) No input driver/identifier specified (ignoring)
[    42.751] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    42.771] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    42.771] (II) Using input driver 'evdev' for 'PMU'
[    42.771] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.771] (**) PMU: always reports core events
[    42.774] (**) PMU: Device: "/dev/input/event0"
[    42.774] (--) PMU: Found keys
[    42.775] (II) PMU: Configuring as keyboard
[    42.775] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    42.775] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
[    42.775] (**) Option "xkb_rules" "evdev"
[    42.775] (**) Option "xkb_model" "pc105"
[    42.775] (**) Option "xkb_layout" "us"
[    42.797] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
[    42.797] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    42.797] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    42.797] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.797] (**) Macintosh mouse button emulation: always reports core events
[    42.798] (**) Macintosh mouse button emulation: Device: "/dev/input/event4"
[    42.798] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    42.798] (--) Macintosh mouse button emulation: Found relative axes
[    42.798] (--) Macintosh mouse button emulation: Found x and y relative axes
[    42.798] (II) Macintosh mouse button emulation: Configuring as mouse
[    42.799] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    42.799] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.799] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    42.799] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    42.799] (II) Macintosh mouse button emulation: initialized for relative axes.
[    42.812] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    42.813] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    42.813] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    42.813] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    42.815] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse1)
[    42.815] (II) No input driver/identifier specified (ignoring)
[    43.080] (II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
[    43.080] (II) No input driver/identifier specified (ignoring)
[    59.943] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
[    59.944] (II) No input driver/identifier specified (ignoring)
[    61.078] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event6)
[    61.078] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    61.078] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    61.078] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    61.079] (**) Mouseemu virtual keyboard: always reports core events
[    61.079] (**) Mouseemu virtual keyboard: Device: "/dev/input/event6"
[    61.079] (--) Mouseemu virtual keyboard: Found keys
[    61.079] (II) Mouseemu virtual keyboard: Configuring as keyboard
[    61.079] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    61.101] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
[    61.101] (**) Option "xkb_rules" "evdev"
[    61.101] (**) Option "xkb_model" "pc105"
[    61.101] (**) Option "xkb_layout" "us"
[    61.111] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event7)
[    61.132] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    61.132] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    61.132] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    61.133] (**) Mouseemu virtual mouse: always reports core events
[    61.133] (**) Mouseemu virtual mouse: Device: "/dev/input/event7"
[    61.133] (--) Mouseemu virtual mouse: Found 15 mouse buttons
[    61.133] (--) Mouseemu virtual mouse: Found scroll wheel(s)
[    61.133] (--) Mouseemu virtual mouse: Found relative axes
[    61.133] (--) Mouseemu virtual mouse: Found x and y relative axes
[    61.133] (II) Mouseemu virtual mouse: Configuring as mouse
[    61.133] (II) Mouseemu virtual mouse: Adding scrollwheel support
[    61.134] (**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    61.134] (**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    61.134] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    61.134] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
[    61.134] (II) Mouseemu virtual mouse: initialized for relative axes.
[    61.135] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    61.135] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    61.135] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    61.135] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4

```

---

### Post by new to ubutnu on 2011-12-13
i forgot to say that the dri looks like it is found now

second i cant find where to change the preferredmode line in the xorg.conf file in the lubuntu instructions but i dont know if i need that

also it is booting faster slightly which is good

---

### Post by rsavage on 2011-12-14
> **new to ubutnu said:**
> i forgot to say that the dri looks like it is found now

Why do you say that?  I see the same messages in your xorg.conf saying that it is disabled.

> 
second i cant find where to change the preferredmode line in the xorg.conf file in the lubuntu instructions but i dont know if i need that
Just remove any references to 1024x768 from your xorg.conf.  If you don't have any then set the DefaultDepth in the screen section to 16.  

What we are trying to do with this is stop the "static buffer allocation" warning in your Xorg.0.log.

I don't know if the mode of your framebuffer effects the mode of the xorg.conf.  We'll have to see about that....don't worry about this for the moment - is just my ramblings!

> 
also it is booting faster slightly which is good
I think you need to get your stop watch out!  

Can you add uninorth-agp and agpgart into your  /etc/initramfs-tools/modules and re-run the  "sudo update-initramfs -u" command please?  Put them in the order I said to before.

Following a reboot can we have the output of "dmesg | grep drm" and "dmesg | grep agp" please?

Success will be when we get a load of drm messages in your Xorg.0.log and much higher FPS when you run glxgears.  Final thing, can we have the output of Xorg.0.log after all the new changes?  Thanks

---

### Post by new to ubutnu on 2011-12-19
> **rsavage said:**
> 

Just remove any references to 1024x768 from your xorg.conf.  If you don't have any then set the DefaultDepth in the screen section to 16.  

I think you need to get your stop watch out!  

Can you add uninorth-agp and agpgart into your  /etc/initramfs-tools/modules and re-run the  "sudo update-initramfs -u" command please?  Put them in the order I said to before.

Following a reboot can we have the output of "dmesg | grep drm" and "dmesg | grep agp" please?



so i set DefaultDepth to 16 because of no 1024x768 but that froze my computer up

also the adding of those two lines froze my computer had to go into single user mode with each to get rid of them

i timed 1:09 for a startup time with neither of these

here are the dmesg outputs
```
adminubuntu@iMacUbuntu:~$ dmesg | grep drm
[    5.701066] [drm] Initialized drm 1.1.0 20060810
[    5.721118] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    5.731245] [drm] No driver support for vblank timestamp query.
[    5.741183] [drm] Initialized r128 2.5.0 20030725 for 0000:00:10.0 on minor 0
adminubuntu@iMacUbuntu:~$ dmesg | grep agp
[    0.498893] Linux agpgart interface v0.103
[   33.457352] agpgart-uninorth 0000:00:0b.0: Apple UniNorth chipset
[   33.459940] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[   33.522507] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0

```

and the Xorg.0.log
```
[    45.899] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    45.932] X Protocol Version 11, Revision 0
[    45.932] Build Operating System: Linux 2.6.35-30-powerpc64-smp ppc Ubuntu
[    45.932] Current Operating System: Linux iMacUbuntu 3.0.0-14-powerpc #23-Ubuntu Mon Nov 21 22:30:24 UTC 2011 ppc
[    45.932] Kernel command line: root=UUID=31740f50-8a45-4e99-8708-ba6661d768f3 ro video=offb:off 
[    45.933] Build Date: 19 October 2011  06:30:26AM
[    45.933] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    45.933] Current version of pixman: 0.22.2
[    45.933]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    45.933] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.934] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 20 01:26:35 2011
[    45.956] (==) Using config file: "/etc/X11/xorg.conf"
[    45.956] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.959] (==) ServerLayout "Default Layout"
[    45.959] (**) |-->Screen "Default Screen" (0)
[    45.972] (**) |   |-->Monitor "iMac"
[    45.974] (**) |   |-->Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
[    45.974] (**) |-->Input Device "Generic Keyboard"
[    45.974] (**) |-->Input Device "Configured Mouse"
[    45.974] (==) Automatically adding devices
[    45.974] (==) Automatically enabling devices
[    45.975] (WW) The directory "/usr/share/X11/fonts/misc" does not exist.
[    45.975]     Entry deleted from font path.
[    45.975] (WW) The directory "/usr/share/X11/cyrillic" does not exist.
[    45.975]     Entry deleted from font path.
[    45.975] (WW) The directory "/usr/share/X11/100dpi/" does not exist.
[    45.975]     Entry deleted from font path.
[    45.975] (WW) The directory "/usr/share/X11/75dpi/" does not exist.
[    45.975]     Entry deleted from font path.
[    45.975] (WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
[    45.996]     Entry deleted from font path.
[    45.996] (WW) The directory "/usr/share/X11/fonts/CID" does not exist.
[    45.996]     Entry deleted from font path.
[    45.996] (WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
[    45.996]     Entry deleted from font path.
[    45.996] (WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
[    45.996]     Entry deleted from font path.
[    45.997] (WW) The directory "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType" does not exist.
[    45.997]     Entry deleted from font path.
[    46.009] (WW) `fonts.dir' not found (or not valid) in "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID".
[    46.009]     Entry deleted from font path.
[    46.009]     (Run 'mkfontdir' on "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID").
[    46.010] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    46.010]     Entry deleted from font path.
[    46.010] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    46.010]     Entry deleted from font path.
[    46.010] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    46.010]     Entry deleted from font path.
[    46.011] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    46.011] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    46.011] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    46.011] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    46.011] (WW) Disabling Generic Keyboard
[    46.011] (WW) Disabling Configured Mouse
[    46.011] (II) Loader magic: 0x101ddbf0
[    46.011] (II) Module ABI versions:
[    46.011]     X.Org ANSI C Emulation: 0.4
[    46.016]     X.Org Video Driver: 10.0
[    46.016]     X.Org XInput driver : 12.3
[    46.016]     X.Org Server Extension : 5.0
[    46.019] (--) PCI:*(0:0:16:0) 1002:524c:1002:524c rev 0, Mem @ 0x94000000/67108864, 0x90000000/16384, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    46.019] (II) Open APM successful
[    46.034] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    46.034] (II) "dbe" will be loaded by default.
[    46.034] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    46.034] (II) "record" will be loaded by default.
[    46.034] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    46.035] (II) "dri2" will be loaded by default.
[    46.035] (II) LoadModule: "i2c"
[    46.049] (II) Module "i2c" already built-in
[    46.049] (II) LoadModule: "ddc"
[    46.049] (II) Module "ddc" already built-in
[    46.049] (II) LoadModule: "dri"
[    46.077] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    46.079] (II) Module dri: vendor="X.Org Foundation"
[    46.079]     compiled for 1.10.4, module version = 1.0.0
[    46.079]     ABI class: X.Org Server Extension, version 5.0
[    46.079] (II) Loading extension XFree86-DRI
[    46.079] (II) LoadModule: "extmod"
[    46.097] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    46.098] (II) Module extmod: vendor="X.Org Foundation"
[    46.098]     compiled for 1.10.4, module version = 1.0.0
[    46.099]     Module class: X.Org Server Extension
[    46.099]     ABI class: X.Org Server Extension, version 5.0
[    46.099] (II) Loading extension MIT-SCREEN-SAVER
[    46.099] (II) Loading extension XFree86-VidModeExtension
[    46.099] (II) Loading extension XFree86-DGA
[    46.099] (II) Loading extension DPMS
[    46.099] (II) Loading extension XVideo
[    46.099] (II) Loading extension XVideo-MotionCompensation
[    46.099] (II) Loading extension X-Resource
[    46.099] (II) LoadModule: "glx"
[    46.115] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    46.128] (II) Module glx: vendor="X.Org Foundation"
[    46.128]     compiled for 1.10.4, module version = 1.0.0
[    46.129]     ABI class: X.Org Server Extension, version 5.0
[    46.129] (==) AIGLX enabled
[    46.129] (II) Loading extension GLX
[    46.129] (II) LoadModule: "int10"
[    46.131] (II) Loading /usr/lib/xorg/modules/libint10.so
[    46.156] (II) Module int10: vendor="X.Org Foundation"
[    46.156]     compiled for 1.10.4, module version = 1.0.0
[    46.157]     ABI class: X.Org Video Driver, version 10.0
[    46.157] (II) LoadModule: "vbe"
[    46.177] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    46.178] (II) Module vbe: vendor="X.Org Foundation"
[    46.178]     compiled for 1.10.4, module version = 1.1.0
[    46.178]     ABI class: X.Org Video Driver, version 10.0
[    46.178] (II) LoadModule: "dbe"
[    46.204] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    46.205] (II) Module dbe: vendor="X.Org Foundation"
[    46.205]     compiled for 1.10.4, module version = 1.0.0
[    46.205]     Module class: X.Org Server Extension
[    46.205]     ABI class: X.Org Server Extension, version 5.0
[    46.205] (II) Loading extension DOUBLE-BUFFER
[    46.205] (II) LoadModule: "record"
[    46.207] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    46.233] (II) Module record: vendor="X.Org Foundation"
[    46.234]     compiled for 1.10.4, module version = 1.13.0
[    46.234]     Module class: X.Org Server Extension
[    46.234]     ABI class: X.Org Server Extension, version 5.0
[    46.234] (II) Loading extension RECORD
[    46.234] (II) LoadModule: "dri2"
[    46.253] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    46.254] (II) Module dri2: vendor="X.Org Foundation"
[    46.254]     compiled for 1.10.4, module version = 1.2.0
[    46.254]     ABI class: X.Org Server Extension, version 5.0
[    46.254] (II) Loading extension DRI2
[    46.254] (II) LoadModule: "ati"
[    46.276] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    46.277] (II) Module ati: vendor="X.Org Foundation"
[    46.277]     compiled for 1.10.2.902, module version = 6.14.99
[    46.277]     Module class: X.Org Video Driver
[    46.277]     ABI class: X.Org Video Driver, version 10.0
[    46.278] (II) LoadModule: "r128"
[    46.279] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    46.300] (II) Module r128: vendor="X.Org Foundation"
[    46.301]     compiled for 1.10.1, module version = 6.8.1
[    46.301]     Module class: X.Org Video Driver
[    46.301]     ABI class: X.Org Video Driver, version 10.0
[    46.301] (II) R128: Driver for ATI Rage 128 chipsets:
    ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
    ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
    ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
    ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
    ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
    ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
    ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
    ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
    ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
    ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
    ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
    ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
    ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
    ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
    ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
    ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
    ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
    ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
    ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
    ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
    ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
    ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
    ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
    ATI Rage 128 Pro ULTRA TU (AGP?)
[    46.320] (++) using VT number 7

[    46.338] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[    46.339] (II) R128(0): PCI bus 0 card 16 func 0
[    46.339] (**) R128(0): Depth 24, (--) framebuffer bpp 32
[    46.339] (II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    46.339] (==) R128(0): Default visual is TrueColor
[    46.339] (II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
[    46.339] (==) R128(0): RGB weight 888
[    46.340] (II) R128(0): Using 8 bits per RGB (8 bit DAC)
[    46.340] (**) R128(0): Using framebuffer device
[    46.341] (II) Loading sub module "fbdevhw"
[    46.341] (II) LoadModule: "fbdevhw"
[    46.342] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    46.343] (II) Module fbdevhw: vendor="X.Org Foundation"
[    46.343]     compiled for 1.10.4, module version = 0.0.2
[    46.361]     ABI class: X.Org Video Driver, version 10.0
[    46.362] (--) R128(0): Chipset: "ATI Rage 128 VR RL (AGP)" (ChipID = 0x524c)
[    46.362] (--) R128(0): Linear framebuffer at 0x94000000
[    46.362] (--) R128(0): MMIO registers at 0x90000000
[    46.362] (--) R128(0): VideoRAM: 8192 kByte (64-bit SDR SGRAM 2:1)
[    46.363] (**) R128(0): Using external CRT for display
[    46.363] (WW) R128(0): Failed to read PCI ROM!
[    46.363] (WW) R128(0): Video BIOS not found!
[    46.363] (II) R128(0): Primary Display == Type 1
[    46.363] (WW) R128(0): Can't determine panel dimensions, and none specified.
    Disabling programming of FP registers.
[    46.368] (II) R128(0): PLL parameters: rf=2950 rd=56 min=12500 max=25000; xclk=5010
[    46.368] (II) Loading sub module "ddc"
[    46.368] (II) LoadModule: "ddc"
[    46.368] (II) Module "ddc" already built-in
[    46.368] (==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
[    46.369] (II) R128(0): iMac: Using hsync value of 60.00 kHz
[    46.369] (II) R128(0): iMac: Using vrefresh range of 75.00-117.00 Hz
[    46.369] (II) R128(0): Clock range:  12.50 to 250.00 MHz
[    46.369] (II) R128(0): Not using default mode "640x350" (hsync out of range)
[    46.369] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.370] (II) R128(0): Not using default mode "320x175" (unknown reason)
[    46.370] (II) R128(0): Not using default mode "640x400" (hsync out of range)
[    46.370] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.370] (II) R128(0): Not using default mode "320x200" (unknown reason)
[    46.370] (II) R128(0): Not using default mode "720x400" (hsync out of range)
[    46.371] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.371] (II) R128(0): Not using default mode "360x200" (unknown reason)
[    46.371] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    46.371] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.371] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    46.371] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    46.384] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.385] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    46.385] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    46.385] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.385] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    46.386] (II) R128(0): Not using default mode "640x480" (hsync out of range)
[    46.386] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.386] (II) R128(0): Not using default mode "320x240" (unknown reason)
[    46.386] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    46.386] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.386] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    46.387] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    46.387] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.387] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    46.387] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    46.387] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.387] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    46.407] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    46.408] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.408] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    46.408] (II) R128(0): Not using default mode "800x600" (hsync out of range)
[    46.408] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.408] (II) R128(0): Not using default mode "400x300" (unknown reason)
[    46.408] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.409] (II) R128(0): Not using default mode "1024x768i" (unknown reason)
[    46.409] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.409] (II) R128(0): Not using default mode "512x384i" (unknown reason)
[    46.409] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    46.409] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.409] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    46.410] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    46.410] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.410] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    46.410] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.410] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    46.410] (II) R128(0): Not using default mode "1024x768" (hsync out of range)
[    46.411] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.411] (II) R128(0): Not using default mode "512x384" (unknown reason)
[    46.411] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.411] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.411] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.411] (II) R128(0): Not using default mode "1280x960" (vrefresh out of range)
[    46.424] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.424] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    46.424] (II) R128(0): Not using default mode "1280x960" (hsync out of range)
[    46.425] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.425] (II) R128(0): Not using default mode "640x480" (unknown reason)
[    46.425] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    46.425] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.425] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    46.425] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    46.426] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.426] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    46.426] (II) R128(0): Not using default mode "1280x1024" (hsync out of range)
[    46.426] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.426] (II) R128(0): Not using default mode "640x512" (unknown reason)
[    46.426] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    46.427] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.427] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    46.427] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    46.427] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.427] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    46.427] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    46.427] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.440] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    46.440] (II) R128(0): Not using default mode "1600x1200" (hsync out of range)
[    46.440] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.441] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    46.441] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.441] (II) R128(0): Not using default mode "1600x1200" (unknown reason)
[    46.441] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.441] (II) R128(0): Not using default mode "800x600" (unknown reason)
[    46.441] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    46.441] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.441] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    46.442] (II) R128(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    46.442] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.442] (II) R128(0): Not using default mode "896x672" (unknown reason)
[    46.442] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    46.442] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.442] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    46.442] (II) R128(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    46.442] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.442] (II) R128(0): Not using default mode "928x696" (unknown reason)
[    46.442] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    46.443] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.443] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    46.443] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    46.443] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.443] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    46.443] (II) R128(0): Not using default mode "832x624" (hsync out of range)
[    46.443] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.454] (II) R128(0): Not using default mode "416x312" (unknown reason)
[    46.454] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.454] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.455] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.455] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.455] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.455] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.455] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.464] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.464] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.464] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.465] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.465] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.465] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.465] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.465] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.465] (II) R128(0): Not using default mode "1152x864" (hsync out of range)
[    46.466] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.466] (II) R128(0): Not using default mode "576x432" (unknown reason)
[    46.466] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    46.466] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.466] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    46.466] (II) R128(0): Not using default mode "1360x768" (hsync out of range)
[    46.466] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.467] (II) R128(0): Not using default mode "680x384" (unknown reason)
[    46.467] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    46.467] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.467] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    46.467] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    46.467] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.479] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    46.479] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    46.479] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.479] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    46.479] (II) R128(0): Not using default mode "1400x1050" (hsync out of range)
[    46.480] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.480] (II) R128(0): Not using default mode "700x525" (unknown reason)
[    46.480] (II) R128(0): Not using default mode "1440x900" (hsync out of range)
[    46.480] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.480] (II) R128(0): Not using default mode "720x450" (unknown reason)
[    46.481] (II) R128(0): Not using default mode "1600x1024" (hsync out of range)
[    46.481] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.481] (II) R128(0): Not using default mode "800x512" (unknown reason)
[    46.481] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    46.481] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.481] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    46.482] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    46.482] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.482] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    46.482] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    46.482] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.482] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    46.483] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    46.483] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.483] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    46.483] (II) R128(0): Not using default mode "1680x1050" (hsync out of range)
[    46.483] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.483] (II) R128(0): Not using default mode "840x525" (unknown reason)
[    46.483] (II) R128(0): Not using default mode "1920x1080" (hsync out of range)
[    46.496] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.496] (II) R128(0): Not using default mode "960x540" (unknown reason)
[    46.496] (II) R128(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    46.497] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.497] (II) R128(0): Not using default mode "960x600" (unknown reason)
[    46.497] (II) R128(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    46.497] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.497] (II) R128(0): Not using default mode "960x720" (unknown reason)
[    46.497] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    46.497] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.497] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    46.497] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    46.498] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.498] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    46.498] (II) R128(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    46.498] (EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
[    46.498] (II) R128(0): Not using default mode "1024x768" (unknown reason)
[    46.498] (II) R128(0): Not using mode "800x600" (no mode of this name)
[    46.498] (II) R128(0): Not using mode "640x480" (no mode of this name)
[    46.499] (--) R128(0): Virtual size is 1024x768 (pitch 1024)
[    46.499] (**) R128(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    46.499] (II) R128(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    46.499] (==) R128(0): DPI set to (96, 96)
[    46.499] (II) Loading sub module "fb"
[    46.499] (II) LoadModule: "fb"
[    46.511] (II) Loading /usr/lib/xorg/modules/libfb.so
[    46.520] (II) Module fb: vendor="X.Org Foundation"
[    46.521]     compiled for 1.10.4, module version = 1.0.0
[    46.521]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.521] (II) Loading sub module "ramdac"
[    46.521] (II) LoadModule: "ramdac"
[    46.521] (II) Module "ramdac" already built-in
[    46.521] (II) Loading sub module "xaa"
[    46.521] (II) LoadModule: "xaa"
[    46.523] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    46.537] (II) Module xaa: vendor="X.Org Foundation"
[    46.537]     compiled for 1.10.4, module version = 1.2.1
[    46.537]     ABI class: X.Org Video Driver, version 10.0
[    46.537] (II) Loading sub module "shadowfb"
[    46.537] (II) LoadModule: "shadowfb"
[    46.539] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    46.548] (II) Module shadowfb: vendor="X.Org Foundation"
[    46.548]     compiled for 1.10.4, module version = 1.0.0
[    46.549]     ABI class: X.Org ANSI C Emulation, version 0.4
[    46.549] (II) R128(0): Page flipping disabled
[    46.549] (!!) R128(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    46.549] (--) Depth 24 pixmap format is 32 bpp
[    46.550] (WW) R128(0): Static buffer allocation failed -- need at least 9216 kB video memory
[    46.551] (II) R128(0): Memory manager initialized to (0,0) (1024,2048)
[    46.551] (II) R128(0): Reserved area from (0,768) to (1024,770)
[    46.560] (II) R128(0): Largest offscreen area available: 1024 x 1278
[    46.561] (II) R128(0): Using XFree86 Acceleration Architecture (XAA)
[    46.561]     Screen to screen bit blits
[    46.561]     Solid filled rectangles
[    46.561]     8x8 mono pattern filled rectangles
[    46.561]     Indirect CPU to Screen color expansion
[    46.561]     Solid Lines
[    46.561]     Dashed Lines
[    46.561]     Scanline Image Writes
[    46.562]     Setting up tile and stipple cache:
[    46.562]         32 128x128 slots
[    46.562]         10 256x256 slots
[    46.562] (II) R128(0): Acceleration enabled
[    46.562] (==) R128(0): Backing store disabled
[    46.562] (==) R128(0): Silken mouse enabled
[    46.563] (II) R128(0): Using hardware cursor (scanline 3080)
[    46.563] (II) R128(0): Largest offscreen area available: 1024 x 1276
[    46.601] (**) R128(0): DPMS enabled
[    46.602] (WW) R128(0): Direct rendering disabled
[    46.602] (==) RandR enabled
[    46.602] (II) Initializing built-in extension Generic Event Extension
[    46.602] (II) Initializing built-in extension SHAPE
[    46.603] (II) Initializing built-in extension MIT-SHM
[    46.603] (II) Initializing built-in extension XInputExtension
[    46.603] (II) Initializing built-in extension XTEST
[    46.603] (II) Initializing built-in extension BIG-REQUESTS
[    46.603] (II) Initializing built-in extension SYNC
[    46.603] (II) Initializing built-in extension XKEYBOARD
[    46.603] (II) Initializing built-in extension XC-MISC
[    46.603] (II) Initializing built-in extension SECURITY
[    46.603] (II) Initializing built-in extension XINERAMA
[    46.603] (II) Initializing built-in extension XFIXES
[    46.603] (II) Initializing built-in extension RENDER
[    46.603] (II) Initializing built-in extension RANDR
[    46.603] (II) Initializing built-in extension COMPOSITE
[    46.620] (II) Initializing built-in extension DAMAGE
[    46.620] (II) Initializing built-in extension GESTURE
[    46.998] (II) AIGLX: Screen 0 is not DRI2 capable
[    46.998] (II) AIGLX: Screen 0 is not DRI capable
[    46.999] (II) AIGLX: Trying DRI driver /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
[    47.158] (II) AIGLX: Loaded and initialized swrast
[    47.158] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    48.311] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.643] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event1)
[    48.652] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    48.652] (II) LoadModule: "evdev"
[    48.654] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.682] (II) Module evdev: vendor="X.Org Foundation"
[    48.682]     compiled for 1.10.2, module version = 2.6.0
[    48.682]     Module class: X.Org XInput Driver
[    48.682]     ABI class: X.Org XInput driver, version 12.3
[    48.682] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    48.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.683] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    48.683] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event1"
[    48.683] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    48.696] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    48.696] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input1/event1"
[    48.696] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    48.696] (**) Option "xkb_rules" "evdev"
[    48.697] (**) Option "xkb_model" "pc105"
[    48.697] (**) Option "xkb_layout" "us"
[    48.724] (II) config/udev: Adding input device Chicony Saitek Eclipse II Keyboard (/dev/input/event2)
[    48.724] (**) Chicony Saitek Eclipse II Keyboard: Applying InputClass "evdev keyboard catchall"
[    48.724] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse II Keyboard'
[    48.724] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.725] (**) Chicony Saitek Eclipse II Keyboard: always reports core events
[    48.725] (**) Chicony Saitek Eclipse II Keyboard: Device: "/dev/input/event2"
[    48.725] (--) Chicony Saitek Eclipse II Keyboard: Found 8 mouse buttons
[    48.725] (--) Chicony Saitek Eclipse II Keyboard: Found keys
[    48.725] (II) Chicony Saitek Eclipse II Keyboard: Configuring as mouse
[    48.726] (II) Chicony Saitek Eclipse II Keyboard: Configuring as keyboard
[    48.726] (**) Chicony Saitek Eclipse II Keyboard: YAxisMapping: buttons 4 and 5
[    48.726] (**) Chicony Saitek Eclipse II Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.726] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input2/event2"
[    48.726] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse II Keyboard" (type: KEYBOARD)
[    48.726] (**) Option "xkb_rules" "evdev"
[    48.727] (**) Option "xkb_model" "pc105"
[    48.727] (**) Option "xkb_layout" "us"
[    48.764] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/event3)
[    48.764] (**) HID 1241:1111: Applying InputClass "evdev pointer catchall"
[    48.764] (II) Using input driver 'evdev' for 'HID 1241:1111'
[    48.764] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.765] (**) HID 1241:1111: always reports core events
[    48.765] (**) HID 1241:1111: Device: "/dev/input/event3"
[    48.766] (--) HID 1241:1111: Found 3 mouse buttons
[    48.766] (--) HID 1241:1111: Found scroll wheel(s)
[    48.766] (--) HID 1241:1111: Found relative axes
[    48.766] (--) HID 1241:1111: Found x and y relative axes
[    48.766] (II) HID 1241:1111: Configuring as mouse
[    48.766] (II) HID 1241:1111: Adding scrollwheel support
[    48.766] (**) HID 1241:1111: YAxisMapping: buttons 4 and 5
[    48.766] (**) HID 1241:1111: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.766] (**) Option "config_info" "udev:/sys/devices/pci0001:10/0001:10:18.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event3"
[    48.767] (II) XINPUT: Adding extended input device "HID 1241:1111" (type: MOUSE)
[    48.767] (II) HID 1241:1111: initialized for relative axes.
[    48.776] (**) HID 1241:1111: (accel) keeping acceleration scheme 1
[    48.776] (**) HID 1241:1111: (accel) acceleration profile 0
[    48.776] (**) HID 1241:1111: (accel) acceleration factor: 2.000
[    48.776] (**) HID 1241:1111: (accel) acceleration threshold: 4
[    48.779] (II) config/udev: Adding input device HID 1241:1111 (/dev/input/mouse0)
[    48.779] (II) No input driver/identifier specified (ignoring)
[    48.941] (II) config/udev: Adding input device PMU (/dev/input/event0)
[    48.941] (**) PMU: Applying InputClass "evdev keyboard catchall"
[    48.942] (II) Using input driver 'evdev' for 'PMU'
[    48.942] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.942] (**) PMU: always reports core events
[    48.942] (**) PMU: Device: "/dev/input/event0"
[    48.943] (--) PMU: Found keys
[    48.943] (II) PMU: Configuring as keyboard
[    48.943] (**) Option "config_info" "udev:/sys/devices/virtual/input/input0/event0"
[    48.943] (II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
[    48.943] (**) Option "xkb_rules" "evdev"
[    48.943] (**) Option "xkb_model" "pc105"
[    48.952] (**) Option "xkb_layout" "us"
[    48.965] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
[    48.965] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    48.965] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    48.965] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    48.966] (**) Macintosh mouse button emulation: always reports core events
[    48.966] (**) Macintosh mouse button emulation: Device: "/dev/input/event4"
[    48.966] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    48.966] (--) Macintosh mouse button emulation: Found relative axes
[    48.966] (--) Macintosh mouse button emulation: Found x and y relative axes
[    48.967] (II) Macintosh mouse button emulation: Configuring as mouse
[    48.967] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    48.967] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    48.967] (**) Option "config_info" "udev:/sys/devices/virtual/input/input4/event4"
[    48.967] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    48.985] (II) Macintosh mouse button emulation: initialized for relative axes.
[    48.986] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    48.986] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    48.986] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    48.986] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    48.997] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse1)
[    48.997] (II) No input driver/identifier specified (ignoring)
[    49.354] (WW) config/udev: device HID 1241:1111 already added. Ignoring.
[    49.374] (WW) config/udev: device Chicony Saitek Eclipse II Keyboard already added. Ignoring.
[    49.538] (WW) config/udev: device PMU already added. Ignoring.
[    49.554] (WW) config/udev: device Chicony Saitek Eclipse II Keyboard already added. Ignoring.
[    49.674] (WW) config/udev: device Macintosh mouse button emulation already added. Ignoring.
[    50.848] (II) config/udev: Adding input device PowerMac Beep (/dev/input/event5)
[    50.848] (II) No input driver/identifier specified (ignoring)
[    60.883] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/mouse2)
[    60.884] (II) No input driver/identifier specified (ignoring)
[    61.122] (II) config/udev: Adding input device Mouseemu virtual mouse (/dev/input/event7)
[    61.122] (**) Mouseemu virtual mouse: Applying InputClass "evdev pointer catchall"
[    61.122] (II) Using input driver 'evdev' for 'Mouseemu virtual mouse'
[    61.122] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    61.123] (**) Mouseemu virtual mouse: always reports core events
[    61.123] (**) Mouseemu virtual mouse: Device: "/dev/input/event7"
[    61.123] (--) Mouseemu virtual mouse: Found 15 mouse buttons
[    61.123] (--) Mouseemu virtual mouse: Found scroll wheel(s)
[    61.123] (--) Mouseemu virtual mouse: Found relative axes
[    61.123] (--) Mouseemu virtual mouse: Found x and y relative axes
[    61.123] (II) Mouseemu virtual mouse: Configuring as mouse
[    61.128] (II) Mouseemu virtual mouse: Adding scrollwheel support
[    61.128] (**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
[    61.128] (**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    61.129] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    61.129] (II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
[    61.129] (II) Mouseemu virtual mouse: initialized for relative axes.
[    61.129] (**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
[    61.130] (**) Mouseemu virtual mouse: (accel) acceleration profile 0
[    61.130] (**) Mouseemu virtual mouse: (accel) acceleration factor: 2.000
[    61.130] (**) Mouseemu virtual mouse: (accel) acceleration threshold: 4
[    61.137] (II) config/udev: Adding input device Mouseemu virtual keyboard (/dev/input/event6)
[    61.138] (**) Mouseemu virtual keyboard: Applying InputClass "evdev keyboard catchall"
[    61.138] (II) Using input driver 'evdev' for 'Mouseemu virtual keyboard'
[    61.138] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    61.138] (**) Mouseemu virtual keyboard: always reports core events
[    61.138] (**) Mouseemu virtual keyboard: Device: "/dev/input/event6"
[    61.139] (--) Mouseemu virtual keyboard: Found keys
[    61.139] (II) Mouseemu virtual keyboard: Configuring as keyboard
[    61.139] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    61.139] (II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
[    61.139] (**) Option "xkb_rules" "evdev"
[    61.139] (**) Option "xkb_model" "pc105"
[    61.139] (**) Option "xkb_layout" "us"

```

---

### Post by rsavage on 2011-12-20
> **new to ubutnu said:**
> so i set DefaultDepth to 16 because of no 1024x768 but that froze my computer up
 
also the adding of those two lines froze my computer had to go into single user mode with each to get rid of them

 
Well that is disappointing. 
 
Searching around on this it seems DRI has been problematic with the r128 for a long time. I'm not entirely convinced anybody has got it fully working at the moment. In a statement of arrogance that will amuse or maybe make some people cringe: Let's assume that everything everbody has done with the r128 has been wrong so far.
 
Certainly that xorg.conf that we downloaded is a load of pap. That Hsync range 60-60 is stopping you changing resolution. That is why, I think, you are stuck on 1024x768. If you look at the lubuntu instructions there are directions for how to find the correct values for your monitor. I would do this or setup modelines for the resolutions you want. Then you can experiment with changing modes.
 
I would remove r128 from the /etc/initramfs-tools/modules file. I don't think it should be loaded so soon. It goes against the documented advice. I would also remove it from the /etc/modules file.
 
Does is crash if you have
 
```

uninorth-agp
agpgart

```
[noparse](and no r128)[/noparse] listed in both the /etc/initramfs-tools/modules and /etc/modules files? Remember to run the "sudo update-initramfs -u" for changes to take effect.
 
Can we have the output of "dmesg | grep drm", "dmesg | grep agp" and "dmesg | grep r128" please?

 
If it does crash is it possible to see the xorg log file from the crash?

---

### Post by new to ubutnu on 2011-12-23
i tried the ddcprobe command from the lubuntu instructions to change the frequency rates but it came up with this error
```
Framebuffer ioctl failed. Exiting.
VESA BIOS Extensions not detected.

```

on the other hand i went on and it didnt crash at all just the same as always

here are the dmesg outputs
```
adminubuntu@iMacUbuntu:~$ dmesg | grep drm
adminubuntu@iMacUbuntu:~$ dmesg | grep agp
[    0.498825] Linux agpgart interface v0.103
[    2.903611] agpgart-uninorth 0000:00:0b.0: Apple UniNorth chipset
[    2.908145] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 64
[    2.911030] agpgart-uninorth 0000:00:0b.0: AGP aperture is 256M @ 0x0
adminubuntu@iMacUbuntu:~$ dmesg | grep r128

```

---

### Post by rsavage on 2011-12-23
> **new to ubutnu said:**
> i tried the ddcprobe command from the lubuntu instructions to change the frequency rates but it came up with this error
```
Framebuffer ioctl failed. Exiting.
VESA BIOS Extensions not detected.

```

Oh, maybe it doesn't work on powerpc?  Did you run it with sudo?

What about finding the modelines instead?  Have you tried that?  Try and get it working so that you can change resolutions.

Your dmesg's are interesting - no drm stuff now so maybe we do have prod r128 at some point?

---

### Post by new to ubutnu on 2011-12-23
so i did sudo ddcprobe and that gave me the output i wanted but when i went into xorg.conf the refresh rates where the same so i dont know what to do on that path

for modelines i don't know what i should type in to get the modeline because the one on the lubuntu instructions is for your ibook should i try crt 800 600 or crt 1024 768 or is it not crt i have no clue

---

### Post by rsavage on 2011-12-23
Yes use the cvt command. You will just get a different output from me. Run it for the resolutions you want.

---

### Post by new to ubutnu on 2011-12-23
so i put it to the 800 600 resolution but it didn't do anything

---

### Post by rsavage on 2011-12-24
To be honest, I can't explain an xorg.conf file any better than in the lubuntu instructions.  It is something you are going to have to experiment with.  If you want me to tell you why the 800x600 resolution is not working then you'll have to supply the xorg.conf you are using and Xorg.0.log.  I suspect you are using a different mode name to that referenced in the screen section.

---

### Post by rsavage on 2011-12-31
> **rsavage said:**
> To be honest, I can't explain an xorg.conf file any better than in the lubuntu instructions. 
 
Well, not true as I've made some more additions.  
 
r128 owners maybe interested in this bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/133119](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-r128/+bug/133119) .  It explains a lot of the commented out options in the xorg.conf that narcisgarcia provided in post #1 of this thread.  You can try adding them to your xorg.conf.

---

### Post by rsavage on 2012-01-01
I've been doing a bit more digging into this - trying to get my head around all the different components at work here. There is a good explanation on around the 6th post in this gentoo thread [http://forums.gentoo.org/viewtopic-t-692266-start-0.html](http://forums.gentoo.org/viewtopic-t-692266-start-0.html) .
 
That seems to suggest there was a problem in 2008 with AIGLX and Rage 128/Mach 64 cards. So I looked up the AIGLX documentation at Fedora [http://fedoraproject.org/wiki/RenderingProject/aiglx](http://fedoraproject.org/wiki/RenderingProject/aiglx) and that still has the cards listed as not working. 
 
So maybe the thing to do is add 
 
```

Section "ServerFlags"
Option  "AIGLX" "off"
EndSection
 
Section "Extensions"
Option "Composite" "Disable"
EndSection

```
to the xorg.conf as suggested at the bottom of the Fedora page?
 
We really need somebody with an r128 card to have a good experiment with all these options and report back.
 
I still can't work out how the framebuffers interact with all this. Do you need to manually set the framebuffer resolution to match the Xorg resolution?  Also, the powerpcFAQ suggests in the tweak section that the UseFBDev option slows 3D performance for radeon cards [https://wiki.ubuntu.com/PowerPCFAQ#A3D_video_drivers.2C_Beryl.2C_Compiz](https://wiki.ubuntu.com/PowerPCFAQ#A3D_video_drivers.2C_Beryl.2C_Compiz) .  This seems to contadict other advice regarding this option for the r128.  Does this option impact the working of AIGLX???

---

### Post by narcisgarcia on 2012-10-30
A domain name has changed for Lapipaplena. Please update the link for:
[http://wiki.gilug.org/index.php/AppleImacG3350-ubuntu1104](http://wiki.gilug.org/index.php/AppleImacG3350-ubuntu1104)

---

