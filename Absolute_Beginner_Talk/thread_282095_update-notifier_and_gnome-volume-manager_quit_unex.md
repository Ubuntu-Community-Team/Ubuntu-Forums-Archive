---
title: "update-notifier and gnome-volume-manager quit unexpectedly..."
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-10-22
When I just logged in this morning I was informed of the following:

[B]The application "update-notifier" has quit unexpectedly.

The application "gnome-volume-manager" has quit unexpectedly.[/B]

I clicked close on each one then went to the terminal and tried:

```
caravel@caravel-desktop:~$ sudo update-notifier
Password:
libnotify-Message: Unable to get session bus: No reply within specified time

** (update-notifier:5251): WARNING **: not starting because user is not in admin group

caravel@caravel-desktop:~$

```

then...

```
caravel@caravel-desktop:~$ sudo gnome-volume-manager
caravel@caravel-desktop:~$
```

gnome-volume-manager appears to restart as it's still there in the sytem monitor.  Update-notifier is not.

I searched the forums and found a thread where two people had the same problem and no one answered.  Though they had were trying to use XGL, wheras I'm not.

---

### Post by Najand on 2006-10-22
Hmm, Can you restart your gnome and see if it works afterwards or not?
For restarting X&#12289;use:
LEFT CTRL+LEFT ALT+BACKSPACE 
and see if it works like before or not?

---

### Post by caravel on 2006-10-22
I have just done it and the two crash error messages are still appearing...

---

### Post by Najand on 2006-10-22
Can you tell me what are the crash messages?

---

### Post by caravel on 2006-10-22
Hi I hope this is the correct dump info.

```
Backtrace was generated from '/usr/bin/update-notifier'

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
[Thread debugging using libthread_db enabled]
[New Thread -1224358208 (LWP 9059)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb745e463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eda8e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7af3c9c in libhal_ctx_new () from /usr/lib/libhal.so.1
#5  0x08050ea7 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1224358208 (LWP 9059)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb745e463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eda8e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7af3c9c in libhal_ctx_new () from /usr/lib/libhal.so.1
No symbol table info available.
#5  0x08050ea7 in ?? ()
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

```
Backtrace was generated from '/usr/bin/gnome-volume-manager'

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
[Thread debugging using libthread_db enabled]
[New Thread -1223608640 (LWP 9067)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7515463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f778e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7b95c9c in libhal_ctx_new () from /usr/lib/libhal.so.1
#5  0x0804e992 in ?? ()
#6  0xb75e4abc in g_param_spec_types () from /usr/lib/libgobject-2.0.so.0
#7  0xb75c23e0 in g_signal_accumulator_true_handled ()
   from /usr/lib/libgobject-2.0.so.0
#8  0x0804f452 in ?? ()
#9  0x08063c00 in ?? ()
#10 0x080531f7 in _IO_stdin_used ()
#11 0x080525c9 in ?? ()
#12 0x00000000 in ?? ()

Thread 1 (Thread -1223608640 (LWP 9067)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7515463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f778e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7b95c9c in libhal_ctx_new () from /usr/lib/libhal.so.1
No symbol table info available.
#5  0x0804e992 in ?? ()
No symbol table info available.
#6  0xb75e4abc in g_param_spec_types () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb75c23e0 in g_signal_accumulator_true_handled ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0x0804f452 in ?? ()
No symbol table info available.
#9  0x08063c00 in ?? ()
No symbol table info available.
#10 0x080531f7 in _IO_stdin_used ()
No symbol table info available.
#11 0x080525c9 in ?? ()
No symbol table info available.
#12 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

Thanks for your help.

Regards

Caravel

---

### Post by caravel on 2006-10-22
Well I've tried everything I can think of.  I've reinstalled both programs to no avail, done killall gnome-panel, killall update-notifier and restarted the x server and it's still there.  I can't find anything relating to  this one the net either.

Any other ideas before I give up?

---

### Post by caravel on 2006-10-22
Bump

](*,) ](*,) ](*,) ](*,)

-Edit: Nevermind I've installed Fedora Core. =;

---

