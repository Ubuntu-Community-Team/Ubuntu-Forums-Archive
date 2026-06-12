---
title: "Installing Radeon 9200se drivers"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by chrisbish on 2007-06-30
how do i install the drivers for this graphics card?
as i can't find a guide.
also i get this error come up sometimes which is something do do with an X config.

---

### Post by chrisbish on 2007-06-30
anyone?
i had a look at Envy but the download link dosn't work

---

### Post by miLl3niUm on 2007-06-30
I have the same question and exactly the same driver :D
I searched for 1 week and the only thing I found it's to install a package:
```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by chrisbish on 2007-06-30
oh kool

i keep getting this message about some X server thing then i can't fix it so now i have to do another install :(

---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> oh kool

i keep getting this message about some X server thing then i can't fix it so now i have to do another install :(


Hi and wait you dont need to reinstall the os. You can reconfigure your xorg. After you install the driver you can use this command to see if it is installed
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]

The driver is under the device section and should look something like this

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"

I am on my lapto which has intel graphics but your should say like ati or fglx
You may try the command in the terminal 
[PHP]sudo dpkg-reconfigure -phigh xserver-xorg [/PHP]
also this will reconfigure xorg so you don't have to reinstall.
Hope this helps good luck! :popcorn:

---

### Post by chrisbish on 2007-06-30
ok so when it boot up and get to the X server thing i got through it and it gets to the terminal
i enter the stuff you gave me right? and then i can install the drivers

---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> ok so when it boot up and get to the X server thing i got through it and it gets to the terminal
i enter the stuff you gave me right? and then i can install the drivers

Hi yes if you reboot and you get the x error then get to command line then enter the second command
[PHP]sudo dpkg-reconfigure -phigh xserver-xorg  [/PHP]
 Then you can use the first command  when you are in the desktop via the terminal and see which driver you are using.

---

### Post by chrisbish on 2007-06-30
ok i did it and it came up with a menu and i selected ati
then i turned it off then turned it on again
now it works thanks man

ill post again in a min with my terminal results

---

### Post by chrisbish on 2007-06-30
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Ok what is the out put of 
[PHP]glxinfo [/PHP]
In the terminal to see if you have direct rendering

---

### Post by chrisbish on 2007-06-30
it just logs me out lol

anyway it works now :P
beryl is running fine the desktop cube is pixaly but i can live with that

also my screen size is ginormous now and there art any smaller screen sizes avalible to choose :(

---

### Post by chrisbish on 2007-06-30
i got it to work

> root@chris-desktop:/home/chris# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
root@chris-desktop:/home/chris# 



---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> it just logs me out lol

anyway it works now :P
beryl is running fine the desktop cube is pixaly but i can live with that

also my screen size is ginormous now and there art any smaller screen sizes avalible to choose :(

Ok how is beryl working with no direct rendering (WOW) Ok use the command in terminal
[PHP] gksudo gedit /etc/X11/xorg.conf[/PHP]
And post the put put here and we will look and help with the resolutions!

---

### Post by chrisbish on 2007-06-30
it said direct rendering when i was following a tutorial

anyway i just changed my xorg.conf using a tutorial on ubuntus website

screen is still to big:(

---

### Post by chrisbish on 2007-06-30
there is nothing in that file 
when i use  gksudo gedit /ets/X11/xorg.conf  ???
what should i put in it?

---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> there is nothing in that file 
when i use  gksudo gedit /ets/X11/xorg.conf  ???
what should i put in it?

Man I feel real stupid right now
[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]
I did a typo in the fist command :(

---

### Post by chrisbish on 2007-06-30
ok its come back now strangely

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
        Identifier      "Radeon 9200"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9200"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by overdrank on 2007-06-30
Ok you said that you were using a "how to" to install beryl. Did you edit your xorg before I ask you to because you don't have the info I do in my screen section ( I know  I am using a intel graphics chpset) But look a my screen info.
[HTML]Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection[/HTML]
I believe you should have a similar output.

---

### Post by chrisbish on 2007-06-30
this was the guide i used

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by chrisbish on 2007-06-30
and this one

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by overdrank on 2007-06-30
> **chrisbish said:**
> and this one

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I have sent you a PM (private message)

---

### Post by chrisbish on 2007-06-30
topic solved

---

### Post by TexMex657 on 2007-07-02
would you mind going through and posting exactly what you had to do to get the drivers installed?  I have the same graphics card and was a little confused by what steps you actually went through to get the drivers setup.

Thanks

---

### Post by overdrank on 2007-07-02
> **TexMex657 said:**
> would you mind going through and posting exactly what you had to do to get the drivers installed?  I have the same graphics card and was a little confused by what steps you actually went through to get the drivers setup.

Thanks

HI the last step that worked  was running
[HTML]sudo dpkg-reconfigure -phigh xserver-xorg[/HTML]
In the terminal located under applications,accessories,terminal.
Remember to backup your xorg because making change and crash the x. Good luck :D

---

### Post by TexMex657 on 2007-07-02
So thats it?  It's just a one step process?

---

### Post by overdrank on 2007-07-02
> **TexMex657 said:**
> So thats it?  It's just a one step process?

In that case it was. Sometimes it works and like for me I have to do nothing with that card the drivers ubuntu install are just right. ;)

---

### Post by TexMex657 on 2007-07-02
Yeah no luck.  I got myself to a higher resolution doing that but my graphics are a still a little messed up.  Windows that are supposed to go transparent sometimes turn into weird colors and just trying to watch video files doesn't quite work so well either.

---

### Post by TexMex657 on 2007-07-02
Ok, , ran nthe command without the -phigh tag as in this thread:

[http://ubuntuforums.org/showthread.php?t=482484&highlight=radeon+9200se](http://ubuntuforums.org/showthread.php?t=482484&highlight=radeon+9200se)

> **Codename said:**
> Hey Try reconfiguring your X server.
```
sudo dpkg-reconfigure xserver-xorg
```
This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Cntrl-Alt-F7 to get back to graphical mode and then Cntrl-Alt-Backspace to reset the X server (so your changes can take effect).

and it looks like my video is working a lot better.  Can even watch video files now correctly.  Now my beryl stuff is not functioning properly anymore haha.  Looks like the application is running but I'm not getting any effects or anything anymore.

---

