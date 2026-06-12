---
title: "Obtaining reverse video by hotkey Win+n"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by A. Situs on 2008-04-15
Hello Community,

When I first installed Ubuntu 7.10 and when I run off a live CD, I was able to obtain reverse video in the current window by hitting the Windows (aka Super_L or <mod4>) key in conjunction with the "n" key. (Also Win+m would reverse video in all windows and Win+e would show all workspaces.) Now, that was on my Dell Inspiron 1150 laptop. On a friend's Dell laptop (not sure of the model), these shortcuts weren't available. These shortcuts no longer work for me either.

So my main question is: what was this shortcut (Win+n) doing? That is, is there a "long way" to get this reverse video?

Another question: What could I have done to destroy this shortcut? I noticed that it stopped working after I install xrandr to use a second monitor. In doing so I changed my xorg.cong file, but I don't think this is the cause of my problem.


```


brad@brad-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

---

### Post by prshah on 2008-04-15
> **A. Situs said:**
> Hello Community,
(Also Win+m would reverse video in all windows and Win+e would show all workspaces.)
So my main question is: what was this shortcut (Win+n) doing? That is, is there a "long way" to get this reverse video?

Another question: What could I have done to destroy this shortcut? I noticed that it stopped 

These are features of Compiz; You can enable it by starting compiz. Alt+F2, then ```
compiz --replace
```.

If something goes wrong (blank screen, white screen, unpredicatable screen), Press Ctrl+Alt+F1, login in, give the command ```
metacity --replace
``` and switch back with Ctrl+Alt+F7

Note that Compiz may not work with your video card "out of the box" but if you run into problems, you can sure get it going by posting or reading these forums.

---

### Post by A. Situs on 2008-04-16
Thanks for your prompt response, prshah.

Are you saying that Compiz could replace my broken feature, or Compiz is what is broken on my computer? 

I tried your suggestions.  The first caused my screen to flash to the desktop then restored the windows.  Other than that, it was uneventful.  The second caused an error about not being able to open X display. 

I will probably just reinstall my OS to fix this; so I'm not too concerned with fixes.  I just want to know what went wrong.

--Brad

---

### Post by prshah on 2008-04-16
> **A. Situs said:**
> Thanks for your prompt response, prshah.

Are you saying that Compiz could replace my broken feature, or Compiz is what is broken on my computer? 


Compiz provides the features that you want. I'm guessing it is not running on your computer.

> 
I tried your suggestions.  The first caused my screen to flash to the desktop then restored the windows.  Other than that, it was uneventful.  The second caused an error about not being able to open X display. 

When the windows were "restored", it means that compiz was started successfully. Did you then try the Win+N, etc shortcuts?

The second command was only if your screen display disappered, or went garbled etc. In this case, it didn't. So there is/was no need for the second "metacity" command, which, in fact, _disables_ compiz. 

Summary: Try the first command again, then try your Win+N etc shortcuts, then post back results (or lack thereof).

---

### Post by A. Situs on 2008-04-17
Sorry about not being explicit. By "uneventful", I meant I found no change in my system including the fact that "Win+n" still doesn't work.  Are you sure that it was Compiz providing this feature?

--Brad

---

### Post by prshah on 2008-04-17
> **A. Situs said:**
> Sorry about not being explicit. By "uneventful", I meant I found no change in my system including the fact that "Win+n" still doesn't work.  Are you sure that it was Compiz providing this feature?

--Brad

Yep. (See attached screenshots)

Maybe you need to install CCSM (Compiz Config Settings Manager). Check if you have it in System->Preferences->Advanced Desktop Effects Settings.

If you dont, a simple ```
sudo apt-get install compizconfig-settings-manager
``` will fetch it for you.

---

### Post by A. Situs on 2008-04-18
OK,

I'm looking at my CCSM. I have the Negative option enabled. I even tried changing the key combination that triggered the effect. It just refuses to work. 

However, now that I have CCSM installed, the command from your first reply gives more interesting feedback...

```
brad@brad-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
 
```

I guess I need to find out more about Xgl?

--Brad

---

### Post by prshah on 2008-04-18
> **A. Situs said:**
> OK,

I'm looking at my CCSM. I have the Negative option enabled. I even tried changing the key combination that triggered the effect. It just refuses to work. 

```
brad@brad-laptop:~$ compiz --replace
aborting and using fallback: /usr/bin/metacity 
 
```
--Brad

Enabling the negative option is of no use if Compiz is not starting up, and seeing the fallback message means that it is not.

I see that you are running an (onboard) intel graphics card. Can you post the result of ```
glxinfo | grep direct
```. If it returns a "yes" to direct rendering, then I'm tapped out.

If it returns, "No", the output of the command ```
LIBGL_DEBUG=verbose glxinfo
``` will help solve the reason why direct rendering is not working, which will in turn probably be why Compiz is not working.

---

### Post by A. Situs on 2008-04-18
Good news for your first request.

```
brad@brad-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Here is what the next command does:

```
brad@brad-laptop:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x4a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

``` 

Could it be that xrandr and Compiz are incompatible in some sense?  I'm thinking about uninstalling xrandr and seeing how it goes.

--Brad

---

### Post by prshah on 2008-04-19
> **A. Situs said:**
> 
```
brad@brad-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```


There seem to be a lot of differences between your glxinfo and mine. I'm also running an Intel onboard video, different chipset, but I think we _should_ be running the same driver.

> 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
Mine```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

I think maybe you are using an older driver.

Also something strange:
> 
client glx vendor string: ATI
client glx version string: 1.3
Mine```

client glx vendor string: SGI
client glx version string: 1.4

```

Why ATI when you DONT have an ATI graphics card?

In any case, please post output of ```
cat /etc/X11/xorg.conf | grep -i driver
sudo apt-get -s install xserver-xorg-video-intel 
```

Note that the second command (apt-get) is "-s" meaning it is in simulation mode, it will not actually install anything.

I hope something final comes out of all this investigation; who would've thought that a simple two-keypress combo would lead to all this.

Why do you think xrandr is responsible? Curious...

---

### Post by A. Situs on 2008-04-22
Again, thank you for the prompt responses. Sorry I was away all weekend and Monday.

Here are the results of the commands:
```
brad@brad-laptop:~$ cat /etc/X11/xorg.conf | grep -i driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "intel"

```

and 

```
brad@brad-laptop:~$ sudo apt-get -s install xserver-xorg-video-intel
[sudo] password for brad:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.

```


The reason that I think xrandr might be to blame is that it was the last thing I installed before a noticed my shortcut not functioning, and I far as I know, it is the only thing I've done that would affect my display, except for playing with my xorg.conf file to get xrandr working.

You are correct about my computer being old. I got it about 3.5 years ago and haven't changed any of the hardware. But, I know that my hardware can, in principle, support this feature.

--Brad

P.S. Here is my entire xorg.conf file in case it helps:

 ```
brad@brad-laptop:~$ cat /etc/X11/xorg.conf 
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
       SubSection "Display"
           Depth                24
           Modes                "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
           # ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           Virtual              2048 2048 
       EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```

---

