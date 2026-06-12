---
title: "[SOLVED] Help Please"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by T2manner on 2008-03-02
i just got Ubuntu installed yesterday.
i wanna figure out how to install the EZ Connect G SMC2862W-G for my SMC wireless adapter.
the adapter works without that software but it looses connection alot.

also, when i tried to go to ADD Programs ( bcs i wanted to get Compiz Fusion ) when i checked the software i wanted it said i had to refresh the list, so i did. then i checked the box again and i had to keep refreshing and it never ended up working :[[[

---

### Post by Cresho on 2008-03-02
first off, you are a newbie. (do not take offense to this please!) :)

You need to post what ubuntu you are running!  anything higher than gutsy has compiz built in.  Secondly, you need to tell us if your videocard is running so someone can help you better.  What is it?  nvidia?  ATI?
is your drivers working?  a none configured xorg.conf will not allow 3d.

---

### Post by T2manner on 2008-03-02
i'm on gutsty gibson.

and idk what video card i'm using :[

---

### Post by Cresho on 2008-03-02
OKAY

1.  COPY AND PASTE THIS IN THE TERMINAL

lspci | grep VGA

PASTE THAT INFO HERE


2.  DO A GLXGEARS AND SEE IF YOUR HARDWARE 3D IS ALREADY RUNNING (IN THE TERMINAL AS WELL)


AWAITING ANSWERES TO 1 AND 2

---

### Post by T2manner on 2008-03-02
before i switch over to ubuntu, whats GLXGEARS

---

### Post by Cresho on 2008-03-02
SORRY, I had caps on.  glxgears needs to by typed small letters in the terminal.
definition of it here.
[http://linux.about.com/cs/linux101/g/glxgears.htm](http://linux.about.com/cs/linux101/g/glxgears.htm)

---

### Post by JoshuaRL on 2008-03-02
Okay, the first command:
```

lspci | grep vga

```
lists the pci info with an arguement for the vga slot.

```

glxgears

```
is a benchmarking CLI app to see what frames per second you are getting.

You could also try:
```

glxinfo | grep direct

```
to see if direct rendering (3D hardware acceleration) is running.

Could you also post the output of:
```

gedit /etc/X11/xorg.conf

```
That is the configuration file for Xorg, the GUI app.  That command won't allow you to edit it, so no worries about messing it up.

---

### Post by T2manner on 2008-03-02
okay so i put that other stuff in the terminal, then i just put in glxgears?

---

### Post by JoshuaRL on 2008-03-02
Do the first one and post it.  Then move on.

---

### Post by T2manner on 2008-03-02
okay brb, i need to get on ubuntu to do this :P
thanks tho.

---

### Post by T2manner on 2008-03-02
okay i put the first code in and hit enter and nothing happened

---

### Post by JoshuaRL on 2008-03-02
You're in the terminal right?  If so, then try the lspci command.

---

### Post by T2manner on 2008-03-02
i did the lspci one first. i'll do the other one the dude posted

---

### Post by T2manner on 2008-03-03
okay sorry i copied the lspci one wrong. i'll show what it says

> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)


---

### Post by T2manner on 2008-03-03
yeah..

---

### Post by JoshuaRL on 2008-03-03
Okay, looks like you have an Intel integrated card.  Linux has good support for those.

Could you try:
```

glxinfo

```

And then:
```

gedit /etc/X11/xorg.conf

```

and post those two please?

---

### Post by T2manner on 2008-03-03
glxinfo:
> name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x62 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon




gedit one:
> # xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"MX70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"MX70"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection

---

### Post by JoshuaRL on 2008-03-03
Okay, what I see there is that your card is configured correctly.  So that isn't a problem.

What exact problems are you having with Compiz now?

---

### Post by dark_harmonics on 2008-03-03
To be honest i just think the user needs to install the settings manager:

from the terminal do a :
```

sudo apt-get install compizconfig-settings-manager

```

Then go to the system -preferences-and you should see an advanced desktop settings listed there. Inside there you can configure compiz.

---

### Post by T2manner on 2008-03-03
my main problem
is i can't get it.
my internet connection is horrible because i'm using wireless adapters, and have not installed the software for it yet.
i've found many guides on it, i'm new to ubuntu and don't know how to do it.

i need to install EZ Connect G  SMC2862W-G

i can get a connection without the software, but it eventually stops working. like right now.
i'm on windows now bcs i lost connection.

---

### Post by T2manner on 2008-03-03
can anybody help

---

### Post by T2manner on 2008-03-03
please

---

### Post by JoshuaRL on 2008-03-03
[I found this thread here.](http://ubuntuforums.org/showthread.php?t=77034)

Couldn't find anything on the help wiki though.  You might see if that works for you.

As far as "getting compiz", it should already be installed.  You would want to do two things to activate it.

1).  Go to Add/Remove and search for "compiz".  That will bring up the Compiz Settings Manager.  That will allow you to configure compiz how you want.

2).  Go to System->Preferences->Appearance and go to the effects tab.  Then enable the custom desktop effects and go into Preferences.  That will open up the Settings Manager.

It should work well after that if your card can do it.

---

### Post by T2manner on 2008-03-03
Everytime i go to the add programs thing and i check some software i want it says i have to reload the list and i reload it. then it keeps asking me to reload

---

### Post by T2manner on 2008-03-03
?

---

### Post by JoshuaRL on 2008-03-03
Alright, could you go into System->Administration->Software Sources.

Then make sure everything is enabled except the CD and source stuff.

Then go to the terminal and try:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Cresho on 2008-03-04
you probably hosed compiz trying to install something which was already installed.  the above what he says should fix the problem.

---

### Post by T2manner on 2008-03-04
THAN KS!
it wasn't enabled.
well now i just need to figure out how to install my smc driver software for my wireless adapter

---

### Post by JoshuaRL on 2008-03-04
> **Cresho said:**
> you probably hosed compiz trying to install something which was already installed.  the above what he says should fix the problem.

He probably didn't hurt compiz with that.  He just couldn't get the Advanced Settings Manager downloaded and installed.  APT is nice like that, hard to mess stuff up that way.

If you have any problem installing that driver T2manner post it here and I'll see if I can help.  I don't have much experience with wifi, but I'll do all I can.

---

### Post by T2manner on 2008-03-05
yes i'm having trouble.
it's not really installing the drive i don't think.
i'm installing the software for the driver.
i've seen guides but idk how to do it.
i'll find one.. 1sec..
[http://ubuntuforums.org/showthread.php?t=77034](http://ubuntuforums.org/showthread.php?t=77034)
it's confusing to me

---

### Post by DaV|d on 2008-03-05
Well, from what I understood from Narkolas' post, you should run the following commands in a terminal. I haven't tested them though.

```

mkdir smc2862W
cd smc2862W
wget http://www.smc.com/files/AE%5C2862wV.2_V.3DR_UT.zip
unzip AE\\2862wV.2_V.3DR_UT.zip
sudo apt-get install ndiswrapper-utils-1.9
cd Driver/WinXP/
sudo ndiswrapper -i SMC2862W.inf
sudo ndiswrapper -l #(shows if the driver is installed) Mine looks like this "smc2862w driver installed, hardware present"
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo apt-get install network-manager-gnome

```

Continue from step 5 of [COLOR="Blue"][Narkolas' post]("http://ubuntuforums.org/showpost.php?p=2058905&postcount=4")[/COLOR].

Good luck :)

---

### Post by T2manner on 2008-03-05
omg!
thanks alot! 
i think it worked!

---

### Post by dark_harmonics on 2008-03-08
Clicked the thank you button on your behalf.

---

### Post by T2manner on 2008-03-19
i thought it worked..
it didn't.
well, idk what happened.
i still loose connection alot :[
it didn't change anything

---

### Post by DaV|d on 2008-03-19
Did the connection work for some time at least?
Or did you apply the commands now?

If the connection used to work, did you apply any updates?
Also, could you please post the output of
```
lsmod | grep ndiswrapper
```
Thanks.

---

### Post by T2manner on 2008-03-19
i always get a connection.
it just disconnects after a random period of time.
at most 20mins.
but yeah.
let me get on ubuntu and i'll post the outcome

---

### Post by T2manner on 2008-03-19
okay
the connection has always been like this.

and i put the code in and nothing happened

---

### Post by DaV|d on 2008-03-19
> **T2manner said:**
> okay
the connection has always been like this.

and i put the code in and nothing happened

ok that means that the module ndiswrapper is not being loaded.
Try this to load the module:
```
sudo modprobe ndiswrapper
```

and if that returns your network to normal, do the following:
```
sudo su
echo ndiswrapper >> /etc/modules
```

Finally, could you please copy and paste the output of:
```
cat /etc/modules
```
Thanks!

---

### Post by T2manner on 2008-03-19
yes i will but i've got to go to church and i'll get back on ubuntu and post around 8:25 pm cst

---

### Post by T2manner on 2008-03-19
okay. the first two didn't have any output. well the first one asked me for a password but after that nothing
this is what the last code outputted

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

---

### Post by DaV|d on 2008-03-20
Your modules file appears to be ok.

Let't try this now:
First of all, if you haven't already done so, reboot after entering yesterday's commands and check whether the connection is all right or still disconnects.

Secondly, please post the output of the following commands (they check whether the driver is installed ok):
```
lsmod | grep ndiswrapper

sudo ndiswrapper -l
```

---

### Post by T2manner on 2008-03-20
okay.
well so far since yesterday i haven't lost connection, but i haven't been on much either since last night.
i'm going to stay on and see if it's working right.

heres what the output:
tyler@Tyler:~$ lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  7 rt2500usb,rt2x00usb,p54usb,ndiswrapper,ehci_hcd,uhci_hcd
tyler@Tyler:~$ 
tyler@Tyler:~$ sudo ndiswrapper -l
smc2862w : driver installed
        device (0707:EE13) present (alternate driver: p54usb)
tyler@Tyler:~$

---

### Post by dstew on 2008-03-20
You may need to blacklist the p54usb module. It might be loading as well as ndiswrapper, and conflicting with it. To blacklist the module, you create a file (any name will do, but most people name it blacklist) with a text editor in the /etc/modprobe.d directory, and put in it the line **blacklist p54usb**. See [this thread]("http://ubuntuforums.org/showthread.php?t=646602"). From the command line, you can do```
gksudo gedit /etc/modprobe.d/blacklist
```to create the file, and put in the blacklist p54usb statement.

---

### Post by T2manner on 2008-03-20
okay,
all i did was put that in the command line
it made a file and i saved it.
is that all i do?
but i think it's fixed.
i haven't been disconnected yet

---

### Post by dstew on 2008-03-21
The file has to contain the line```
blacklist p54usb
```Did you put that line in the file before you saved it?

---

### Post by T2manner on 2008-03-21
i'm not sure.
i don't remember
but about 2minutes ago, for the first time since two days ago, i lost connection twice!

---

### Post by Mazza558 on 2008-03-21
> **T2manner said:**
> i'm not sure.
i don't remember
but about 2minutes ago, for the first time since two days ago, i lost connection twice!

To be honest, this sounds like something wrong with your ISP/Connection rather than Ubuntu itself.

---

### Post by dstew on 2008-03-21
Just look at the /etc/modprobe.d/blacklist file with the text editor:```
gksudo gedit /etc/modprobe.d/blacklist
```If there is nothing in the file, add the line **blacklist p54usb**, save the file, and reboot.

---

### Post by T2manner on 2008-03-21
this is what the file says

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by dstew on 2008-03-21
So, just add the line blacklist p54usb to the end of the file. If you want to, add an explanatory comment like```
#interferes with ndiswrapper
blacklist p54usb
```

---

### Post by T2manner on 2008-03-22
okay thanks

---

