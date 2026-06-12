---
title: "problems after upgrade to Edgey"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by pheryllt on 2007-03-25
upgraded to edgey and now get this error on boot up:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

The name org.gnome.SettingsDaemon was not provided by any .service files

GNOME will still try to restart the Settings Daemon next time you log in.

Also bug buddy comes up with this error:

Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1227318624 (LWP 5223)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb763434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7dcb1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7b1391f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb7c12d7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb7c13218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7c13318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb75beaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#13 0xb75c0802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#14 0xb75c37df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#15 0xb75c3b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#16 0xb7b01574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
#18 0xb735f8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#19 0x080672e1 in ?? ()

Thread 1 (Thread -1227318624 (LWP 5223)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb763434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7dcb1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7b1391f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb7c12d7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7c122b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb7c13218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7c13318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb75beaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0xb75c0802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb75c37df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb75c3b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7b01574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#17 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
No symbol table info available.
#18 0xb735f8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#19 0x080672e1 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


Any ideas,   The most annoying thing is that i cannot get folders to open up at all, and bug buddy will not go away.

---

### Post by tipsqueal on 2007-03-27
Honestly, this isn't going to be what you want. But I would suggest a fresh install. I'm sure there are ways to recover from this and whatnot, but It's always better to do a fresh install instead of upgrading from Dapper to Edgy. I tried an upgrade and it got completely messed up and I ended up just doing a fresh install of Edgy.

---

