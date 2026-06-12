---
title: "Bug Buddy in Xfce4"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by X86 on 2007-03-18
hey I and getting this error message when I login to Xfce4
Bug Buddy comes up everytime I log in... should I remove evolution-alarm-notify?

Memory status: size: 51834880 vsize: 0 resident: 51834880 share: 0 rss: 9695232 rss_rlim: 0
CPU usage: start_time: 1174254652 rtime: 0 utime: 54 stime: 0 cutime:44 cstime: 0 timeout: 10 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-alarm-notify'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233189200 (LWP 4621)]
[New Thread -1243124832 (LWP 4664)]
[New Thread -1234465888 (LWP 4629)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)Memory status: size: 51834880 vsize: 0 resident: 51834880 share: 0 rss: 9695232 rss_rlim: 0
CPU usage: start_time: 1174254652 rtime: 0 utime: 54 stime: 0 cutime:44 cstime: 0 timeout: 10 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-alarm-notify'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233189200 (LWP 4621)]
[New Thread -1243124832 (LWP 4664)]
[New Thread -1234465888 (LWP 4629)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb727a6cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d9e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7215770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7216ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb73e7122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb73e7159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 3 (Thread -1234465888 (LWP 4629)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72af803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb73e1813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb73e1b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb797b7e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb73fc38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7023504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72b951e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 2 (Thread -1243124832 (LWP 4664)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7026816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb72c5a3d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#3  0xb7c0bdc2 in e_cal_remove () from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#4  0xb7c0c124 in e_cal_remove () from /usr/lib/libecal-1.2.so.7
No symbol table info available.
#5  0xb73fc38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7023504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72b951e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1233189200 (LWP 4621)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb727a6cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7d9e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7215770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7216ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb73e7122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb73e7159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by Skia_42 on 2007-03-18
[This thread]("http://www.ubuntuforums.org/showthread.php?t=311258") should solve your problem.

---

### Post by X86 on 2007-03-18
nice thanks lol

---

### Post by X86 on 2007-03-18
unfortunately this did not work.... 

rm .recently-used.xbel

still getting the error with the Bug 
what I'm doing wrong?
Thanks :-)

---

### Post by X86 on 2007-03-18
going to go and EaT Me SoMe PeAcHe'S

---

