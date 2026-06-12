---
title: "Beryl window manager won't activate?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by DaH-RaT on 2007-08-14
i installed ndiswrapper with the broadcom drivers with python's installer.py , ive had this problem before but forgot the console command does anyone know how to clear beryl's files back to first time default? when i select beryl as my window manager it activates but instantly deactivates back to it's backup manager ( meta ). :(

i think i need to replace my xorg.conf and redo it's sh files.

---

### Post by moffa on 2007-08-14
if you run it from a terminal you can probably see the error

---

### Post by DaH-RaT on 2007-08-15
beryl is running, the menu comes up fine, its just when i select "beryl" for my window manager it switches to it but only for 1 seconda dn switches back to meta city.  it wont let me stay on beryl as my window manager.

i tried some of the commands but im still kinda noobish so i dont know them all but here goes.

beryl-manager --no-force-window-manager just brings up the menu as if i would click on it.

:confused:

laptop
intel centrino 2.49ghz 
1gb ddr2
7800 GTX Go
dell precision|m70

i also tried to do this. 

----------------

dah-rat@chicken-turtle-soup:~$ LD_PRELOAD=/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746 beryl --replace &
[1] 15172
dah-rat@chicken-turtle-soup:~$ ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
**************************************************************
* Beryl system compatibility check                           *
**************************************************************
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

[Warning ]: Relaunching beryl with __GL_YIELD="NOTHING"

ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
**************************************************************
* Beryl system compatibility check                           *
**************************************************************
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/opengl/nvidia/lib/libGL.so.1.0.9746' from LD_PRELOAD cannot be preloaded: ignored.

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

beryl: Failed to load slide: /home/dah-rat/themes/liquid.jpg
beryl: Failed to load slide: /home/dah-rat/themes/liquid.jpg
dah-rat@chicken-turtle-soup:~$

---

### Post by DaH-RaT on 2007-08-15
ok im ready to just reformat. i tried uninstalling beryl and reinstalling it, im still having the same problem.... can anyone help me?

---

### Post by DaH-RaT on 2007-08-15
sorry for the spamming people. but i fixed it. all of you out there that are wanting to uninstall beryl but reinstall with the same proble, uninstall everything you need to install, THEN go to your home folder, hit control+H , delete the .beryl  and .emerald folders . that way the next install of beryl will be with default first time settings. :)

---

