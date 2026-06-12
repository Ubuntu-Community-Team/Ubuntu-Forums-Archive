---
title: "Bug buddy not letting me in (gnome-panel errors)"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by General_Ts0 on 2007-04-01
Trying to burn a CD for first time and when I'm extracting files out of an ISO, all of sudden get this error pop-up in a window
```
Either --appname or --package arguments are required.
```
followed by a bug report which has defaults to title of 'gnome-panel-bugreport.txt and the contents of it are:
```
Memory status: size: 36265984 vsize: 0 resident: 36265984 share: 0 rss: 13987840 rss_rlim: 0
CPU usage: start_time: 1175406854 rtime: 0 utime: 70 stime: 0 cutime:66 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

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
[Thread debugging using libthread_db enabled]
[New Thread -1225832784 (LWP 4797)]
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
#1  0xb75ab323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ea31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7493770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7494ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76af122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76af159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76af1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7afed5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7afedba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7afa591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76a4aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76a6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76a97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76a9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7aa8574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225832784 (LWP 4797)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75ab323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ea31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7493770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7494ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76af122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76af159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76af1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7afed5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7afedba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7afa591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76a4aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76a6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76a97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76a9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7aa8574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

and the only thing I can do is close/save.  Both of which put the BUG BUDDY in a loop which makes everything else unaccessible (except right click on trash and right click on desktop)  If I log in as another user (root) there are no problems.  I don't know how to kill this process for my default user account or to create another user account now that I can get in as root.


[Same thing here ]("http://www.ubuntuforums.org/showthread.php?t=392655") but no fix listed, hoping users watching this section can help.

---

### Post by General_Ts0 on 2007-04-03
upgrading to Feisty seems to have 'patched' it.  Still get the error message pop-up but no bug buddy loops. ugh.

---

