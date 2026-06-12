---
title: "log files in my home folder?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2007-12-13
i keep getting  files in my home folder withodd names and content .....what are they ?

here is a file name

> hs_err_pid12472.log


and here is its contents sorry its LONG > #
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002af299184e11, pid=12472, tid=1074792784
#
# Java VM: IcedTea 64-Bit Server VM (1.7.0-b21 mixed mode linux-amd64)
# Problematic frame:
# V  [libjvm.so+0x5c9e11]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

---------------  T H R E A D  ---------------

Current thread (0x0000000000609400):  JavaThread "main" [_thread_in_vm, id=12474, stack(0x0000000040000000,0x0000000040101000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=128 (), si_addr=0x0000000000000000

Registers:
RAX=0x0000000000609400, RBX=0x0000000000609400, RCX=0x0000000000609400, RDX=0x00002af297d29280
RSP=0x00000000400fe260, RBP=0x00000000400fe290, RSI=0x0000000040100a30, RDI=0x0000000000000001
R8 =0x0000000000000000, R9 =0x0000000000000000, R10=0x00002aaaabd80783, R11=0x00002af2990f42f0
R12=0xdc01e88000002ab3, R13=0x0000000000609400, R14=0x00000000400fe330, R15=0x00002af29958a6c0
RIP=0x00002af299184e11, EFL=0x0000000000010246, CSGSFS=0x0000000000000033, ERR=0x0000000000000000
  TRAPNO=0x000000000000000d

Top of Stack: (sp=0x00000000400fe260)
0x00000000400fe260:   00000000400fe380 00002aaaaef44fd0
0x00000000400fe270:   0000000000000101 00002aaaaef44fd0
0x00000000400fe280:   00000000400fe330 0000000000609400
0x00000000400fe290:   00000000400fe300 00002aaaabd807b0
0x00000000400fe2a0:   00000000008884a0 00000000008884c0
0x00000000400fe2b0:   00000000008884c8 00000000008884c8
0x00000000400fe2c0:   00000000400fe2c0 0000000000000000
0x00000000400fe2d0:   00000000400fe330 00002aaaaef48a48
0x00000000400fe2e0:   0000000000000000 00002aaaaef44fd0
0x00000000400fe2f0:   0000000000000000 00000000400fe320
0x00000000400fe300:   00000000400fe380 00002aaaabd74342
0x00000000400fe310:   0000000000000000 00002aaaabd7ccee
0x00000000400fe320:   dc01e88000002ab3 00000000008884a8
0x00000000400fe330:   00002aaacdcf90c0 00000000000000ff
0x00000000400fe340:   00000000400fe340 00002aaaaf507617
0x00000000400fe350:   00000000400fe398 00002aaaaf50aae0
0x00000000400fe360:   0000000000000000 00002aaaaf507630
0x00000000400fe370:   00000000400fe320 00000000400fe390
0x00000000400fe380:   00000000400fe3e0 00002aaaabd742b8
0x00000000400fe390:   dc01e88000002ab3 00002aaaabd741e9
0x00000000400fe3a0:   00000000400fe3a0 00002aaaaf5076ec
0x00000000400fe3b0:   00000000400fe400 00002aaaaf50aae0
0x00000000400fe3c0:   0000000000000000 00002aaaaf507710
0x00000000400fe3d0:   00000000400fe390 00000000400fe3f0
0x00000000400fe3e0:   00000000400fe448 00002aaaabd742b8
0x00000000400fe3f0:   0000000000000009 dc01e88000002aaa
0x00000000400fe400:   0000000000000000 00000000400fe408
0x00000000400fe410:   00002aaaaf4da6a1 00000000400fe4d8
0x00000000400fe420:   00002aaaaf4e18b8 0000000000000000
0x00000000400fe430:   00002aaaaf4da930 00000000400fe3f0
0x00000000400fe440:   00000000400fe4e0 00000000400fe520
0x00000000400fe450:   00002aaaabd7411a 0000000000000000 

Instructions: (pc=0x00002af299184e11)
0x00002af299184e01:   00 00 8b 38 e8 1e 04 b7 ff c6 80 44 02 00 00 01
0x00002af299184e11:   45 0f b6 34 24 c6 80 44 02 00 00 00 48 8b 5b 48 

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
  0x00000000007adc00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=12495, stack(0x0000000040b0b000,0x0000000040c0c000)]
  0x00000000006abc00 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=12491, stack(0x0000000040909000,0x0000000040a0a000)]
  0x00000000006a8c00 JavaThread "CompilerThread1" daemon [_thread_blocked, id=12489, stack(0x0000000040808000,0x0000000040909000)]
  0x00000000006a5000 JavaThread "CompilerThread0" daemon [_thread_blocked, id=12486, stack(0x0000000040707000,0x0000000040808000)]
  0x00000000006a3400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=12485, stack(0x0000000040606000,0x0000000040707000)]
  0x000000000067bc00 JavaThread "Finalizer" daemon [_thread_blocked, id=12484, stack(0x0000000040505000,0x0000000040606000)]
  0x000000000067a000 JavaThread "Reference Handler" daemon [_thread_blocked, id=12482, stack(0x0000000040404000,0x0000000040505000)]
=>0x0000000000609400 JavaThread "main" [_thread_in_vm, id=12474, stack(0x0000000040000000,0x0000000040101000)]

Other Threads:
  0x0000000000674800 VMThread [stack: 0x0000000040303000,0x0000000040404000] [id=12479]
  0x00000000006adc00 WatcherThread [stack: 0x0000000040a0a000,0x0000000040b0b000] [id=12493]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 9152K, used 3018K [0x00002aaacdcf0000, 0x00002aaace720000, 0x00002aaad8040000)
  eden space 7872K, 38% used [0x00002aaacdcf0000,0x00002aaacdfe2be8,0x00002aaace4a0000)
  from space 1280K, 0% used [0x00002aaace5e0000,0x00002aaace5e0000,0x00002aaace720000)
  to   space 1280K, 0% used [0x00002aaace4a0000,0x00002aaace4a0000,0x00002aaace5e0000)
 PSOldGen        total 20864K, used 0K [0x00002aaab9640000, 0x00002aaabaaa0000, 0x00002aaacdcf0000)
  object space 20864K, 0% used [0x00002aaab9640000,0x00002aaab9640000,0x00002aaabaaa0000)
 PSPermGen       total 21248K, used 6957K [0x00002aaaaee40000, 0x00002aaab0300000, 0x00002aaab9640000)
  object space 21248K, 32% used [0x00002aaaaee40000,0x00002aaaaf50b7f0,0x00002aaab0300000)

Dynamic libraries:
00400000-00401000 r-xp 00000000 08:11 10355597                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00600000-00601000 rw-p 00000000 08:11 10355597                           /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer
00601000-00d25000 rw-p 00601000 00:00 0                                  [heap]
40000000-40003000 ---p 40000000 00:00 0 
40003000-40101000 rwxp 40003000 00:00 0 
40101000-40102000 ---p 40101000 00:00 0 
40102000-40202000 rwxp 40102000 00:00 0 
40202000-40203000 ---p 40202000 00:00 0 
40203000-40303000 rwxp 40203000 00:00 0 
40303000-40304000 ---p 40303000 00:00 0 
40304000-40404000 rwxp 40304000 00:00 0 
40404000-40407000 ---p 40404000 00:00 0 
40407000-40505000 rwxp 40407000 00:00 0 
40505000-40508000 ---p 40505000 00:00 0 
40508000-40606000 rwxp 40508000 00:00 0 
40606000-40609000 ---p 40606000 00:00 0 
40609000-40707000 rwxp 40609000 00:00 0 
40707000-4070a000 ---p 40707000 00:00 0 
4070a000-40808000 rwxp 4070a000 00:00 0 
40808000-4080b000 ---p 40808000 00:00 0 
4080b000-40909000 rwxp 4080b000 00:00 0 
40909000-4090c000 ---p 40909000 00:00 0 
4090c000-40a0a000 rwxp 4090c000 00:00 0 
40a0a000-40a0b000 ---p 40a0a000 00:00 0 
40a0b000-40b0b000 rwxp 40a0b000 00:00 0 
40b0b000-40b0e000 ---p 40b0b000 00:00 0 
40b0e000-40c0c000 rwxp 40b0e000 00:00 0 
2aaaaaac0000-2aaaaaac8000 r-xp 00000000 08:11 34292314                   /lib/librt-2.6.1.so
2aaaaaac8000-2aaaaacc7000 ---p 00008000 08:11 34292314                   /lib/librt-2.6.1.so
2aaaaacc7000-2aaaaacc9000 rw-p 00007000 08:11 34292314                   /lib/librt-2.6.1.so
2aaaaacc9000-2aaaaacca000 r--p 2aaaaacc9000 00:00 0 
2aaaaacca000-2aaaaaccb000 rw-p 2aaaaacca000 00:00 0 
2aaaaaccb000-2aaaaacd3000 r-xp 00000000 08:11 10355592                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaacd3000-2aaaaaed2000 ---p 00008000 08:11 10355592                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed2000-2aaaaaed4000 rw-p 00007000 08:11 10355592                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/native_threads/libhpi.so
2aaaaaed4000-2aaaaaedc000 rw-s 00000000 08:11 7340342                    /tmp/hsperfdata_lolo/12472
2aaaaaee7000-2aaaaaefd000 r-xp 00000000 08:11 34292304                   /lib/libnsl-2.6.1.so
2aaaaaefd000-2aaaab0fc000 ---p 00016000 08:11 34292304                   /lib/libnsl-2.6.1.so
2aaaab0fc000-2aaaab0fe000 rw-p 00015000 08:11 34292304                   /lib/libnsl-2.6.1.so
2aaaab0fe000-2aaaab100000 rw-p 2aaaab0fe000 00:00 0 
2aaaab100000-2aaaab108000 r-xp 00000000 08:11 34292305                   /lib/libnss_compat-2.6.1.so
2aaaab108000-2aaaab307000 ---p 00008000 08:11 34292305                   /lib/libnss_compat-2.6.1.so
2aaaab307000-2aaaab309000 rw-p 00007000 08:11 34292305                   /lib/libnss_compat-2.6.1.so
2aaaab309000-2aaaab313000 r-xp 00000000 08:11 34292309                   /lib/libnss_nis-2.6.1.so
2aaaab313000-2aaaab512000 ---p 0000a000 08:11 34292309                   /lib/libnss_nis-2.6.1.so
2aaaab512000-2aaaab514000 rw-p 00009000 08:11 34292309                   /lib/libnss_nis-2.6.1.so
2aaaab514000-2aaaab51e000 r-xp 00000000 08:11 34292307                   /lib/libnss_files-2.6.1.so
2aaaab51e000-2aaaab71d000 ---p 0000a000 08:11 34292307                   /lib/libnss_files-2.6.1.so
2aaaab71d000-2aaaab71f000 rw-p 00009000 08:11 34292307                   /lib/libnss_files-2.6.1.so
2aaaab71f000-2aaaab72d000 r-xp 00000000 08:11 10355590                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab72d000-2aaaab92c000 ---p 0000e000 08:11 10355590                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92c000-2aaaab92e000 rw-p 0000d000 08:11 10355590                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libverify.so
2aaaab92e000-2aaaab95c000 r-xp 00000000 08:11 10355571                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaab95c000-2aaaabb5b000 ---p 0002e000 08:11 10355571                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5b000-2aaaabb5f000 rw-p 0002d000 08:11 10355571                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libjava.so
2aaaabb5f000-2aaaabb6f000 r-xp 00000000 08:11 10355591                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabb6f000-2aaaabd6f000 ---p 00010000 08:11 10355591                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd6f000-2aaaabd71000 rw-p 00010000 08:11 10355591                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libzip.so
2aaaabd71000-2aaaabfe1000 rwxp 2aaaabd71000 00:00 0 
2aaaabfe1000-2aaaaed71000 rwxp 2aaaabfe1000 00:00 0 
2aaaaed71000-2aaaaed7b000 rwxp 2aaaaed71000 00:00 0 
2aaaaed7b000-2aaaaee31000 rwxp 2aaaaed7b000 00:00 0 
2aaaaee40000-2aaab0300000 rwxp 2aaaaee40000 00:00 0 
2aaab0300000-2aaab9640000 rwxp 2aaab0300000 00:00 0 
2aaab9640000-2aaabaaa0000 rwxp 2aaab9640000 00:00 0 
2aaabaaa0000-2aaacdcf0000 rwxp 2aaabaaa0000 00:00 0 
2aaacdcf0000-2aaace720000 rwxp 2aaacdcf0000 00:00 0 
2aaace720000-2aaad8040000 rwxp 2aaace720000 00:00 0 
2aaad8040000-2aaad804b000 rwxp 2aaad8040000 00:00 0 
2aaad804b000-2aaad8094000 rwxp 2aaad804b000 00:00 0 
2aaad8094000-2aaad809f000 rwxp 2aaad8094000 00:00 0 
2aaad809f000-2aaad8137000 rwxp 2aaad809f000 00:00 0 
2aaad8137000-2aaad813d000 rwxp 2aaad8137000 00:00 0 
2aaad813d000-2aaad8189000 rwxp 2aaad813d000 00:00 0 
2aaad8189000-2aaad8195000 rwxp 2aaad8189000 00:00 0 
2aaad8195000-2aaad822e000 rwxp 2aaad8195000 00:00 0 
2aaad822e000-2aaad8239000 rwxp 2aaad822e000 00:00 0 
2aaad8239000-2aaad8282000 rwxp 2aaad8239000 00:00 0 
2aaad8282000-2aaad82aa000 rw-p 2aaad8282000 00:00 0 
2aaad82aa000-2aaad8424000 r--s 035c6000 08:11 5373962                    /usr/lib/jvm/java-7-icedtea/jre/lib/rt.jar
2aaad8424000-2aaad84b7000 rw-p 2aaad8424000 00:00 0 
2aaad84b7000-2aaad84f6000 r--p 00000000 08:11 10404857                   /usr/lib/locale/en_US.utf8/LC_CTYPE
2aaad84f6000-2aaad84fd000 r--s 00000000 08:11 20611073                   /usr/lib/gconv/gconv-modules.cache
2aaad84fd000-2aaad859b000 r-xp 00000000 08:11 10355560                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad859b000-2aaad879a000 ---p 0009e000 08:11 10355560                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad879a000-2aaad87a6000 rw-p 0009d000 08:11 10355560                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libawt.so
2aaad87a6000-2aaad87ca000 rw-p 2aaad87a6000 00:00 0 
2aaad87ca000-2aaad8812000 r-xp 00000000 08:11 10355595                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad8812000-2aaad8a12000 ---p 00048000 08:11 10355595                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad8a12000-2aaad8a15000 rw-p 00048000 08:11 10355595                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/xawt/libmawt.so
2aaad8a15000-2aaad8a17000 rw-p 2aaad8a15000 00:00 0 
2aaad8a17000-2aaad8a20000 r--s 00065000 08:11 5685264                    /usr/lib/jvm/java-7-icedtea/jre/lib/ext/gnome-java-bridge.jar
2aaad8a2a000-2aaad8a2c000 r-xp 00000000 08:11 10339645                   /usr/lib/libXinerama.so.1.0.0
2aaad8a2c000-2aaad8c2b000 ---p 00002000 08:11 10339645                   /usr/lib/libXinerama.so.1.0.0
2aaad8c2b000-2aaad8c2c000 rw-p 00001000 08:11 10339645                   /usr/lib/libXinerama.so.1.0.0
2aaad8c2c000-2aaad8c3d000 r-xp 00000000 08:11 10339635                   /usr/lib/libXext.so.6.4.0
2aaad8c3d000-2aaad8e3c000 ---p 00011000 08:11 10339635                   /usr/lib/libXext.so.6.4.0
2aaad8e3c000-2aaad8e3d000 rw-p 00010000 08:11 10339635                   /usr/lib/libXext.so.6.4.0
2aaad8e3d000-2aaad8e42000 r-xp 00000000 08:11 10339663                   /usr/lib/libXtst.so.6.1.0
2aaad8e42000-2aaad9042000 ---p 00005000 08:11 10339663                   /usr/lib/libXtst.so.6.1.0
2aaad9042000-2aaad9043000 rw-p 00005000 08:11 10339663                   /usr/lib/libXtst.so.6.1.0
2aaad9043000-2aaad904b000 r-xp 00000000 08:11 10339643                   /usr/lib/libXi.so.6.0.0
2aaad904b000-2aaad924b000 ---p 00008000 08:11 10339643                   /usr/lib/libXi.so.6.0.0
2aaad924b000-2aaad924c000 rw-p 00008000 08:11 10339643                   /usr/lib/libXi.so.6.0.0
2aaad924c000-2aaad9292000 r-xp 00000000 08:11 10355563                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaad9292000-2aaad9491000 ---p 00046000 08:11 10355563                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaad9491000-2aaad9495000 rw-p 00045000 08:11 10355563                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/libfontmanager.so
2aaad9495000-2aaad94a5000 rw-p 2aaad9495000 00:00 0 
2aaad94b8000-2aaad9532000 r-xp 00000000 08:11 10339836                   /usr/lib/libfreetype.so.6.3.16
2aaad9532000-2aaad9732000 ---p 0007a000 08:11 10339836                   /usr/lib/libfreetype.so.6.3.16
2aaad9732000-2aaad9737000 rw-p 0007a000 08:11 10339836                   /usr/lib/libfreetype.so.6.3.16
2aaad9737000-2aaad9744000 r-xp 00000000 08:11 34291778                   /lib/libgcc_s.so.1
2aaad9744000-2aaad9944000 ---p 0000d000 08:11 34291778                   /lib/libgcc_s.so.1
2aaad9944000-2aaad9945000 rw-p 0000d000 08:11 34291778                   /lib/libgcc_s.so.1
2aaad9945000-2aaad995b000 r-xp 00000000 08:11 10340396                   /usr/lib/libz.so.1.2.3.3
2aaad995b000-2aaad9b5b000 ---p 00016000 08:11 10340396                   /usr/lib/libz.so.1.2.3.3
2aaad9b5b000-2aaad9b5c000 rw-p 00016000 08:11 10340396                   /usr/lib/libz.so.1.2.3.3
2aaad9b5c000-2aaad9b62000 r--s 000f6000 08:11 5373961                    /usr/lib/jvm/java-7-icedtea/jre/lib/resources.jar
2aaad9b62000-2aaad9b91000 r-xp 00000000 08:11 10355580                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaad9b91000-2aaad9d90000 ---p 0002f000 08:11 10355580                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaad9d90000-2aaad9d92000 rw-p 0002e000 08:11 10355580                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/liblcms.so
2aaad9d92000-2aaad9d94000 rw-p 2aaad9d92000 00:00 0 
2aaad9fb4000-2aaad9fbb000 r--s 00000000 08:11 28213859                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaad9fbb000-2aaad9fc0000 r--s 00000000 08:11 28214138                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaad9fc0000-2aaad9fc6000 r--s 00000000 08:11 28214139                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaad9fc6000-2aaad9fd0000 r--s 00000000 08:11 28214140                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaad9fd0000-2aaad9fd1000 r--s 00000000 08:11 28214141                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaad9fd1000-2aaad9fd9000 r--s 00000000 08:11 28214142                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaad9fd9000-2aaad9fdf000 r--s 00000000 08:11 28214143                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaad9fdf000-2aaad9fe0000 r--s 00000000 08:11 28214144                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaad9fe0000-2aaad9fe1000 r--s 00000000 08:11 28214145                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaad9fe1000-2aaad9fe2000 r--s 00000000 08:11 28214146                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaad9fe2000-2aaad9fe5000 r--s 00000000 08:11 28214147                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaad9fe5000-2aaad9fe8000 r--s 00000000 08:11 28214148                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaad9fe8000-2aaad9fee000 r--s 00000000 08:11 28214149                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaad9fee000-2aaad9ff5000 r--s 00000000 08:11 28214150                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaad9ff5000-2aaad9ff6000 r--s 00000000 08:11 28214151                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaad9ff6000-2aaad9ff8000 r--s 00000000 08:11 28214152                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaad9ff8000-2aaad9ff9000 r--s 00000000 08:11 28214153                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaad9ff9000-2aaad9ffb000 r--s 00000000 08:11 28214154                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaad9ffb000-2aaada004000 r--s 00000000 08:11 28214155                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaada004000-2aaada008000 r--s 00000000 08:11 28214156                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaada008000-2aaada00b000 r--s 00000000 08:11 28214157                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaada00b000-2aaada00c000 r--s 00000000 08:11 28214158                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaada00c000-2aaada00d000 r--s 00000000 08:11 28214159                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaada00d000-2aaada00e000 r--s 00000000 08:11 28214160                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaada00e000-2aaada010000 r--s 00000000 08:11 28213657                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaada010000-2aaada014000 r--s 00000000 08:11 28213869                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaada014000-2aaada01b000 r--s 00000000 08:11 28214122                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaada01b000-2aaada01e000 r--s 00000000 08:11 28214123                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaada01e000-2aaada03d000 r--s 00000000 08:11 28214124                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaada03d000-2aaada03e000 r--s 00000000 08:11 28214125                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaada03e000-2aaada046000 r--s 00000000 08:11 28214126                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaada046000-2aaada051000 r--s 00000000 08:11 28214127                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaada051000-2aaada054000 r--s 00000000 08:11 28214128                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaada054000-2aaada05c000 r--s 00000000 08:11 28214129                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaada05c000-2aaada05e000 r--s 00000000 08:11 28214130                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaada05e000-2aaada062000 r--s 00000000 08:11 28214131                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaada062000-2aaada063000 r--s 00000000 08:11 28214132                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaada063000-2aaada064000 r--s 00000000 08:11 28214133                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaada064000-2aaada069000 r--s 00000000 08:11 28214134                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaada069000-2aaada06c000 r--s 00000000 08:11 28214135                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaada06c000-2aaada074000 r--s 00000000 08:11 28213333                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaada297000-2aaada29e000 r--s 00000000 08:11 28213859                   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86-64.cache-2
2aaada29e000-2aaada2a3000 r--s 00000000 08:11 28214138                   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86-64.cache-2
2aaada2a3000-2aaada2a9000 r--s 00000000 08:11 28214139                   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86-64.cache-2
2aaada2a9000-2aaada2b3000 r--s 00000000 08:11 28214140                   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86-64.cache-2
2aaada2b3000-2aaada2b4000 r--s 00000000 08:11 28214141                   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86-64.cache-2
2aaada2b4000-2aaada2bc000 r--s 00000000 08:11 28214142                   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86-64.cache-2
2aaada2bc000-2aaada2c2000 r--s 00000000 08:11 28214143                   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86-64.cache-2
2aaada2c2000-2aaada2c3000 r--s 00000000 08:11 28214144                   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86-64.cache-2
2aaada2c3000-2aaada2c4000 r--s 00000000 08:11 28214145                   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86-64.cache-2
2aaada2c4000-2aaada2c5000 r--s 00000000 08:11 28214146                   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86-64.cache-2
2aaada2c5000-2aaada2c8000 r--s 00000000 08:11 28214147                   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86-64.cache-2
2aaada2c8000-2aaada2cb000 r--s 00000000 08:11 28214148                   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86-64.cache-2
2aaada2cb000-2aaada2d1000 r--s 00000000 08:11 28214149                   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86-64.cache-2
2aaada2d1000-2aaada2d8000 r--s 00000000 08:11 28214150                   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86-64.cache-2
2aaada2d8000-2aaada2d9000 r--s 00000000 08:11 28214151                   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86-64.cache-2
2aaada2d9000-2aaada2db000 r--s 00000000 08:11 28214152                   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86-64.cache-2
2aaada2db000-2aaada2dc000 r--s 00000000 08:11 28214153                   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86-64.cache-2
2aaada2dc000-2aaada2de000 r--s 00000000 08:11 28214154                   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86-64.cache-2
2aaada2de000-2aaada2e7000 r--s 00000000 08:11 28214155                   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86-64.cache-2
2aaada2e7000-2aaada2eb000 r--s 00000000 08:11 28214156                   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86-64.cache-2
2aaada2eb000-2aaada2ee000 r--s 00000000 08:11 28214157                   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86-64.cache-2
2aaada2ee000-2aaada2ef000 r--s 00000000 08:11 28214158                   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86-64.cache-2
2aaada2ef000-2aaada2f0000 r--s 00000000 08:11 28214159                   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86-64.cache-2
2aaada2f0000-2aaada2f1000 r--s 00000000 08:11 28214160                   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86-64.cache-2
2aaada2f1000-2aaada2f3000 r--s 00000000 08:11 28213657                   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86-64.cache-2
2aaada2f3000-2aaada2f7000 r--s 00000000 08:11 28213869                   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86-64.cache-2
2aaada2f7000-2aaada2fe000 r--s 00000000 08:11 28214122                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86-64.cache-2
2aaada2fe000-2aaada301000 r--s 00000000 08:11 28214123                   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86-64.cache-2
2aaada301000-2aaada320000 r--s 00000000 08:11 28214124                   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86-64.cache-2
2aaada320000-2aaada321000 r--s 00000000 08:11 28214125                   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86-64.cache-2
2aaada321000-2aaada329000 r--s 00000000 08:11 28214126                   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86-64.cache-2
2aaada329000-2aaada334000 r--s 00000000 08:11 28214127                   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86-64.cache-2
2aaada334000-2aaada337000 r--s 00000000 08:11 28214128                   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86-64.cache-2
2aaada337000-2aaada33f000 r--s 00000000 08:11 28214129                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86-64.cache-2
2aaada33f000-2aaada341000 r--s 00000000 08:11 28214130                   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86-64.cache-2
2aaada341000-2aaada345000 r--s 00000000 08:11 28214131                   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86-64.cache-2
2aaada345000-2aaada346000 r--s 00000000 08:11 28214132                   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86-64.cache-2
2aaada346000-2aaada347000 r--s 00000000 08:11 28214133                   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86-64.cache-2
2aaada347000-2aaada34c000 r--s 00000000 08:11 28214134                   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86-64.cache-2
2aaada34c000-2aaada34f000 r--s 00000000 08:11 28214135                   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86-64.cache-2
2aaada34f000-2aaada357000 r--s 00000000 08:11 28213333                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86-64.cache-2
2aaadc000000-2aaadc12f000 rw-p 2aaadc000000 00:00 0 
2aaadc12f000-2aaae0000000 ---p 2aaadc12f000 00:00 0 
2af2978f5000-2af297912000 r-xp 00000000 08:11 34291779                   /lib/ld-2.6.1.so
2af297912000-2af297915000 rw-p 2af297912000 00:00 0 
2af297b11000-2af297b13000 rw-p 0001c000 08:11 34291779                   /lib/ld-2.6.1.so
2af297b13000-2af297b29000 r-xp 00000000 08:11 34292312                   /lib/libpthread-2.6.1.so
2af297b29000-2af297d28000 ---p 00016000 08:11 34292312                   /lib/libpthread-2.6.1.so
2af297d28000-2af297d2a000 rw-p 00015000 08:11 34292312                   /lib/libpthread-2.6.1.so
2af297d2a000-2af297d2e000 rw-p 2af297d2a000 00:00 0 
2af297d2e000-2af297e38000 r-xp 00000000 08:11 10339614                   /usr/lib/libX11.so.6.2.0
2af297e38000-2af298038000 ---p 0010a000 08:11 10339614                   /usr/lib/libX11.so.6.2.0
2af298038000-2af29803f000 rw-p 0010a000 08:11 10339614                   /usr/lib/libX11.so.6.2.0
2af29803f000-2af29804f000 r-xp 00000000 08:11 10355558                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2af29804f000-2af29824f000 ---p 00010000 08:11 10355558                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2af29824f000-2af298251000 rw-p 00010000 08:11 10355558                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/jli/libjli.so
2af298251000-2af298252000 rw-p 2af298251000 00:00 0 
2af298252000-2af298254000 r-xp 00000000 08:11 34292301                   /lib/libdl-2.6.1.so
2af298254000-2af298454000 ---p 00002000 08:11 34292301                   /lib/libdl-2.6.1.so
2af298454000-2af298456000 rw-p 00002000 08:11 34292301                   /lib/libdl-2.6.1.so
2af298456000-2af2985a8000 r-xp 00000000 08:11 34292225                   /lib/libc-2.6.1.so
2af2985a8000-2af2987a7000 ---p 00152000 08:11 34292225                   /lib/libc-2.6.1.so
2af2987a7000-2af2987aa000 r--p 00151000 08:11 34292225                   /lib/libc-2.6.1.so
2af2987aa000-2af2987ac000 rw-p 00154000 08:11 34292225                   /lib/libc-2.6.1.so
2af2987ac000-2af2987b1000 rw-p 2af2987ac000 00:00 0 
2af2987b1000-2af2987b3000 r-xp 00000000 08:11 10339620                   /usr/lib/libXau.so.6.0.0
2af2987b3000-2af2989b2000 ---p 00002000 08:11 10339620                   /usr/lib/libXau.so.6.0.0
2af2989b2000-2af2989b3000 rw-p 00001000 08:11 10339620                   /usr/lib/libXau.so.6.0.0
2af2989b3000-2af2989b4000 rw-p 2af2989b3000 00:00 0 
2af2989b4000-2af2989b9000 r-xp 00000000 08:11 10339631                   /usr/lib/libXdmcp.so.6.0.0
2af2989b9000-2af298bb8000 ---p 00005000 08:11 10339631                   /usr/lib/libXdmcp.so.6.0.0
2af298bb8000-2af298bb9000 rw-p 00004000 08:11 10339631                   /usr/lib/libXdmcp.so.6.0.0
2af298bb9000-2af298bbb000 rw-p 2af298bb9000 00:00 0 
2af298bbb000-2af299303000 r-xp 00000000 08:11 10355593                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2af299303000-2af299503000 ---p 00748000 08:11 10355593                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2af299503000-2af29957d000 rw-p 00748000 08:11 10355593                   /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/server/libjvm.so
2af29957d000-2af2995b7000 rw-p 2af29957d000 00:00 0 
2af2995ca000-2af29964a000 r-xp 00000000 08:11 34292302                   /lib/libm-2.6.1.so
2af29964a000-2af299849000 ---p 00080000 08:11 34292302                   /lib/libm-2.6.1.so
2af299849000-2af29984b000 rw-p 0007f000 08:11 34292302                   /lib/libm-2.6.1.so
7fff131a0000-7fff131b4000 rwxp 7fff131a0000 00:00 0                      [stack]
7fff131b4000-7fff131b5000 rw-p 7fff131b4000 00:00 0 
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]

VM Arguments:
jvm_args: -Dapplication.home=/usr/lib/jvm/java-7-icedtea/jre 
java_command: sun.applet.PluginMain /home/lolo/.gcjwebplugin/gcj-instance-11880-0-plugin-to-appletviewer /home/lolo/.gcjwebplugin/gcj-instance-11880-0-appletviewer-to-plugin
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
USERNAME=lolo
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

uname:Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
libc:glibc 2.6.1 NPTL 2.6.1 
rlimit: STACK 8192k, CORE 0k, NPROC 15871, NOFILE 1024, AS infinity
load average:0.69 0.38 0.30

CPU:total 2 (2 cores per cpu, 1 threads per core) family 15 model 67 stepping 3, cmov, cx8, fxsr, mmx, sse, sse2, sse3, mmxext, 3dnow, 3dnowext

Memory: 4k page, physical 1998992k(15532k free), swap 5855652k(5814872k free)

vm_info: IcedTea 64-Bit Server VM (1.7.0-b21) for linux-amd64 JRE (1.7.0-b21), built on Oct 16 2007 00:19:54 by "buildd" with gcc 4.2.1 (Ubuntu 4.2.1-5ubuntu4)

time: Mon Dec 10 20:26:22 2007
elapsed time: 2 seconds


---

### Post by deepank on 2007-12-14
As much as I can tell from the log files, they are being caused by segmentation faults occuring while running Java Runtime Environment. The scary amount of data that is there in the file is to help a developer debug the program. It contains the stack contents and other such stuff recorded when the error occured. Although, I am no expert in Java, but I think that either you are running some Java applet which is still being debugged or there are some problems with your Java installation. 

So, if otherwise, your other Java applets are running fine  and you are able to browse and access Java based games, applets etc, then there is no cause for a worry

---

### Post by rexxxlo on 2007-12-14
i dont know what i am using that requires java although im sure its something on the net 

im not into games so its not that 

an i just continue to delete them or can i reinstall java somehow?

---

### Post by FuturePilot on 2007-12-14
You can probably delete them. Unless you plan on filing a bug report or something in which case those would be helpful. You shouldn't need to reinstall Java.

---

### Post by rexxxlo on 2007-12-14
i guess what i am wondering is how to make it stop?

---

### Post by rkd on 2007-12-14
I did a Google search for java-7-icedtea, the name of the Java package the log file said it was from, and I found that there have been some problems with it.  This post might show you how to get a corrected version:

[http://ubuntuforums.org/showpost.php?p=3611402&postcount=24](http://ubuntuforums.org/showpost.php?p=3611402&postcount=24)

but I don't know whether it really will be the solution for you.  It might be a good idea to read through the whole thread, rather than just that one post, before trying what it says.  It is a pretty long thread and I didn't take the time to read it all.  Maybe there is an easier or better solution elsewhere in the thread.

Good luck!

---

