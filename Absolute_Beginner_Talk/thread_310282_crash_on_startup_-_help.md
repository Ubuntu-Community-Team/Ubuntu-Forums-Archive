---
title: "crash on startup - help"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by protarchus on 2006-11-30
Hi. I'm relatively new to linux and I was really happy with my switch from windows until today. I was trying to run masters of orion 2 with wine when I got a bug report. I restarted but the same crash occurs. The problem involves my applications bar. I can use everything else on the computer fine as long as I can locate it in the filesystem(being new this isnt always easy but I'm beginning to get a feel for it. I suppose in some way its good that this happened as its forcing me to learn about the operating system), but the applications bar is completely inaccessible. I get a bug report window with the following contents. (I realize that the "no debugging symbol found" message repeated over and over again probably isnt helpful, but I thought it would be a mistake to start making decsions about what information would be useful to people who actually knew what was going on.) 


Memory status: size: 32444416 vsize: 0 resident: 32444416 share: 0 rss: 13422592 rss_rlim: 0
CPU usage: start_time: 1164948007 rtime: 0 utime: 109 stime: 0 cutime:95 cstime: 0 timeout: 14 it_real_value: 0 frequency: 0

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
[New Thread -1225619792 (LWP 22875)]
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
#1  0xb75de323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ed71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74c7770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74c8ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76e3122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76e3159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76e31d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b32d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b32dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b2e591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76d8aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76da802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76dd7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76ddb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7adc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225619792 (LWP 22875)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75de323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ed71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74c7770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74c8ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76e3122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76e3159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76e31d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b32d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b32dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b2e591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76d8aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76da802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76dd7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76ddb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7adc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

I save the record, and as soon as I do the applications bar refreshes and I get a new identical bug report. I appreciate anyone who has read this far. Any help would be greatly appreciated. Thanks in advance.

---

### Post by K.Mandla on 2006-12-01
It looks like something is screwy with gnome-panel, as you might have guessed already. :roll:

You could take a chance and remove gnome-panel, and reinstall it. It seems rather drastic, though. I'm not an avid Gnome fan so I hesitate to suggest it. 

Perhaps a Gnome expert will chime in. [-o<

---

