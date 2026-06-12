---
title: "help fixing error"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by killaray on 2007-01-20
i was just trying to make an archive (zip file) and it gave me originally an error that i could not make an archive of an archive... then i closed the error and then the bug report came up with this message.. now everytime i close it it just opens up again and again with the same error... and i cant access my top bar at all and cant get into terminal or anything.. can anyone assist me plz

this is the bug report down below

> Memory status: size: 34086912 vsize: 0 resident: 34086912 share: 0 rss: 15183872 rss_rlim: 0
CPU usage: start_time: 1169279533 rtime: 0 utime: 123 stime: 0 cutime:117 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

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
[New Thread -1225034064 (LWP 9156)]
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
#1  0xb766e323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f661b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7556770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7557ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7772122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7772159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77721d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bc1d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bc1dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bbd591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7767aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7769802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb776c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb776cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b6b574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225034064 (LWP 9156)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb766e323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f661b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7556770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7557ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7772122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7772159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77721d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bc1d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bc1dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bbd591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7767aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7769802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb776c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb776cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b6b574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


---

### Post by killaray on 2007-01-20
this is very frustrating i cant access anything basically.. could anyone help me out i dont want to have to reformat

---

### Post by killaray on 2007-01-21
can i atleast get pointed to where i can get help?

---

### Post by killaray on 2007-01-21
ok so my Ubuntu apparently fixed itself is this normal?

---

