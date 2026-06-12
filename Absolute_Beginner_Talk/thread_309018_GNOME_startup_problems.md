---
title: "GNOME startup problems"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-11-29
In both Dapper and Edgy, I keep having a weird startup problem.  I can get to the login screen fine, but once I log in, 99% of the time instead of getting the GNOME splash screen after a few seconds, I see a blank desktop for a few minutes and then a white box that I think is a terminal window (but without the title bar or border... or any text) pops up and nothing happens for around 10-15 minutes.  At that time, GNOME starts up but with a different theme to the one I want, and I get a message saying that there was an error with gnome-settings-daemon.  Then if I launch the gnome-settings-daemon from the terminal or a launcher, everything goes back to the way it should be.  The weird thing is, if I log out and back in without actually rebooting, everything usually goes fine.

Anyone know what's causing this?

---

### Post by Sef on 2006-11-29
What is your graphics card and system specs?

---

### Post by crazybrit4967 on 2006-11-29
> **Sef said:**
> What is your graphics card and system specs?AMD Athlon XP 3000+ (2.16 GHz, I think)
ATI Radeon 9600, 256 MB (But I had the same problem with a 9250)
1 GB of RAM

Also, I never seem to have this problem when I boot up from a completely fresh install, so I'm guessing one of the packages I've installed or a setting I changed has messed something up.

---

### Post by crazybrit4967 on 2006-11-29
Does anyone know?  Also, if it helps, when I start gnome-settings-daemon in a terminal window I get messages saying things like "line 343 conflicts with line 224".  I would post the exact output, but I can't even get Ubuntu to start up at the moment. :(

---

### Post by crazybrit4967 on 2006-11-29
Okay, I logged into the failsafe terminal setting and launched gnome-settings-daemon, which returned the following:

```
(gnome-settings-daemon:5123): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (gnome-settings-daemon:5123): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:5123): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:5123): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
```


Can anyone make sense of any of that?

Edit- by the way, that's not the same message I get when I launch gnome-settings-daemon from a terminal window in GNOME

Also, a Bug Buddy window just popped up with the following info about gnome-settings-daemon:

```
Memory status: size: 28184576 vsize: 0 resident: 28184576 share: 0 rss: 7098368 rss_rlim: 0
CPU usage: start_time: 1164846162 rtime: 0 utime: 8 stime: 0 cutime:6 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-settings-daemon'

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
[Thread debugging using libthread_db enabled]
[New Thread -1226029392 (LWP 5123)]
[New Thread -1227289696 (LWP 5125)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb784e34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f4b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0806915d in keyboard_config_registry_get_type ()
#5  0xb787e89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#6  0xb7865952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#7  0xb7863bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#8  0xb786473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#9  0xb78648f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
#11 0x080551ea in gnome_settings_daemon_new ()
#12 0x08053efc in main ()

Thread 2 (Thread -1227289696 (LWP 5125)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb784d3fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb77b545d in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb77d238f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7847504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb770551e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1226029392 (LWP 5123)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb784e34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f4b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0806915d in keyboard_config_registry_get_type ()
No symbol table info available.
#5  0xb787e89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb7865952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb7863bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb786473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb78648f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
No symbol table info available.
#11 0x080551ea in gnome_settings_daemon_new ()
No symbol table info available.
#12 0x08053efc in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by DaveHartburn on 2006-11-30
I have exactly the same problem after upgrading Daper to Edgy, so at least you are not alone. I don't know how to solve it either!

---

### Post by DaveHartburn on 2006-11-30
Searching other threads, it appears the dbus variables are not being set, and you need to run:
eval `dbus-launch --auto-syntax`

As I'm connecting to my machine over VNC, I've put this in my xstartup file.

Find the most suitable place to put it for you and that should do the job.

---

### Post by hanshan on 2006-11-30
Did you (the OP) get this sorted out yet? I experienced this problem a couple of days ago, and discovered that my firewall was responsible - I had to enable all traffic on the loopback (lo) device to get things working.

---

