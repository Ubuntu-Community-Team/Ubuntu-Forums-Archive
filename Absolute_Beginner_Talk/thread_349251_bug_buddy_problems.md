---
title: "bug buddy problems"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by insanitywetrust on 2007-01-29
help please
have had to do an upgrade of a few hundred updates, went to reboot, now says something is wrong, i filled out the bug buddy info, cannot send it as no idea how to use sendmail and now my desktop is not fully functional.... any suggestions? i tried rebooting four times, still nothing and keep getting that bug buddy stuff, fill the form, hit save, cause no can send and then it comes right back up again, is this normal?

---

### Post by irish_flu on 2007-01-29
I woulnd't call a bunch of errors normal.  :)

Is there some way for you to cut-and-paste the errors for us to see?

---

### Post by insanitywetrust on 2007-01-29
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
[New Thread -1226487136 (LWP 8210)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb76fc34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e931b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7bdb91f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb7cdad7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb7cdb218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7cdb318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7686aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#13 0xb7688802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#14 0xb768b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#15 0xb768bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#16 0xb7bc9574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#17 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
#18 0xb74278cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#19 0x080672e1 in ?? ()

Thread 1 (Thread -1226487136 (LWP 8210)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76fc34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e931b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7bdb91f in gtk_menu_shell_insert () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb7cdad7a in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7cda2b0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb7cdb218 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7cdb318 in gtk_ui_manager_get_ui () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7686aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0xb7688802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb768b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb768bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7bc9574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#17 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
No symbol table info available.
#18 0xb74278cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#19 0x080672e1 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


is one list and cannot access the image of the desktop as the desktop is no there anymore

i did get sendmail installed and sent off two emails, maybe i could send more, but would they be read? or sent to bill gates i mean the dead email office? >smiles<

---

### Post by irish_flu on 2007-01-30
Thanks for posting that, unfortunately I don't know what to make of it.  Hopefully somebody less n00bish than I am will come along.  :o

---

### Post by insanitywetrust on 2007-01-30
thanks for your reply
i have the second system on ubuntu desktop
and then, found the ctrl+alt+f1 to get to the root command
and then i sent a line of something with dist-update or upgrade
and now waiting for this to be done, and maybe i can access
the music files, get them out and then format all over and start anew
i am wondering if i installed all the stuff the wrong way, and um, yep
probably is my fault, as per usual.... so will keep trying as i go....

thanks for the help

---

