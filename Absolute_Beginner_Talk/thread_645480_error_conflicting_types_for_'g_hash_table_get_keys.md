---
title: "error: conflicting types for 'g_hash_table_get_keys'"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by xeb07170 on 2007-12-20
hello again,

i feel i am so close to actually being able to solve this,

i get the message 'error: conflicting types for 'g_hash_table_get_keys' when i use the make command for gtk.

I am absolutely stumped and would not  have a clue how to advance from here


any help appreciated


Thanks


Paul

---

### Post by xeb07170 on 2007-12-20
TK_SYSCONFDIR=\"/usr/local/etc\" -DGTK_VERSION=\"2.8.16\" -DGTK_BINARY_VERSION=\                                      "2.4.0\" -DGTK_HOST=\"i686-pc-linux-gnu\" -DGTK_COMPILATION -I../gtk -I.. -I../g                                      dk -I../gdk -I../gdk-pixbuf -I../gdk-pixbuf -DG_DISABLE_DEPRECATED -DGDK_PIXBUF_                                      DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGTK_FILE_                                      SYSTEM_ENABLE_UNSUPPORTED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/local/include/                                      glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pango-1.0 -I/usr                                      /local/include/cairo -I/usr/local/include/atk-1.0 -g -O2 -Wall -MT gtkiconfactor                                      y.lo -MD -MP -MF .deps/gtkiconfactory.Tpo -c gtkiconfactory.c  -fPIC -DPIC -o .l                                      ibs/gtkiconfactory.o
gtkiconfactory.c:2943: error: conflicting types for 'g_hash_table_get_keys'
/usr/local/include/glib-2.0/glib/ghash.h:81: error: previous declaration of 'g_h                                      ash_table_get_keys' was here
make[4]: *** [gtkiconfactory.lo] Error 1
make[4]: Leaving directory `/home/paul/Desktop/gtk+-2.8.16/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/paul/Desktop/gtk+-2.8.16/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/paul/Desktop/gtk+-2.8.16/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/Desktop/gtk+-2.8.16'
make: *** [all] Error 2
root@paul-desktop:~/Desktop/gtk+-2.8.16#

---

### Post by kjmathew on 2008-02-05
Looks like you are trying to compile an old version of GTK+ with a new version of Glib. This error is due to a naming conflict with the recent GLib implementation of the similar function **g_hash_table_get_keys** (See: [http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html#id3357478](http://library.gnome.org/devel/glib/stable/glib-Hash-Tables.html#id3357478) and search for g_hash_table_get_keys). The solution is to use the latest version of GTK+. But if you are absolutely certain that you want to compile this GTK+-2.8.16 version, you need to downgrade glib to below 2.6.10.

**Not recommended**: You could also try a work around to avoid the naming conflict by replacing **g_hash_table_get_keys** with **hash_table_get_keys** in files **gtk/gtkiconfactory.c** and **gtk/gtkstock.c** (Ref: [http://ftp.acc.umu.se/pub/GNOME/sources/gtk+/2.10/gtk+-2.10.12.changes](http://ftp.acc.umu.se/pub/GNOME/sources/gtk+/2.10/gtk+-2.10.12.changes)). But then you'd face more incompatibilities like with GMemChunk which is deprecated (See [http://library.gnome.org/devel/glib/unstable/glib-Memory-Chunks.html#id3338951](http://library.gnome.org/devel/glib/unstable/glib-Memory-Chunks.html#id3338951))

---

