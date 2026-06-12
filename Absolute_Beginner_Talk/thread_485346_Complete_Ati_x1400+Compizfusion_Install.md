---
title: "Complete Ati x1400+Compizfusion Install"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by grabler on 2007-06-26
I just learn this linux thingi, and here's my first tutorial+link of reference, enjoy trying.

Howto install ati driver's+ compizfusion on x1400

Reference:
Ati Driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Compizfusion:
[http://ubuntuforums.org/showthread.php?p=2902636](http://ubuntuforums.org/showthread.php?p=2902636)

*Add Trevino Repo if you want some eye candy:

key:
wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

Add repo to the list:
sudo gedit /etc/apt/sources.list

Add this line at the very end section of the list:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

* Install linux-restricted-modules and restricted-manager provied in the restricted repositories:

sudo apt-get update

sudo apt-get install linux-restricted-modules-generic restricted-manager

*Editing the xorg.conf
sudo gedit /etc/X11/xorg.conf

The Section "Module" should include:

Load "dri"
Load "glx"
Load "vbe"

Section "Device" starts with:
Identifier "ATI Radeon"
Driver "fglrx"
Busid "PCI:6:0:0"

*All the number doesn't have to be the same

At the end section add this:

Section "DRI"
Mode 0666
EndSection
Section "Extensions"
Option "Composite" "0"
EndSection

Install The driver

sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo apt-get install fglrx-control

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

Open System -> Administration -> Restricted Drivers Manager check the box with ati in it and restart.

If you want compiz or compiz fusion as your eyecandy do this:

Add an xgl:

sudo apt-get install xserver-xgl

make a startup script:

sudo gedit /usr/local/bin/startxgl.sh

Add this inside:

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
dbus-launch --exit-with-session gnome-session

Save it and make it executable

sudo chmod a+x /usr/local/bin/startxgl.sh

Make a login session entry to enter xgl so it wont ruin ur usual gnome session:

sudo mkdir -p /etc/X11/sessions

sudo gedit /etc/X11/sessions/xgl.desktop

Add this to it:

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Were Done making the xgl session. do the xserver reset:

ctrl+alt+backspace

it will show the login screen, press option on the bottom left screen and select session>xgl>enter ur username>enter ur password>enter login

welcome to the xgl

To be sure run this script into the terminal:

fglrxinfo

My output is:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

Run 

glxinfo

My output is:

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6334 (8.34.8))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

If the result look like that then we are in the right track...

Installed compizfusion:

sudo aptitude update

sudo aptitude upgrade

sudo aptitude remove compiz-core desktop-effects

sudo aptitude install compiz 

sudo aptitude install compizconfig-settings-manager

sudo aptitude install libcompizconfig-backend-gconf

sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported

That's it, to start compiz run this in the terminal:

compiz --replace

Enjoy..... Jakarta Rule.....:popcorn:

---

### Post by solid0409 on 2007-06-27
[B]hey

when i type   fglrxinfo  i get this [/B]

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

[B]and is correct but then

 when i type glxinfo

instead of getting  this[/B]

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6334 (8.34.)

**i get  this**

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.2)

**do you have any idea why it says Mesa instead of ATI?**


**my entire output is:**

name of display: localhost:1.0
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: localhost:1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.2)
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
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by grabler on 2007-06-28
My friend, have you log into the xgl session, cos i'm sure u didnt... (or maybe i'm wrong)

---

### Post by solid0409 on 2007-06-28
i am logged in into xgl session  and i got compiz fusion install. its working great, but it laggs a little. 
i follow all your directions step by step and everything is working.  i was just wondering why it says mesa instead of ATI. 
 
PS. my shutdown and restart option are not there when i go to 
System ->Quiz.

do you know how i can solve this problem?

---

### Post by keenish27 on 2007-08-02
i followed your instructions and compiz kinda works....like i have wobbly windows and thats about it......i can edit its settings tho

here is my output
name of display: localhost:1.0
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
display: localhost:1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.2)
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
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

any ideas?

oh and i know it says mesa....and i am logged into xgl...

---

### Post by levele304 on 2007-08-26
Hey, I followed your guide and got Compiz-fusion to work.

However, it is still a little screwy.

Rotate Cube works, so I know compiz is running BUT  the Window Edges are not showing (where FIle, Edit, Help, etc menu lists should be on the top of the windows are gone, and also the bottom edges.

I run compiz --replace in terminal and this is the error output I get:
------------------------------------------------------------------------------------------------------------------
compiz --replace
/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
------------------------------------------------------------------------------------------------------------------------

Please help!

---

### Post by okanss on 2007-09-20
Hello,
You can use the orders in [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")
At the First steps part your problem have a solution.

---

