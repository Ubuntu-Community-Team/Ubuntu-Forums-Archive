---
title: "Minecraft/Java - EXCEPTION_ACCESS_VIOLATION"
date: 2012-01-15
forum: Any Other OS
---

### Post by DaimyoKirby on 2012-01-15
Hello there.
I got a new (old) desktop, a Dell Dimension 2350 with Windows XP and a Radeon 9200 LE Family video card, and so naturally, after I'm done installing the numerous Windows XP updates that come with installing Windows, I downloaded Minecraft and Java 7. Originally, I was getting everyone's favorite "no accelerated OpenGL/Pixel Format Not Accelerated" error, but after a little bit of searching, I found myself at AMD's site, and I downloaded and installed the ATI Catalyst Control Center thing, and restarted.

Now, when I log in to Minecraft, it completely crashes (skips the purple crash screen), and a text file appeared on my desktop, with this seemingly much more complicated error (take note of the more in-depth system specs at the bottom of the report):
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x524cb4c7, pid=2828, tid=1700
#
# JRE version: 7.0_02-b13
# Java VM: Java HotSpot(TM) Client VM (22.0-b10 mixed mode windows-x86 )
# Problematic frame:
# C  [atioglx1.dll+0x3fb4c7]
#
# Failed to write core dump. Minidumps are not enabled by default on client versions of Windows
#
# If you would like to submit a bug report, please visit:
#   http://bugreport.sun.com/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x497b0800):  JavaThread "Minecraft main thread" daemon [_thread_in_native, id=1700, stack(0x49f10000,0x49f60000)]

siginfo: ExceptionCode=0xc0000005, reading address 0x000000be

Registers:
EAX=0x00000000, EBX=0x00000000, ECX=0x00000000, EDX=0x49f5f310
ESP=0x49f5f2d0, EBP=0x52797fc0, ESI=0x00000000, EDI=0x527ce028
EIP=0x524cb4c7, EFLAGS=0x00010206

Top of Stack: (sp=0x49f5f2d0)
0x49f5f2d0:   5271e368 00000000 31433833 31313235
0x49f5f2e0:   30305c7d 4f5c3030 476e6570 72505c4c
0x49f5f2f0:   000000f0 00000065 00000000 00000000
0x49f5f300:   00000000 00000000 524ebc3b 49f5f338
0x49f5f310:   00000000 00000608 00000000 00008000
0x49f5f320:   00001000 00000000 00000000 00000000
0x49f5f330:   00000000 00000000 49f5f294 49f5f37c
0x49f5f340:   49f5f37c 7c90e920 7c910060 ffffffff 

Instructions: (pc=0x524cb4c7)
0x524cb4a7:   e8 74 f5 ff ff b8 01 00 00 00 5f 5d 5e 5b 83 c4
0x524cb4b7:   30 c2 04 00 cc cc cc cc cc 83 ec 30 53 56 8b f1
0x524cb4c7:   8a 86 be 00 00 00 84 c0 8b da 74 1c e8 68 07 00
0x524cb4d7:   00 8a 86 be 00 00 00 84 c0 74 0d 5e b8 c8 00 00 


Register to memory mapping:

EAX=0x00000000 is an unknown value
EBX=0x00000000 is an unknown value
ECX=0x00000000 is an unknown value
EDX=0x49f5f310 is pointing into the stack for thread: 0x497b0800
ESP=0x49f5f2d0 is pointing into the stack for thread: 0x497b0800
EBP=0x52797fc0 is an unknown value
ESI=0x00000000 is an unknown value
EDI=0x527ce028 is an unknown value


Stack: [0x49f10000,0x49f60000],  sp=0x49f5f2d0,  free space=316k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [atioglx1.dll+0x3fb4c7]  atiPPHSN+0x356217

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  org.lwjgl.opengl.WindowsContextImplementation.nCreate(Ljava/nio/ByteBuffer;Ljava/nio/IntBuffer;Ljava/nio/ByteBuffer;)Ljava/nio/ByteBuffer;+0
j  org.lwjgl.opengl.WindowsContextImplementation.create(Lorg/lwjgl/opengl/PeerInfo;Ljava/nio/IntBuffer;Ljava/nio/ByteBuffer;)Ljava/nio/ByteBuffer;+10
j  org.lwjgl.opengl.Context.<init>(Lorg/lwjgl/opengl/PeerInfo;Lorg/lwjgl/opengl/ContextAttribs;Lorg/lwjgl/opengl/Context;)V+104
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;Lorg/lwjgl/opengl/Drawable;Lorg/lwjgl/opengl/ContextAttribs;)V+88
j  org.lwjgl.opengl.Display.create(Lorg/lwjgl/opengl/PixelFormat;)V+9
j  net.minecraft.client.Minecraft.a()V+151
j  net.minecraft.client.Minecraft.run()V+6
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
=>0x497b0800 JavaThread "Minecraft main thread" daemon [_thread_in_native, id=1700, stack(0x49f10000,0x49f60000)]
  0x4979c000 JavaThread "Timer hack thread" daemon [_thread_blocked, id=428, stack(0x49a60000,0x49ab0000)]
  0x003c7000 JavaThread "DestroyJavaVM" [_thread_blocked, id=3036, stack(0x009c0000,0x00a10000)]
  0x48f03400 JavaThread "TimerQueue" daemon [_thread_blocked, id=1536, stack(0x49a10000,0x49a60000)]
  0x48f13400 JavaThread "SwingWorker-pool-1-thread-1" daemon [_thread_blocked, id=1504, stack(0x499c0000,0x49a10000)]
  0x49567800 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=2824, stack(0x49970000,0x499c0000)]
  0x49564c00 JavaThread "AWT-Shutdown" [_thread_blocked, id=3276, stack(0x49920000,0x49970000)]
  0x48fdac00 JavaThread "AWT-Windows" daemon [_thread_in_native, id=2372, stack(0x49290000,0x492e0000)]
  0x48fd7c00 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=2268, stack(0x491f0000,0x49240000)]
  0x48e88400 JavaThread "Service Thread" daemon [_thread_blocked, id=3160, stack(0x49150000,0x491a0000)]
  0x48e7a400 JavaThread "C1 CompilerThread0" daemon [_thread_blocked, id=3132, stack(0x49100000,0x49150000)]
  0x48e78800 JavaThread "Attach Listener" daemon [_thread_blocked, id=3124, stack(0x490b0000,0x49100000)]
  0x48e77400 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=3108, stack(0x49060000,0x490b0000)]
  0x48d50400 JavaThread "Finalizer" daemon [_thread_blocked, id=3096, stack(0x48e10000,0x48e60000)]
  0x48d4b400 JavaThread "Reference Handler" daemon [_thread_blocked, id=3080, stack(0x48dc0000,0x48e10000)]

Other Threads:
  0x48d45c00 VMThread [stack: 0x48d70000,0x48dc0000] [id=3076]
  0x48e94000 WatcherThread [stack: 0x491a0000,0x491f0000] [id=3164]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
def new generation   total 157248K, used 84680K [0x02ab0000, 0x0d550000, 0x18000000)
  eden space 139776K,  60% used [0x02ab0000, 0x07d623d8, 0x0b330000)
  from space 17472K,   0% used [0x0b330000, 0x0b330000, 0x0c440000)
  to   space 17472K,   0% used [0x0c440000, 0x0c440000, 0x0d550000)
tenured generation   total 349568K, used 0K [0x18000000, 0x2d560000, 0x42ab0000)
   the space 349568K,   0% used [0x18000000, 0x18000000, 0x18000200, 0x2d560000)
compacting perm gen  total 12288K, used 11628K [0x42ab0000, 0x436b0000, 0x46ab0000)
   the space 12288K,  94% used [0x42ab0000, 0x4360b300, 0x4360b400, 0x436b0000)
No shared spaces configured.

Code Cache  [0x00a30000, 0x00c10000, 0x02a30000)
total_blobs=1116 nmethods=856 adapters=195 free_code_cache=30873Kb largest_free_block=31614208

Dynamic libraries:
0x00400000 - 0x0042f000     C:\Program Files\Java\jre7\bin\javaw.exe
0x7c900000 - 0x7c9b2000     C:\WINDOWS\system32\ntdll.dll
0x7c800000 - 0x7c8f6000     C:\WINDOWS\system32\kernel32.dll
0x77dd0000 - 0x77e6b000     C:\WINDOWS\system32\ADVAPI32.dll
0x77e70000 - 0x77f03000     C:\WINDOWS\system32\RPCRT4.dll
0x77fe0000 - 0x77ff1000     C:\WINDOWS\system32\Secur32.dll
0x7e410000 - 0x7e4a1000     C:\WINDOWS\system32\USER32.dll
0x77f10000 - 0x77f59000     C:\WINDOWS\system32\GDI32.dll
0x773d0000 - 0x774d3000     C:\WINDOWS\WinSxS\x86_Microsoft.Windows.Common-Controls_6595b64144ccf1df_6.0.2600.6028_x-ww_61e65202\COMCTL32.dll
0x77c10000 - 0x77c68000     C:\WINDOWS\system32\msvcrt.dll
0x77f60000 - 0x77fd6000     C:\WINDOWS\system32\SHLWAPI.dll
0x76390000 - 0x763ad000     C:\WINDOWS\system32\IMM32.DLL
0x78aa0000 - 0x78b5e000     C:\Program Files\Java\jre7\bin\msvcr100.dll
0x6d830000 - 0x6db58000     C:\Program Files\Java\jre7\bin\client\jvm.dll
0x71ad0000 - 0x71ad9000     C:\WINDOWS\system32\WSOCK32.dll
0x71ab0000 - 0x71ac7000     C:\WINDOWS\system32\WS2_32.dll
0x71aa0000 - 0x71aa8000     C:\WINDOWS\system32\WS2HELP.dll
0x76b40000 - 0x76b6d000     C:\WINDOWS\system32\WINMM.dll
0x76bf0000 - 0x76bfb000     C:\WINDOWS\system32\PSAPI.DLL
0x6d7c0000 - 0x6d7cc000     C:\Program Files\Java\jre7\bin\verify.dll
0x6d2f0000 - 0x6d310000     C:\Program Files\Java\jre7\bin\java.dll
0x6d810000 - 0x6d823000     C:\Program Files\Java\jre7\bin\zip.dll
0x6d000000 - 0x6d142000     C:\Program Files\Java\jre7\bin\awt.dll
0x77120000 - 0x771ab000     C:\WINDOWS\system32\OLEAUT32.dll
0x774e0000 - 0x7761e000     C:\WINDOWS\system32\ole32.dll
0x5ad70000 - 0x5ada8000     C:\WINDOWS\system32\uxtheme.dll
0x60d20000 - 0x60d88000     C:\PROGRAM FILES\NORTON 360\ENGINE\5.1.0.29\ASOEHOOK.DLL
0x78520000 - 0x785c3000     C:\PROGRAM FILES\NORTON 360\ENGINE\5.1.0.29\Microsoft.VC90.CRT\MSVCR90.dll
0x78480000 - 0x7850e000     C:\PROGRAM FILES\NORTON 360\ENGINE\5.1.0.29\Microsoft.VC90.CRT\MSVCP90.dll
0x74720000 - 0x7476c000     C:\WINDOWS\system32\MSCTF.dll
0x755c0000 - 0x755ee000     C:\WINDOWS\system32\msctfime.ime
0x7c9c0000 - 0x7d1d7000     C:\WINDOWS\system32\SHELL32.dll
0x6d240000 - 0x6d26a000     C:\Program Files\Java\jre7\bin\fontmanager.dll
0x6d5e0000 - 0x6d5f4000     C:\Program Files\Java\jre7\bin\net.dll
0x6d600000 - 0x6d60f000     C:\Program Files\Java\jre7\bin\nio.dll
0x71a50000 - 0x71a8f000     C:\WINDOWS\System32\mswsock.dll
0x76f20000 - 0x76f47000     C:\WINDOWS\system32\DNSAPI.dll
0x76d60000 - 0x76d79000     C:\WINDOWS\system32\iphlpapi.dll
0x76fb0000 - 0x76fb8000     C:\WINDOWS\System32\winrnr.dll
0x76f60000 - 0x76f8c000     C:\WINDOWS\system32\WLDAP32.dll
0x76fc0000 - 0x76fc6000     C:\WINDOWS\system32\rasadhlp.dll
0x662b0000 - 0x66308000     C:\WINDOWS\system32\hnetcfg.dll
0x71a90000 - 0x71a98000     C:\WINDOWS\System32\wshtcpip.dll
0x68000000 - 0x68036000     C:\WINDOWS\system32\rsaenh.dll
0x769c0000 - 0x76a74000     C:\WINDOWS\system32\USERENV.dll
0x5b860000 - 0x5b8b5000     C:\WINDOWS\system32\netapi32.dll
0x6d730000 - 0x6d750000     C:\Program Files\Java\jre7\bin\sunec.dll
0x6d760000 - 0x6d791000     C:\Program Files\Java\jre7\bin\t2k.dll
0x49250000 - 0x49257000     C:\WINDOWS\system32\ctagent.dll
0x76fd0000 - 0x7704f000     C:\WINDOWS\system32\CLBCATQ.DLL
0x77050000 - 0x77115000     C:\WINDOWS\system32\COMRes.dll
0x77c00000 - 0x77c08000     C:\WINDOWS\system32\VERSION.dll
0x6d750000 - 0x6d759000     C:\Program Files\Java\jre7\bin\sunmscapi.dll
0x77a80000 - 0x77b15000     C:\WINDOWS\system32\CRYPT32.dll
0x77b20000 - 0x77b32000     C:\WINDOWS\system32\MSASN1.dll
0x49f60000 - 0x49fcb000     C:\Documents and Settings\Alden\Application Data\.minecraft\bin\natives\lwjgl.dll
0x5ed00000 - 0x5edcc000     C:\WINDOWS\system32\OPENGL32.dll
0x68b20000 - 0x68b40000     C:\WINDOWS\system32\GLU32.dll
0x73760000 - 0x737ab000     C:\WINDOWS\system32\DDRAW.dll
0x73bc0000 - 0x73bc6000     C:\WINDOWS\system32\DCIMAN32.dll
0x6d320000 - 0x6d326000     C:\Program Files\Java\jre7\bin\jawt.dll
0x69000000 - 0x694d9000     C:\WINDOWS\system32\atioglxx.dll
0x520d0000 - 0x52748000     C:\WINDOWS\system32\atioglx1.dll

VM Arguments:
jvm_args: -Xms512m -Xmx1024m 
java_command: C:\Documents and Settings\Alden\Desktop\Minecraft.exe
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\Program Files\ATI Technologies\ATI.ACE\;C:\Program Files\Java\jre7\bin
USERNAME=Alden
OS=Windows_NT
PROCESSOR_IDENTIFIER=x86 Family 15 Model 2 Stepping 7, GenuineIntel



---------------  S Y S T E M  ---------------

OS: Windows XP Build 2600 Service Pack 3

CPU:total 1 (1 cores per cpu, 1 threads per core) family 15 model 2 stepping 7, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1047024k(497852k free), swap 2520864k(1583584k free)

vm_info: Java HotSpot(TM) Client VM (22.0-b10) for windows-x86 JRE (1.7.0_02-b13), built on Nov 17 2011 17:17:32 by "java_re" with unknown MS VC++:1600

time: Sun Jan 15 14:57:16 2012
elapsed time: 27 seconds


```

Does anyone know what's up with that?

---

### Post by DaimyoKirby on 2012-02-13
**EDIT: What is stated below in this post, contrary to what I previously thought, is wrong. Please ignore this post and continue on.**

Well, in the end, it seems that I just didn't have enough RAM. Apparently one of my RAM sticks was the wrong clock speed (333 instead of 266), so I really had 512Mb instead of 1024Mb. So I just switched it out with a 256Mb-266Mhz that I had lying around, and now I can get it to run!

To anyone in the future that is looking for an answer -
The only thing I can suggest is to make sure all your RAM is the right clock speed, and if they are, then see if your computer supports more RAM than you current have installed; if it does, get more. That *should* fix it.
At least, it did for me.

---

### Post by MichaelSeph on 2012-02-19
I got exactly the same problem report than you, the important part of it:

# Problematic frame:
# C  [atioglx1.dll+0x3fb4c7]

 It was not a problem with the driver, neither with the Java version (as I updated it), neither with Minecraft lwjgl version(as some said it could have conflicts wit hthe driver).


At the bottom it says this(for me):

Memory: 4k page, physical 1047024k(592776k free), swap 2518808k(1673736k free)

And CPU-Z scanner tells it's a 1024 MBytes DDR ram, DRAM Frequency 160.0 Mhz, single channel.
 But reading the ticket over the RAM it tells: DDR 400 (3) 

 What's what I should do ? Changing the ram is not rlly an option....

---

### Post by Perfect Storm on 2012-02-19
Moved to Other OS/Distro Talk.

---

### Post by MichaelSeph on 2012-02-20
Well, chaging the DRAM speed from BIOS is not possible, it only has 166 as max speed. So no matter the speed of the RAM card if the motherboard goes at that speed...


 the thing is that with an older RAM stick, Minecraft worked... well, they were 1x 256 + 1x 512, but now I'm only using 1 of 1024 mb.

---

### Post by DaimyoKirby on 2012-02-27
Ok, so I've now had experience with a few other computers, and it actually seems that I was just using a terrible graphics cards. My Radeon 9200 is notorious for having issues, and this was no exception.
Basically, I think that you might want to check about getting a better graphics card, depending on how old your computer is.

Someone else confirmed this in a post I made on the MC Forums [here]("http://www.minecraftforum.net/topic/1034967-lighting-issues/page__p__12882803__fromsearch__1#entry12882803"). While it doesn't discuss the same problem, Minecraft only worked when I had the integrated graphics on my computer also enabled; since I've starting using a better card, I haven't had any problems at all.

---

