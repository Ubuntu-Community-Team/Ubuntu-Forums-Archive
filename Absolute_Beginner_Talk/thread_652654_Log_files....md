---
title: "Log files..."
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by helixed on 2007-12-29
Lately a bunch of log files have been showing up in my home folder.  Now I don't have anything against log files personally, but I like to keep my home folder kind of clean.  I was wondering if there's any way to auto hide the log files or to make them move to another directory.

Thanks,

Helixed

---

### Post by p_quarles on 2007-12-29
Log files for what? The only program that logs to my home directory is Virtualbox, but perhaps you're using something different. Whichever app it is, it's going to require changing something in its configuration.

---

### Post by helixed on 2007-12-29
Thanks for your quick reply.

The programs leaving the log files are VirtualBox, Azureus, something which has a filename of hs_err_pid (there's a bunch of these, so I'm suspecting they're related to Azureus), and a nautilus_debug_log.txt

Thanks,

Helixed

---

### Post by RichJacot on 2008-01-11
Hello.  I've just noticed a bunch of these in my home dir also.

```
-rw-r--r-- 1 rjacot 3332 35582 2007-11-08 07:35 hs_err_pid10824.log
-rw-r--r-- 1 rjacot 3332 35688 2007-11-08 07:35 hs_err_pid10896.log
-rw-r--r-- 1 rjacot 3332 35634 2007-11-12 12:28 hs_err_pid18885.log
-rw-r--r-- 1 rjacot 3332 35675 2007-11-12 15:57 hs_err_pid5522.log
-rw-r--r-- 1 rjacot 3332 35690 2007-11-26 12:32 hs_err_pid25743.log
-rw-r--r-- 1 rjacot 3332 35584 2007-11-26 12:32 hs_err_pid25805.log
-rw-r--r-- 1 rjacot 3332 35584 2007-11-26 12:33 hs_err_pid25956.log
-rw-r--r-- 1 rjacot 3332 35584 2007-11-28 11:05 hs_err_pid13710.log
-rw-r--r-- 1 rjacot 3332 35686 2007-12-04 08:07 hs_err_pid30122.log
-rw-r--r-- 1 rjacot 3332 35674 2007-12-12 08:31 hs_err_pid8254.log
-rw-r--r-- 1 rjacot 3332 35634 2007-12-13 09:54 hs_err_pid23240.log
-rw-r--r-- 1 rjacot 3332 35581 2007-12-13 09:54 hs_err_pid23309.log
-rw-r--r-- 1 rjacot 3332 35581 2007-12-17 08:45 hs_err_pid20460.log
-rw-r--r-- 1 rjacot 3332 35581 2007-12-17 08:45 hs_err_pid20449.log
-rw-r--r-- 1 rjacot 3332 35581 2007-12-17 08:45 hs_err_pid20427.log
-rw-r--r-- 1 rjacot 3332 35688 2007-12-17 09:20 hs_err_pid25745.log
-rw-r--r-- 1 rjacot 3332 35688 2007-12-18 09:28 hs_err_pid17210.log
-rw-r--r-- 1 rjacot 3332 35556 2007-12-18 15:13 hs_err_pid734.log
-rw-r--r-- 1 rjacot 3332 35687 2007-12-20 08:54 hs_err_pid25886.log
-rw-r--r-- 1 rjacot 3332 35585 2008-01-03 07:58 hs_err_pid29439.log
-rw-r--r-- 1 rjacot 3332 35583 2008-01-03 07:58 hs_err_pid29411.log
-rw-r--r-- 1 rjacot 3332 35530 2008-01-03 07:58 hs_err_pid29537.log
-rw-r--r-- 1 rjacot 3332 35583 2008-01-03 07:59 hs_err_pid29563.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-04 12:52 hs_err_pid2005.log
-rw-r--r-- 1 rjacot 3332 35622 2008-01-08 06:57 hs_err_pid8046.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8120.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8109.log
-rw-r--r-- 1 rjacot 3332 35675 2008-01-08 06:57 hs_err_pid8089.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8078.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8067.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8131.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8164.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8178.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:57 hs_err_pid8208.log
-rw-r--r-- 1 rjacot 3332 35569 2008-01-08 06:57 hs_err_pid8193.log
-rw-r--r-- 1 rjacot 3332 35677 2008-01-08 06:58 hs_err_pid8224.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8253.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8238.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8268.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8299.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8285.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8314.log
-rw-r--r-- 1 rjacot 3332 35571 2008-01-08 06:58 hs_err_pid8328.log
-rw-r--r-- 1 rjacot 3332 35530 2008-01-09 09:20 hs_err_pid31053.log
-rw-r--r-- 1 rjacot 3332 35583 2008-01-09 09:21 hs_err_pid31123.log
-rw-r--r-- 1 rjacot 3332 35584 2008-01-10 13:11 hs_err_pid28854.log
-rw-r--r-- 1 rjacot 3332 35584 2008-01-11 11:57 hs_err_pid25798.log

```

And they go back even further.  Here's what in the latest one.

```
~$ cat hs_err_pid25798.log
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002abba60e9e11, pid=25798, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609400):  JavaThread "main" [_thread_in_vm, id=25800, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609400, RBX=0x0000000000609400, RCX=0x0000000000609400, RDX=0x00002abba4c8e280
RSP=0x00000000400fe260, RBP=0x00000000400fe290, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd80743, R11=0x00002abba60592f0
R12=0x0086cdd000000009, R13=0x0000000000609400, R14=0x00000000400fe330, R15=0x00002abba64ef6c0
RIP=0x00002abba60e9e11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe260)
0x00000000400fe260:   00000000400fe380 00002aaad8944fd0
0x00000000400fe270:   0000000000000101 00002aaad8944fd0
0x00000000400fe280:   00000000400fe330 0000000000609400
0x00000000400fe290:   00000000400fe300 00002aaaabd80770
0x00000000400fe2a0:   0000000000a06598 0000000000a065b8
0x00000000400fe2b0:   0000000000a065c0 0000000000a065c0
0x00000000400fe2c0:   00000000400fe2c0 0000000000000000
0x00000000400fe2d0:   00000000400fe330 00002aaad8948a48
0x00000000400fe2e0:   0000000000000000 00002aaad8944fd0
0x00000000400fe2f0:   0000000000000000 00000000400fe320
0x00000000400fe300:   00000000400fe380 00002aaaabd74342
0x00000000400fe310:   0000000000000000 00002aaaabd7ccce
0x00000000400fe320:   0086cdd000000009 0000000000a065a0
0x00000000400fe330:   00002aaaaf0945c8 00000000000000ff
0x00000000400fe340:   00000000400fe340 00002aaad8f08b0f
0x00000000400fe350:   00000000400fe398 00002aaad8f0bfd8
0x00000000400fe360:   0000000000000000 00002aaad8f08b28
0x00000000400fe370:   00000000400fe320 00000000400fe390
0x00000000400fe380:   00000000400fe3e0 00002aaaabd742b8
0x00000000400fe390:   0086cdd000000009 00002aaaabd741e9
0x00000000400fe3a0:   00000000400fe3a0 00002aaad8f08be4
0x00000000400fe3b0:   00000000400fe400 00002aaad8f0bfd8
0x00000000400fe3c0:   0000000000000000 00002aaad8f08c08
0x00000000400fe3d0:   00000000400fe390 00000000400fe3f0
0x00000000400fe3e0:   00000000400fe448 00002aaaabd742b8
0x00000000400fe3f0:   0000000000000009 0086cdd000000000
0x00000000400fe400:   0000000000000000 00000000400fe408
0x00000000400fe410:   00002aaad8edbb99 00000000400fe4d8
0x00000000400fe420:   00002aaad8ee2db0 0000000000000000
0x00000000400fe430:   00002aaad8edbe28 00000000400fe3f0
0x00000000400fe440:   00000000400fe4e0 00000000400fe520
0x00000000400fe450:   00002aaaabd7411a 0000000000000000 

Instructions: (pc=0x00002abba60e9e11)
0x00002abba60e9e01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002abba60e9e11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

Stack: [0x0000000040000000,0x0000000040101000],  sp=0x00000000400fe260,  free space=1016k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x5c9e11]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x30ec06]
V  [libjvm.so+0x30fe0d]
V  [libjvm.so+0x3102f1]
V  [libjvm.so+0x389aaa]
V  [libjvm.so+0x3943fa]
C  [libjava.so+0x1242d]  Java_java_lang_Class_forName0+0x15d
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x39b888]
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
V  [libjvm.so+0x331d9b]
V  [libjvm.so+0x330f18]
V  [libjvm.so+0x33b231]
V  [libjvm.so+0x3583d5]
C  [libjli.so+0x3abd]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::Interpreter
v  ~BufferBlob::StubRoutines (1)

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00000000007a9800 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=25825, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00000000006a7800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=25814, stack(0x0000000040707000,0x0000000040808000)]
  0x00000000006a5000 JavaThread "CompilerThread1" daemon [_thread_blocked, id=25812, stack(0x0000000040606000,0x0000000040707000)]
  0x00000000006a1400 JavaThread "CompilerThread0" daemon [_thread_blocked, id=25810, stack(0x0000000040505000,0x0000000040606000)]
  0x000000000069fc00 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=25808, stack(0x0000000040404000,0x0000000040505000)]
  0x0000000000678000 JavaThread "Finalizer" daemon [_thread_blocked, id=25806, stack(0x0000000040303000,0x0000000040404000)]
  0x0000000000676400 JavaThread "Reference Handler" daemon [_thread_blocked, id=25804, stack(0x0000000040202000,0x0000000040303000)]
=>0x0000000000609400 JavaThread "main" [_thread_in_vm, id=25800, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000670c00 VMThread [stack: 0x0000000040101000,0x0000000040202000] [id=25801]
  0x00000000006a9c00 WatcherThread [stack: 0x0000000040808000,0x0000000040909000] [id=25816]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 2368K, used 2195K [0x00002aaaaee40000, 0x00002aaaaf0d0000, 0x00002aaabcc40000)
  eden space 2112K,  91% used [0x00002aaaaee40000, 0x00002aaaaf024eb0, 0x00002aaaaf050000)
  from space 256K,  99% used [0x00002aaaaf090000, 0x00002aaaaf0cfff8, 0x00002aaaaf0d0000)
  to   space 256K,   0% used [0x00002aaaaf050000, 0x00002aaaaf050000, 0x00002aaaaf090000)
 tenured generation   total 5312K, used 445K [0x00002aaabcc40000, 0x00002aaabd170000, 0x00002aaad8840000)
   the space 5312K,   8% used [0x00002aaabcc40000, 0x00002aaabccaf598, 0x00002aaabccaf600, 0x00002aaabd170000)
 compacting perm gen  total 21248K, used 6963K [0x00002aaad8840000, 0x00002aaad9d00000, 0x00002aaae3040000)
   the space 21248K,  32% used [0x00002aaad8840000, 0x00002aaad8f0cce8, 0x00002aaad8f0ce00, 0x00002aaad9d00000)
No shared spaces configured.

Dynamic libraries:
00400000-00401000 r-xp 00000000 09:02 11733305                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00600000-00601000 rw-p 00000000 09:02 11733305                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00601000-00c85000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40205000 ---p 40202000 00:00 0 
40205000-40303000 rwxp 40205000 00:00 0 
40303000-40306000 ---p 40303000 00:00 0 
40306000-40404000 rwxp 40306000 00:00 0 
40404000-40407000 ---p 40404000 00:00 0 
40407000-40505000 rwxp 40407000 00:00 0 
40505000-40508000 ---p 40505000 00:00 0 
40508000-40606000 rwxp 40508000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-40809000 ---p 40808000 00:00 0 
40809000-40909000 rwxp 40809000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
2aaaaaac0000-2aaaaaac8000 r-xp 00000000 09:02 28869821                   /lib/librt-2.6.1.so
2aaaaaac8000-2aaaaacc7000 ---p 00008000 09:02 28869821                   /lib/librt-2.6.1.so
2aaaaacc7000-2aaaaacc9000 rw-p 00007000 09:02 28869821                   /lib/librt-2.6.1.so
2aaaaacc9000-2aaaaacca000 r--p 2aaaaacc9000 00:00 0 
2aaaaacca000-2aaaaaccb000 rwxp 2aaaaacca000 00:00 0 
2aaaaaccb000-2aaaaacd3000 r-xp 00000000 09:02 11717652                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd3000-2aaaaaed2000 ---p 00008000 09:02 11717652                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed2000-2aaaaaed4000 rw-p 00007000 09:02 11717652                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed4000-2aaaaaedc000 rw-s 00000000 09:02 11601324                   /tmp/hsperfdata_rjacot/25798
2aaaaaee7000-2aaaaaefd000 r-xp 00000000 09:02 28869811                   /lib/libnsl-2.6.1.so
2aaaaaefd000-2aaaab0fc000 ---p 00016000 09:02 28869811                   /lib/libnsl-2.6.1.so
2aaaab0fc000-2aaaab0fe000 rw-p 00015000 09:02 28869811                   /lib/libnsl-2.6.1.so
2aaaab0fe000-2aaaab100000 rw-p 2aaaab0fe000 00:00 0 
2aaaab100000-2aaaab108000 r-xp 00000000 09:02 28869812                   /lib/libnss_compat-2.6.1.so
2aaaab108000-2aaaab307000 ---p 00008000 09:02 28869812                   /lib/libnss_compat-2.6.1.so
2aaaab307000-2aaaab309000 rw-p 00007000 09:02 28869812                   /lib/libnss_compat-2.6.1.so
2aaaab309000-2aaaab313000 r-xp 00000000 09:02 28869816                   /lib/libnss_nis-2.6.1.so
2aaaab313000-2aaaab512000 ---p 0000a000 09:02 28869816                   /lib/libnss_nis-2.6.1.so
2aaaab512000-2aaaab514000 rw-p 00009000 09:02 28869816                   /lib/libnss_nis-2.6.1.so
2aaaab514000-2aaaab51e000 r-xp 00000000 09:02 28869814                   /lib/libnss_files-2.6.1.so
2aaaab51e000-2aaaab71d000 ---p 0000a000 09:02 28869814                   /lib/libnss_files-2.6.1.so
2aaaab71d000-2aaaab71f000 rw-p 00009000 09:02 28869814                   /lib/libnss_files-2.6.1.so
2aaaab71f000-2aaaab72d000 r-xp 00000000 09:02 11702327                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab72d000-2aaaab92c000 ---p 0000e000 09:02 11702327                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92c000-2aaaab92e000 rw-p 0000d000 09:02 11702327                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92e000-2aaaab95c000 r-xp 00000000 09:02 11702308                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab95c000-2aaaabb5b000 ---p 0002e000 09:02 11702308                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5b000-2aaaabb5f000 rw-p 0002d000 09:02 11702308                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5f000-2aaaabb6f000 r-xp 00000000 09:02 11702328                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb6f000-2aaaabd6f000 ---p 00010000 09:02 11702328                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6f000-2aaaabd71000 rw-p 00010000 09:02 11702328                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd71000-2aaaabfe1000 rwxp 2aaaabd71000 00:00 0 
2aaaabfe1000-2aaaaed71000 rwxp 2aaaabfe1000 00:00 0 
2aaaaed71000-2aaaaed7b000 rwxp 2aaaaed71000 00:00 0 
2aaaaed7b000-2aaaaee31000 rwxp 2aaaaed7b000 00:00 0 
2aaaaee40000-2aaaaf0d0000 rwxp 2aaaaee40000 00:00 0 
2aaaaf0d0000-2aaabcc40000 rwxp 2aaaaf0d0000 00:00 0 
2aaabcc40000-2aaabd170000 rwxp 2aaabcc40000 00:00 0 
2aaabd170000-2aaad8840000 rwxp 2aaabd170000 00:00 0 
2aaad8840000-2aaad9d00000 rwxp 2aaad8840000 00:00 0 
2aaad9d00000-2aaae3040000 rwxp 2aaad9d00000 00:00 0 
2aaae3040000-2aaae3042000 rwxp 2aaae3040000 00:00 0 
2aaae3042000-2aaae30af000 rwxp 2aaae3042000 00:00 0 
2aaae30af000-2aaae30b2000 rwxp 2aaae30af000 00:00 0 
2aaae30b2000-2aaae318d000 rwxp 2aaae30b2000 00:00 0 
2aaae318d000-2aaae3198000 rwxp 2aaae318d000 00:00 0 
2aaae3198000-2aaae31e1000 rwxp 2aaae3198000 00:00 0 
2aaae31e1000-2aaae31e5000 rwxp 2aaae31e1000 00:00 0 
2aaae31e5000-2aaae32c1000 rwxp 2aaae31e5000 00:00 0 
2aaae32c1000-2aaae32cc000 rwxp 2aaae32c1000 00:00 0 
2aaae32cc000-2aaae3316000 rwxp 2aaae32cc000 00:00 0 
2aaae3316000-2aaae333e000 rw-p 2aaae3316000 00:00 0 
2aaae333e000-2aaae34b8000 r--s 035c6000 09:02 11683432                   /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaae34b8000-2aaae34e8000 rw-p 2aaae34b8000 00:00 0 
2aaae34e8000-2aaae3527000 r--p 00000000 09:02 11519979                   /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaae3527000-2aaae352e000 r--s 00000000 09:02 11486162                   /usr/lib/gconv/gconv-modules.cache
2aaae352e000-2aaae35cc000 r-xp 00000000 09:02 11702297                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae35cc000-2aaae37cb000 ---p 0009e000 09:02 11702297                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37cb000-2aaae37d7000 rw-p 0009d000 09:02 11702297                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaae37d7000-2aaae37fb000 rw-p 2aaae37d7000 00:00 0 
2aaae37fb000-2aaae3843000 r-xp 00000000 09:02 11733302                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3843000-2aaae3a43000 ---p 00048000 09:02 11733302                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a43000-2aaae3a46000 rw-p 00048000 09:02 11733302                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaae3a46000-2aaae3a48000 rw-p 2aaae3a46000 00:00 0 
2aaae3a48000-2aaae3a51000 r--s 00065000 09:02 11683411                   /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaae3a5b000-2aaae3a5d000 r-xp 00000000 09:02 11489050                   /usr/lib/libXinerama.so.1.0.0
2aaae3a5d000-2aaae3c5c000 ---p 00002000 09:02 11489050                   /usr/lib/libXinerama.so.1.0.0
2aaae3c5c000-2aaae3c5d000 rw-p 00001000 09:02 11489050                   /usr/lib/libXinerama.so.1.0.0
2aaae3c5d000-2aaae3c6e000 r-xp 00000000 09:02 11488936                   /usr/lib/libXext.so.6.4.0
2aaae3c6e000-2aaae3e6d000 ---p 00011000 09:02 11488936                   /usr/lib/libXext.so.6.4.0
2aaae3e6d000-2aaae3e6e000 rw-p 00010000 09:02 11488936                   /usr/lib/libXext.so.6.4.0
2aaae3e6e000-2aaae3e73000 r-xp 00000000 09:02 11489052                   /usr/lib/libXtst.so.6.1.0
2aaae3e73000-2aaae4073000 ---p 00005000 09:02 11489052                   /usr/lib/libXtst.so.6.1.0
2aaae4073000-2aaae4074000 rw-p 00005000 09:02 11489052                   /usr/lib/libXtst.so.6.1.0
2aaae4074000-2aaae407c000 r-xp 00000000 09:02 11489036                   /usr/lib/libXi.so.6.0.0
2aaae407c000-2aaae427c000 ---p 00008000 09:02 11489036                   /usr/lib/libXi.so.6.0.0
2aaae427c000-2aaae427d000 rw-p 00008000 09:02 11489036                   /usr/lib/libXi.so.6.0.0
2aaae427d000-2aaae42c3000 r-xp 00000000 09:02 11702300                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae42c3000-2aaae44c2000 ---p 00046000 09:02 11702300                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae44c2000-2aaae44c6000 rw-p 00045000 09:02 11702300                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaae44c6000-2aaae44d6000 rw-p 2aaae44c6000 00:00 0 
2aaae44e9000-2aaae4563000 r-xp 00000000 09:02 11488945                   /usr/lib/libfreetype.so.6.3.16
2aaae4563000-2aaae4763000 ---p 0007a000 09:02 11488945                   /usr/lib/libfreetype.so.6.3.16
2aaae4763000-2aaae4768000 rw-p 0007a000 09:02 11488945                   /usr/lib/libfreetype.so.6.3.16
2aaae4768000-2aaae4775000 r-xp 00000000 09:02 28868622                   /lib/libgcc_s.so.1
2aaae4775000-2aaae4975000 ---p 0000d000 09:02 28868622                   /lib/libgcc_s.so.1
2aaae4975000-2aaae4976000 rw-p 0000d000 09:02 28868622                   /lib/libgcc_s.so.1
2aaae4976000-2aaae498c000 r-xp 00000000 09:02 11487279                   /usr/lib/libz.so.1.2.3.3
2aaae498c000-2aaae4b8c000 ---p 00016000 09:02 11487279                   /usr/lib/libz.so.1.2.3.3
2aaae4b8c000-2aaae4b8d000 rw-p 00016000 09:02 11487279                   /usr/lib/libz.so.1.2.3.3
2aaae4b8d000-2aaae4b94000 r--s 00000000 09:02 16698990                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae4b94000-2aaae4b99000 r--s 00000000 09:02 16698994                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae4b99000-2aaae4b9f000 r--s 00000000 09:02 16698995                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae4b9f000-2aaae4ba5000 r--s 000f6000 09:02 11683431                   /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaae4dd5000-2aaae4ddf000 r--s 00000000 09:02 16698997                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae4ddf000-2aaae4de0000 r--s 00000000 09:02 16698998                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae4de0000-2aaae4de8000 r--s 00000000 09:02 16699001                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae4de8000-2aaae4dee000 r--s 00000000 09:02 16699002                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae4dee000-2aaae4def000 r--s 00000000 09:02 16699003                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae4def000-2aaae4df0000 r--s 00000000 09:02 16699004                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaae4df0000-2aaae4df1000 r--s 00000000 09:02 16699007                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae4df1000-2aaae4df4000 r--s 00000000 09:02 16699015                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae4df4000-2aaae4dfb000 r--s 00000000 09:02 16699022                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae4dfb000-2aaae4e01000 r--s 00000000 09:02 16699028                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae4e01000-2aaae4e08000 r--s 00000000 09:02 16699031                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae4e08000-2aaae4e09000 r--s 00000000 09:02 16699032                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae4e09000-2aaae4e0b000 r--s 00000000 09:02 16699036                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae4e0b000-2aaae4e0c000 r--s 00000000 09:02 16699040                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae4e0c000-2aaae4e0e000 r--s 00000000 09:02 16699041                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae4e0e000-2aaae4e17000 r--s 00000000 09:02 16699042                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae4e17000-2aaae4e1b000 r--s 00000000 09:02 16699043                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae4e1b000-2aaae4e1e000 r--s 00000000 09:02 16699044                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaae4e1e000-2aaae4e1f000 r--s 00000000 09:02 16699048                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaae4e1f000-2aaae4e20000 r--s 00000000 09:02 16699054                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae4e20000-2aaae4e21000 r--s 00000000 09:02 16699059                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaae4e21000-2aaae4e23000 r--s 00000000 09:02 16698738                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae4e23000-2aaae4e27000 r--s 00000000 09:02 16698754                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae4e27000-2aaae4e2e000 r--s 00000000 09:02 16698755                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae4e2e000-2aaae4e31000 r--s 00000000 09:02 16698757                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae4e31000-2aaae4e50000 r--s 00000000 09:02 16698759                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaae4e50000-2aaae4e51000 r--s 00000000 09:02 16698760                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae4e51000-2aaae4e59000 r--s 00000000 09:02 16698766                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae4e59000-2aaae4e64000 r--s 00000000 09:02 16698779                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae4e64000-2aaae4e67000 r--s 00000000 09:02 16698781                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae4e67000-2aaae4e6f000 r--s 00000000 09:02 16698783                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae4e6f000-2aaae4e71000 r--s 00000000 09:02 16698792                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae4e71000-2aaae4e75000 r--s 00000000 09:02 16698795                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae4e75000-2aaae4e76000 r--s 00000000 09:02 16698819                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae4e76000-2aaae4e7a000 r--s 00000000 09:02 16698914                   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86-64.cache-2
2aaae4e7a000-2aaae4e7b000 r--s 00000000 09:02 16698947                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae4e7b000-2aaae4e80000 r--s 00000000 09:02 16698954                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae4e80000-2aaae4e83000 r--s 00000000 09:02 16698965                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae4e83000-2aaae4e8b000 r--s 00000000 09:02 16698978                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae4fe5000-2aaae4fec000 r--s 00000000 09:02 16698990                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaae4fec000-2aaae4ff1000 r--s 00000000 09:02 16698994                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaae4ff1000-2aaae4ff7000 r--s 00000000 09:02 16698995                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaae4ff7000-2aaae5001000 r--s 00000000 09:02 16698997                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaae5001000-2aaae5002000 r--s 00000000 09:02 16698998                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaae5002000-2aaae500a000 r--s 00000000 09:02 16699001                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaae500a000-2aaae5010000 r--s 00000000 09:02 16699002                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaae5010000-2aaae5011000 r--s 00000000 09:02 16699003                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaae5011000-2aaae5012000 r--s 00000000 09:02 16699004                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaae5012000-2aaae5013000 r--s 00000000 09:02 16699007                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaae5013000-2aaae5016000 r--s 00000000 09:02 16699015                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaae5016000-2aaae501d000 r--s 00000000 09:02 16699022                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaae501d000-2aaae5023000 r--s 00000000 09:02 16699028                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaae5023000-2aaae502a000 r--s 00000000 09:02 16699031                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaae502a000-2aaae502b000 r--s 00000000 09:02 16699032                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaae502b000-2aaae502d000 r--s 00000000 09:02 16699036                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaae502d000-2aaae502e000 r--s 00000000 09:02 16699040                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaae502e000-2aaae5030000 r--s 00000000 09:02 16699041                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaae5030000-2aaae5039000 r--s 00000000 09:02 16699042                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaae5039000-2aaae503d000 r--s 00000000 09:02 16699043                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaae503d000-2aaae5040000 r--s 00000000 09:02 16699044                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaae5040000-2aaae5041000 r--s 00000000 09:02 16699048                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaae5041000-2aaae5042000 r--s 00000000 09:02 16699054                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaae5042000-2aaae5043000 r--s 00000000 09:02 16699059                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaae5043000-2aaae5045000 r--s 00000000 09:02 16698738                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaae5045000-2aaae5049000 r--s 00000000 09:02 16698754                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaae5049000-2aaae5050000 r--s 00000000 09:02 16698755                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaae5050000-2aaae5053000 r--s 00000000 09:02 16698757                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaae5053000-2aaae5072000 r--s 00000000 09:02 16698759                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaae5072000-2aaae5073000 r--s 00000000 09:02 16698760                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaae5073000-2aaae507b000 r--s 00000000 09:02 16698766                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaae507b000-2aaae5086000 r--s 00000000 09:02 16698779                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaae5086000-2aaae5089000 r--s 00000000 09:02 16698781                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaae5089000-2aaae5091000 r--s 00000000 09:02 16698783                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaae5091000-2aaae5093000 r--s 00000000 09:02 16698792                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaae5093000-2aaae5097000 r--s 00000000 09:02 16698795                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaae5097000-2aaae5098000 r--s 00000000 09:02 16698819                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaae5098000-2aaae509c000 r--s 00000000 09:02 16698914                   /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86-64.cache-2
2aaae509c000-2aaae509d000 r--s 00000000 09:02 16698947                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaae509d000-2aaae50a2000 r--s 00000000 09:02 16698954                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaae50a2000-2aaae50a5000 r--s 00000000 09:02 16698965                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaae50a5000-2aaae50ad000 r--s 00000000 09:02 16698978                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaae50ad000-2aaae50dc000 r-xp 00000000 09:02 11702317                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae50dc000-2aaae52db000 ---p 0002f000 09:02 11702317                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae52db000-2aaae52dd000 rw-p 0002e000 09:02 11702317                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaae52dd000-2aaae52df000 rw-p 2aaae52dd000 00:00 0 
2abba485a000-2abba4877000 r-xp 00000000 09:02 28869801                   /lib/ld-2.6.1.so
2abba4877000-2abba487a000 rw-p 2abba4877000 00:00 0 
2abba4a76000-2abba4a78000 rw-p 0001c000 09:02 28869801                   /lib/ld-2.6.1.so
2abba4a78000-2abba4a8e000 r-xp 00000000 09:02 28869819                   /lib/libpthread-2.6.1.so
2abba4a8e000-2abba4c8d000 ---p 00016000 09:02 28869819                   /lib/libpthread-2.6.1.so
2abba4c8d000-2abba4c8f000 rw-p 00015000 09:02 28869819                   /lib/libpthread-2.6.1.so
2abba4c8f000-2abba4c93000 rw-p 2abba4c8f000 00:00 0 
2abba4c93000-2abba4d9d000 r-xp 00000000 09:02 11488934                   /usr/lib/libX11.so.6.2.0
2abba4d9d000-2abba4f9d000 ---p 0010a000 09:02 11488934                   /usr/lib/libX11.so.6.2.0
2abba4f9d000-2abba4fa4000 rw-p 0010a000 09:02 11488934                   /usr/lib/libX11.so.6.2.0
2abba4fa4000-2abba4fb4000 r-xp 00000000 09:02 11702295                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2abba4fb4000-2abba51b4000 ---p 00010000 09:02 11702295                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2abba51b4000-2abba51b6000 rw-p 00010000 09:02 11702295                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2abba51b6000-2abba51b7000 rw-p 2abba51b6000 00:00 0 
2abba51b7000-2abba51b9000 r-xp 00000000 09:02 28869808                   /lib/libdl-2.6.1.so
2abba51b9000-2abba53b9000 ---p 00002000 09:02 28869808                   /lib/libdl-2.6.1.so
2abba53b9000-2abba53bb000 rw-p 00002000 09:02 28869808                   /lib/libdl-2.6.1.so
2abba53bb000-2abba550d000 r-xp 00000000 09:02 28869805                   /lib/libc-2.6.1.so
2abba550d000-2abba570c000 ---p 00152000 09:02 28869805                   /lib/libc-2.6.1.so
2abba570c000-2abba570f000 r--p 00151000 09:02 28869805                   /lib/libc-2.6.1.so
2abba570f000-2abba5711000 rw-p 00154000 09:02 28869805                   /lib/libc-2.6.1.so
2abba5711000-2abba5716000 rw-p 2abba5711000 00:00 0 
2abba5716000-2abba5718000 r-xp 00000000 09:02 11488930                   /usr/lib/libXau.so.6.0.0
2abba5718000-2abba5917000 ---p 00002000 09:02 11488930                   /usr/lib/libXau.so.6.0.0
2abba5917000-2abba5918000 rw-p 00001000 09:02 11488930                   /usr/lib/libXau.so.6.0.0
2abba5918000-2abba5919000 rw-p 2abba5918000 00:00 0 
2abba5919000-2abba591e000 r-xp 00000000 09:02 11488932                   /usr/lib/libXdmcp.so.6.0.0
2abba591e000-2abba5b1d000 ---p 00005000 09:02 11488932                   /usr/lib/libXdmcp.so.6.0.0
2abba5b1d000-2abba5b1e000 rw-p 00004000 09:02 11488932                   /usr/lib/libXdmcp.so.6.0.0
2abba5b1e000-2abba5b20000 rw-p 2abba5b1e000 00:00 0 
2abba5b20000-2abba6268000 r-xp 00000000 09:02 11717654                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2abba6268000-2abba6468000 ---p 00748000 09:02 11717654                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2abba6468000-2abba64e2000 rw-p 00748000 09:02 11717654                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2abba64e2000-2abba651c000 rw-p 2abba64e2000 00:00 0 
2abba652f000-2abba65af000 r-xp 00000000 09:02 28869809                   /lib/libm-2.6.1.so
2abba65af000-2abba67ae000 ---p 00080000 09:02 28869809                   /lib/libm-2.6.1.so
2abba67ae000-2abba67b0000 rw-p 0007f000 09:02 28869809                   /lib/libm-2.6.1.so
7fff0623a000-7fff0624e000 rwxp 7fff0623a000 00:00 0                      [stack]
7fff0624e000-7fff06250000 rw-p 7fff0624e000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Dapplication.home=/usr/lib/jvm/java-7-icedtea/jre 
java_command: sun.applet.PluginMain /home/rjacot/.gcjwebplugin/gcj-instance-27270-0-plugin-to-appletviewer /home/rjacot/.gcjwebplugin/gcj-instance-27270-0-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=rjacot
LD_LIBRARY_PATH=/usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server:/usr/lib/jvm/java-7-icedtea/jre/lib/amd64:/usr/lib/jvm/java-7-icedtea/jre/../lib/amd64:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mre/mre
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x5e97a0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x4c9560], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x4ccc50], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x4ca920], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:lenny/sid

uname:Linux 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 16383, NOFILE 1024, AS infinity
load average:0.30 0.70 0.77

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 39 stepping 1, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 2063632k(422768k free), swap 1951800k(1465440k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Fri Jan 11 11:57:04 2008
elapsed time: 3 seconds

```

Anyone have any ideas?

Thanks,
Rich

---

### Post by dcstar on 2008-01-11
> **RichJacot said:**
> Hello.  I've just noticed a bunch of these in my home dir also.
..........
Anyone have any ideas?

Thanks,
Rich

They are error logs from the Icedtea Java package, you are free to ignore/delete them if they are not affecting your use of the system.

---

