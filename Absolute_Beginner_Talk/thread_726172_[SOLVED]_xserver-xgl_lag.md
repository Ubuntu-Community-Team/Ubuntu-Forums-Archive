---
title: "[SOLVED] xserver-xgl lag"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by naits1986 on 2008-03-16
Hello! I just installed ubuntu 7.10 on my laptop, with a ati x1800 mobility card..
But when I try to turn on the desktop effects, it tells me ''desktop effects could not be enabled. 
So i installed xserver-xgl, and changed the xorg.conf from 0 to 1.
But then all boxes etc. started lag.. plz help me fix the desktop effects:)

---

### Post by jan quark on 2008-03-16
do not change the composite extension in the xorg.file to 1 from 0

leave it at 0

during the login in change the session to xclient 

that is what I had to do to enable the effects

you can also install the ccsm manager to tweak the effects

---

### Post by naits1986 on 2008-03-16
Okey, thanx:) But can u tell me a little more spesifeic on how to do it in to logon screen? I'm cind of noob:p

---

### Post by IsawSp4rks on 2008-03-16
Better yet, update to the latest ATI catalyst fglrx driver (8.3), howto here:-

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

- best to do step 2.2 for a guaranteed installation

then follow the steps "3D desktop effects" in the Specific Issues section

and finally remove xserver-xgl via Synaptic as the later ATI fglrx drivers do not need it and it will slow Compiz Fusion.  As a bonus your games will work properly too.

Good Luck.

---

### Post by naits1986 on 2008-03-16
Did all the steps, but the tesktop effects still tell me ''desktop effekts could not be enabled''.. Any other tip? :)

---

### Post by IsawSp4rks on 2008-03-16
open a terminal and type 'compiz' without the quotes

paste its output here.

---

### Post by naits1986 on 2008-03-16
stian@stian-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by IsawSp4rks on 2008-03-16
Are you sure you followed the steps "3D desktop effects" in the Specific Issues section?

because it's reporting that it can't find your fglrx driver as whitelisted.

Also, it looks like the driver isn't installed correctly, or your xorg.conf has extra settings that are confusing the driver/compiz fusion

this is what the output should like similar to on your machine if fglrx is properly installed:-

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

your PCI ID will be different as I'm using an x1600 Mobility.  Also your resolution may be different. Finally, I use Emerald as my Window Decorator.

---

### Post by naits1986 on 2008-03-16
I told it to skip the test instead because i could not understand the other method.. But i'll give it a shot:)

---

### Post by naits1986 on 2008-03-17
:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7102 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:6684): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension

Does anyine know how to fix all this?? :)

---

### Post by naits1986 on 2008-03-20
I installed ubuntu over and followed the instructions, then it worked. Thnx:)

---

