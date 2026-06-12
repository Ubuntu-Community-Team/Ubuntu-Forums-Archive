---
title: "Simulation of wireless TFRC tcl"
date: 2013-04-23
forum: Any Other OS
---

### Post by ines8989 on 2013-04-23
Hi . i 'am newer at tcl deelopping and ns2 . i have simulated a script tcl for wireless scénario with ns2.35 with linux mint version .
I have this result 

```
num_nodes is set 8
INITIALIZE THE LIST xListHead
Starting Simulation...
channel.cc:sendUp - Calc highestAntennaZ_ and distCST_
highestAntennaZ_ = 1.5,  distCST_ = 550.0
SORTING LISTS ...DONE!
*** buffer overflow detected ***: ns terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0xdb48d5]
/lib/i386-linux-gnu/libc.so.6(+0xe66d7)[0xdb36d7]
/lib/i386-linux-gnu/libc.so.6(+0xe5a0d)[0xdb2a0d]
ns(_ZN8CMUTrace10nam_formatEP6Packeti+0x97)[0x81fb527]
ns(_ZN8CMUTrace6formatEP6PacketPKc+0x66)[0x81fbdf6]
ns(_ZN8CMUTrace4recvEP6PacketP7Handler+0x44)[0x81fc124]
ns(_ZN13TfrcSinkAgent7nextpktEd+0x18)[0x82504d8]
ns(_ZN13TfrcSinkAgent4recvEP6PacketP7Handler+0x2fe)[0x825084e]
ns(_ZN8DSRAgent19handlePacketReceiptER8SRPacket+0x17f)[0x820edbf]
ns(_ZN8DSRAgent4recvEP6PacketP7Handler+0x38f)[0x821160f]
ns(_ZN8NsObject6handleEP5Event+0x1f)[0x813472f]
ns(_ZN9Scheduler3runEv+0x3f)[0x813348f]
ns(_ZN9Scheduler7commandEiPKPKc+0x3e4)[0x8133954]
ns(_ZN8TclClass12dispatch_cmdEPvP10Tcl_InterpiPPKc+0x32)[0x82da146]
/usr/lib/libotcl.so.1(+0x2221)[0x711221]
/usr/lib/libtcl8.5.so.0(TclInvokeStringCommand+0x77)[0x7cffb7]
/usr/lib/libtcl8.5.so.0(+0x1e95e)[0x7d195e]
/usr/lib/libtcl8.5.so.0(+0x675d8)[0x81a5d8]
/usr/lib/libtcl8.5.so.0(+0x64863)[0x817863]
/usr/lib/libtcl8.5.so.0(+0x69263)[0x81c263]
/usr/lib/libtcl8.5.so.0(TclObjInterpProcCore+0x131)[0x8634a1]
/usr/lib/libtcl8.5.so.0(TclObjInterpProc+0x69)[0x863359]
/usr/lib/libtcl8.5.so.0(TclInvokeObjectCommand+0xe3)[0x7d00c3]
/usr/lib/libotcl.so.1(+0x23a1)[0x7113a1]
/usr/lib/libtcl8.5.so.0(TclInvokeStringCommand+0x77)[0x7cffb7]
/usr/lib/libtcl8.5.so.0(+0x1e95e)[0x7d195e]
/usr/lib/libtcl8.5.so.0(+0x675d8)[0x81a5d8]
/usr/lib/libtcl8.5.so.0(TclObjInterpProcCore+0x131)[0x8634a1]
/usr/lib/libtcl8.5.so.0(TclObjInterpProc+0x69)[0x863359]
/usr/lib/libtcl8.5.so.0(TclInvokeObjectCommand+0xe3)[0x7d00c3]
/usr/lib/libotcl.so.1(+0x2221)[0x711221]
/usr/lib/libtcl8.5.so.0(TclInvokeStringCommand+0x77)[0x7cffb7]
/usr/lib/libtcl8.5.so.0(+0x1e95e)[0x7d195e]
/usr/lib/libtcl8.5.so.0(+0x1f7d4)[0x7d27d4]
/usr/lib/libtcl8.5.so.0(Tcl_EvalEx+0x3b)[0x7d216b]
/usr/lib/libtcl8.5.so.0(Tcl_FSEvalFileEx+0x29c)[0x841f9c]
/usr/lib/libtcl8.5.so.0(Tcl_Main+0x426)[0x8496c6]
ns(nslibmain+0x1f)[0x82d94df]
ns(main+0x1b)[0x812ab6b]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0xce6113]
ns[0x812ab91]
======= Memory map: ========
00110000-00113000 r-xp 00000000 08:01 134973     /lib/i386-linux-gnu/libdl-2.13.so
00113000-00114000 r--p 00002000 08:01 134973     /lib/i386-linux-gnu/libdl-2.13.so
00114000-00115000 rw-p 00003000 08:01 134973     /lib/i386-linux-gnu/libdl-2.13.so
00115000-0011d000 r-xp 00000000 08:01 134999     /lib/i386-linux-gnu/libnss_compat-2.13.so
0011d000-0011e000 r--p 00007000 08:01 134999     /lib/i386-linux-gnu/libnss_compat-2.13.so
0011e000-0011f000 rw-p 00008000 08:01 134999     /lib/i386-linux-gnu/libnss_compat-2.13.so
001d2000-001dc000 r-xp 00000000 08:01 135007     /lib/i386-linux-gnu/libnss_nis-2.13.so
001dc000-001dd000 r--p 00009000 08:01 135007     /lib/i386-linux-gnu/libnss_nis-2.13.so
001dd000-001de000 rw-p 0000a000 08:01 135007     /lib/i386-linux-gnu/libnss_nis-2.13.so
001df000-001ea000 r-xp 00000000 08:01 135003     /lib/i386-linux-gnu/libnss_files-2.13.so
001ea000-001eb000 r--p 0000a000 08:01 135003     /lib/i386-linux-gnu/libnss_files-2.13.so
001eb000-001ec000 rw-p 0000b000 08:01 135003     /lib/i386-linux-gnu/libnss_files-2.13.so
0024a000-00328000 r-xp 00000000 08:01 9001       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00328000-00329000 ---p 000de000 08:01 9001       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00329000-0032d000 r--p 000de000 08:01 9001       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
0032d000-0032e000 rw-p 000e2000 08:01 9001       /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
0032e000-00335000 rw-p 00000000 00:00 0 
003ed000-00404000 r-xp 00000000 08:01 135022     /lib/i386-linux-gnu/libpthread-2.13.so
00404000-00405000 r--p 00016000 08:01 135022     /lib/i386-linux-gnu/libpthread-2.13.so
00405000-00406000 rw-p 00017000 08:01 135022     /lib/i386-linux-gnu/libpthread-2.13.so
00406000-00408000 rw-p 00000000 00:00 0 
005a8000-005a9000 r-xp 00000000 00:00 0          [vdso]
0070f000-00718000 r-xp 00000000 08:01 44596      /usr/lib/libotcl.so.1.14
00718000-00719000 r--p 00008000 08:01 44596      /usr/lib/libotcl.so.1.14
00719000-0071a000 rw-p 00009000 08:01 44596      /usr/lib/libotcl.so.1.14
007b3000-008c6000 r-xp 00000000 08:01 44897      /usr/lib/libtcl8.5.so.0
008c6000-008c8000 r--p 00113000 08:01 44897      /usr/lib/libtcl8.5.so.0
008c8000-008cc000 rw-p 00115000 08:01 44897      /usr/lib/libtcl8.5.so.0
008cc000-008cd000 rw-p 00000000 00:00 0 
00910000-00938000 r-xp 00000000 08:01 134992     /lib/i386-linux-gnu/libm-2.13.so
00938000-00939000 r--p 00028000 08:01 134992     /lib/i386-linux-gnu/libm-2.13.so
00939000-0093a000 rw-p 00029000 08:01 134992     /lib/i386-linux-gnu/libm-2.13.so
009d6000-009eb000 r-xp 00000000 08:01 134997     /lib/i386-linux-gnu/libnsl-2.13.so
009eb000-009ec000 r--p 00015000 08:01 134997     /lib/i386-linux-gnu/libnsl-2.13.so
009ec000-009ed000 rw-p 00016000 08:01 134997     /lib/i386-linux-gnu/libnsl-2.13.so
009ed000-009ef000 rw-p 00000000 00:00 0 
00b85000-00ba3000 r-xp 00000000 08:01 134949     /lib/i386-linux-gnu/ld-2.13.so
00ba3000-00ba4000 r--p 0001d000 08:01 134949     /lib/i386-linux-gnu/ld-2.13.so
00ba4000-00ba5000 rw-p 0001e000 08:01 134949     /lib/i386-linux-gnu/ld-2.13.so
00ccd000-00e43000 r-xp 00000000 08:01 134962     /lib/i386-linux-gnu/libc-2.13.so
00e43000-00e45000 r--p 00176000 08:01 134962     /lib/i386-linux-gnu/libc-2.13.so
00e45000-00e46000 rw-p 00178000 08:01 134962     /lib/i386-linux-gnu/libc-2.13.so
00e46000-00e49000 rw-p 00000000 00:00 0 
00e53000-00e6f000 r-xp 00000000 08:01 134983     /lib/i386-linux-gnu/libgcc_s.so.1
00e6f000-00e70000 r--p 0001b000 08:01 134983     /lib/i386-linux-gnu/libgcc_s.so.1
00e70000-00e71000 rw-p 0001c000 08:01 134983     /lib/i386-linux-gnu/libgcc_s.so.1
08048000-083b4000 r-xp 00000000 08:01 44984      /usr/bin/ns
083b4000-083b5000 r--p 0036b000 08:01 44984      /usr/bin/ns
083b5000-08439000 rw-p 0036c000 08:01 44984      /usr/bin/ns
08439000-08441000 rw-p 00000000 00:00 0 
08486000-09540000 rw-p 00000000 00:00 0          [heap]
b6c0e000-b6e5b000 rw-p 00000000 00:00 0 
b6e5b000-b6e62000 r--s 00000000 08:01 9339       /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b6e62000-b6e63000 ---p 00000000 00:00 0 
b6e63000-b7663000 rw-p 00000000 00:00 0 
b7663000-b7664000 r--p 00859000 08:01 12662      /usr/lib/locale/locale-archive
b7664000-b76a4000 r--p 002bd000 08:01 12662      /usr/lib/locale/locale-archive
b76a4000-b78a4000 r--p 00000000 08:01 12662      /usr/lib/locale/locale-archive
b78a4000-b78a8000 rw-p 00000000 00:00 0 
b78bc000-b78be000 rw-p 00000000 00:00 0 
bfd1e000-bfd3f000 rw-p 00000000 00:00 0          [stack]
Aborted
```

-----------------------------
I don't understand what about the backtrace and the memory map . Please help me 
Thanks for you in advance

---

### Post by Perfect Storm on 2013-04-23
Moved to Other OS/Distro Support.

---

