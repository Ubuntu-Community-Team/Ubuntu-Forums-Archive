---
title: "Installing drivers for Radeon 9800 Pro. How to check install?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-05-16
Hi,

I;ve got a Radeon 9800 pro video card and i am trying to ensure i have my drivers from ATI installed properly.

I use the ATI installer just point and click. It said everything worked fine.

I also ran through all of the steps outlined here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.34.8_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_1:_Install_the_8.34.8_Driver_the_Ubuntu_Way)
under Method 2.

when i use fglrxinfo it returns:
> catfish@delta:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


The Xlib line is the problem, and all of the Mesa stuff its saying.
The final post of this thread here: [http://www.linuxquestions.org/questions/showthread.php?t=277294](http://www.linuxquestions.org/questions/showthread.php?t=277294)
Says to use the restricted device manager to enable the ATI driver. I update to Ubuntu 7.04 and did that but it still returns the same as above.

After I installed the driver, Xorg video updating seems a lot faster, and I had more options in screen resolutions to choose from. So I guess the driver is being used by Xorg but how can I verify it is being used and how can I get fglrxinfo to recognize this?

The reason I want to fix it is that Google Earth refuses to run out of software mode until the driver is "installed" and available correctly.

---

### Post by m0rph on 2007-05-16
Have you tried
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri

P.S.

In the console have you tried

fgl_glxgears

---

### Post by Catfish81 on 2007-05-17
yes i did the trouble shooting guides. (made sym link)

the command you gave outputs:
> catfish@delta:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30


same old same old?

---

