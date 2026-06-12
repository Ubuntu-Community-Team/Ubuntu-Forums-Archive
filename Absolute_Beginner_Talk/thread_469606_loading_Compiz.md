---
title: "loading Compiz"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-10
Hello!
I have installed Compiz and all the other things it needs but now when I try and start compiz from terminal I get this error message:

/usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

also when I run compiz-tray-icon I get this:

(compiz-tray-icon:6014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6014): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:6014): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:6014): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


I am not sure what to do!

---

### Post by viciouslime on 2007-06-10
Which version of ubuntu are you using, because if you use feisty this can all be done automatically for you... If not you need to edit your xorg.conf, presuming you have a nvidia card, Type "sudo gedit /etc/X11/xorg.conf" in a terminal. Then scroll down until you find a section like below:

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7800 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
EndSection


The two lines:

	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"

Won't be there, add them and that should solve your problem :)

REMEMBER this is assuming you're using a nvidia card and a version of ubuntu below feisty! If you are using feisty, this method will still work, but you don't have to do it, as using the restricted drivers manager and then desktop effects to enable compiz, will sort all that out for you.

---

### Post by matteospqr on 2007-06-10
I am using Fesity and I have an ATI video card! What should I do?

---

### Post by matteospqr on 2007-06-10
I added the two lines in the xorg.conf file in the device section but I still get the same error.  The restricted drivers are enabled aswell!

:(

---

