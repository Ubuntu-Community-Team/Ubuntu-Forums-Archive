---
title: "oops. i deffinitly broke something. help please"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-19
hey everyone. i was trying to change my screen resolution by doing.. sudo dpkg-reconfigure -phigh xserver-xorg

 and i changed it, and restarted. but now i only last like ten seconds in a session before i go to a black screen?  :(

 how do i fix this??

---

### Post by taurus on 2007-03-19
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by j2p2f2 on 2007-03-19
If you can get to the terminal (or maybe through recovery mode) there is a backup xorg.conf file that you can use named xorg.conf.bak to replace your current xorg.conf

I dont know if this is exact steps, but this is how i did it

sudo -s           // (login)
cd /etc/X11/    // (browse to your folder with xorg.conf)
dir                   // (confirm that xorg.conf.bak exists before continuing)
rm xorg.conf    // (deletes current xorg.conf)
mv xorg.conf.bak xorg.conf   // (renames xorg.conf.bak to xorg.conf)

then hit crtl alt del to restart

if this works, immediately after you get into your desktop i recommend making a backup of your current xorg.conf incase it happens again.

The best way to change your resolution is to simply go to System > Preferences > Screen Resolution

I hope this helps :)

---

### Post by j2p2f2 on 2007-03-19
yeah, try his way first :)

sorry for double post

---

### Post by da1nonlymikeo on 2007-03-19
i just realized that only as soon as beryl starts it crashes. changing the resolution messed up beryl wich crashed my entire system?

 but yeah how do i get back to my default resolution settings when i do sudo dpkg-reconfigure xserver-xorg

i get a bunch of questions that im not sure of the answers. :/

---

### Post by da1nonlymikeo on 2007-03-19
and now i just got a bug report??


Memory status: size: 42405888 vsize: 0 resident: 42405888 share: 0 rss: 18325504 rss_rlim: 0
CPU usage: start_time: 1174361259 rtime: 0 utime: 140 stime: 0 cutime:130 cstime: 0 timeout: 10 it_real_value: 0 frequency: 0

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
[New Thread -1225922896 (LWP 6855)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7595323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e8d1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb5eda677 in wnck_workspace_get_viewport_x ()
   from /usr/lib/libwnck-1.so.18
#5  0xb5ecea3b in wnck_tasklist_get_type () from /usr/lib/libwnck-1.so.18
#6  0xb7a97b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb77d979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#8  0xb77e9b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#9  0xb77eae7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#10 0xb77eb279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#11 0xb7bab5f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7a90ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7a920f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb791b7ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#15 0xb7690802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#16 0xb76937df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#17 0xb7693b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#18 0xb7a92574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x08061d8c in main ()

Thread 1 (Thread -1225922896 (LWP 6855)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7595323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e8d1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb5eda677 in wnck_workspace_get_viewport_x ()
   from /usr/lib/libwnck-1.so.18
No symbol table info available.
#5  0xb5ecea3b in wnck_tasklist_get_type () from /usr/lib/libwnck-1.so.18
No symbol table info available.
#6  0xb7a97b00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb77d979b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb77e9b93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb77eae7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb77eb279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb7bab5f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7a90ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7a920f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0xb791b7ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#15 0xb7690802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76937df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7693b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#18 0xb7a92574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#19 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

