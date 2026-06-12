---
title: "ubuntu gutsy ATI FireGL 5250 opengl issues"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kalpax on 2008-01-20
Hi,

I recently installed ubuntu gutsy on my thinkpad T60p which has an ATI FireGL 5250 card. I am having trouble getting opengl applications to run on this setup.

output of fglrxinfo is below...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5250
OpenGL version string: 2.0.6473 (8.37.6)


when i run a simple opengl program (draws two lines), i get...

freeglut (./a.out):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  27
  Current serial number in output stream:  30

Also Applications->Screen and Graphics Preferences->Graphics Card shows
"Graphics card (VESA driver (generic))" with driver = fglrx.

Any ideas?
Thanks for your help,
Shirley.

---

### Post by A4006 on 2008-01-20
I've had problems with the generic drivers that Ubuntu auto-configures.  You might want to try and use Envy to reinstall the ATI drivers.

---

### Post by kalpax on 2008-01-21
I installed Envy (and compiz) and I still get the same GL error. Also the desktop size is now down to  1280 X 1024 and the whole system is super-slow.

---

### Post by softtower on 2008-01-21
Congratulations gentleman, we have the worst video card in the world when it comes to Linux compatibility. After endless hours of experimenting, I only found one version of driver that works fine (albeit without composing effects).

More specifically: 
[LIST]
[*]it hibernates/suspends, 
[*]it runs OpenGL apps hardware-accelerated 
[*]Does not produce any errors in Xorg.0.log file.
[/LIST]
Which version is it? It's the one that comes by default with Ubuntu 7.04 (Feisty), you get by running:
```
sudo aptitude install xorg-driver-fglrx
```

The version is 8.34

This is the main reason why I cannot upgrade to Gutsy, it comes with brain-damaged driver. The latest ATI-published driver (released on Jan 19th) is messed up too - DRI won't start and it fails "acquiring" available video memory. I don't have exact error messages (since I cleared up logs).

---

### Post by kalpax on 2008-01-21
I am really frustrated with the driver situation. Will I have better luck with the ATI drivers on other versions of Linux like Suse or Fedora?

---

### Post by kalpax on 2008-01-22
Just wanted to share the final solution -- Gutsy and the ATI FireGL drivers don't seem to work well together. So I moved back to Feisty Fawn (7.04). The fglrx drivers that come bundled with this version of ubuntu seem to work (no compositing of course). 

I followed exactly the instructions on this website:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60)

INSTRUCTIONS:

**$[B] fglrxinfo**[/B]
(Initially this was some "Mesa"-related output, so reinstall the fglrx driver)
[B]
$ sudo apt-get remove xorg-driver-fglrx fglrx-control
$ sudo apt-get install xorg-driver-fglrx fglrx-control
$ sudo depmod -a[/B]

Logout, and login again. 
Now the command 'fglrxinfo' should print the proper vendor string.

If the error persists and there is no 3D acceleration: 

comment out the line involving 'fglrx' in **/etc/modprobe.d/lrm-video** , then

**$ sudo modprobe -v fglrx**

and restart the X server (control+alt+del). Check that the driver is loaded:
[B]
$ lsmod[/B]
   fglrx                 540004  11
   agpgart                35400  2 fglrx,intel_agp

The driver fglrx should be listed.

**$ fglrxinfo **
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6334 (8.34.8 )

If this error is reported in the Xorg logs (under System / Administration / System Logs):

  (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
  (EE) AIGLX: reverting to software rendering

Turn off AIGLX by adding the following to** /etc/X11/xorg.conf**:
[B]
 Section "ServerFlags"
   Option "AIGLX" "off"
 EndSection[/B]

Remember that **/etc/X11/xorg.conf **should have the Composite option disabled.

[B] Section "Extensions"
   Option      "Composite" "0"
 EndSection[/B]

Finally to test, use 
[B]$ glxgears
$ fgl_glxgears[/B]

I also installed  gltron and tested it out. Things seem to be working. Thanks everyone (especially softtower).

---

