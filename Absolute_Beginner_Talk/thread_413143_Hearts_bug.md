---
title: "Hearts bug"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-04-18
Hi,
I Installed Heart from the repository and when I try to run it Bug Buddy comes into play with the following message:

(By the way can someone tell me how to report bugs to the appropriate bug tracker????)
 
[QUOTE=Bug Buddy]
Bug Reporting Tool

The information about the crash has been successfully collected.

The application that crashed is not known to bug-buddy, therefore the bug report can not be sent to the GNOME Bugzilla.  Please save the bug to a text file and report it to the appropriate bug tracker for this application.

emory status: size: 66019328 vsize: 0 resident: 66019328 share: 0 rss: 12312576 rss_rlim: 0
CPU usage: start_time: 1176946589 rtime: 0 utime: 53 stime: 0 cutime:48 cstime: 0 timeout: 5 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/games/gnome-hearts'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1225058640 (LWP 8315)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb748b34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f661b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0804e068 in cards_image_set_size ()
#5  0x0804ec67 in on_configure_event ()
#6  0xb7a89b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#8  0xb7569b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#9  0xb756ae7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#10 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#11 0xb7b9d5f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7a07240 in gtk_drawing_area_new () from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#14 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#15 0xb755987d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#16 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#17 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#18 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#19 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7b991b2 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#22 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#23 0xb755987d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#24 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#26 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#27 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7bb2b91 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#30 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#31 0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#32 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#33 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#34 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#35 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb79f474c in gtk_container_resize_children ()
   from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb7bb2df4 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7566b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#39 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#40 0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#41 0xb756a1e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#42 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#43 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#44 0xb79f47e3 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#45 0xb79f4863 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb74deaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#47 0xb74e0802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#48 0xb74e37df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#49 0xb74e3b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#50 0xb7a84574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#51 0x08051f42 in main ()

Thread 1 (Thread -1225058640 (LWP 8315)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb748b34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f661b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0804e068 in cards_image_set_size ()
No symbol table info available.
#5  0x0804ec67 in on_configure_event ()
No symbol table info available.
#6  0xb7a89b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7569b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb756ae7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb7b9d5f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7a07240 in gtk_drawing_area_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb755987d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0xb7b991b2 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb755987d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#28 0xb7bb2b91 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0xb7566199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#31 0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#32 0xb756a02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb7ba27ea in gtk_widget_size_allocate ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#36 0xb79f474c in gtk_container_resize_children ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#37 0xb7bb2df4 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0xb7566b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb7557fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb755979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#41 0xb756a1e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#42 0xb756b0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#43 0xb756b279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0xb79f47e3 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0xb79f4863 in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0xb74deaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#47 0xb74e0802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#48 0xb74e37df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#49 0xb74e3b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#50 0xb7a84574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0x08051f42 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()



[/QUOTE]

---

### Post by wormser on 2007-04-18
The report bug directions are a sticky at the top of the form.

Here is the direct link.
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by mozkaynak on 2007-04-18
hi, 
In launchpad I found the solution which is "Just sync gnome-hearts-0.1.3 from debian"

But I dont know how to do that? what is to sync? and how to do that?
Thanks...

---

