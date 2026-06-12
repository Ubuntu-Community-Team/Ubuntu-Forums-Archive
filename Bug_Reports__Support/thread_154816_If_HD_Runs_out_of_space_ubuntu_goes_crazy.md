---
title: "If HD Runs out of space ubuntu goes crazy"
date: 2006-04-03
forum: Bug Reports / Support
---

### Post by cpscotti on 2006-04-03
I'm using 5.10

This afternoon I got a really strange error msg! My ubuntu booted ok, I entered my login/passwd and when gnome was about to start, BAM!

GDM was unable to write to permission (or authorization, or something like this) files.
This could be happening because there is no more disk space or because....

```
localhost sudo (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=myusername
```

When I saw it, ocurred to me that it could really be the thruth but but I was stuck in GDM...

So, I rebooted and entered Recovery mode, deleted some 1,2Gb and rebooted again, now comes the problem!

Gnome started and I got some software panic!

Klipper (that runned for more than 8 months perfectly in my machine) crashed with a SIGABRT signal, and "The KDE Crash Handler" annoyed me about reporting the bug and those things..
When I saw it I though:  No Problem! apt-get would fix like it did for me a thousand times!
But this time NO: I already "Complete Removed" klipper for 5 times! and the same Crash occurs always!

Another problem:
The Sticky Notes simply had lost ALL his info! I mean ALL, and I really cared about the info stored on those little pieces of text!

Reason for my post: Shouldn't ubuntu realyze (or if it does this, WARN the user!) the system is running out of disk space!

I was looking the system log and it confirms the hypotesis of no Disk Space at runtime and ubuntu didn't showed a msg for me!

the last (at the time the hd runned out of space during the last boot) msg in log says something like this:

```
localhost gconfd (nofx-7821) Failed to log addition of listener gedit (Failed: Failed to log addition of listener to gconfd logfile; won't be able to re-add the listener if gconfd exits or shuts down (No space left on device)
```

another one:

```

localhost gconfd (nofx-7821) Failed to flush client add to saved state file: No space left on device

```

thanks in advance!
(PS, my klipper continues to crash at startup!!)
(the klipper crash message concerns about bad_alloc!)

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
...
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231198528 (LWP 7670)]
(no debugging symbols found)
...
(no debugging symbols found)
[KCrash handler]
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb6a2c9d1 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb6a2e2e9 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb6c1a533 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#8  0xb6c17ed4 in __gxx_personality_v0 () from /usr/lib/libstdc++.so.6
#9  0xb6c17f11 in std::terminate () from /usr/lib/libstdc++.so.6
#10 0xb6c1809c in __cxa_throw () from /usr/lib/libstdc++.so.6
#11 0xb6c1852a in operator new () from /usr/lib/libstdc++.so.6
#12 0xb6c185fc in operator new[] () from /usr/lib/libstdc++.so.6
#13 0xb74f40f5 in operator>> () from /usr/lib/libqt-mt.so.3
#14 0xb7f5e5d0 in KlipperWidget::loadHistory ()
   from /usr/lib/libkdeinit_klipper.so
#15 0xb7f61149 in KlipperWidget::readProperties ()
   from /usr/lib/libkdeinit_klipper.so
#16 0xb7f6379c in KlipperWidget::KlipperWidget ()
   from /usr/lib/libkdeinit_klipper.so
#17 0xb7f63ffc in Klipper::Klipper () from /usr/lib/libkdeinit_klipper.so
#18 0xb7f640c9 in kdemain () from /usr/lib/libkdeinit_klipper.so
#19 0xb6a18ec2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#20 0x080485a1 in ?? ()

```

---

