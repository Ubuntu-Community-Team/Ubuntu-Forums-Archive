---
title: "grip error"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by loclei on 2006-11-12
hy i've tried grip and then removed it 
and now that i've reinstalled it i get this error
```

Memory status: size: 37072896 vsize: 0 resident: 37072896 share: 0 rss: 15839232 rss_rlim: 0
CPU usage: start_time: 1163332704 rtime: 0 utime: 89 stime: 0 cutime:81 cstime: 0 timeout: 8 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/grip'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb715d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7b731b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb78feada in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#5  0x0805b63a in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1228723920 (LWP 6330)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb715d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7b731b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb78feada in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0x0805b63a in ?? ()
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```
cand someone help me?
all i want is to be able to rip cd's to mp3 format and be able to get cddb  
info through a proxy same as i use the proxy setup from firefox
thx

---

