---
title: "Nvidia NO direct rendering"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by heathguy on 2007-03-11
I cannot get Direct Rendering with my Nvidia Card. 

I followed the steps at this site to setup my Nvidia Driver:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)       (method 2)

But when i run glxinfo | grep direct   it says direct rendering NO

What am I missing?

glxinfo shows this:
```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7800 GT/PCI/SSE2/3DNOW!
OpenGL version string: 1.2 (2.1.0 NVIDIA 97.55)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_IBM_texture_mirrored_repeat, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 1701667175 796029813 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 892549937 809330281 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 774519349 859517232 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 809329783 2016291386 Ncon

```

---

### Post by PaulFXH on 2007-03-11
> What am I missing?
Almost certainly the 3d accelerator driver for your card.
Use Alberto Milone's Envy script to get the correct driver.

---

### Post by heathguy on 2007-03-11
Isnt that the driver I download straight from Nvidia site: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by heathguy on 2007-03-11
I just saw this and thought it was weird:

```

$ nvidia-settings 

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.
$

```

---

### Post by PaulFXH on 2007-03-11
Unfortunately, I'm a very long way from my Ubuntu machine right now so I can't check anything for you.
However, installation of the correct driver may also require that appropriate adjustments are made to your /etc/X11/xorg.conf file.
The Envy script will choose and install the correct driver as well as updating your xorg.conf file.
I would suggest you try this before embarking on any more elaborate fix.

---

### Post by heathguy on 2007-03-11
I just downloaded and ran the program Envy

Still no luck my glxinfo looks the same

```

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7800 GT/PCI/SSE2/3DNOW!
OpenGL version string: 1.2 (2.1.0 NVIDIA 97.55)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_program, 
    GL_ARB_fragment_program, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_ATI_texture_mirror_once, GL_IBM_texture_mirrored_repeat, 
    GL_NV_blend_square, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 1701667175 796029813 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 892549937 809330281 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0 774519349 859517232 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0 809329783 2016291386 Ncon

```

Thanks for the continued help paul but I'm STUCK!

---

### Post by heathguy on 2007-03-11
Anyone with any suggestions? I've searched though the forums but still no luck as to how to solve this problem.

---

### Post by Bachstelze on 2007-03-11
First, are you sure your nvidia drivers are installed correctly ? Try

```
glxgears --printfps
```

and tell me what you get.

---

### Post by heathguy on 2007-03-11
```

$ glxgears -printfps
12773 frames in 5.0 seconds = 2554.032 FPS
14370 frames in 5.0 seconds = 2854.596 FPS
17100 frames in 5.0 seconds = 3406.126 FPS
17070 frames in 5.0 seconds = 3398.963 FPS
16188 frames in 5.0 seconds = 3221.623 FPS

```

When i do nvidia-settings I get the nvidia settings box but NO options except the configuration i.e. enable tool tips, display status then help/quit

Shouldn't this show many different Nvidia configuration options? this is why i think something is messed up. Also look above at an earlier post of my output from running nvidia-settings

Thanks for replying

edit: i have a nvidia 7800 gtx so i would expect huge results for rendering 3 moving gears :)

---

### Post by Bachstelze on 2007-03-11
Yep, that's indeed a bit low results for such a high end card - I get about 6000 fps on my Go 7600... How did you install your drivers ? Also, please paste your xorg.conf.

---

### Post by heathguy on 2007-03-11
I looked at these 2 sites:

[ [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy ]( [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy )
[ http://www.albertomilone.com/nvidia_scripts1.html ]( http://www.albertomilone.com/nvidia_scripts1.html )

XORG:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL 2005FPW"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"

#    Option         "TripleBuffer" "true"
#    Option         "RenderAccel" "true"
#    Option         "AllowGLXWithComposite" "true"
#    Option         "AddARGBGLXVisuals" "true"
#    Option         "DisableGLXRootClipping" "true"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL 2005FPW"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by Patrick K on 2007-03-11
> Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
Try addind this line underneath the Driver line.
>     BusID	   "PCI:1:0:0"

My card didn't work right without it. My is an AGP card. if your's is PCIe, I don't know about that.

---

### Post by Bachstelze on 2007-03-11
Try to uncoment this line :

#    Option         "RenderAccel" "true"

(i.e. remove the #)

Just as an example, here's mine :

```

Section "ServerLayout"
        Identifier      "X.org Configured"
        Screen  0       "Screen0"       0       0
        InputDevice     "Mouse"
        InputDevice     "Keyboard"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Files"
        RgbPath         "/usr/share/X11/rgb"
        ModulePath      "/usr/lib/xorg/modules"
        FontPath        "/usr/share/fonts/misc/"
        FontPath        "/usr/share/fonts/TTF/"
        FontPath        "/usr/share/fonts/OTF"
        FontPath        "/usr/share/fonts/Type1/"
        FontPath        "/usr/share/fonts/CID/"
        FontPath        "/usr/share/fonts/100dpi/"
        FontPath        "/usr/share/fonts/75dpi/"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbLayout"     "fr"
        Option          "XkbModel"      "pc105"
        Option          "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
        Identifier      "Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "ImPS/2"
        Option          "Device"                "/dev/input/mouse1"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection


Section "Monitor"
        Identifier      "Monitor0"
        HorizSync       28.0 - 64.0
        VertRefresh     43.0 - 60.0
        Option  "DPMS"
EndSection

Section "Device"
        Identifier      "Card0"
        Driver          "nvidia"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

```

---

### Post by Patrick K on 2007-03-11
I just noticed this:

> Section "Extensions"
    Option         "Composite" "Enable"
EndSectio

Try disabling it. Change it to this:
> Section "Extensions"
    Option         "Composite" "Disable"
EndSection
Other have reported needing to do this.

---

### Post by heathguy on 2007-03-11
Thanks for the replies BUT....

I tried those fixes to my xorg.conf and then did a gdm stop and restart but still my Direct Rendering is "NO"

:/

---

### Post by Bachstelze on 2007-03-11
In the Modules section, add a line to load the "dri" module.

---

### Post by heathguy on 2007-03-11
Thanks for sticking with me guys..

Hymn...I added that "Load dri" and restarted gdm but still no direct rendering?

Also this is kind of strange:

[IMG]http://69.145.95.171/nvidiasettingscreen.png[/IMG]


*i hope you can view the image*

---

### Post by Bachstelze on 2007-03-11
Can't help you further, I'm afraid. There might be something additional to tweak for the Ubuntu drivers, I don't know... I always use the drivers from nvidia :p

---

### Post by Patrick K on 2007-03-11
That's exactly what my nvidia dialog looked like before installing the nvidia drivers. The first time I installed the drivers I had to install them a three times before they "took". Yet, it looks like you have them installed. Very strange. I wonder if there isn't something wrong with the card.

I'd suggest PMing tseliot. He seems to be the resident expert on these matters. Just point him to this thread rather than repeating it. [http://www.ubuntuforums.org/member.php?u=19388](http://www.ubuntuforums.org/member.php?u=19388)

---

### Post by Erlander on 2007-03-11
My settings screen looked like that too after the first run of Envy.

I ran it again and got the full set of screens.

Even so I still had to manually enter the full range of resolutions into xorg.conf.

I'd run Envy at least once more.

Rob

---

### Post by heathguy on 2007-03-12
I checked my sources.list file and apparently I had copied over the sources list from some site I had copied the dapper souces list and had been updating with that (for atleast a day now)!?!? I caught this about an hour or so ago and have changed to edgy sources list.

I have since ran apt-get update and upgrade.. are there any others i should run to flush out any dapper version files?

Erlander - I ran Envy just now and still no luck. NO direct rendering ?! bah I am so tired and annoyed and angry and frustrated.

More comments/suggestions are appreciated. Thanks to those that have helped thus far.

---

### Post by alienexplorers on 2007-03-12
I followed the directions in the NVIDIA Forums:

Debian GNU/Linux or Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

If you require further assistance after following the instructions above, please see:

To download and install the drivers, follow the steps below:

STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File

Download (Right click and select "Save Target/Link As..." and save the driver to a local directory)
NVIDIA-Linux-x86-1.0-9755-pkg1.run

SuSE users: please read the SuSE NVIDIA Installer HOWTO before downloading the driver.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-1.0-9755-pkg1.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

If you have any questions or problems, please check the linux discussion forum. If you don't find an answer to your question there, you can send email (in English) to [email]linux-bugs@nvidia.com[/email].

When emailing [email]linux-bugs@nvidia.com[/email], please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh". 

Since following these directions I gained Direct Rendering and all the options in the Nvidia-settings program.

---

### Post by heathguy on 2007-03-12
alien: no go on the direct route :/ still no direct rendering....i wish i knew what caused this... I DID have direct rendering at one point.. pre beryl / compiz ... i uninstalled both of them... I hope that would not have affected my video driver settings......

---

### Post by noarc on 2008-05-07
Just wanted to say I have the same problem, with a 6600 Go.

Here's something interesting, though.

Try:

$ glxgears -display :0.0
$ glxinfo -display :0.0

Do you get direct rendering? I do with :0.0. Question: how can I make this work on the default display?

---

### Post by Erlander on 2008-05-08
I have had trouble loading the NVidia drivers on a system with an AMD 3200+ cpu, 512 Mb memory and an AGP 7600GS.

I have updated my other system and moved the 1 Gb of memory from it to the machine in question.  With 1.5 Gb memory the NVidia drivers load well and all is well.  This was with Ubuntu 7.10 and 8.04.

Rob

---

