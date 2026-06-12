---
title: "Gnome-Panel Problem-"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Darrious on 2007-01-16
I'm having a problem with my gnome-panel. 

It just won't work. It keeps on just freezing up so that I can't click on it, and something called Bug Buddy pops up saying this.

```
Memory status: size: 36143104 vsize: 0 resident: 36143104 share: 0 rss: 13660160 rss_rlim: 0
CPU usage: start_time: 1168994343 rtime: 0 utime: 69 stime: 0 cutime:66 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

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
[New Thread -1225165136 (LWP 4707)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb764e323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f461b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7536770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7537ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7752122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7752159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77521d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7ba1d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7ba1dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b9d591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7747aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7749802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb774c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb774cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b4b574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225165136 (LWP 4707)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb764e323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f461b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7536770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7537ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7752122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7752159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77521d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7ba1d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7ba1dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b9d591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7747aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7749802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb774c7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb774cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b4b574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```This has happened before. I think it happened right after using reconstructor. 
Although I know that it is not reconstructor. Because I burn my iso, then the live cd does not work, and I go back into Ubuntu, and this error pops up. 

I tried running gnome-panel from the terminal, and it works, but it flashes on and off whenever I put my mouse over it. 

And  my package manager does not work aka. synaptic.

Also, everything in firfox is reset and in evolution too. I mean that the bookmarks are gone, and all of my information to get my email also. But those are the only ones I checked.
.................Just now, Firefox turned off because I went to my terminal and clicked control-c and it stopped the gnome panel and Firefox. I'm going to try to see if I can install packages with the terminal and see how I do.

---

### Post by riven0 on 2007-01-16
Not exactly sure on the solution, but have you tried doing a re-installation of gnome-panel?: 
> 
sudo apt-get install --reinstall gnome-panel gnome-panel-data 

---

### Post by ComplexNumber on 2007-01-16
**Darrious**
has it always been like that, or is there any event(maybe installation or uninstallation of a piece of software) before it started misbehaving?

---

### Post by Darrious on 2007-01-17
I tried reinstalling the gnome-panel although it did not work and, this has only happened once before. It was just after using the live cd. 

I brought up reconstructor, and made a live cd. Although, when I reboot, the live cd does not work. All it does is just show the boot screen when the live cd starts. I try to boot into the live cd, but it says some type of error has occured. 

So then I eject the cd, and boot into Ubuntu, but it always comes up with an error saying this

> Memory status: size: 36065280 vsize: 0 resident: 36065280 share: 0 rss: 13484032 rss_rlim: 0
CPU usage: start_time: 1169063663 rtime: 0 utime: 71 stime: 0 cutime:68 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

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
[New Thread -1225800016 (LWP 12004)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb75b3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eab1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb749b770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb749cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76b7122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76b7159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76b71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b06d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b06dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b02591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76acaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76ae802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76b17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76b1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ab0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225800016 (LWP 12004)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75b3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eab1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb749b770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb749cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76b7122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76b7159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76b71d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b06d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b06dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b02591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76acaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76ae802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76b17df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76b1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ab0574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
So it only happens whenever I boot the live cd made with reconstructor. But the live cd has never worked.

---

### Post by Darrious on 2007-01-17
bump

---

### Post by jd65pl on 2007-01-17
Post a bug report with the information you have. Maybe the developer can find a solution. I don't think many people in here will be able to find a solution to your problem with a 60% incomplete error message. You could check /var/log for any other debug information available.

---

### Post by Darrious on 2007-01-17
Okay, but I'm not really sure what I'm going to look for in /var/log and I've already submitted it, but got nothin.

---

