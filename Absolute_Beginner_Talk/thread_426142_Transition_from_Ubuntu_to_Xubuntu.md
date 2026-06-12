---
title: "Transition from Ubuntu to Xubuntu ?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-28
Hi 

I have beeen using ubuntu(edgy) for a while and I like xubuntu(edgy) better: it is simpler and faster.  I could not install xubuntu from live cd, cd gave errors (I tried a couple of CD, stg like hd error) but ubuntu and windows work on it nicely, so I could not understand the reson. 

Then I installed xubuntu desktop on ubuntu by synaptic. Is there away to get rid of now ubuntu and its many packets? Would it help my computer performance? (I want to mention again that I installed xubuntu desktop on buntu synaptic.

thank you
findik

---

### Post by Najand on 2007-04-28
Look at:
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by findik1 on 2007-04-28
I want to also add that, arch time I login to Xubuntu I get a bug report like this, does anyboy know why and how to correct it? 
> The information about the crash has been successfully collected.

The application that crashed is not known to bug-buddy, therefore the bug report can not be sent to the GNOME Bugzilla.  Please save the bug to a text file and report it to the appropriate bug tracker for this application./QUOTE]

[QUOTE]Memory status: size: 26517504 vsize: 0 resident: 26517504 share: 0 rss: 9273344 rss_rlim: 0
CPU usage: start_time: 1177766175 rtime: 0 utime: 10 stime: 0 cutime:9 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0

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
[New Thread -1232947536 (LWP 4498)]
[New Thread -1234240608 (LWP 4503)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb72b46cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7dd71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb724f770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7250ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7421122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7421159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1234240608 (LWP 4503)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72e9803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb741b813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb741bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb79b57e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb743638f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb705e504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72f351e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1232947536 (LWP 4498)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b46cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7dd71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb724f770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7250ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7421122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7421159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


---

### Post by findik1 on 2007-04-28
> **Najand said:**
> Look at:
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)


Thank you, that answers my first issue, that was fast!

----------------------------------------------------------------------

Second issue (bug) may be related to my DVD drive?  Since this is only a DVD drive and for some reason I can install ubuntu cd but not xubuntu cd. And some a few data CD that I created cannot be opened on Xubuntu but definitely I used it to install some files on Ubuntu. Any idea what's happening? On Xubuntu : my dataCD does not open automatically but everything was OK on ubuntu.

thanks in advance
findik

---

