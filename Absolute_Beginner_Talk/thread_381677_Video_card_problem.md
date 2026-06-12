---
title: "Video card problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by ax-ax on 2007-03-11
I upgraded my nVidia driver for my TNT and its fine, but everything is too much to the left, its a black stripe on the right!

Second problem: UT doesn't work, not native or with wine. if i start it on wine it says:

```
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x33f39c,0x33f398): stub
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e523000 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x34f3bc,0x34f3b8): stub
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x173460) : stub, simulating 64MB for now, returning 64MB left
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x172c78)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
Xlib:  extension "GLX" missing on display ":0.0".
err:d3d:IWineD3DImpl_FillGLCaps    GLX_Extensions returns NULL
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x172c78)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
wine: Critical section 7e523000 wait failed at address 0x7efaddf0 (thread 000d), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) (null)
        0000000d    0
        00000009    0
wine client error:9: write: Bad file descriptor

``` 
whats the problem? what to do? :confused: :confused: :confused:

---

### Post by mrmonday on 2007-03-11
Can you post a screenshot of what you see? It might help.

---

### Post by RomeReactor on 2007-03-11
Hi. What's the output of running

```
glxinfo | grep rendering
```

in the terminal? I'm guessing it has to do direct rendering not being enabled; did you run

```
sudo nvidia-glx-config enable
```

after installing the drivers?

---

### Post by ax-ax on 2007-03-11
If i run  sudo nvidia-glx-config enable
it says:
```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
``` i runned md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum

and on  glxinfo | grep rendering:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

:confused:

---

### Post by RomeReactor on 2007-03-12
In case you haven't solved your card's issue yet, run this in the terminal:

```
gksudo gedit /etc/X11/xorg.conf
```

That will show you the contents of your xorg.conf file. Running **sudo nvidia-glx-config enable** changes the driver from **nv** (no 3d acceleration) to **nvidia** (acceleration enabled), so the driver should read "nvidia" when you scroll down to the "Device" section. If it doesn't, then change it so it looks like this:

```
Section "Device"
        Identifier      "YOUR_NVIDIA_CARD"
        Driver          **"nvidia"**
```

Save the file and reboot; if after rebooting you can't get to your desktop (no graphical interface) and there's only the command line, then run this command:

```
sudo nano /etc/X11/xorg.conf
```

again scroll down to the "Device" section, change the driver back to "nv", pressCTRL+O (to save the file) and CTRL+X (to close nano, the command line text editor); then write

```
sudo reboot
```

and that should bring you back to your desktop (minus the rendering acceleration). That means we'll still have to configure the card further.

---

### Post by ax-ax on 2007-03-12
:confused: 
I've done everything  (except resetting) but it's a even bigger stripe now, if  you change from 75 to 70 or 60Hz , it gets even bigger

---

### Post by RomeReactor on 2007-03-12
Do you have rendering acceleration now? Run

```
glxinfo
```

in the terminal to find out (it should inform you which extensions your card supports, instead of printing error messages). If you still don't have acceleration, let's try this: Open your xorg.conf file again

```
gksudo gedit /etc/X11/xorg.conf
```

go to the "Device" section, and below **BusID** add the following lines

```
Option          "NoLogo"
Option          "RenderAccel" "true"
```

so it looks like this

```
Section "Device"
        Identifier      "NVIDIA Corporation NV40? [Unknown nVidia Card]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel" "true"
```

Note that the **BusID** and **Identifier** in my post are for my card; don't change yours. Now scroll to the end of the page and see if there's an entry like this

```
Section "DRI"
        Mode    0666
EndSection
```

If it's not there, add it also. Now save the file, reboot, and see if the stripe is gone. Note that after enabling 3d acceleration you might still have to fiddle with your monitor's buttons to move the screen to one side so the stripe disappears.

---

### Post by ax-ax on 2007-03-20
Sorry for not answering, but we had some problems here in Sweden.

I tryed, and it works! I can play UT now. :D 

Thanks

---

