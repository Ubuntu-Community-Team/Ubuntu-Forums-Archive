---
title: "[SOLVED] Xara Xtreme crashes a lot on Gutsy"
date: 2007-11-02
forum: Art &amp; Design
---

### Post by galvao on 2007-11-02
Greetings.

I'm having some nasty problems with Xara Xtreme on Gutsy (worked as a charm on Feisty):

If I try a menu options like "File -> Page options", "Utility -> Options" and such the program just crashes...

Here's the output from the console:

*** Begin Output
galvao@galvao-desktop ~> xaralx

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
*** glibc detected *** xaralx: free(): invalid pointer: 0x0a73cc60 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75d9d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75dd800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77f7961]
xaralx[0x8c88348]
xaralx[0x8c88836]
xaralx[0x8080113]
xaralx[0x8395957]
xaralx[0x867a57a]
xaralx[0x8500258]
xaralx[0x8682f73]
xaralx[0x80993ba]
xaralx[0x8071d78]
xaralx[0x8d8be28]
xaralx[0x8e1b008]
xaralx[0x8e1a58c]
xaralx[0x8e1b18d]
xaralx[0x8cd10fd]
xaralx[0x8e1b12d]
xaralx[0x8ca034c]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb789fc09]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7892772]
/usr/lib/libgobject-2.0.so.0[0xb78a3323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb78a4847]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78a4a09]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58)[0xb7e1ffe8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x14a)[0xb7d0a38a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d0bf28]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d03178]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7cfd1de]
/usr/lib/libgobject-2.0.so.0[0xb7890f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7892772]
/usr/lib/libgobject-2.0.so.0[0xb78a3973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78a460f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78a4a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e1b498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x14f)[0xb7cf636f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x307)[0xb7cf7587]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b62b9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb77f011c]
/usr/lib/libglib-2.0.so.0[0xb77f355f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb77f3909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cf79e4]
xaralx[0x8d66c99]
xaralx[0x8cbb442]
xaralx[0x8cbb57a]
xaralx[0x8dca0ed]
xaralx[0x805f4eb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7586050]
xaralx[0x805eec1]
======= Memory map: ========
08048000-09351000 r-xp 00000000 08:15 1864975    /usr/bin/xaralx
09351000-09468000 rw-p 01308000 08:15 1864975    /usr/bin/xaralx
09468000-0a760000 rw-p 09468000 00:00 0          [heap]
b5a00000-b5a21000 rw-p b5a00000 00:00 0 
b5a21000-b5b00000 ---p b5a21000 00:00 0 
b5b0e000-b5c26000 r-xp 00000000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5c26000-b5c2b000 rw-p 00118000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5c2b000-b5c2c000 rw-p b5c2b000 00:00 0 
b5c2c000-b5c5e000 r-xp 00000000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5c5e000-b5c61000 rw-p 00031000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5c61000-b5c62000 r-xp 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5c62000-b5c63000 rw-p 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5c63000-b5c66000 rw-s 00000000 00:09 30310438   /SYSV00000000 (deleted)
b5c66000-b6122000 rw-p b5c66000 00:00 0 
b6122000-b6881000 r--p 00000000 08:15 2178286    /usr/share/icons/gnome/icon-theme.cache
b6881000-b692c000 r--p 00000000 08:15 2176925    /usr/share/icons/Tangerine/icon-theme.cache
b692c000-b6b48000 r--p 00000000 08:15 2060521    /usr/share/fonts/truetype/unfonts/UnDotum.ttf
b6b71000-b6bd1000 rw-s 00000000 00:09 30113826   /SYSV00000000 (deleted)
b6bd1000-b6d37000 r--p 00000000 08:15 2175390    /usr/share/icons/Human/icon-theme.cache
b6d37000-b6ecb000 rw-p b6d37000 00:00 0 
b6ecb000-b6f56000 r--p 00000000 08:15 2060480    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6f66000-b6f96000 r-xp 00000000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f96000-b6f99000 rw-p 0002f000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f99000-b6f9a000 rw-p b6f99000 00:00 0 
b6f9a000-b6fd7000 r--p 00000000 08:15 2060484    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b6fd7000-b7022000 r--p 00000000 08:15 2060482    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b703d000-b706d000 r-xp 00000000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b706d000-b706e000 rw-p 00030000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b706e000-b709f000 r--p 00000000 08:15 2060494    /usr/share/fonts/truetype/ttf-indic-fonts-core/Vemana.ttf
b709f000-b70c2000 r--p 00000000 08:15 2076773    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b70c4000-b70dfish: Job 1, “xaralx” terminated by signal SIGABRT (Abort)
*** End output

Anyone experiencing this? Any suggestions?

TIA,

---

### Post by smartboyathome on 2007-11-02
> **galvao said:**
> Greetings.

I'm having some nasty problems with Xara Xtreme on Gutsy (worked as a charm on Feisty):

If I try a menu options like "File -> Page options", "Utility -> Options" and such the program just crashes...

Here's the output from the console:

*** Begin Output
galvao@galvao-desktop ~> xaralx

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(xaralx:14986): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
*** glibc detected *** xaralx: free(): invalid pointer: 0x0a73cc60 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75d9d65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75dd800]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb77f7961]
xaralx[0x8c88348]
xaralx[0x8c88836]
xaralx[0x8080113]
xaralx[0x8395957]
xaralx[0x867a57a]
xaralx[0x8500258]
xaralx[0x8682f73]
xaralx[0x80993ba]
xaralx[0x8071d78]
xaralx[0x8d8be28]
xaralx[0x8e1b008]
xaralx[0x8e1a58c]
xaralx[0x8e1b18d]
xaralx[0x8cd10fd]
xaralx[0x8e1b12d]
xaralx[0x8ca034c]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb789fc09]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7892772]
/usr/lib/libgobject-2.0.so.0[0xb78a3323]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb78a4847]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78a4a09]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58)[0xb7e1ffe8]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x14a)[0xb7d0a38a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d0bf28]
/usr/lib/libgtk-x11-2.0.so.0[0xb7d03178]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7cfd1de]
/usr/lib/libgobject-2.0.so.0[0xb7890f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7892772]
/usr/lib/libgobject-2.0.so.0[0xb78a3973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb78a460f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb78a4a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e1b498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x14f)[0xb7cf636f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x307)[0xb7cf7587]
/usr/lib/libgdk-x11-2.0.so.0[0xb7b62b9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb77f011c]
/usr/lib/libglib-2.0.so.0[0xb77f355f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb77f3909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7cf79e4]
xaralx[0x8d66c99]
xaralx[0x8cbb442]
xaralx[0x8cbb57a]
xaralx[0x8dca0ed]
xaralx[0x805f4eb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7586050]
xaralx[0x805eec1]
======= Memory map: ========
08048000-09351000 r-xp 00000000 08:15 1864975    /usr/bin/xaralx
09351000-09468000 rw-p 01308000 08:15 1864975    /usr/bin/xaralx
09468000-0a760000 rw-p 09468000 00:00 0          [heap]
b5a00000-b5a21000 rw-p b5a00000 00:00 0 
b5a21000-b5b00000 ---p b5a21000 00:00 0 
b5b0e000-b5c26000 r-xp 00000000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5c26000-b5c2b000 rw-p 00118000 08:15 1866220    /usr/lib/libxml2.so.2.6.30
b5c2b000-b5c2c000 rw-p b5c2b000 00:00 0 
b5c2c000-b5c5e000 r-xp 00000000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5c5e000-b5c61000 rw-p 00031000 08:15 1865570    /usr/lib/libcroco-0.6.so.3.0.1
b5c61000-b5c62000 r-xp 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5c62000-b5c63000 rw-p 00000000 08:15 1913713    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5c63000-b5c66000 rw-s 00000000 00:09 30310438   /SYSV00000000 (deleted)
b5c66000-b6122000 rw-p b5c66000 00:00 0 
b6122000-b6881000 r--p 00000000 08:15 2178286    /usr/share/icons/gnome/icon-theme.cache
b6881000-b692c000 r--p 00000000 08:15 2176925    /usr/share/icons/Tangerine/icon-theme.cache
b692c000-b6b48000 r--p 00000000 08:15 2060521    /usr/share/fonts/truetype/unfonts/UnDotum.ttf
b6b71000-b6bd1000 rw-s 00000000 00:09 30113826   /SYSV00000000 (deleted)
b6bd1000-b6d37000 r--p 00000000 08:15 2175390    /usr/share/icons/Human/icon-theme.cache
b6d37000-b6ecb000 rw-p b6d37000 00:00 0 
b6ecb000-b6f56000 r--p 00000000 08:15 2060480    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6f66000-b6f96000 r-xp 00000000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f96000-b6f99000 rw-p 0002f000 08:15 1865812    /usr/lib/libgsf-1.so.114.0.7
b6f99000-b6f9a000 rw-p b6f99000 00:00 0 
b6f9a000-b6fd7000 r--p 00000000 08:15 2060484    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b6fd7000-b7022000 r--p 00000000 08:15 2060482    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b703d000-b706d000 r-xp 00000000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b706d000-b706e000 rw-p 00030000 08:15 1866110    /usr/lib/librsvg-2.so.2.18.2
b706e000-b709f000 r--p 00000000 08:15 2060494    /usr/share/fonts/truetype/ttf-indic-fonts-core/Vemana.ttf
b709f000-b70c2000 r--p 00000000 08:15 2076773    /usr/share/fonts/type1/gsfonts/n021003l.pfb
b70c4000-b70dfish: Job 1, “xaralx” terminated by signal SIGABRT (Abort)
*** End output

Anyone experiencing this? Any suggestions?

TIA,

by doing a search on google for your error, i came up with this thread from the Arch Linux forums:
[http://bbs.archlinux.org/viewtopic.php?pid=289695](http://bbs.archlinux.org/viewtopic.php?pid=289695)
Looks like it might have to be compiled in order for it to work. :(

---

### Post by galvao on 2007-11-02
Ok, here comes the weird part: as you can see [here]("http://ubuntuforums.org/showthread.php?t=588132"), I've already installed Xara Xtreme (it even shows up at the Applications -> Graphics menu and I don't manually add menu entries).

When I tried:

sudo apt-get purge xaralx

or

sudo apt-get remove xaralx

I got "Package xaralx is not installed, so not removed"(!!!)

So I just installed it by doing:

sudo apt-get install xaralx

And now everything seems fine... Go figure... :roll:

Thanks a lot for your reply :)

---

### Post by Tiede on 2007-12-23
Well, that IS really strange galvao.
I had the same problem, and just like you mentioned, apt-get declared to me that xaralx was not installed (although I could do almost everything in there - except things that require a dialog box)...
I did a quick```
sudo aptitude install xaralx
``` and now everything is seemingly fine...

Hmmm... I wonder, did you dist-upgrade from feisty to gusty?
That's what I did, and I am thinking maybe update-manager messed with a little too much for it's own sake...

---

### Post by JugglinPhil on 2009-10-14
I don't really see why this is marked as solved, if it is then how do you fix the crashes? I've got the same problem, I mean it is quite a good program but it is kind of useless if you can't even export your files.. :confused:

---

### Post by Merk42 on 2009-10-14
> **JugglinPhil said:**
> I don't really see why this is marked as solved, if it is then how do you fix the crashes? I've got the same problem, I mean it is quite a good program but it is kind of useless if you can't even export your files.. :confused:

> **galvao said:**
> 

So I just installed it by doing:

sudo apt-get install xaralx

**And now everything seems fine... Go figure... :roll:**

Thanks a lot for your reply :)

Emphasis mine


Judging by his signature he has since upgraded to Jaunty. Gutsy is no longer supported and the last post is this thread **is almost 2 years old**.

---

### Post by JugglinPhil on 2009-10-15
Okay it worked, sorry for the inconvenience..

---

