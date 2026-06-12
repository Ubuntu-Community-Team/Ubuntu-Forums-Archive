---
title: "[SOLVED] Self-compiled Compiz Fusion crashes..."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2008-01-05
Hello all,

I compiled Compiz Fusion 0.6.2 myself because I was forced to stay on Feisty. I used a guide that was made for Gutsy, but I'm pretty sure it works fine with Feisty (I did compile and install correctly and 90% of the time CF works beautifully) One minor problem...Sometimes I get these random crashes...I posted the output file. I was hoping someone could shed some light on this!

here's the guide I used: [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html]("http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html")

```
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz, process 22154
Reading symbols from /usr/lib/libXcomposite.so.1...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libSM.so.6...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXxf86vm.so.1...done.
Loaded symbols for /usr/lib/libXxf86vm.so.1
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...done.
[Thread debugging using libthread_db enabled]
[New Thread -1213933888 (LWP 22154)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libdrm.so.2...done.
Loaded symbols for /usr/lib/libdrm.so.2
Reading symbols from /lib/ld-linux.so.2...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/libXcursor.so.1...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/compiz/libccp.so...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libini.so...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libfirepaint.so...done.
Loaded symbols for /usr/lib/compiz/libfirepaint.so
Reading symbols from /usr/lib/compiz/libpng.so...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libshowdesktop.so...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libresize.so...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libplace.so...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/libglib-2.0.so.0...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /usr/lib/compiz/libmove.so...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libthumbnail.so...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libswitcher.so...done.
Loaded symbols for /usr/lib/compiz/libswitcher.so
Reading symbols from /usr/lib/compiz/libdecoration.so...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libexpo.so...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/libGLU.so.1...done.
Loaded symbols for /usr/lib/libGLU.so.1
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /usr/lib/compiz/libsvg.so...done.
Loaded symbols for /usr/lib/compiz/libsvg.so
Reading symbols from /usr/lib/libcairo.so.2...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libfreetype.so.6...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libfontconfig.so.1...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libgsf-1.so.114...done.
Loaded symbols for /usr/lib/libgsf-1.so.114
Reading symbols from /usr/lib/libcroco-0.6.so.3...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/compiz/libcrashhandler.so...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libput.so...done.
Loaded symbols for /usr/lib/compiz/libput.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libshift.so...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libvideo.so...done.
Loaded symbols for /usr/lib/compiz/libvideo.so
Reading symbols from /usr/lib/compiz/libezoom.so...done.
Loaded symbols for /usr/lib/compiz/libezoom.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libneg.so...done.
Loaded symbols for /usr/lib/compiz/libneg.so
Reading symbols from /usr/lib/compiz/libtext.so...done.
Loaded symbols for /usr/lib/compiz/libtext.so
Reading symbols from /usr/lib/compiz/libwall.so...done.
Loaded symbols for /usr/lib/compiz/libwall.so
Reading symbols from /usr/lib/compiz/libwobbly.so...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libanimation.so...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/libfade.so...done.
Loaded symbols for /usr/lib/compiz/libfade.so
Reading symbols from /usr/lib/compiz/libtrailfocus.so...done.
Loaded symbols for /usr/lib/compiz/libtrailfocus.so
Reading symbols from /usr/lib/compiz/libscale.so...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libscaleaddon.so...done.
Loaded symbols for /usr/lib/compiz/libscaleaddon.so
Reading symbols from /usr/lib/compiz/libgroup.so...done.
Loaded symbols for /usr/lib/compiz/libgroup.so
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/pango/1.6.0/modules/pango-basic-fc.so...done.
Loaded symbols for /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1213933888 (LWP 22154)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c2c6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7bd3a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb78e9972 in crash_handler (sig=11) at crashhandler.c:57
	count = 1
#4  <signal handler called>
#5  0xb74509ba in fxAirplane3DLinearAnimStepPolygon (w=0x816add8, 
    p=0x89acd30, forwardProgress=0) at airplane3d.c:775
	as = <value optimized out>
	aw = (AnimWindow *) 0x8628618
	airplanePathLength = 1
	airplaneFly2TaskBar = 1
	aep = (AirplaneEffectParameters *) 0x0
#6  0xb745ad0f in polygonsAnimStep (s=0x8157310, w=0x816add8, time=8)
    at polygon.c:1484
	i = 0
	aw = (AnimWindow *) 0x8628618
	forwardProgress = 0
#7  0xb745077f in fxAirplane3DAnimStep (s=0x8157310, w=0x816add8, time=8)
    at airplane3d.c:963
No locals.
#8  0xb744da14 in animPreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at animation.c:2152
	i = 0
	aw = (AnimWindow *) 0x8628618
	animStillInProgress = 0
	w = (CompWindow *) 0x0
	as = (AnimScreen *) 0x85c28b8
#9  0xb743bd50 in fadePreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at fade.c:181
	w = <value optimized out>
	steps = 2621
	fs = (FadeScreen *) 0x863d898
#10 0xb742cc80 in scalePreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at scale.c:922
	sw = <value optimized out>
	w = (CompWindow *) 0x8157310
	steps = 134750576
	amount = 0
	chunk = 4.51079794e-34
	ss = (ScaleScreen *) 0x87a4190
#11 0xb7415321 in groupPreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at paint.c:938
	group = <value optimized out>
	gs = (GroupScreen *) 0x866cac0
#12 0x08055379 in eventLoop () at display.c:1685
	pBox = <value optimized out>
	nBox = 1
	y = <value optimized out>
	event = {type = 117, xany = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880}, xkey = {
    type = 117, serial = 1208863, send_event = 0, display = 0x8082170, 
    window = 25165880, root = 54526664, subwindow = 0, time = 0, x = 4001509, 
    y = 406, x_root = 8126530, y_root = 44302450, state = 8127515, 
    keycode = 3, same_screen = 1}, xbutton = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, root = 54526664, 
    subwindow = 0, time = 0, x = 4001509, y = 406, x_root = 8126530, 
    y_root = 44302450, state = 8127515, button = 3, same_screen = 1}, 
  xmotion = {type = 117, serial = 1208863, send_event = 0, 
    display = 0x8082170, window = 25165880, root = 54526664, subwindow = 0, 
    time = 0, x = 4001509, y = 406, x_root = 8126530, y_root = 44302450, 
    state = 8127515, is_hint = 3 '\003', same_screen = 1}, xcrossing = {
    type = 117, serial = 1208863, send_event = 0, display = 0x8082170, 
    window = 25165880, root = 54526664, subwindow = 0, time = 0, x = 4001509, 
    y = 406, x_root = 8126530, y_root = 44302450, mode = 8127515, detail = 3, 
    same_screen = 1, focus = 0, state = 0}, xfocus = {type = 117, 
    serial = 1208863, send_event = 0, display = 0x8082170, window = 25165880, 
    mode = 54526664, detail = 0}, xexpose = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, x = 54526664, 
    y = 0, width = 0, height = 4001509, count = 406}, xgraphicsexpose = {
    type = 117, serial = 1208863, send_event = 0, display = 0x8082170, 
    drawable = 25165880, x = 54526664, y = 0, width = 0, height = 4001509, 
    count = 406, major_code = 8126530, minor_code = 44302450}, xnoexpose = {
    type = 117, serial = 1208863, send_event = 0, display = 0x8082170, 
    drawable = 25165880, major_code = 54526664, minor_code = 0}, 
  xvisibility = {type = 117, serial = 1208863, send_event = 0, 
    display = 0x8082170, window = 25165880, state = 54526664}, 
  xcreatewindow = {type = 117, serial = 1208863, send_event = 0, 
    display = 0x8082170, parent = 25165880, window = 54526664, x = 0, y = 0, 
    width = 4001509, height = 406, border_width = 8126530, 
    override_redirect = 44302450}, xdestroywindow = {type = 117, 
    serial = 1208863, send_event = 0, display = 0x8082170, event = 25165880, 
    window = 54526664}, xunmap = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, event = 25165880, window = 54526664, 
    from_configure = 0}, xmap = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, event = 25165880, window = 54526664, 
    override_redirect = 0}, xmaprequest = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, parent = 25165880, 
    window = 54526664}, xreparent = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, event = 25165880, window = 54526664, 
    parent = 0, x = 0, y = 4001509, override_redirect = 406}, xconfigure = {
    type = 117, serial = 1208863, send_event = 0, display = 0x8082170, 
    event = 25165880, window = 54526664, x = 0, y = 0, width = 4001509, 
    height = 406, border_width = 8126530, above = 44302450, 
    override_redirect = 8127515}, xgravity = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, event = 25165880, window = 54526664, 
    x = 0, y = 0}, xresizerequest = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, width = 54526664, 
    height = 0}, xconfigurerequest = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, parent = 25165880, 
    window = 54526664, x = 0, y = 0, width = 4001509, height = 406, 
    border_width = 8126530, above = 44302450, detail = 8127515, 
    value_mask = 3}, xcirculate = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, event = 25165880, window = 54526664, 
    place = 0}, xcirculaterequest = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, parent = 25165880, 
    window = 54526664, place = 0}, xproperty = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, atom = 54526664, 
    time = 0, state = 0}, xselectionclear = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, 
    selection = 54526664, time = 0}, xselectionrequest = {type = 117, 
    serial = 1208863, send_event = 0, display = 0x8082170, owner = 25165880, 
    requestor = 54526664, selection = 0, target = 0, property = 4001509, 
    time = 406}, xselection = {type = 117, serial = 1208863, send_event = 0, 
    display = 0x8082170, requestor = 25165880, selection = 54526664, 
    target = 0, property = 0, time = 4001509}, xcolormap = {type = 117, 
    serial = 1208863, send_event = 0, display = 0x8082170, window = 25165880, 
    colormap = 54526664, new = 0, state = 0}, xclient = {type = 117, 
    serial = 1208863, send_event = 0, display = 0x8082170, window = 25165880, 
    message_type = 54526664, format = 0, data = {
      b = "\000\000\000\000å\016=\000\226\001\000\000B\000|\000r\000€\002", 
      s = {0, 0, 3813, 61, 406, 0, 66, 124, 114, 676}, l = {0, 4001509, 406, 
        8126530, 44302450}}}, xmapping = {type = 117, serial = 1208863, 
    send_event = 0, display = 0x8082170, window = 25165880, 
    request = 54526664, first_keycode = 0, count = 0}, xerror = {type = 117, 
    display = 0x12721f, resourceid = 0, serial = 134750576, 
    error_code = 56 '8', request_code = 0 '\0', minor_code = 128 '\200'}, 
  xkeymap = {type = 117, serial = 1208863, send_event = 0, 
    display = 0x8082170, window = 25165880, 
    key_vector = "È\002@\003\000\000\000\000\000\000\000\000å\016=\000\226\001\000\000B\000|\000r\000€\002\033\004|"}, pad = {117, 1208863, 0, 134750576, 
    25165880, 54526664, 0, 0, 4001509, 406, 8126530, 44302450, 8127515, 3, 1, 
    0, 0, 0, 2048, 1028, 0, 0, 0, 0}}
	timeDiff = 8
	tv = {tv_sec = 1199519470, tv_usec = 121968}
	display = (CompDisplay *) 0x80767c0
	s = <value optimized out>
	time = <value optimized out>
	timeToNextRedraw = <value optimized out>
	w = <value optimized out>
	damageMask = 3
	mask = <value optimized out>
#13 0x08051b00 in main (argc=6, argv=0xbfbe3fa4) at main.c:441
	size = 1
	ctx = {offset = 3694, pluginData = 0x8078008 "\030", 
  textureFilterData = 0x0, refreshRateData = 0x0}
	displayName = 0x0
	plugin = {0xbfbe4d1c "ccp", 0xb7a6225c "trstr", 0xb7a6225f "tr", 0x0, 
  0x0, 0x1 <Address 0x1 out of bounds>, 0x364 <Address 0x364 out of bounds>, 
  0xb7a4e790 "È3Š·\020ii\r", 0xb7e8bab0 "", 0xb7a6225b "strstr", 
  0xb7ba97a8 "", 0xb7a61078 "£", 0x1 <Address 0x1 out of bounds>, 
  0xb7f22ff4 "(\237\001", 0xb7a771b8 "<8ò·", 0xbfbe3bd8 "hBº·°ºè·", 
  0xbfbe3bf4 "0<Ÿ¿R^ñ·žq§·\220ç€·\001", 0xb7f12103 "\203ø", 0xb7a61078 "£", 
  0xbfbe3bd8 "hBº·°ºè·", 0xb7f2383c "èj\027\b\033", 0x0, 
  0xb7a4e790 "È3Š·\020ii\r", 0x1 <Address 0x1 out of bounds>, 0x0, 
  0x1 <Address 0x1 out of bounds>, 0xbfbe3b6c "\001", 
  0xb7f18fa8 "\205Àt\027\2118\203À\b\211F\004\211ð\213]ô\213uø\213}ü\211ì]Ã1öëí\211ö\215Œ'", 0x11 <Address 0x11 out of bounds>, 
  0x8 <Address 0x8 out of bounds>, 0xb7f09468 "", 0xbfbe3be4 "²\232«\aô/ò·", 
  0xb7a4d000 "", 0x1 <Address 0x1 out of bounds>, 0xbfbe3ba0 "\210", 
  0xbfbe3c20 "M", 0xb7a77000 "", 0xb7a6225b "strstr", 
  0x1000000 <Address 0x1000000 out of bounds>, 
  0x1c93db57 <Address 0x1c93db57 out of bounds>, 0x0, 0x0, 
  0xb7f21434 "_dl_allocate_tls_init", 0x0, 
  0xb7f21434 "_dl_allocate_tls_init", 0xb7f09700 "l\236\001", 
  0x88 <Address 0x88 out of bounds>, 0x0, 0x0, 0x0, 
  0xb7a64300 "U\211å\203ì\024\211]ô\213M\f\211uø\211}üèCÿÿÿ\201ÃÝü", 
  0x10000004 <Address 0x10000004 out of bounds>, 
  0xb7ef6000 "[core]\nas_active_plugins = firepaint;png;showdesktop;resize;place;move;thumbnail;workarounds;switcher;decoration;expo;svg;crashhandler;put;vpswitch;shift;video;ezoom;imgjpeg;neg;text;wall;wobbly;anima"..., 0x0, 0x0, 0x0, 
  0x0, 0x0, 0x0, 0x0, 0xb7ba4268 "\030G", 0xb7e8bab0 "", 0x0, 
  0x7ab9ab2 <Address 0x7ab9ab2 out of bounds>, 0xb7f22ff4 "(\237\001", 
  0xb7a77000 "", 0xb7a61078 "£", 
  0xbfbe3c30 "ºòŠ·ŒòŠ·'=Ÿ -=Ÿ¿ŒÖ€·d<Ÿ¿\b?Ÿ¿zGŠ·'=Ÿ¿¹òŠ·", 
  0xb7f15e52 "\213Uð\203ì\024\211Á1À\205Òt\t\205Ét\002\213\001\003B\004\213\213\030ýÿÿ\205Éu\t\213Mè\213Uì\211\004\021\215eô[^_]Ã1Àë\223\215\203ðàÿÿ\211D$\f\215\203³àÿÿ\211D$\004\215\203ÀàÿÿÇD$\bM", 0xb7a771b8 "<8ò·", 
  0xb7a4e790 "È3Š·\020ii\r", 0x1 <Address 0x1 out of bounds>, 
  0x1 <Address 0x1 out of bounds>, 0x0, 0xb7a6225b "strstr", 
  0x34 <Address 0x34 out of bounds>, 0xb7a60000 "\177ELF\001\001\001", 
  0x500140b8 <Address 0x500140b8 out of bounds>, 
  0x4d <Address 0x4d out of bounds>, 0x0, 0xb7a4d6bc "", 0xbfbe3c64 "Linux", 
  0xb7a6f2ba "MP", 0xb7a6f2bc "", 
  0x20be3d27 <Address 0x20be3d27 out of bounds>, 
  0xbfbe3d2d " Tue Dec 18 05:45:12 UTC 2007", 0xb7a4d6bc "", 
  0xbfbe3c64 "Linux", 0xbfbe3f08 "x?Ÿ¿Œ.»·à,ò·@)\a\bx?Ÿ¿Œ.»·\006", 
  0xb7a6477a "\205À\017\225À\017¶À\211\203À!", 
  0xbfbe3d27 "#2 SMP Tue Dec 18 05:45:12 UTC 2007", 0xb7a6f2b9 "SMP", 0x0, 
  0x0, 0xbfbe3e68 "<8ò·", 0x756e694c <Address 0x756e694c out of bounds>, 
  0x78 <Address 0x78 out of bounds>, 0x0 <repeats 14 times>, 
  0x61736900 <Address 0x61736900 out of bounds>, 
  0x6c2d6361 <Address 0x6c2d6361 out of bounds>, 
  0x6f747061 <Address 0x6f747061 out of bounds>, 
  0x70 <Address 0x70 out of bounds>, 0x0 <repeats 12 times>, 
  0x2e320000 <Address 0x2e320000 out of bounds>, 
  0x30322e36 <Address 0x30322e36 out of bounds>, 
  0x2d36312d <Address 0x2d36312d out of bounds>, 
  0x656e6567 <Address 0x656e6567 out of bounds>, 
  0x636972 <Address 0x636972 out of bounds>, 0x0 <repeats 11 times>, 
  0x23000000 <Address 0x23000000 out of bounds>, 
  0x4d532032 <Address 0x4d532032 out of bounds>, 
  0x75542050 <Address 0x75542050 out of bounds>, 
  0x65442065 <Address 0x65442065 out of bounds>, 
  0x38312063 <Address 0x38312063 out of bounds>, 
  0x3a353020 <Address 0x3a353020 out of bounds>, 
  0x313a3534 <Address 0x313a3534 out of bounds>, 
  0x54552032 <Address 0x54552032 out of bounds>, 
  0x30322043 <Address 0x30322043 out of bounds>, 
  0x3730 <Address 0x3730 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x36383669 <Address 0x36383669 out of bounds>, 0x0, 0x0, 0x0, 0x0, 0x0, 
  0x0, 0x0, 0x0, 0x0, 0x804f1c6 "GLIBC_2.1", 
  0xd696910 <Address 0xd696910 out of bounds>, 0xb7ba8fa8 "ª*", 
  0xbfbe3dd4 "X>Ÿ¿B\037ñ·", 
  0xb7f11b79 "\205À\017\204rÿÿÿ\213Eà\213@\b\205À\017\205bÿÿÿ\205ö\017\205Zÿÿÿf\203}ä", 0xb7baecd4 "GLIBC_2.0", 0x804f1bc "GLIBC_2.0", 0xb7e8ba64 ".so.6", 
  0xb7e8ba54 "`ºè·", 0xb7a77d10 "Œñ\004\b\020ii\r", 0xbfbe0002 "", 
  0xb7f16c69 "\205Àuç\203Ä\bž\001", 0x804d0cb "libc.so.6", 
  0xb7e8ba60 "libm.so.6", 0xb7f22ff4 "(\237\001", 0xb7a77cbc "°ºè·Pœè·", 
  0xd <Address 0xd out of bounds>, 0xbfbe3e58 "$?Ÿ¿\003!ñ·L£\004\b\b?Ÿ¿<8ò·", 
  0xb7f11f42 "\205Àt»é\235þÿÿ\220\215t&", 0x0, 0x0, 0x0, 0x0, 
  0x123 <Address 0x123 out of bounds>, 
  0x3d8f5 <Address 0x3d8f5 out of bounds>, 0xbfbe3e24 "", 0xbfbe3e24 "", 
  0xbfbe3f14 "@)\a\bx?Ÿ¿Œ.»·\006", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0xb7e8bab0 "", 
  0x19 <Address 0x19 out of bounds>, 0xb7ba0c28 "", 
  0xb7ba0a28 "/N=öÎ\030L\017ùÄ-×\204\"\233|øÔ\217Ó\205\"\233|ìûÀ=°\"\225Ã8Ç\031uÿ\001Ä\022ÉBY\020ÜÏìµ¶w\035\rGÞÍ%µV1ýÇr1\035\a;úL\214\t)\020\t~\222\0348µï0jÝù{\004\\H±Ô¡\034 \002êÙ\0179µï0X?\227|\030\034sìT\200ÌsÙ\202c\002;H\205\0336\rfý2vàÕš§KáŒ\234#\217Ö\036h\233£\230Ëò\234\002Y1\nŽ\006ßœèe\235J\032\223šPµš\020\205)%~\016|\030¹Ñ8\a\221\222þ\206ïŠ:VÓñIµ$\202¡7äQhoìð€\017l"..., 
  0x804d280 "__libc_start_main", 
  0xf63d4e2e <Address 0xf63d4e2e out of bounds>, 0x804d28c "_main", 
  0x804d284 "bc_start_main"...}
	i = 1
	nPlugin = 1
	disableSm = 1
	clientId = 0x0
	refreshRateArg = 0x0
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7c2c6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7bd3a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb78e9972 in crash_handler (sig=11) at crashhandler.c:57
#4  <signal handler called>
#5  0xb74509ba in fxAirplane3DLinearAnimStepPolygon (w=0x816add8, 
    p=0x89acd30, forwardProgress=0) at airplane3d.c:775
#6  0xb745ad0f in polygonsAnimStep (s=0x8157310, w=0x816add8, time=8)
    at polygon.c:1484
#7  0xb745077f in fxAirplane3DAnimStep (s=0x8157310, w=0x816add8, time=8)
    at airplane3d.c:963
#8  0xb744da14 in animPreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at animation.c:2152
#9  0xb743bd50 in fadePreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at fade.c:181
#10 0xb742cc80 in scalePreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at scale.c:922
#11 0xb7415321 in groupPreparePaintScreen (s=0x8157310, msSinceLastPaint=8)
    at paint.c:938
#12 0x08055379 in eventLoop () at display.c:1685
#13 0x08051b00 in main (argc=6, argv=0xbfbe3fa4) at main.c:441
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 22154
```

Thanks!

---

### Post by shareMenaPeace on 2008-01-08
Well maybe try beryl (Which is not continued and now compiz fusion).

---

