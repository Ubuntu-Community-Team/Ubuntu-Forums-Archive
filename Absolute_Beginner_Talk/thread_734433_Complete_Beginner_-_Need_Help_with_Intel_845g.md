---
title: "Complete Beginner - Need Help with Intel 845g"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Spanky2k5 on 2008-03-24
Hey Guys

I only decided to give Ubuntu a go yesterday (my first time ever with Linux) and had the same problem
I booted the Live CD in VGA safe mode and installed from there and all worked since then

Thing is I installed Xubuntu to see what Compiz Fusion could do first hand but I'm having problems myself
I think its to do with the driver I'm using for the onboard Intel 845g graphics, but neither I810 and Intel seem to work, so I'm stuck with Vesa

If anyone has any ideas what I can do to get Compiz Fusion working I'm running Xubuntu 7.10 on an old iFriend NC202i4 notebook. I believe it a 2ghz Celeron, 512mb Ram and the Intel 845g Graphics.

If anyone wants me to post my xorg.conf file they'll need to tell me how to do it first (seriously, never used Linux before last night).

Also trying to get a Phillips SNU5600 Wireless USB installed but haven't really tried doing anything with that yet as VGA's my priority.

Cheers for any help

---

### Post by Mazza558 on 2008-03-24
what does 

> glxinfo

show? Post the results here (enter that code into the terminal)

---

### Post by Spanky2k5 on 2008-03-24
Cheers dude,
this is what I got from glxinfo;

name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
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
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by Spanky2k5 on 2008-03-25
Just to mention I'm pretty sure I've tried every available fix for this so far like using the Alien app to do something with the drivers and manually changing the xorg.conf settings for the drivers. Don't seem to be able to install Xgl for Compiz either, despite following all the tutorials.

One fix I found on the forum involved changing the Video memory in the BIOS to 8mb, My iFriend runs some old phoenix BIOS that doesn't have an option for this and I'm not sure I can update it (It's a seriously lacking BIOS)

--Was halfway through typing this on the iFriend when the screen turned off, Ctr + Alt + F1 brought part of it back, about 1/4 was visible on the left

---

### Post by toobuntu on 2008-03-25
A fix was recently released (see [https://bugs.launchpad.net/bugs/177492]("https://bugs.launchpad.net/bugs/177492")).

Please run:

```
sudo aptitude update && sudo aptitude full-upgrade
```

in a terminal, or upgrade via Synaptic.

The relevant package to be upgraded is

> xserver-xorg-video-intel

to version 2:2.2.1-1ubuntu6

If that still doesn't do it for you, then also run the following in a terminal and reboot:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Spanky2k5 on 2008-03-25
cheers for the help, i couldn't find the package using the terminal command but I got it in Synaptic.

 It shows the xserver-xorg-video-intel package I have installed is version 2.2.1.1 Ubuntu 9.1 and says this is the Latest Version as well. 

I'm not sure how to upgrade this to the 2.2.2.1-1ubuntu6 version you mentioned. I right click and 'Mark for Upgrade' is grayed out.

I'm probably being really stupid but I don't know a thing about Linux and figured it was about time I learnt

---

### Post by toobuntu on 2008-03-25
My bad, I didn't bother to look and see that you're using Gutsy and not Hardy.  The version you have installed is the current version for Gutsy.

That said, I have installed the Hardy version of the intel graphics driver on 3 Gutsy systems without incident.  To do so in a terminal, just do the following:

```
cd /var/cache/apt/archives
sudo wget -c 'http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu6_i386.deb'
sudo dpkg -i xserver-xorg-video-intel_2.2.1-1ubuntu6_i386.deb
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

Note that the .deb I listed above is for i386 systems, not the newer 64-bit ones.

---

### Post by Spanky2k5 on 2008-03-26
beginning to think this was not meant to be;
first time I did the cd it said directory not found, must have typed it in wrong
second time I tried it nothing changed, just another command line appeared exactly the same as the first one.

I continued with the commands although the first sudo dpkg gave me what seemed to be an error in updating xserver-xorg-video-intel

After sudo reboot I've got a completely blank screen. Ctrl Alt F1 isn't bringing anything up for me. 
I'll reinstall and try again

---

### Post by toobuntu on 2008-03-26
I'm sorry to hear that things are not working out well for you.  You may not need to reinstall.  Try rebooting into safe mode and copying back your old xorg.conf (dpkg-reconfigure should have automatically saved a backup of the old one), and then rebooting normally again.

Let me know if you need more detailed instructions.

---

### Post by glennric on 2008-03-26
> **toobuntu said:**
> ```
cd /var/cache/apt/archives
sudo wget -c 'http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu6_i386.deb'
sudo dpkg -i xserver-xorg-video-intel_2.2.1-1ubuntu6_i386.deb
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

Note that the .deb I listed above is for i386 systems, not the newer 64-bit ones.

That deb will not work on Gutsy.  It depends on a libc6 with version >= 2.7-1, but the version on Gutsy is 2.6.1

Spanky2k5:  I have the same video card that you have on one of my computers.  I couldn't get the "intel" driver to work for it.  All I ever get with that is a blank screen, and the monitor reporting that it is out of range.  Sadly enough, this is the driver that "dpkg-reconfigure -phigh xserver-xorg" will choose for the card.  You should try the "i810" driver.  You will need to manually set up your xorg.conf file.  If you post the contents of your's here, I will help you do it.

---

### Post by Spanky2k5 on 2008-03-26
bah It's probably me. I haven't got a clue what I'm doing - Just having fun with an old notebook.
I never seem able to get cd commands working either.

Restarting now after fresh install -I wouldn't know how to copy back and old xorg.conf file or boot into safe mode as I can't see a thing on the screen anyway!

---

### Post by glennric on 2008-03-26
How are you installing?  Are you using the live cd (i.e. the graphical installer)?

---

### Post by Spanky2k5 on 2008-03-26
what command do I use to get the contents of my xorg.conf file?

I think I may have tried manually configuring the driver a couple of days ago but I'm willing to give it a shot again.

This is the message I get when I do the first dpkg commang is;
> 
2.1-1ubuntu6_i386.deb
(Reading database ... 88022 files and directories currently installed.)
Preparing to replace xserver-xorg-video-intel 2:2.1.1-0ubuntu9 (using xserver-xorg-video-intel_2.2.1-1ubuntu6_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on libc6 (>= 2.7-1); however:
  Version of libc6 on system is 2.6.1-1ubuntu9.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.4); however:
  Version of xserver-xorg-core on system is 2:1.3.0.0.dfsg-12ubuntu8.
dpkg: error processing xserver-xorg-video-intel (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xserver-xorg-video-intel

Which I think is pretty much what you just told me....:(

EDIT: I'm installing via the Live CD but have to go into Safe Graphics mode first so I can see the screen
        I understand there's a text based Alternative Installer CD too but I wouldn't know where to begin with that

---

### Post by toobuntu on 2008-03-26
Sorry guys, I did it again.  After checking the Gutsy machines and retracing my steps I realized that, indeed, I did not install the Hardy driver on Gutsy, but an unreleased Gutsy driver provided by the developer in:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151044]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/151044")

I cannot say that this driver will solve all of your problems, but it has provided some added stability for these machines.

```
cd /var/cache/apt/archives
sudo wget -c 'http://www2.eng.cam.ac.uk/~pcjc2/ubuntu/xserver-xorg-video-intel_2.1.1-0ubuntu10~pcjc2.2_i386.deb'
sudo dpkg -i xserver-xorg-video-intel_2.1.1-0ubuntu10~pcjc2.2_i386.deb
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

It is usually easiest to copy/paste into the terminal.  In gnome-terminal, Ctrl-Shift-V, Ctrl-Shift-Insert, or middle-click should paste.

You should be able to run these commands after rebooting into recovery mode (but would not be able to copy/paste).

---

### Post by glennric on 2008-03-26
> **Spanky2k5 said:**
> what command do I use to get the contents of my xorg.conf file?

I think I may have tried manually configuring the driver a couple of days ago but I'm willing to give it a shot again.

This is the message I get when I do the first dpkg commang is;


Which I think is pretty much what you just told me....:(

EDIT: I'm installing via the Live CD but have to go into Safe Graphics mode first so I can see the screen
        I understand there's a text based Alternative Installer CD too but I wouldn't know where to begin with that

I have exactly the same problem with the live cd on that computer.  I have to either use the alternate installer or save graphics mode.  The reason is that the default driver is the "intel" one that doesn't work.  Perhaps what toobuntu is suggesting with the updated intel driver may work, but I have the i810 driver working with compiz and no problems.

---

### Post by toobuntu on 2008-03-26
The i810 driver is no longer supported upstream, and that's why folks are trying to get the intel driver working.

---

### Post by Spanky2k5 on 2008-03-26
```
cd /var/cache/apt/archives
sudo wget -c 'http://www2.eng.cam.ac.uk/~pcjc2/ubuntu/xserver-xorg-video-intel_2.1.1-0ubuntu10~pcjc2.2_i386.deb'
sudo dpkg -i xserver-xorg-video-intel_2.1.1-0ubuntu10~pcjc2.2_i386.deb
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

I just gave this a go and again my screens completely black, It doesn't seem to like anything but the Vesa driver

---

### Post by glennric on 2008-03-26
> **toobuntu said:**
> The i810 driver is no longer supported upstream, and that's why folks are trying to get the intel driver working.

I know that, and every couple of months I try again to get the intel driver to work with no success.

---

### Post by Spanky2k5 on 2008-03-26
Does it make any difference that I'm using Xubuntu rather than Ubuntu? 

I figured it'd run faster as I read the xfce desktop uses fewer resources than GNOME, so it's better for older pc's.

---

### Post by glennric on 2008-03-26
> **Spanky2k5 said:**
> Does it make any difference that I'm using Xubuntu rather than Ubuntu? 

I figured it'd run faster as I read the xfce desktop uses fewer resources than GNOME, so it's better for older pc's.

That won't make any difference.  The xserver is under both of those.  This is a problem at the xserver level, not the desktop management level.

---

### Post by Spanky2k5 on 2008-03-26
Ok, I've never used flickr before either but I think this should show exactly what I see on my laptop screen now (was black, then pressed ctrl)

This is straight from boot


[http://www.flickr.com/photos/25067821@N06/2364210044/](http://www.flickr.com/photos/25067821@N06/2364210044/)

---

### Post by glennric on 2008-03-26
After a little testing I see that the situation with my computer is even worse than with yours.  If I boot the live cd in any graphical mode (even the safe mode) all I get is a black screen.  The only driver that gives me anything in a normal boot is the i810 driver.  Even the vesa driver doesn't work.  Try typing
```
cat /etc/X11/xorg.conf
```
in a terminal and then cut and paste the output and post is here.

Edit:  If you are not able to get the xserver started you can't do this, duh.  Is there any way you can copy that file to another computer and then post it here?

---

### Post by Spanky2k5 on 2008-03-26
I'll try it as soon as I get into the system again, If I booted the live CD and typed that command in I presume i'd get the settings for the CD, not my installation.
At the moment I can't really do anything. just part of some text on a black screen;
[http://www.flickr.com/photos/25067821@N06/2364210044/](http://www.flickr.com/photos/25067821@N06/2364210044/)

EDIT: I don't think I can copy it to another computer. I've got my Vista PC I'm using now and the Notebook running (trying to) Gutsy, and another XP laptop. They;re all networked but I don't think that'll do me much good.
I can try booting from the Live CD and reinstalling again?

---

### Post by glennric on 2008-03-26
Yes to the live cd comment.  However, it can still be done from the live cd.  You will have to mount your usual partition and then we can get to your file.  

By the way, I finally got the intel driver to work on my computer.  I used the default xserver-xorg-video-intel package for gutsy.  It turned out that it was an issue with the monitor refresh rates.  For some reason the refresh rates that are detected by dpkg-reconfigure worked with the i810 drivers, but not the intel drivers.  After commenting those out I was able to get the xserver to work.  However, the xserver still won't even start if I try to use the vesa drivers.

---

### Post by Spanky2k5 on 2008-03-26
Ok I'm on the Live CD now, this is the contents of my xorg.conf from the disk

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by glennric on 2008-03-26
And that xorg.conf is the one that gives you trouble...Hmm.  So it may be that you need to figure out the proper horizontal and vertical refresh rates of your monitor.  When you booted to that xorg.conf you just get a black screen, right?  Does your monitor say out of range or something like that?

---

### Post by Spanky2k5 on 2008-03-26
Nope, doesn't say anything-  just a black screen after BIOS, I waited a while then pressed ctrl alt f1, which I believe is supposed to bring up a terminal or something and I get the cut off text shown in the picture earlier.
As its a laptop monitor there are no auto adjust buttons either, should they do anything to help

---

### Post by glennric on 2008-03-26
You have a black screen right after the bios?  You don't even see grub or something about hitting esc to see the grub menu?

---

### Post by Spanky2k5 on 2008-03-26
my bad, I do see the grub menu, it's after that that it goes black

---

### Post by toobuntu on 2008-03-26
Can you post the output of the following (you could get these by using the live CD):

```
sudo lshw -C  system -C display
```

and

```
sudo xresprobe intel
```

and from your hard disk install:

```
cat /etc/usplash.conf
```

It is curious that the live CD seems to work for you with the intel graphics driver, but once installed onto the hard disk it no longer works.

Also, have you considered downloading the Xubuntu Hardy beta and trying that?  It features an updated Xorg and intel graphics driver.

---

### Post by glennric on 2008-03-26
> **toobuntu said:**
> It is curious that the live CD seems to work for you with the intel graphics driver, but once installed onto the hard disk it no longer works.

Also, have you considered downloading the Xubuntu Hardy beta and trying that?  It features an updated Xorg and intel graphics driver.

The live cd with the intel driver doesn't work for him.  He has to boot the live cd to safe graphics mode (i.e. with the vesa driver)

---

### Post by Spanky2k5 on 2008-03-26
Just to clarify I'm running the Live CD, opening a terminal and using the first two commands, and you want me to copy and paste the data in my etc/usplash.conf on the hard disk?

I've thought about using Hardy, but as it's only a beta I don't know if Compiz would work correctly on it, or how stable it is. The download page tells me its intended for developers only and I'm far from the being a developer

---

### Post by glennric on 2008-03-26
We can get this working.  I have some ideas.  There should be no need to switch to Hardy just yet.

---

### Post by glennric on 2008-03-26
Can you get to the grub menu at all when you boot to your hard disk?

---

### Post by toobuntu on 2008-03-26
> The live cd with the intel driver doesn't work for him. He has to boot the live cd to safe graphics mode (i.e. with the vesa driver)

The xorg.conf shows that the intel driver is being used, but I suppose that's wherein lies his blank screen issues.

> **Spanky2k5 said:**
> Just to clarify I'm running the Live CD, opening a terminal and using the first two commands, and you want me to copy and paste the data in my etc/usplash.conf on the hard disk?

I've thought about using Hardy, but as it's only a beta I don't know if Compiz would work correctly on it, or how stable it is. The download page tells me its intended for developers only and I'm far from the being a developer

From the live CD, open a terminal, run the first two commands, which query your hardware information.  Then paste the output here if you can.

Also from the live CD, I'm asking if you can mount your hard drive and run the third command on your mounted partition which contains the Xubuntu installation.  As an example:

```
sudo mkdir /mnt/xubuntu
sudo mount -t ext3 /dev/sda1 /mnt/xubuntu
cat /mnt/xubuntu/etc/usplash.conf
cat /mnt/xubuntu/etc/X11/xorg.conf
sudo umount /mnt/xubuntu
sudo rmdir /mnt/xubuntu
```

Hardy is a Long Term Support release, and the beta is actually surprisingly stable.  But I do understand your reticence.

---

### Post by Spanky2k5 on 2008-03-26
I can get to the GRUB menu when I try to boot to disc by pressing esc within the 1 sec timeframe I'm given, From there it offers recovery mode, normal mode and memtest

These are the results from the 3 commands toobuntu suggested, run from the Live CD

```
    description: Computer
    product: NBGV - Northwood/Brookdale-G Validation Board
    vendor: Intel Corporation
    version: Revision A0
    serial: 0123456789
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific frontpanel_password=unknown keyboard_password=unknown
  *-display
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

```

xresprobe one didn't do much
```

id: 
res: 
freq: 
disptype: lcd/lvds

```

and the contents of /etc/usplash.conf on the hard disk
```

# Usplash configuration file
xres=1280
yres=1024

```

Presuming thats my resolution that seems a little high 1024 x 768 seems more appropriate

EDIT: Just to clarify I didn't mount my hard disk for the last one, I browsed to the file through the hard disk via the Live CD and opened it in AbiWord

---

### Post by glennric on 2008-03-26
Yeah, you will need to change your usplash.conf to be 1024x768.  Then you will have to type
```
sudo dpkg-reconfigure usplash
```
however, this won't affect what happens once the xserver is running.  That is why you have a black screen up to the point where the xserver starts.  Then you have other issues.

---

### Post by toobuntu on 2008-03-26
FYI - on my 1280x1024 monitor, I use a usplash.conf like this:

```
$ cat /etc/usplash.conf
# Usplash configuration file
xres=640
yres=480
```

which is plenty fine for me.

Also, xresprobe without and with sudo:

```
$ xresprobe intel
id:
res:
freq:
disptype:
```

```
$ sudo xresprobe intel
id: DELL 1905FP
res: 1280x1024 1152x864 1024x768 800x600 720x400 640x480
freq: 30-81 56-76
disptype:
```

---

### Post by Spanky2k5 on 2008-03-26
So if I use a text editor to edit it while on Live CD then attempt to boot from hard disk it's not likely to do anything, other than give me a nice splash screen to look at?

---

### Post by glennric on 2008-03-26
Well, maybe.  That is if there aren't other issues.  You are most likely going to have to add a vga=??? kernel parameter.  That is most likely what is causing your cut off text screenshot that you posted.

---

### Post by Spanky2k5 on 2008-03-26
I tried editing the usplash.conf in a text editor from Live CD but I can't save any changes for some reason

---

### Post by glennric on 2008-03-26
What you should probably try now is to boot to the hard disk and get to the grub menu.  Then select your default boot option and hit e.  Then select the kernel line and hit e again.  Then add to the end of that line vga=791 (that may not work but it is a pretty safe bet).  Then hit enter and b to boot.  See what that does.

---

### Post by glennric on 2008-03-26
> **Spanky2k5 said:**
> I tried editing the usplash.conf in a text editor from Live CD but I can't save any changes for some reason

That is most likely a permissions issue.  You will have to edit with sudo.

---

### Post by Spanky2k5 on 2008-03-26
Ok, added vga=791 to the end of the kernel line...

...still nothing I'm afraid, black screen- ctrl alt f1 doesn't seem to want to do anything either.
Should I reformat, reinstall again and try sorting driver out from there?

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Hey Guys

I only decided to give Ubuntu a go yesterday (my first time ever with Linux) and had the same problem
I booted the Live CD in VGA safe mode and installed from there and all worked since then

Thing is I installed Xubuntu to see what Compiz Fusion could do first hand but I'm having problems myself
I think its to do with the driver I'm using for the onboard Intel 845g graphics, but neither I810 and Intel seem to work, so I'm stuck with Vesa

If anyone has any ideas what I can do to get Compiz Fusion working I'm running Xubuntu 7.10 on an old iFriend NC202i4 notebook. I believe it a 2ghz Celeron, 512mb Ram and the Intel 845g Graphics.

If anyone wants me to post my xorg.conf file they'll need to tell me how to do it first (seriously, never used Linux before last night).

Also trying to get a Phillips SNU5600 Wireless USB installed but haven't really tried doing anything with that yet as VGA's my priority.

Cheers for any help
you will be very lucky if you get it working...!!!

intel integrated graphics seems to give problems

i have an integrated 945G/GZ chipset... could never work out 1440 x 900 native resolution even after installing 915resolution utility... could only get 1024 x 768 resolution... eventually installed a nvidia card & everthing is alright...

if you run dpkg, remember to backup your xorg.conf file

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

regards,

devang.

---

### Post by toobuntu on 2008-03-26
There are some other steps you could take, but it is a bit cumbersome to go through every detail in these forum posts.  Let us know if you want us to try to help in that way, though.

My personal recommendation is to go ahead and try the Hardy beta.  I just ran the live CD on an intel 845 machine yesterday with positive results.  Don't forget to perform a full upgrade, though, after you install it.

---

### Post by Spanky2k5 on 2008-03-26
think I will give the Hardy beta a go then.

What will happen with the Beta in 29 days time when it's released? Will it update to the Official release or will that need to be installed again?

Does Compiz Fusion work on Hardy to achieve those tasty effects?

---

### Post by glennric on 2008-03-26
> **Spanky2k5 said:**
> think I will give the Hardy beta a go then.

What will happen with the Beta in 29 days time when it's released? Will it update to the Official release or will that need to be installed again?

Does Compiz Fusion work on Hardy to achieve those tasty effects?

Compiz should work in Hardy.  The beta will update to the official release as soon as it is out.  It will pretty much already be there in fact.  The beta will update as updates are available until it is the official release.

---

### Post by Spanky2k5 on 2008-03-26
Tried running Hardy from Live CD and again I've got no damn screen!

---

### Post by toobuntu on 2008-03-26
> **Spanky2k5 said:**
> think I will give the Hardy beta a go then.

What will happen with the Beta in 29 days time when it's released? Will it update to the Official release or will that need to be installed again?

Does Compiz Fusion work on Hardy to achieve those tasty effects?

Compiz is enabled by default in Hardy (in Gutsy, too).  Hardy uses a newer release of both Xorg and the intel driver, so hopefully those will help.  I should warn you, though, that your first boot into Hardy may not go well, in which case just Ctrl-Alt-F1 and log on to the console, and run

```
sudo nano /etc/apt/sources.list
```

uncomment (i.e. delete the hash mark # at the beginning of the line) any commented out repositories, but do ensure that the top ones for the CD-ROM _are_ commented out.

Ctrl-O to write out, Ctrl-X to exit, then

```
sudo aptitude update && sudo aptitude full-upgrade
```

then

```
sudo reboot
```

So long as you run another full upgrade after the final release, you will have a bona fide Hardy release and will not need to reinstall.  Or, via the GUI: System->Administration->Update Manager.

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Tried running Hardy from Live CD and again I've got no damn screen!
did you try 915resolution?

[http://www.geocities.com/stomljen/]("http://www.geocities.com/stomljen/")

---

### Post by toobuntu on 2008-03-26
> **fourthofjuly said:**
> did you try 915resolution?

[http://www.geocities.com/stomljen/]("http://www.geocities.com/stomljen/")

915resolution works with the i810 driver, but is not relevant to and does not work with the intel driver which used dexconf for autoconfig.

---

### Post by Spanky2k5 on 2008-03-26
don't know how to get 915 resolution when installing. 
Tried booting straight into Live CD - no screen
Hit F4 to install Hard in VGA safe mode, that wouldn't do anything
So had to just hit 'Install Now'
CD-ROM was being read (up until 20 seconds ago)
But still no screen

---

### Post by fourthofjuly on 2008-03-26
ok, you can install 915resolution after your system is installed...

you get a blank screen even with the live CD?

---

### Post by Spanky2k5 on 2008-03-26
Yeah seems like no matter what I do I get a blank screen

EDIT: ffs, tried just loading from Live CD in VGA safe mode and my screens blank. Even Gutsy let me do that!

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Yeah seems like no matter what I do I get a blank screen
don't mind but Hardy Beta is only for testers,

what if you run the Gutsy live CD?

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Yeah seems like no matter what I do I get a blank screen

EDIT: ffs, tried just loading from Live CD in VGA safe mode and my screens blank. Even Gutsy let me do that!
ok, so you pop in the Gutsy live CD and reboot your system, how far do you go?

do you get the boot menu options for start or install / safe graphics mode, memory testing, boot from first hard disk  and so on?

if yes, did you select the first option of start or install and then got a blank screen?

---

### Post by Spanky2k5 on 2008-03-26
Gutsy live cd works its just setting my the driver up for the Intel 845g graphics that causes pain. It only seems to work with Vesa, anything else I try gives me a black screen.

My latest idea: I have another Laptop (well...it's my girlfriends) I could try installing ubuntu on.
This one is still old but slightly newer and uses an ATI chipset which I preume will give me sexier results than the 845g I'm currently dealing with.

This laptop has XP installed on it, only taking up about 4gb of the 40gb it has, so is it possible to install Ubuntu as a secondary OS by creating a partition even though XP is already installed? -If that makes sense. I just wanna retain XP on the laptop for my girlfriend while I mess about with Ubuntu.

Also which flavour should I use? Hardy or Gutsy?

---

### Post by Spanky2k5 on 2008-03-26
> **fourthofjuly said:**
> ok, so you pop in the Gutsy live CD and reboot your system, how far do you go?

do you get the boot menu options for start or install / safe graphics mode, memory testing, boot from first hard disk  and so on?

if yes, did you select the first option of start or install and then got a blank screen?

Got to the options to install, Gutsy works fine as long as I run Life CD, or Install in safe graphics mode. Once it's installed though and I try to change the driver to a more appropriate one I get a black screen. It doesn't like anything but Vesa

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Gutsy live cd works its just setting my the driver up for the Intel 845g graphics that causes pain. It only seems to work with Vesa, anything else I try gives me a black screen.

My latest idea: I have another Laptop (well...it's my girlfriends) I could try installing ubuntu on.
This one is still old but slightly newer and uses an ATI chipset which I preume will give me sexier results than the 845g I'm currently dealing with.

This laptop has XP installed on it, only taking up about 4gb of the 40gb it has, so is it possible to install Ubuntu as a secondary OS by creating a partition even though XP is already installed? -If that makes sense. I just wanna retain XP on the laptop for my girlfriend while I mess about with Ubuntu.

Also which flavour should I use? Hardy or Gutsy?
please continue with Gutsy, as i said, Hardy is in Beta stage and only for testing...

if you want a dual boot with XP, first run disk defragmenter before you edit / resize the partitions...

maybe you can try Virtualbox to run Ubuntu within XP...

[http://www.virtualbox.org/]("http://www.virtualbox.org/")

in case you do not want to dual boot / change partitions... it will create a virtual harddisk for Ubuntu within XP...

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Got to the options to install, Gutsy works fine as long as I run Life CD, or Install in safe graphics mode. Once it's installed though and I try to change the driver to a more appropriate one I get a black screen. It doesn't like anything but Vesa
as i mentioned, intel integrated graphics do have this problem...

what if you do not change the driver, if its manageable?

---

### Post by Spanky2k5 on 2008-03-26
Gutsy it is then!
Can I sort the partitions out while installing Gutsy or do I have to do this seperately?

---

### Post by Spanky2k5 on 2008-03-26
> **fourthofjuly said:**
> as i mentioned, intel integrated graphics do have this problem...

what if you do not change the driver, if its manageable?

It'd defeat my reasoning for installing ubuntu. I know nothing about it so I wanted to learn by doing and experiment with the Compiz Fusion plugins, which won't work with Vesa on my notebook

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> It'd defeat my reasoning for installing ubuntu. I know nothing about it so I wanted to learn by doing and experiment with the Compiz Fusion plugins, which won't work with Vesa on my notebook
my solution was to install a new nvidia graphics card and use it as default...

---

### Post by fourthofjuly on 2008-03-26
> **Spanky2k5 said:**
> Gutsy it is then!
Can I sort the partitions out while installing Gutsy or do I have to do this seperately?
ok, run a complete disk defragment in XP, BACKUP your data and reboot with your live CD...

at the time of install, you can resize (reduce) your XP partition(s) to make free space (i guess you have free space on XP partitions)

use the free space to create ext3  and swap partitions and continue install 

do update me how it goes...

regards,

devang.

---

### Post by Spanky2k5 on 2008-03-26
Going well so far
Partition been created and XP install defragmented
Booted Live CD first to see how it looks and it's a lot smoother & prettier on this laptop.
Didn't bother backing up XP data - If I lose my girlfriends data she'll live with it...

---

### Post by Spanky2k5 on 2008-03-26
Lost my girlfriends data...she's living with it....

---

