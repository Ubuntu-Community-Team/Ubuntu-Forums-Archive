---
title: "Counter Strike 1.6 + AMD"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-06-21
Hello people
Ive just changed my old computer and shifted to an AMD 64 X2 3800+ Processor...
I ran the Counter strike 1.6 server with ease on the previous computer
But on this system whenever i try to run the server...
```

./hlds_run -game cstrike -insecure -nomaster
```

It gives me the following output.... 
```

Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash

Console initialized.
scandir failed:/home/ashish/hlds/./platform/SAVE
Protocol version 47
Exe version 1.1.2.5/Stdio (cstrike)
Exe build: 02:38:45 Jul  7 2004 (2738)
STEAM Auth Server
couldn't exec language.cfg
Server IP address 127.0.1.1:27015
   
   Metamod version 1.19p28 Copyright (c) 2001-2006 Will Day
     Patch: Metamod-P (mm-p) v28 Copyright (c) 2004-2006 Jussi Kivilinna
   Metamod comes with ABSOLUTELY NO WARRANTY; for details type `meta gpl'.
   This is free software, and you are welcome to redistribute it
   under certain conditions; type `meta gpl' for details.
   
*** glibc detected *** ./hlds_amd: free(): invalid pointer: 0x080b45b1 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7def8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7defa44]
./cstrike/addons/metamod/dlls/metamod_i386.so[0xb47877d8]
======= Memory map: ========
08048000-08053000 r-xp 00000000 08:07 1261851    /home/ashish/hlds/hlds_amd
08053000-0805b000 rwxp 0000a000 08:07 1261851    /home/ashish/hlds/hlds_amd
0805b000-080c7000 rwxp 0805b000 00:00 0          [heap]
b4300000-b4321000 rwxp b4300000 00:00 0 
b4321000-b4400000 ---p b4321000 00:00 0 
b44e7000-b46af000 r-xp 00000000 08:07 1277955    /home/ashish/hlds/cstrike/dlls/cs_i386.so
b46af000-b46cd000 rwxp 001c7000 08:07 1277955    /home/ashish/hlds/cstrike/dlls/cs_i386.so
b46cd000-b4784000 rwxp b46cd000 00:00 0 
b4784000-b47a6000 r-xp 00000000 08:07 49794      /home/ashish/hlds/cstrike/addons/metamod/dlls/metamod_i386.so
b47a6000-b47a8000 rwxp 00022000 08:07 49794      /home/ashish/hlds/cstrike/addons/metamod/dlls/metamod_i386.so
b47a8000-b47b2000 rwxp b47a8000 00:00 0 
b47b2000-b47bb000 r-xp 00000000 08:08 582996     /lib/tls/i686/cmov/libnss_files-2.4.so
b47bb000-b47bd000 rwxp 00008000 08:08 582996     /lib/tls/i686/cmov/libnss_files-2.4.so
b47cb000-b746e000 rwxp b47cb000 00:00 0 
b748b000-b74a6000 r-xp 00000000 08:07 1261850    /home/ashish/hlds/filesystem_stdio_i386.so
b74a6000-b74ad000 rwxp 0001a000 08:07 1261850    /home/ashish/hlds/filesystem_stdio_i386.so
b74ad000-b74af000 rwxp b74ad000 00:00 0 
b74af000-b7676000 r-xp 00000000 08:07 1261840    /home/ashish/hlds/libSteamValidateUserIDTickets_i386.so
b7676000-b76c4000 rwxp 001c6000 08:07 1261840    /home/ashish/hlds/libSteamValidateUserIDTickets_i386.so
b76c4000-b76c7000 rwxp b76c4000 00:00 0 
b76c7000-b78b6000 r-xp 00000000 08:07 1261794    /home/ashish/hlds/engine_amd.so
b78b6000-b78f0000 rwxp 001ee000 08:07 1261794    /home/ashish/hlds/engine_amd.so
b78f0000-b7d89000 rwxp b78f0000 00:00 0 
b7d89000-b7eb6000 r-xp 00000000 08:08 582987     /lib/tls/i686/cmov/libc-2.4.so
b7eb6000-b7eb8000 r-xp 0012c000 08:08 582987     /lib/tls/i686/cmov/libc-2.4.so
b7eb8000-b7eba000 rwxp 0012e000 08:08 582987     /lib/tls/i686/cmov/libc-2.4.so
b7eba000-b7ebd000 rwxp b7eba000 00:00 0 
b7ebd000-b7ee1000 r-xp 00000000 08:08 582991     /lib/tls/i686/cmov/libm-2.4.so
b7ee1000-b7ee3000 rwxp 00023000 08:08 582991     /lib/tls/i686/cmov/libm-2.4.so
b7ee3000-b7ee4000 rwxp b7ee3000 00:00 0 
b7ee4000-b7ef3000 r-xp 00000000 08:08 583001     /lib/tls/i686/cmov/libpthread-2.4.so
b7ef3000-b7ef5000 rwxp 0000f000 08:08 583001     /lib/tls/i686/cmov/libpthread-2.4.so
b7ef5000-b7ef7000 rwxp b7ef5000 00:00 0 
b7ef7000-b7ef8000 rwxp 00000000 08:08 582990     /lib/tls/i686/cmov/libdl-2.4.so
b7ef8000-b7ef9000 r-xp 00001000 08:08 582990     /lib/tls/i686/cmov/libdl-2.4.so
b7ef9000-b7efb000 rwxp 00001000 08:08 582990     /lib/tls/i686/cmov/libdl-2.4.so
b7efd000-b7f07000 r-xp 00000000 08:08 550595     /lib/libgcc_s.so.1
b7f07000-b7f08000 rwxp 00009000 08:08 550595     /lib/libgcc_s.so.1
b7f08000-b7f0c000 rwxp b7f08000 00:00 0 
b7f0c000-b7f25000 r-xp 00000000 08:08 550532     /lib/ld-2.4.so
b7f25000-b7f27000 rwxp 00018000 08:08 550532     /lib/ld-2.4.so
bfd1f000-bfd35000 rwxp bfd1f000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted (core dumped)
Add "-debug" to the ./hlds_run command line to generate a debug.log to help with solving this problem
Fri Jun 22 00:16:06 IST 2007: Server restart in 10 seconds
Fri Jun 22 00:16:07 IST 2007: Server Quit

```

Im utterly confused , 
Thanks :)

---

### Post by Obeleh on 2007-06-21
> **ashmew2 said:**
> 
```

Add "-debug" to the ./hlds_run command line to generate a debug.log to help with solving this problem

```

Thats the only line that makes sense to me ;)

---

### Post by ashmew2 on 2007-06-21
Well i was thinking of doing it first , but i thought it wudnt be needed :)
But here ya go mate ..

Debug.log contains these lines :

----------------------------------------------
CRASH: Fri Jun 22 00:31:57 IST 2007
Start Line: ./hlds_amd -game cstrike -nomaster +maxplayers 18 +map de_dust2 +ip 192.168.1.3 -debug -pidfile hlds.6292.pid
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
End of crash report
----------------------------------------------
Hope it really helps...

Im waitin to play cs !! :D

---

### Post by Obeleh on 2007-06-21
Doesnt really say why it crashed.

Maybe running steamupdate could help? If i remember right it overwrites everything thats not exactly as it should be. And adds everything that isnt there yet

---

### Post by ashmew2 on 2007-06-21
Yah..but come on!Am i the only one with this problem ? :((

---

### Post by ashmew2 on 2007-07-22
People , i really need to get this working...plz help me
will installing 64 bit Ubuntu help ??

---

