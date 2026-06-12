---
title: "Problems using Mono"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Kikuta on 2008-04-15
Hi when I try to get RatioMaster working by using mono, this is what I get:
> ******@******-desktop:~$ mono /home/name/RatioMaster.exe

** (/home/name/RatioMaster.exe:6736): WARNING **: The following assembly referenced from /home/name/RatioMaster.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/name).


** (/home/name/RatioMaster.exe:6736): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (/home/name/RatioMaster.exe:6736): WARNING **: Missing method EnableVisualStyles in assembly /home/name/RatioMaster.exe, type System.Windows.Forms.Application
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x8176370]
        mono [0x817699e]
        mono [0x8176a98]
        mono [0x8176f2d]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d52050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210865968 (LWP 6736)]
[New Thread -1220744304 (LWP 6738)]
[New Thread -1214989424 (LWP 6737)]
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
  3 Thread -1214989424 (LWP 6737)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220744304 (LWP 6738)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210865968 (LWP 6736)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214989424 (LWP 6737)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eb79f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb794b3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220744304 (LWP 6738)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eb4676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb78b81dc in ?? ()
#4  0xb78b81c4 in ?? ()
#5  0xb7eb2541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb78b81dc in ?? ()
#8  0xb78b81c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210865968 (LWP 6736)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e08301 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f27780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f27b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bf5844 in ?? ()
#6  0xb7bf582c in ?? ()
#7  0xb7bf5828 in ?? ()
#8  0xb7bf5824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

Anyone have ideas on what's gone wrong? Thanks in advance :)

---

### Post by Cadmus on 2008-04-15
Hmm, it seems it can't find System.Windows.Forms

Does that even come with mono or is it MS only?

---

### Post by Kikuta on 2008-04-15
> **Cadmus said:**
> Hmm, it seems it can't find System.Windows.Forms

Does that even come with mono or is it MS only?

I'm not sure if it comes with mono or not, but it does sound like it originates from MS. I've just tried using the same mono command to run RM through root which showed a window of RM, but if I click on the tabs it freezes (yet my mouse can move but unable to click on anything, hence I have to use the power button to shut down :( )

---

### Post by Kikuta on 2008-04-16
Now, I've just managed to narrow down the errors:
> ******@******-desktop:~$ mono /home/name/RatioMaster.exe

Unhandled Exception: System.NotImplementedException: The requested feature is not implemented.
  at System.Threading.SynchronizationContext.SetSynchronizationContext (System.Threading.SynchronizationContext syncContext) [0x00000] 
  at System.Windows.Forms.Control..ctor () [0x00000] 
  at System.Windows.Forms.ScrollableControl..ctor () [0x00000] 
  at System.Windows.Forms.ContainerControl..ctor () [0x00000] 
  at System.Windows.Forms.Form..ctor () [0x00000] 
  at RatioMaster_source.NewVersionForm..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) RatioMaster_source.NewVersionForm:.ctor ()
  at RatioMaster_source.MainForm..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) RatioMaster_source.MainForm:.ctor ()
  at RatioMaster_source.Program.Main () [0x00000] 


I wonder what's wrong now?

---

