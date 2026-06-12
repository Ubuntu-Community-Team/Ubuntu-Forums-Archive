---
title: "aMuled keeps crashing it's Ubuntu, how can i pinpoint the crash?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-01-01
Hi,

Im using aMuled CVS from [http://forum.amule.org/index.php?topic=13700.0](http://forum.amule.org/index.php?topic=13700.0) for Ubuntu 7.10 32bit

Im following the wiki advice on ' Create a backtrace' from 

[http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

and in my post [http://forum.amule.org/index.php?topic=14081.0](http://forum.amule.org/index.php?topic=14081.0) they say it's not an aMule thing...

So if it's Ubuntu how can i pinpoint the cause of the aMuled crash as it crashes every 10 mins and aMule runs without crashing...

thanks..

---

### Post by hyper_ch on 2008-01-01
start amule from the terminal. You should get some output then of what's wrong.

And why did you complie it from CVS anyway?

---

### Post by hopelessone on 2008-01-01
Hi,

i start amuled and amule in (gdb) and no info..

I didn't compile it.... Festor from [http://forum.amule.org/index.php?topic=13700.0](http://forum.amule.org/index.php?topic=13700.0) compiles it for Ubuntu 7.10 users...

As i said aMule has no probs...aMuled has the crash where they said it an OS thing...

I upgraded from 2.1.3 because amule kept crashing...now amule CVS dosen't crash amuled does as per link...(please read first)

It's an Ubuntu thing...what can i do?

---

### Post by Xavieran on 2008-01-01
try running ```
amuled -v
``` (v should make it "verbose") from your terminal

EDIT:Sorry that should be amuled...right...

---

### Post by hopelessone on 2008-01-01
Thanks !!

box@firebox-desktop:~$ amuled -v
amuled: OnInit - starting timer
aMuled CVS using wxGTK2 v2.8.4 (Snapshot: Sun Dec 30 07:01:56 CET 2007) (OS: Linux)
box@firebox-desktop:~$ 

aMuled is not running is it supposed to?

---

### Post by hyper_ch on 2008-01-01
aMule is in the Ubutnu Repos... so I still wonder why you use the CVS one...

---

### Post by hopelessone on 2008-01-01
hyper_ch - i can understand your question... because aMule used to crash 15 times a day...after the CVS aMule NO CRASHES ...

I seen also that aMuled uses WAY LESS MEMORY(1/2)  and decided to run it...as now aMule dosen't crash but wondering why aMuled crashes frequently...

Oh yeah + better performance than 2.1.3 i.e. downloads triple speed in aMule CVS !!!

---

### Post by hopelessone on 2008-01-01
Hi,

Anyway to debug better than (GDB) ??

thanks..

---

### Post by hopelessone on 2008-01-02
----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMuled CVS using wxGTK2 v2.8.4 (Snapshot: Tue Jan  1 07:01:55 CET 2008)
Running on: Linux 2.6.22-14-generic i686

[2] std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string() in /usr/bin/amuled [0x8061451]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0xb7e405d6]
[4] ?? in [0xffffe420]
[5] ?? in /usr/bin/amuled [0x8059049]
[6] ?? in /usr/bin/amuled [0x805a486]
[7] ?? in /usr/bin/amuled [0x805a674]
[8] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0xb7dd025a]
[9] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.8.so.0[0xb7dd0307]
[10] ?? in /usr/bin/amuled [0x805a720]
[11] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb7adb050]
[12] wxIPV4address::IsLocalHost() const in /usr/bin/amuled[0x8058db1]


--------------------------------------------------------------------------------

Program received signal SIGABRT, Aborted.
0xffffe410 in __kernel_vsyscall ()
(gdb) 

any helpful information here?

thanks

---

