---
title: "Compiz &amp; Radeon 7500 issues."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by lnlds on 2008-02-03
I just installed Ubuntu on my t42, and everything works flawlessly :) however, i've had trouble getting compiz to work. I followed this guide [http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200) but it still does not work. I'm hesitant to install anything as i was reading about how some fxgl files are difficult to remove and every newbie needs his/her hand held until he/she gets comfortable. After searching a lot of threads talk about the xorg file? and I don't know how to edit it yet
edit: i have a radeon 7500 32mb

Anyways this is my compiz terminal printout.

compiz
andy@andy-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c57 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity

---

### Post by chewit on 2008-02-03
Compiz worked fine for me. But I didn't try out the cube thing, the standard compiz worked fine (shadows on windows, wobberly windows). I have a slow card, ATi Radeon 7000, but mine is the 64mb model

---

### Post by lnlds on 2008-02-03
how did you get it to work?

---

### Post by lnlds on 2008-02-03
ugh so dumb...I lowered the resolution to 1024 and it worked flawlessly

---

### Post by chewit on 2008-02-03
lol, yeh my resoultion is at 1024 x 768, but i don't use compiz. Slows my PC down abit. I prefer to have a fast PC than a one with fancy stuff.

---

### Post by EdGato on 2008-04-30
Got a 7500 PCI. Tried the stuff here. Still can't configure it. I'm too afraid to install xgl :( What's the worst that can happen if I do that?

> ... -desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:0b.0 0300: 1002:5157 (prog-if 00 [VGA controller])
01:00.0 0300: 1039:6330 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (800x600) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (colorfilter) - Fatal: Fragment program support missing.
/usr/bin/compiz.real (mag) - Warn: GL_ARB_fragment_program not supported. Fisheye mode will not work.
(no debugging symbols found)
Attaching to program: /usr/bin/compiz.real, process 7313
Reading symbols from /usr/lib/libX11-xcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11-xcb.so.1
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libxcb.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb.so.1
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /usr/lib/libxcb-xlib.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-xlib.so.0
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/libXrender.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xb7aef6b0 (LWP 7313)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libini.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libbench.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libbench.so
Reading symbols from /usr/lib/compiz/libmove.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libwidget.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwidget.so
Reading symbols from /usr/lib/compiz/libput.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libmblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libmaximumize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmaximumize.so
Reading symbols from /usr/lib/compiz/libannotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libannotate.so
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libpixman-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpixman-1.so.0
Reading symbols from /usr/lib/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libsession.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsession.so
Reading symbols from /usr/lib/compiz/libglib.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/libglib-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpcre.so.3
Reading symbols from /lib/libselinux.so.1...
(no debugging symbols found)...done.
Loaded symbols for /lib/libselinux.so.1
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/compiz/libextrawm.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libwater.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwater.so
Reading symbols from /usr/lib/compiz/libwinrules.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwinrules.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libinotify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libzoom.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libsplash.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsplash.so
Reading symbols from /usr/lib/compiz/libsvg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgsf-1.so.114...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgio-2.0.so.0
Reading symbols from /lib/libbz2.so.1.0...
(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libfadedesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfadedesktop.so
Reading symbols from /usr/lib/compiz/libscreenshot.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscreenshot.so
Reading symbols from /usr/lib/compiz/libclone.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libclone.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libshelf.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshelf.so
Reading symbols from /usr/lib/compiz/libtext.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/compiz/libshift.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libring.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libring.so
Reading symbols from /usr/lib/compiz/libblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libblur.so
Reading symbols from /usr/lib/libGLU.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/compiz/libloginout.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libloginout.so
Reading symbols from /usr/lib/compiz/libvideo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/libbs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libbs.so
Reading symbols from /usr/lib/compiz/libwobbly.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libfade.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libopacify.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopacify.so
Reading symbols from /usr/lib/compiz/libreflex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libreflex.so
Reading symbols from /usr/lib/compiz/libcolorfilter.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcolorfilter.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/libtrailfocus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libtrailfocus.so
Reading symbols from /usr/lib/compiz/libmag.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmag.so
Reading symbols from /usr/lib/compiz/libaddhelper.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libaddhelper.so
Reading symbols from /usr/lib/compiz/lib3d.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/lib3d.so
Reading symbols from /usr/lib/compiz/libgears.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgears.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libgroup.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /usr/lib/compiz/libcubereflex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcubereflex.so
Reading symbols from /usr/lib/compiz/libcubecaps.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcubecaps.so
Reading symbols from /usr/lib/compiz/libshowmouse.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowmouse.so
Reading symbols from /usr/lib/compiz/libexpo.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libezoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libscale.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libswitcher.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libscalefilter.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscalefilter.so

(no debugging symbols found)
0xb7fd5410 in __kernel_vsyscall Undefined command: "-e".  Try "help".
()
(gdb) (gdb) 
Thread 1 (Thread 0xb7aef6b0 (LWP 7313)):
#0  0xb7fd5410 in __kernel_vsyscall ()
#1  0xb7b8b5fa in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb759cc4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  0xbf85c458 in ?? ()
#4  0x00000400 in ?? ()
#5  0xb759cd9c in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbf85f83b in ?? ()
#7  0x00001c91 in ?? ()
#8  0x082e53a8 in ?? ()
#9  0x00001c91 in ?? ()
#10 0x082e53a8 in ?? ()
#11 0x00001c91 in ?? ()
#12 0x00001c91 in ?? ()
#13 0x082e53a8 in ?? ()
#14 0xb7bbaf83 in _IO_default_xsputn () from /lib/tls/i686/cmov/libc.so.6
#15 <signal handler called>
#16 0xb732d670 in ?? () from /usr/lib/compiz/libcolorfilter.so
#17 0x08de0468 in ?? ()
#18 0x08de0468 in ?? ()
#19 0xbf85cb88 in ?? ()
#20 0xb732f284 in ?? () from /usr/lib/compiz/libcolorfilter.so
#21 0x0807a960 in ?? ()
#22 0x0893e218 in ?? ()
#23 0xbf85cb88 in ?? ()
#24 0xb732cd3f in ?? () from /usr/lib/compiz/libcolorfilter.so
#25 0x080c1c90 in ?? ()
#26 0x08de0468 in ?? ()
#27 0x08de0468 in ?? ()
#28 0x08de0468 in ?? ()
#29 0x08ddfe00 in ?? ()
#30 0x080c1c90 in ?? ()
#31 0xbf85cbe8 in ?? ()
#32 0x08067815 in addWindow ()
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
#0  0xb7fd5410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xb7fd5410 in __kernel_vsyscall ()
#1  0xb7b8b5fa in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb759cc4c in ?? () from /usr/lib/compiz/libcrashhandler.so
#3  0xbf85c458 in ?? ()
#4  0x00000400 in ?? ()
#5  0xb759cd9c in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbf85f83b in ?? ()
#7  0x00001c91 in ?? ()
#8  0x082e53a8 in ?? ()
#9  0x00001c91 in ?? ()
#10 0x082e53a8 in ?? ()
#11 0x00001c91 in ?? ()
#12 0x00001c91 in ?? ()
#13 0x082e53a8 in ?? ()
#14 0xb7bbaf83 in _IO_default_xsputn () from /lib/tls/i686/cmov/libc.so.6
#15 <signal handler called>
#16 0xb732d670 in ?? () from /usr/lib/compiz/libcolorfilter.so
#17 0x08de0468 in ?? ()
#18 0x08de0468 in ?? ()
#19 0xbf85cb88 in ?? ()
#20 0xb732f284 in ?? () from /usr/lib/compiz/libcolorfilter.so
#21 0x0807a960 in ?? ()
#22 0x0893e218 in ?? ()
#23 0xbf85cb88 in ?? ()
#24 0xb732cd3f in ?? () from /usr/lib/compiz/libcolorfilter.so
#25 0x080c1c90 in ?? ()
#26 0x08de0468 in ?? ()
#27 0x08de0468 in ?? ()
#28 0x08de0468 in ?? ()
#29 0x08ddfe00 in ?? ()
#30 0x080c1c90 in ?? ()
#31 0xbf85cbe8 in ?? ()
#32 0x08067815 in addWindow ()
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 7313

[CRASH_HANDLER]: "/tmp/compiz_crash-7313.out" created!



---

