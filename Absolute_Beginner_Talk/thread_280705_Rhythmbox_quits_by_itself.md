---
title: "Rhythmbox quits by itself"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by klato on 2006-10-19
I've just started messing about with Rhythmbox, and whenever I am playing a track, the program will just immediately quit by itself...no warning messages or anything.  Anyone with a similar experience?

Thanks.

---

### Post by mun3kh on 2006-10-20
I am having a similar experience today. I click to load Rhythmbox, and it quits by itself before it can load. I am running Edgy
 Eft, currently the development version and rhythmbox  was working yesterday. I grabbed some updates this morning
 though before trying to load rhythmbox.

I ran it in a terminal, with -d and this is the output:
```

ian@ian-desktop:~$ rhythmbox -d
(10:08:39) [0x8161118] [rb_debug_init_match] rb-debug.c:141: Debugging enabled
(10:08:39) [0x8161118] [main] main.c:204: initializing Rhythmbox 0.9.6
(10:08:39) [0x8161118] [main] main.c:212: going to create DBus object
(10:08:39) [0x8161118] [main] main.c:399: THE END
ian@ian-desktop:~$

```

I have the rhythmbox-dbg package installed, so I ran it in gdb, and
this is what I saw

```

ian@ian-desktop:~$ gdb rhythmbox
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /usr/bin/rhythmbox 
[Thread debugging using libthread_db enabled]
[New Thread -1229101392 (LWP 20907)]
[New Thread -1230394464 (LWP 20913)]
[Thread -1230394464 (LWP 20913) exited]

Program exited normally.
(gdb)

```

I was in #lugradio at the time, so asked for some help. mrben came
back with a suggestion to try a music file as a command line argument.
Here it is, terminal, then gdb.
```

ian@ian-desktop:~$ rhythmbox audio/music/The\ Hives/Tyrannosaurus\ Hives/01-The\ Hives-Abra\ Cadaver.mp3 -d
(10:30:45) [0x8161308] [rb_debug_init_match] rb-debug.c:141: Debugging enabled
(10:30:45) [0x8161308] [main] main.c:204: initializing Rhythmbox 0.9.6
(10:30:45) [0x8161308] [main] main.c:212: going to create DBus object
(10:30:45) [0x8161308] [load_uri_args] main.c:417: examining argument audio/music/The Hives/Tyrannosaurus Hives/01-The Hives-Abra Cadaver.mp3
(10:30:45) [0x8161308] [dbus_load_uri] main.c:435: Sending loadURI for file:///home/ian/audio/music/The%20Hives/Tyrannosaurus%20Hives/01-The%20Hives-Abra%20Cadaver.mp3

ian@ian-desktop:~$

```
I did a CTRL-c in gdb, then a bt to see a trace
```

ian@ian-desktop:~$ gdb rhythmbox
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run audio/music/The\ Hives/Tyrannosaurus\ Hives/01-The\ Hives-Abra\ Cadaver.mp3
Starting program: /usr/bin/rhythmbox audio/music/The\ Hives/Tyrannosaurus\ Hives/01-The\ Hives-Abra\ Cadaver.mp3
[Thread debugging using libthread_db enabled]
[New Thread -1229031760 (LWP 20919)]

Program received signal SIGINT, Interrupt.
[Switching to Thread -1229031760 (LWP 20919)]
0xffffe410 in __kernel_vsyscall ()
(gdb) bt
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6e987cb in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b13c6b in dbus_malloc () from /usr/lib/libdbus-1.so.3
#3  0xb7b0dae9 in dbus_threads_init_default () from /usr/lib/libdbus-1.so.3
#4  0xb7b0c1cc in dbus_threads_init_default () from /usr/lib/libdbus-1.so.3
#5  0xb7af81fd in dbus_connection_set_watch_functions () from /usr/lib/libdbus-1.so.3
#6  0xb7af923b in dbus_connection_flush () from /usr/lib/libdbus-1.so.3
#7  0xb7b065b1 in dbus_pending_call_block () from /usr/lib/libdbus-1.so.3
#8  0xb7b501a8 in dbus_g_proxy_cancel_call () from /usr/lib/libdbus-glib-1.so.2
#9  0xb7b50d89 in dbus_g_proxy_call () from /usr/lib/libdbus-glib-1.so.2
#10 0x0806c1f7 in dbus_load_uri (
    filename=0x81e49b8 "file:///home/ian/audio/music/The%20Hives/Tyrannosaurus%20Hives/01-The%20Hives-Abra%20Cadaver.mp3", 
    proxy=0x81e5658) at main.c:436
#11 0x0806c089 in main (argc=2, argv=0xbfc4db74) at main.c:422
(gdb)

```

I'm not sure where to go next, but I'm considering filing a bug. Would be nice to get some feedback from some forum ninjas first though.

---

### Post by doclivingston on 2006-10-21
The debug log indicates that Rhythmbox is already running, and it isn't starting a second copy. When you do this, it should bring up the first window though.

---

