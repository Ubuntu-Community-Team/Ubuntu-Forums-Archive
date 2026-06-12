---
title: "Problems installing the Ati driver"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Diversion on 2007-04-30
I am currently running Edgy and am trying to install the ati display driver for my X1600 Mobility Radeon.

When I made the .run file executable and I try to run it, I get the following message:
" you need to run this installer as superuser" 


how do I bypass this?

thnx in advance,

Colin

---

### Post by freebird54 on 2007-04-30
Put **sudo** in front of the command.

---

### Post by Diversion on 2007-04-30
thanks, that did the trick :)

only problem now is that i can't get the resolution up to 1280x800 which is supported by my graphical card.
I'm beginning to doubt if the installation of the driver went accordingly. Is there a way to check if it went right?

---

### Post by freebird54 on 2007-04-30
Open a terminal and type :
```

fglrxinfo
```

if that appears to work - try 

```
fgl_glxgears
```

to see how it does :)  If you post the output here, I'll let you know if anything went wrong...

---

### Post by Diversion on 2007-04-30
colin@laptopcolin:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


colin@laptopcolin:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30


I have no idea what it states, but I'm guesing the installation went wrong ;)

---

### Post by freebird54 on 2007-04-30
Yeah - should have been closer to:
```

freebird@roost:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)

freebird@roost:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1566 frames in 5.0 seconds = 313.200 FPS
1754 frames in 5.0 seconds = 350.800 FPS
```

with probably better performance (my card was cheap)

OK - here are a couple of  things to check first.

Make sure there is a section in the file /etc/X11/xorg.conf like this:

```

Section "Device"
        Identifier  "ATI Radeon 9550"
[B]        Driver      "fglrx"
        Option      "UseFBDev" "true"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"[/B]
        BusID       "PCI:1:0:0"
EndSection
```

You are looking for the driver being fglrx, and the bolded options added.

You can check/change this by first creating backup:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_070430
```

and then editing with
```

gksudo gedit /etc/X11/xorg.conf
```

This file is the control file for lots of things - including available resolutions, vido drivers, mouse recognition etcm by the way  :)

Let me know - I have 20 mins more at the moment...

---

### Post by Diversion on 2007-04-30
nevermind, forgot to scroll down..
this is in the file:

Section "Device"
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"

---

### Post by freebird54 on 2007-04-30
OK - you made the backup, right?  Change out the 'vesa' line with the other bolded ones, and retry.  If it messes up,  boot to recovery, and:

```
sudo cp /etc/X11/xorg.conf.backup_070430 /etc/X11/xorg.conf
```

to return to where you are now...

---

### Post by Diversion on 2007-04-30
I'm off now so will be trying this tonight,
Thanks again for the help, It has been greatly appreciated!

---

### Post by freebird54 on 2007-04-30
OK - there are lots more similar problems being solved here.  Try the Search This Forum on the top right when you come in, and browse through for more 'ATI problems' or similar to find more.  That should get you going..  I'm off too!

---

### Post by Diversion on 2007-05-01
Tried it and it worked like a charm after the reboot!
thanks for the help!

---

