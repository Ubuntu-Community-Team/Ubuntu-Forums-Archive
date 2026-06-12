---
title: "Weird Bug report on Xubuntu but not on Ubuntu !!!!"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-04-28
Hi,

I reposting again since I wont be able to connect to the internet anymore, I dont have internet at home, so I want to fix this bug while I brought here at my office. Thanks you.

Whenever I login into Xubuntu get a bug report like this, does anyboy know why and how to correct it?
I installed xubuntu desktop on ubuntu by synaptic. Is there away to get rid of now ubuntu and its many packets? Would it help my computer performance? (I want to mention again that I installed xubuntu desktop on ubuntu synaptic.

Bug may be related to my DVD drive? Since this is only a DVD drive and for some reason I can install ubuntu cd but not xubuntu cd. And some a few data CD that I created cannot be opened on Xubuntu but definitely I used it to install some files on Ubuntu. Any idea what's happening? On Xubuntu : my dataCD does not open automatically but everything was OK on ubuntu.

The bug report:

*The information about the crash has been successfully collected. The application that crashed is not known to bug-buddy, therefore the bug report can not be sent to the GNOME Bugzilla. Please save the bug to a text file and report it to the appropriate bug tracker for this application*
```
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
[New Thread -1232947536 (LWP 449]
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
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb72b46cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2 0xb7dd71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3 <signal handler called>
#4 0xffffe410 in __kernel_vsyscall ()
#5 0xb724f770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6 0xb7250ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7 0xb7421122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8 0xb7421159 in g_log () from /usr/lib/libglib-2.0.so.0
#9 0x0805d500 in main ()

Thread 2 (Thread -1234240608 (LWP 4503)):
#0 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1 0xb72e9803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2 0xb741b813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3 0xb741bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4 0xb79b57e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5 0xb743638f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6 0xb705e504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7 0xb72f351e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1232947536 (LWP 449):
#0 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1 0xb72b46cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2 0xb7dd71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3 <signal handler called>
No symbol table info available.
#4 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5 0xb724f770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6 0xb7250ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7 0xb7421122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8 0xb7421159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9 0x0805d500 in main ()
No symbol table info available.
#0 0xffffe410 in __kernel_vsyscall ()
```

---

### Post by findik1 on 2007-04-28
Bug report solved!!!! I just uninstall Evolution...

Any idea why I canNOT read one of me my dataCD from my DVD drive? I can read it in Ubuntu. I was supposed to install a software in this drive but it does not open.  THis may be related to similar problem that Xubuntu live CD did not work to install, but Ubuntu worked, that's why firts I installed Ubuntu then from Synaptic of Ubuntu, I installed Xubuntu desktop

---

### Post by findik1 on 2007-04-28
> **findik1 said:**
> Bug report solved!!!! I just uninstall Evolution...

Any idea why I canNOT read one of me my dataCD from my DVD drive? I can read it in Ubuntu. I was supposed to install a software in this drive but it does not open.  THis may be related to similar problem that Xubuntu live CD did not work to install, but Ubuntu worked, that's why firts I installed Ubuntu then from Synaptic of Ubuntu, I installed Xubuntu desktop

Open CD issue is also resolved. Cd was created with K3b, and after I installed K3b on Xubuntu now Xubuntu sees CD when I put it on the drive. I dont know why I had to install K3B to see my data CD but, that's OK

---

