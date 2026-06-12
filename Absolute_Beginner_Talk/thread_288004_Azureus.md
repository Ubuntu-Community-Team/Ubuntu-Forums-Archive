---
title: "Azureus"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by parradux on 2006-10-29
I have JRE installed along with Azureus. However, whenever I start it up it just crashes. How do I fix this?

---

### Post by whatintheworldisthat on 2006-10-29
Start it from a terminal and post the output so we can see what is going on.

---

### Post by Bachstelze on 2006-10-29
Did you follow the Wiki page about Azureus ?

---

### Post by parradux on 2006-10-29
Yes I did follow the wiki. 

Here it is from the terminal:

changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=8799, tid=3084990128
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# An error report file with more information is saved as hs_err_pid8799.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

---

### Post by mahy on 2006-10-29
Try downloading Azureus from its own website, unpack it and run it. Then share your experiences.

---

### Post by maniacmusician on 2006-10-29
what method did you use to install it? unless you're running a 64-bit ubuntu, i'd recommend using automatix. it's usually the way to go for a no-hassle solution. if you like playing with it, however, continue as you were.

but what method did you use to install it?

---

### Post by parradux on 2006-10-29
I used the ubuntu guide. So basically sudo apt-get install JRE packages, then sudo apt-get install azureus. 

I also tried it with automatix, and it still crashes.

---

### Post by maniacmusician on 2006-10-29
the post with the terminal run indicated that there was an error file with more information. you could try posting that file up here to see if anyone can catch anything from it.

---

### Post by parradux on 2006-10-29
Here is is

```

#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  Internal Error (53484152454432554E54494D450E43505001A3), pid=27693, tid=3085235888
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)

---------------  T H R E A D  ---------------

Current thread (0x0805cf18):  JavaThread "main" [_thread_in_Java, id=27693]

Stack: [0xbfb56000,0xbfd56000),  sp=0xbfd50040,  free space=2024k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
V  [libjvm.so+0x3251c3]
V  [libjvm.so+0x12442c]
V  [libjvm.so+0x2c257e]
V  [libjvm.so+0x28ce24]
V  [libjvm.so+0x28a034]
C  [+0x440]  __kernel_rt_sigreturn+0x0
V  [libjvm.so+0x18629a]
C  [libglibjni-0.4.so+0x8d51]
C  [libglib-2.0.so.0+0x33f87]  g_logv+0x327
C  [libglib-2.0.so.0+0x34159]  g_log+0x29
C  [libgtk-x11-2.0.so.0+0x25590b]  gtk_widget_size_allocate+0x2ab
C  [libswt-pi-gtk-3235.so+0x33ed4]  Java_org_eclipse_swt_internal_gtk_OS__1gtk_1widget_1size_1allocate+0x44
j  org.eclipse.swt.internal.gtk.OS._gtk_widget_size_allocate(ILorg/eclipse/swt/internal/gtk/GtkAllocation;)V+0
j  org.eclipse.swt.internal.gtk.OS.gtk_widget_size_allocate(ILorg/eclipse/swt/internal/gtk/GtkAllocation;)V+9
j  org.eclipse.swt.widgets.Shell.forceResize(II)V+63
j  org.eclipse.swt.widgets.Shell.resizeBounds(IIZ)V+73
j  org.eclipse.swt.widgets.Shell.setBounds(IIIIZZ)I+300
j  org.eclipse.swt.widgets.Control.setBounds(Lorg/eclipse/swt/graphics/Rectangle;)V+40
j  org.gudy.azureus2.ui.swt.shells.MessageSlideShell$1.run()V+119
j  org.eclipse.swt.widgets.RunnableLock.run()V+11
j  org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Z)Z+29
j  org.eclipse.swt.widgets.Display.runAsyncMessages(Z)Z+5
j  org.eclipse.swt.widgets.Display.readAndDispatch()Z+41
j  org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(Lcom/aelitis/azureus/ui/IUIIntializer;)V+161
j  org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(Lcom/aelitis/azureus/ui/IUIIntializer;)V+33
j  org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Lcom/aelitis/azureus/core/AzureusCore;Lorg/gudy/azureus2/ui/swt/StartServer;[Ljava/lang/String;)V+76
j  org.gudy.azureus2.ui.swt.Main.<init>([Ljava/lang/String;)V+447
j  org.gudy.azureus2.ui.swt.Main.main([Ljava/lang/String;)V+4
v  ~StubRoutines::call_stub
V  [libjvm.so+0x17a75c]
V  [libjvm.so+0x28afd8]
V  [libjvm.so+0x17a58f]
V  [libjvm.so+0x1a4e32]
V  [libjvm.so+0x196042]
C  [java+0x1873]
C  [libc.so.6+0x158cc]  __libc_start_main+0xdc


---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x088c0dd0 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=27747]
  0x088b9ae8 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=27746]
  0x088aea90 JavaThread "Slidey" daemon [_thread_blocked, id=27745]
  0x087d8ae0 JavaThread "DHTControl:internallookups[1]" daemon [_thread_blocked, id=27744]
  0x087e4bf8 JavaThread "PRUDPPacketHandler:sender" daemon [_thread_blocked, id=27743]
  0x087c1e38 JavaThread "Process Data Sources[1]" daemon [_thread_blocked, id=27742]
  0x087c4f40 JavaThread "Process Data Sources[1]" daemon [_thread_blocked, id=27741]
  0x0879b0e0 JavaThread "GUI updater" [_thread_blocked, id=27740]
  0x08786e18 JavaThread "Timer:Process Data Sources" daemon [_thread_blocked, id=27739]
  0x0873d530 JavaThread "Timer:Process Data Sources" daemon [_thread_blocked, id=27738]
  0x08705c30 JavaThread "MagnetPlugin:init" daemon [_thread_blocked, id=27736]
  0x08702b18 JavaThread "DHTTrackerPlugin:init" daemon [_thread_blocked, id=27735]
  0x08700798 JavaThread "DHTPlugin.init" daemon [_thread_blocked, id=27734]
  0x086ffbd8 JavaThread "Universal Plug and Play (UPnP)::SSDP:queryLoop" daemon [_thread_blocked, id=27733]
  0x086fd530 JavaThread "MCGroup:CtrlListener" daemon [_thread_in_native, id=27731]
  0x084a5858 JavaThread "MCGroup:MCListener" daemon [_thread_in_vm, id=27730]
  0x08701448 JavaThread "AZInstanceManager:initialSearch" daemon [_thread_blocked, id=27729]
  0x086fccb8 JavaThread "MCGroup:CtrlListener" daemon [_thread_in_native, id=27728]
  0x086fcfa8 JavaThread "MCGroup:MCListener" daemon [_thread_in_native, id=27727]
  0x086f0e60 JavaThread "MagnetURIHandler" daemon [_thread_in_native, id=27723]
  0x086f89c0 JavaThread "HostNameToIPResolver" daemon [_thread_blocked, id=27722]
  0x086dadc8 JavaThread "TRHost:ListenDispatcher" daemon [_thread_blocked, id=27721]
  0x08697088 JavaThread "StatsWriter" daemon [_thread_blocked, id=27720]
  0x085ef7e0 JavaThread "Global Status Checker" [_thread_blocked, id=27719]
  0x085e3518 JavaThread "TRHost::stats.loop" daemon [_thread_blocked, id=27718]
  0x085e92d0 JavaThread "Tracker Scrape" daemon [_thread_blocked, id=27717]
  0x085c6680 JavaThread "NonDaemonTaskRunner" [_thread_blocked, id=27716]
  0x08506db0 JavaThread "GM:ListenDispatcher" daemon [_thread_blocked, id=27715]
  0x08442360 JavaThread "Start Server" daemon [_thread_in_native, id=27713]
  0x08444c70 JavaThread "NetworkGlueUDP" daemon [_thread_blocked, id=27712]
  0x08445a80 JavaThread "PRUDPPacketReciever:48554" daemon [_thread_in_native, id=27711]
  0x0842dc38 JavaThread "WriteController:WriteSelector" daemon [_thread_in_native, id=27710]
  0x0842e7b0 JavaThread "ReadController:ReadSelector" daemon [_thread_in_native, id=27709]
  0x0842e200 JavaThread "VServerSelector:port48554" daemon [_thread_in_native, id=27708]
  0x08428650 JavaThread "ConnectDisconnectManager" daemon [_thread_in_native, id=27707]
  0x0841f200 JavaThread "ReadController:ReadProcessor" daemon [_thread_blocked, id=27706]
  0x08420400 JavaThread "WriteController:WriteProcessor" daemon [_thread_blocked, id=27705]
  0x08325958 JavaThread "Timer:Simple Timer" daemon [_thread_blocked, id=27704]
  0x082f2ac8 JavaThread "SystemTime" daemon [_thread_blocked, id=27703]
  0x080a71b8 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=27701]
  0x080a5c10 JavaThread "CompilerThread0" daemon [_thread_blocked, id=27700]
  0x080a4c38 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=27699]
  0x0809d2c0 JavaThread "Finalizer" daemon [_thread_blocked, id=27698]
  0x0809c5d8 JavaThread "Reference Handler" daemon [_thread_blocked, id=27697]
=>0x0805cf18 JavaThread "main" [_thread_in_Java, id=27693]

Other Threads:
  0x080999e8 VMThread [id=27696]
  0x080a86a0 WatcherThread [id=27702]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 def new generation   total 576K, used 80K [0x889b0000, 0x88a50000, 0x88e90000)
  eden space 512K,   3% used [0x889b0000, 0x889b43b0, 0x88a30000)
  from space 64K, 100% used [0x88a30000, 0x88a40000, 0x88a40000)
  to   space 64K,   0% used [0x88a40000, 0x88a40000, 0x88a50000)
 tenured generation   total 3928K, used 3842K [0x88e90000, 0x89266000, 0x8c9b0000)
   the space 3928K,  97% used [0x88e90000, 0x89250988, 0x89250a00, 0x89266000)
 compacting perm gen  total 11264K, used 11167K [0x8c9b0000, 0x8d4b0000, 0x909b0000)
   the space 11264K,  99% used [0x8c9b0000, 0x8d497e70, 0x8d498000, 0x8d4b0000)
    ro space 8192K,  68% used [0x909b0000, 0x90f2eaf8, 0x90f2ec00, 0x911b0000)
    rw space 12288K,  48% used [0x911b0000, 0x91779d78, 0x91779e00, 0x91db0000)

Dynamic libraries:
08048000-08057000 r-xp 00000000 03:05 1237542    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java
08057000-08059000 rwxp 0000e000 03:05 1237542    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java
08059000-0897d000 rwxp 08059000 00:00 0          [heap]
889b0000-88a50000 rwxp 889b0000 00:00 0 
88a50000-88e90000 rwxp 88a50000 00:00 0 
88e90000-89266000 rwxp 88e90000 00:00 0 
89266000-8c9b0000 rwxp 89266000 00:00 0 
8c9b0000-8d4b0000 rwxp 8c9b0000 00:00 0 
8d4b0000-909b0000 rwxp 8d4b0000 00:00 0 
909b0000-90f2f000 r-xs 00001000 03:05 1249273    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
90f2f000-911b0000 rwxp 90f2f000 00:00 0 
911b0000-9177a000 rwxp 00580000 03:05 1249273    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
9177a000-91db0000 rwxp 9177a000 00:00 0 
91db0000-91e80000 rwxp 00b4a000 03:05 1249273    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
91e80000-921b0000 rwxp 91e80000 00:00 0 
921b0000-921b4000 r-xs 00c1a000 03:05 1249273    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/classes.jsa
921b4000-925b0000 rwxp 921b4000 00:00 0 
ad479000-ad600000 r-xp 00000000 03:05 1189725    /usr/share/icons/hicolor/icon-theme.cache
ad600000-adc5c000 r-xp 00000000 03:05 1189201    /usr/share/icons/gnome/icon-theme.cache
adc5c000-adeb4000 r-xp 00000000 03:05 1189198    /usr/share/icons/Tango/icon-theme.cache
adeb4000-adf05000 r-xp 00000000 03:05 1189196    /usr/share/icons/Tangerine/icon-theme.cache
adf05000-ae066000 r-xp 00000000 03:05 1187850    /usr/share/icons/Human/icon-theme.cache
ae066000-ae06d000 r-xp 00000000 03:05 958668     /usr/lib/libfam.so.0.0.0
ae06d000-ae06e000 rwxp 00006000 03:05 958668     /usr/lib/libfam.so.0.0.0
ae06e000-ae073000 r-xp 00000000 03:05 405628     /lib/libacl.so.1.1.0
ae073000-ae074000 rwxp 00005000 03:05 405628     /lib/libacl.so.1.1.0
ae074000-ae077000 r-xp 00000000 03:05 405634     /lib/libattr.so.1.1.0
ae077000-ae078000 rwxp 00002000 03:05 405634     /lib/libattr.so.1.1.0
ae078000-ae084000 r-xp 00000000 03:05 990442     /usr/lib/gnome-vfs-2.0/modules/libfile.so
ae084000-ae085000 rwxp 0000b000 03:05 990442     /usr/lib/gnome-vfs-2.0/modules/libfile.so
ae085000-ae138000 r-xp 00000000 03:05 958533     /usr/lib/libasound.so.2.0.0
ae138000-ae13d000 rwxp 000b2000 03:05 958533     /usr/lib/libasound.so.2.0.0
ae13d000-ae140000 r-xp 00000000 03:05 958456     /usr/lib/libORBitCosNaming-2.so.0.1.0
ae140000-ae141000 rwxp 00003000 03:05 958456     /usr/lib/libORBitCosNaming-2.so.0.1.0
ae141000-ae173000 r-xp 00000000 03:05 405715     /lib/libsepol.so.1
ae173000-ae174000 rwxp 00031000 03:05 405715     /lib/libsepol.so.1
ae174000-ae17e000 rwxp ae174000 00:00 0 
ae17e000-ae1ca000 r-xp 00000000 03:05 632741     /usr/lib/libgcrypt.so.11.2.1
ae1ca000-ae1cc000 rwxp 0004b000 03:05 632741     /usr/lib/libgcrypt.so.11.2.1
ae1cc000-ae1de000 r-xp 00000000 03:05 633192     /usr/lib/libtasn1.so.3.0.5
ae1de000-ae1df000 rwxp 00011000 03:05 633192     /usr/lib/libtasn1.so.3.0.5
ae1df000-ae1f4000 r-xp 00000000 03:05 958442     /usr/lib/libICE.so.6.3.0
ae1f4000-ae1f5000 rwxp 00014000 03:05 958442     /usr/lib/libICE.so.6.3.0
ae1f5000-ae1f7000 rwxp ae1f5000 00:00 0 
ae1f7000-ae1ff000 r-xp 00000000 03:05 958460     /usr/lib/libSM.so.6.0.0
ae1ff000-ae200000 rwxp 00007000 03:05 958460     /usr/lib/libSM.so.6.0.0
ae200000-ae21e000 r-xp 00000000 03:05 632980     /usr/lib/libjpeg.so.62.0.0
ae21e000-ae21f000 rwxp 0001d000 03:05 632980     /usr/lib/libjpeg.so.62.0.0
ae21f000-ae22a000 r-xp 00000000 03:05 632823     /usr/lib/libgnome-keyring.so.0.0.1
ae22a000-ae22b000 rwxp 0000a000 03:05 632823     /usr/lib/libgnome-keyring.so.0.0.1
ae22b000-ae23f000 r-xp 00000000 03:05 958531     /usr/lib/libart_lgpl_2.so.2.3.17
ae23f000-ae240000 rwxp 00013000 03:05 958531     /usr/lib/libart_lgpl_2.so.2.3.17
ae240000-ae268000 r-xp 00000000 03:05 632835     /usr/lib/libgnomecanvas-2.so.0.1400.0
ae268000-ae269000 rwxp 00027000 03:05 632835     /usr/lib/libgnomecanvas-2.so.0.1400.0
ae269000-ae2c3000 r-xp 00000000 03:05 958571     /usr/lib/libbonoboui-2.so.0.0.0
ae2c3000-ae2c6000 rwxp 0005a000 03:05 958571     /usr/lib/libbonoboui-2.so.0.0.0
ae2c6000-ae2e4000 r-xp 00000000 03:05 958548     /usr/lib/libaudiofile.so.0.0.2
ae2e4000-ae2e6000 rwxp 0001e000 03:05 958548     /usr/lib/libaudiofile.so.0.0.2
ae2e6000-ae2ef000 r-xp 00000000 03:05 958651     /usr/lib/libesd.so.0.2.36
ae2ef000-ae2f0000 rwxp 00008000 03:05 958651     /usr/lib/libesd.so.0.2.36
ae2f0000-ae302000 r-xp 00000000 03:05 958569     /usr/lib/libbonobo-activation.so.4.0.0
ae302000-ae304000 rwxp 00012000 03:05 958569     /usr/lib/libbonobo-activation.so.4.0.0
ae304000-ae354000 r-xp 00000000 03:05 958567     /usr/lib/libbonobo-2.so.0.0.0
ae354000-ae35e000 rwxp 0004f000 03:05 958567     /usr/lib/libbonobo-2.so.0.0.0
ae35e000-ae370000 r-xp 00000000 03:05 405714     /lib/libselinux.so.1
ae370000-ae372000 rwxp 00011000 03:05 405714     /lib/libselinux.so.1
ae372000-ae380000 r-xp 00000000 03:05 958550     /usr/lib/libavahi-client.so.3.2.0
ae380000-ae381000 rwxp 0000e000 03:05 958550     /usr/lib/libavahi-client.so.3.2.0
ae381000-ae38b000 r-xp 00000000 03:05 958552     /usr/lib/libavahi-common.so.3.4.2
ae38b000-ae38c000 rwxp 00009000 03:05 958552     /usr/lib/libavahi-common.so.3.4.2
ae38c000-ae3f5000 r-xp 00000000 03:05 632855     /usr/lib/libgnutls.so.13.0.5
ae3f5000-ae3fb000 rwxp 00068000 03:05 632855     /usr/lib/libgnutls.so.13.0.5
ae3fb000-ae42a000 r-xp 00000000 03:05 958604     /usr/lib/libdbus-1.so.3.0.0
ae42a000-ae42b000 rwxp 0002f000 03:05 958604     /usr/lib/libdbus-1.so.3.0.0
ae42b000-ae445000 r-xp 00000000 03:05 958606     /usr/lib/libdbus-glib-1.so.2.0.0
ae445000-ae446000 rwxp 00019000 03:05 958606     /usr/lib/libdbus-glib-1.so.2.0.0
ae446000-ae559000 r-xp 00000000 03:05 633232     /usr/lib/libxml2.so.2.6.26
ae559000-ae55e000 rwxp 00113000 03:05 633232     /usr/lib/libxml2.so.2.6.26
ae55e000-ae55f000 rwxp ae55e000 00:00 0 
ae55f000-ae5a6000 r-xp 00000000 03:05 958452     /usr/lib/libORBit-2.so.0.1.0
ae5a6000-ae5b0000 rwxp 00046000 03:05 958452     /usr/lib/libORBit-2.so.0.1.0
ae5b0000-ae5de000 r-xp 00000000 03:05 632739     /usr/lib/libgconf-2.so.4.1.0
ae5de000-ae5e1000 rwxp 0002e000 03:05 632739     /usr/lib/libgconf-2.so.4.1.0
ae5e1000-ae666000 r-xp 00000000 03:05 632847     /usr/lib/libgnomeui-2.so.0.1600.1
ae666000-ae66a000 rwxp 00084000 03:05 632847     /usr/lib/libgnomeui-2.so.0.1600.1
ae66a000-ae6bf000 r-xp 00000000 03:05 632849     /usr/lib/libgnomevfs-2.so.0.1600.1
ae6bf000-ae6c2000 rwxp 00054000 03:05 632849     /usr/lib/libgnomevfs-2.so.0.1600.1
ae6c2000-ae6c5000 ---p ae6c2000 00:00 0 
ae6c5000-ae743000 rwxp ae6c5000 00:00 0 
ae743000-ae746000 ---p ae743000 00:00 0 
ae746000-ae7c4000 rwxp ae746000 00:00 0 
ae7c4000-ae82b000 r-xp 00000000 03:05 1237585    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libfontmanager.so
ae82b000-ae835000 rwxp 00067000 03:05 1237585    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libfontmanager.so
ae835000-ae839000 rwxp ae835000 00:00 0 
ae839000-ae8ff000 r-xp 00000000 03:05 1237581    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libmlib_image.so
ae8ff000-ae900000 rwxp 000c5000 03:05 1237581    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libmlib_image.so
ae900000-ae960000 r-xp 00000000 03:05 1237582    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libawt.so
ae960000-ae966000 rwxp 0005f000 03:05 1237582    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libawt.so
ae966000-ae98a000 rwxp ae966000 00:00 0 
ae98a000-ae98d000 ---p ae98a000 00:00 0 
ae98d000-aea0b000 rwxp ae98d000 00:00 0 
aea0b000-aea77000 r-xp 00000000 03:05 1119608    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
aea77000-aea7a000 ---p aea77000 00:00 0 
aea7a000-aeaf8000 rwxp aea7a000 00:00 0 
aeaf8000-aeafb000 ---p aeaf8000 00:00 0 
aeafb000-aeb79000 rwxp aeafb000 00:00 0 
aeb79000-aeb7c000 ---p aeb79000 00:00 0 
aeb7c000-aebfa000 rwxp aeb7c000 00:00 0 
aebfa000-aebfd000 ---p aebfa000 00:00 0 
aebfd000-aec7b000 rwxp aebfd000 00:00 0 
aec7b000-aec7e000 ---p aec7b000 00:00 0 
aec7e000-aecfc000 rwxp aec7e000 00:00 0 
aecfc000-aecff000 ---p aecfc000 00:00 0 
aecff000-aed7d000 rwxp aecff000 00:00 0 
aed7d000-aed80000 ---p aed7d000 00:00 0 
aed80000-aedfe000 rwxp aed80000 00:00 0 
aedfe000-aee01000 ---p aedfe000 00:00 0 
aee01000-aee7f000 rwxp aee01000 00:00 0 
aee7f000-aee82000 ---p aee7f000 00:00 0 
aee82000-aef21000 rwxp aee82000 00:00 0 
aef21000-af000000 ---p aef21000 00:00 0 
af001000-af004000 r-xp 00000000 03:05 632859     /usr/lib/libgpg-error.so.0.2.0
af004000-af005000 rwxp 00002000 03:05 632859     /usr/lib/libgpg-error.so.0.2.0
af005000-af019000 r-xp 00000000 03:05 632819     /usr/lib/libgnome-2.so.0.1600.0
af019000-af01a000 rwxp 00013000 03:05 632819     /usr/lib/libgnome-2.so.0.1600.0
af01a000-af07a000 rwxs 00000000 00:08 5865501    /SYSV00000000 (deleted)
af07a000-af07d000 ---p af07a000 00:00 0 
af07d000-af0fb000 rwxp af07d000 00:00 0 
af0fb000-af0fe000 ---p af0fb000 00:00 0 
af0fe000-af17c000 rwxp af0fe000 00:00 0 
af17c000-af17f000 ---p af17c000 00:00 0 
af17f000-af1fd000 rwxp af17f000 00:00 0 
af1fd000-af200000 ---p af1fd000 00:00 0 
af200000-af27e000 rwxp af200000 00:00 0 
af27e000-af281000 ---p af27e000 00:00 0 
af281000-af2ff000 rwxp af281000 00:00 0 
af2ff000-af302000 ---p af2ff000 00:00 0 
af302000-af380000 rwxp af302000 00:00 0 
af380000-af383000 ---p af380000 00:00 0 
af383000-af401000 rwxp af383000 00:00 0 
af401000-af410000 r-xp 00000000 03:05 438456     /lib/tls/i686/cmov/libresolv-2.4.so
af410000-af412000 rwxp 0000f000 03:05 438456     /lib/tls/i686/cmov/libresolv-2.4.so
af412000-af414000 rwxp af412000 00:00 0 
af414000-af418000 r-xp 00000000 03:05 438443     /lib/tls/i686/cmov/libnss_dns-2.4.so
af418000-af41a000 rwxp 00003000 03:05 438443     /lib/tls/i686/cmov/libnss_dns-2.4.so
af41c000-af422000 r-xp 00000000 03:05 405704     /lib/libpopt.so.0.0.0
af422000-af423000 rwxp 00006000 03:05 405704     /lib/libpopt.so.0.0.0
af423000-af426000 rwxs 00000000 00:08 5832732    /SYSV00000000 (deleted)
af426000-af429000 ---p af426000 00:00 0 
af429000-af4a7000 rwxp af429000 00:00 0 
af4a7000-af4aa000 ---p af4a7000 00:00 0 
af4aa000-af528000 rwxp af4aa000 00:00 0 
af528000-af52a000 r-xp 00000000 03:05 1055333    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
af52a000-af52b000 rwxp 00001000 03:05 1055333    /usr/lib/pango/1.5.0/modules/pango-basic-fc.so
af52b000-af59c000 r-xp 00000000 03:05 1119612    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
af59c000-af59f000 ---p af59c000 00:00 0 
af59f000-af61d000 rwxp af59f000 00:00 0 
af61d000-af61f000 r-xp 00000000 03:05 1250114    /usr/share/locale-langpack/en_CA/LC_MESSAGES/atk10.mo
af61f000-af622000 ---p af61f000 00:00 0 
af622000-af6a0000 rwxp af622000 00:00 0 
af6a0000-af6a3000 ---p af6a0000 00:00 0 
af6a3000-af721000 rwxp af6a3000 00:00 0 
af721000-af781000 rwxs 00000000 00:08 5799963    /SYSV00000000 (deleted)
af782000-af784000 r-xp 00000000 03:05 438462     /lib/tls/i686/cmov/libutil-2.4.so
af784000-af786000 rwxp 00001000 03:05 438462     /lib/tls/i686/cmov/libutil-2.4.so
af786000-af788000 r-xp 00000000 03:05 958556     /usr/lib/libavahi-glib.so.1.0.1
af788000-af789000 rwxp 00002000 03:05 958556     /usr/lib/libavahi-glib.so.1.0.1
af78e000-af795000 r-xp 00000000 03:05 1250233    /usr/share/locale-langpack/en_CA/LC_MESSAGES/totem.mo
af795000-af798000 r-xp 00000000 03:05 1138954    /usr/lib/jni/libswt-gnome-gtk-3235.so
af798000-af799000 rwxp 00002000 03:05 1138954    /usr/lib/jni/libswt-gnome-gtk-3235.so
af799000-af7c7000 r-xp 00000000 03:05 1249254    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/xawt/libmawt.so
af7c7000-af7ca000 rwxp 0002e000 03:05 1249254    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/xawt/libmawt.so
af7ca000-af7cb000 rwxp af7ca000 00:00 0 
af7cb000-af7ce000 ---p af7cb000 00:00 0 
af7ce000-af84c000 rwxp af7ce000 00:00 0 
af84c000-af84f000 ---p af84c000 00:00 0 
af84f000-af8cd000 rwxp af84f000 00:00 0 
af8cd000-af8d0000 ---p af8cd000 00:00 0 
af8d0000-af94e000 rwxp af8d0000 00:00 0 
af94e000-af961000 r-xs 00000000 03:05 1058268    /usr/share/azureus/plugins/bdcc/bdcc_2.2.2.jar
af961000-af98d000 r-xs 00000000 03:05 1058265    /usr/share/azureus/plugins/azplugins/azplugins_2.1.1.jar
af98d000-afb14000 r-xp 00000000 03:05 1189725    /usr/share/icons/hicolor/icon-theme.cache
afb14000-b0170000 r-xp 00000000 03:05 1189201    /usr/share/icons/gnome/icon-theme.cache
b0170000-b03c8000 r-xp 00000000 03:05 1189198    /usr/share/icons/Tango/icon-theme.cache
b03c8000-b0419000 r-xp 00000000 03:05 1189196    /usr/share/icons/Tangerine/icon-theme.cache
b0419000-b057a000 r-xp 00000000 03:05 1187850    /usr/share/icons/Human/icon-theme.cache
b057a000-b057e000 r-xp 00000000 03:05 1250154    /usr/share/locale-langpack/en_CA/LC_MESSAGES/glib20.mo
b057e000-b058b000 r-xp 00000000 03:05 1139006    /usr/lib/jni/libglibjni-0.4.so
b058b000-b058c000 rwxp 0000c000 03:05 1139006    /usr/lib/jni/libglibjni-0.4.so
b058c000-b063c000 r-xp 00000000 03:05 1138984    /usr/lib/jni/libgtkjni-2.10.so
b063c000-b063f000 rwxp 000af000 03:05 1138984    /usr/lib/jni/libgtkjni-2.10.so
b063f000-b0642000 ---p b063f000 00:00 0 
b0642000-b06c0000 rwxp b0642000 00:00 0 
b06c0000-b06d1000 r-xp 00000000 03:05 990490     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b06d1000-b06d2000 rwxp 00011000 03:05 990490     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b06d2000-b0707000 r-xp 00000000 03:05 1138957    /usr/lib/jni/libswt-gtk-3235.so
b0707000-b0709000 rwxp 00034000 03:05 1138957    /usr/lib/jni/libswt-gtk-3235.so
b0709000-b070a000 rwxp b0709000 00:00 0 
b070a000-b070b000 r-xp 00000000 03:05 974530     /usr/lib/gconv/ISO8859-1.so
b070b000-b070d000 rwxp 00001000 03:05 974530     /usr/lib/gconv/ISO8859-1.so
b070d000-b0728000 r-xp 00000000 03:05 1250193    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20-properties.mo
b0728000-b0732000 r-xp 00000000 03:05 1250194    /usr/share/locale-langpack/en_CA/LC_MESSAGES/gtk20.mo
b0732000-b0809000 r-xp 00000000 03:05 1006765    /usr/lib/locale/en_CA.utf8/LC_COLLATE
b0809000-b0825000 r-xp 00000000 03:05 958664     /usr/lib/libexpat.so.1.0.0
b0825000-b0827000 rwxp 0001c000 03:05 958664     /usr/lib/libexpat.so.1.0.0
b0827000-b0849000 r-xp 00000000 03:05 633110     /usr/lib/libpng12.so.0.1.2.8
b0849000-b084a000 rwxp 00021000 03:05 633110     /usr/lib/libpng12.so.0.1.2.8
b084a000-b084e000 r-xp 00000000 03:05 958479     /usr/lib/libXdmcp.so.6.0.0
b084e000-b084f000 rwxp 00003000 03:05 958479     /usr/lib/libXdmcp.so.6.0.0
b084f000-b0851000 r-xp 00000000 03:05 958470     /usr/lib/libXau.so.6.0.0
b0851000-b0852000 rwxp 00001000 03:05 958470     /usr/lib/libXau.so.6.0.0
b0852000-b0865000 r-xp 00000000 03:05 633244     /usr/lib/libz.so.1.2.3
b0865000-b0866000 rwxp 00012000 03:05 633244     /usr/lib/libz.so.1.2.3
b0866000-b08cd000 r-xp 00000000 03:05 958680     /usr/lib/libfreetype.so.6.3.10
b08cd000-b08d0000 rwxp 00067000 03:05 958680     /usr/lib/libfreetype.so.6.3.10
b08d0000-b08fa000 r-xp 00000000 03:05 633089     /usr/lib/libpangoft2-1.0.so.0.1400.5
b08fa000-b08fb000 rwxp 00029000 03:05 633089     /usr/lib/libpangoft2-1.0.so.0.1400.5
b08fb000-b08ff000 r-xp 00000000 03:05 958485     /usr/lib/libXfixes.so.3.1.0
b08ff000-b0900000 rwxp 00003000 03:05 958485     /usr/lib/libXfixes.so.3.1.0
b0900000-b0908000 r-xp 00000000 03:05 958475     /usr/lib/libXcursor.so.1.0.2
b0908000-b0909000 rwxp 00007000 03:05 958475     /usr/lib/libXcursor.so.1.0.2
b0909000-b090b000 r-xp 00000000 03:05 958503     /usr/lib/libXrandr.so.2.0.0
b090b000-b090c000 rwxp 00002000 03:05 958503     /usr/lib/libXrandr.so.2.0.0
b090c000-b0913000 r-xp 00000000 03:05 958491     /usr/lib/libXi.so.6.0.0
b0913000-b0914000 rwxp 00006000 03:05 958491     /usr/lib/libXi.so.6.0.0
b0914000-b0916000 r-xp 00000000 03:05 958493     /usr/lib/libXinerama.so.1.0.0
b0916000-b0917000 rwxp 00001000 03:05 958493     /usr/lib/libXinerama.so.1.0.0
b0917000-b091e000 r-xp 00000000 03:05 958505     /usr/lib/libXrender.so.1.3.0
b091e000-b091f000 rwxp 00006000 03:05 958505     /usr/lib/libXrender.so.1.3.0
b091f000-b0948000 r-xp 00000000 03:05 958670     /usr/lib/libfontconfig.so.1.0.4
b0948000-b094d000 rwxp 00028000 03:05 958670     /usr/lib/libfontconfig.so.1.0.4
b094d000-b094e000 rwxp b094d000 00:00 0 
b094e000-b095a000 r-xp 00000000 03:05 958483     /usr/lib/libXext.so.6.4.0
b095a000-b095b000 rwxp 0000c000 03:05 958483     /usr/lib/libXext.so.6.4.0
b095b000-b0962000 r-xp 00000000 03:05 438458     /lib/tls/i686/cmov/librt-2.4.so
b0962000-b0964000 rwxp 00006000 03:05 438458     /lib/tls/i686/cmov/librt-2.4.so
b0964000-b09c4000 r-xp 00000000 03:05 958575     /usr/lib/libcairo.so.2.9.2
b09c4000-b09c6000 rwxp 0005f000 03:05 958575     /usr/lib/libcairo.so.2.9.2
b09c6000-b0a57000 r-xp 00000000 03:05 632805     /usr/lib/libglib-2.0.so.0.1200.4
b0a57000-b0a58000 rwxp 00091000 03:05 632805     /usr/lib/libglib-2.0.so.0.1200.4
b0a58000-b0a91000 r-xp 00000000 03:05 632857     /usr/lib/libgobject-2.0.so.0.1200.4
b0a91000-b0a92000 rwxp 00038000 03:05 632857     /usr/lib/libgobject-2.0.so.0.1200.4
b0a92000-b0aaa000 r-xp 00000000 03:05 958542     /usr/lib/libatk-1.0.so.0.1213.0
b0aaa000-b0aac000 rwxp 00017000 03:05 958542     /usr/lib/libatk-1.0.so.0.1213.0
b0aac000-b0b72000 r-xp 00000000 03:05 958464     /usr/lib/libX11.so.6.2.0
b0b72000-b0b75000 rwxp 000c5000 03:05 958464     /usr/lib/libX11.so.6.2.0
b0b75000-b0bad000 r-xp 00000000 03:05 633085     /usr/lib/libpango-1.0.so.0.1400.5
b0bad000-b0baf000 rwxp 00037000 03:05 633085     /usr/lib/libpango-1.0.so.0.1400.5
b0baf000-b0bb6000 r-xp 00000000 03:05 633087     /usr/lib/libpangocairo-1.0.so.0.1400.5
b0bb6000-b0bb7000 rwxp 00006000 03:05 633087     /usr/lib/libpangocairo-1.0.so.0.1400.5
b0bb7000-b0c38000 r-xp 00000000 03:05 632756     /usr/lib/libgdk-x11-2.0.so.0.1000.6
b0c38000-b0c3b000 rwxp 00081000 03:05 632756     /usr/lib/libgdk-x11-2.0.so.0.1000.6
b0c3b000-b0c50000 r-xp 00000000 03:05 632758     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b0c50000-b0c51000 rwxp 00015000 03:05 632758     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.6
b0c51000-b0c55000 r-xp 00000000 03:05 958511     /usr/lib/libXtst.so.6.1.0
b0c55000-b0c56000 rwxp 00003000 03:05 958511     /usr/lib/libXtst.so.6.1.0
b0c56000-b0c5a000 r-xp 00000000 03:05 632909     /usr/lib/libgthread-2.0.so.0.1200.4
b0c5a000-b0c5b000 rwxp 00003000 03:05 632909     /usr/lib/libgthread-2.0.so.0.1200.4
b0c5b000-b0fa4000 r-xp 00000000 03:05 632912     /usr/lib/libgtk-x11-2.0.so.0.1000.6
b0fa4000-b0faa000 rwxp 00349000 03:05 632912     /usr/lib/libgtk-x11-2.0.so.0.1000.6
b0faa000-b0fab000 rwxp b0faa000 00:00 0 
b0fac000-b0fad000 r-xp 00000000 03:05 973828     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b0fad000-b0fae000 rwxp 00000000 03:05 973828     /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b0fae000-b0faf000 r-xp 00000000 03:05 1006771    /usr/lib/locale/en_CA.utf8/LC_NUMERIC
b0faf000-b0fb0000 r-xp 00000000 03:05 1006774    /usr/lib/locale/en_CA.utf8/LC_TIME
b0fb0000-b0fb1000 r-xp 00000000 03:05 1006769    /usr/lib/locale/en_CA.utf8/LC_MONETARY
b0fb1000-b0fb2000 r-xp 00000000 03:05 1022152    /usr/lib/locale/en_CA.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b0fb2000-b0fb3000 r-xp 00000000 03:05 1006772    /usr/lib/locale/en_CA.utf8/LC_PAPER
b0fb3000-b0fb4000 r-xp 00000000 03:05 1006770    /usr/lib/locale/en_CA.utf8/LC_NAME
b0fb4000-b0fb5000 r-xp 00000000 03:05 1006764    /usr/lib/locale/en_CA.utf8/LC_ADDRESS
b0fb5000-b0fb6000 r-xp 00000000 03:05 1006773    /usr/lib/locale/en_CA.utf8/LC_TELEPHONE
b0fb6000-b0fb7000 r-xp 00000000 03:05 1006768    /usr/lib/locale/en_CA.utf8/LC_MEASUREMENT
b0fb7000-b100d000 r-xp 00000000 03:05 1138958    /usr/lib/jni/libswt-pi-gtk-3235.so
b100d000-b100f000 rwxp 00055000 03:05 1138958    /usr/lib/jni/libswt-pi-gtk-3235.so
b100f000-b1012000 ---p b100f000 00:00 0 
b1012000-b1090000 rwxp b1012000 00:00 0 
b1090000-b1093000 ---p b1090000 00:00 0 
b1093000-b1111000 rwxp b1093000 00:00 0 
b1111000-b1114000 ---p b1111000 00:00 0 
b1114000-b1192000 rwxp b1114000 00:00 0 
b1192000-b1195000 ---p b1192000 00:00 0 
b1195000-b1213000 rwxp b1195000 00:00 0 
b1213000-b1216000 ---p b1213000 00:00 0 
b1216000-b1294000 rwxp b1216000 00:00 0 
b1294000-b1297000 ---p b1294000 00:00 0 
b1297000-b1315000 rwxp b1297000 00:00 0 
b1315000-b1318000 ---p b1315000 00:00 0 
b1318000-b1396000 rwxp b1318000 00:00 0 
b1396000-b139c000 r-xp 00000000 03:05 1237575    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnio.so
b139c000-b139d000 rwxp 00005000 03:05 1237575    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnio.so
b139d000-b13a0000 ---p b139d000 00:00 0 
b13a0000-b141e000 rwxp b13a0000 00:00 0 
b141e000-b1421000 ---p b141e000 00:00 0 
b1421000-b149f000 rwxp b1421000 00:00 0 
b149f000-b153f000 r-xs 00000000 03:05 1071936    /usr/share/java/gtk2.10.jar
b153f000-b1547000 r-xs 00000000 03:05 1071935    /usr/share/java/cairo1.0.jar
b1547000-b154d000 r-xs 00000000 03:05 1071934    /usr/share/java/glib0.4.jar
b154d000-b16fa000 r-xs 00000000 03:05 1138968    /usr/lib/eclipse/plugins/org.eclipse.swt.gtk.linux.x86_3.2.1.v3235.jar
b16fa000-b1702000 r-xs 00000000 03:05 1071929    /usr/share/java/commons-cli-1.0.jar
b1702000-b1736000 r-xs 00000000 03:05 1071931    /usr/share/java/log4j-1.2.13.jar
b1736000-b182b000 r-xs 00000000 03:05 1071925    /usr/share/java/bcprov.jar
b182b000-b182e000 ---p b182b000 00:00 0 
b182e000-b18ac000 rwxp b182e000 00:00 0 
b18ac000-b18af000 ---p b18ac000 00:00 0 
b18af000-b192d000 rwxp b18af000 00:00 0 
b192d000-b193e000 r-xp 00000000 03:05 1237574    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnet.so
b193e000-b193f000 rwxp 00011000 03:05 1237574    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libnet.so
b193f000-b1965000 rwxp b193f000 00:00 0 
b1965000-b2092000 r-xs 00000000 03:05 1071915    /usr/share/java/Azureus2.jar
b2092000-b2156000 r-xs 00000000 03:05 1249270    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/localedata.jar
b2156000-b2181000 r-xs 00000000 03:05 1249260    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/sunpkcs11.jar
b2181000-b21a8000 r-xs 00000000 03:05 1249268    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/sunjce_provider.jar
b21a8000-b21a9000 ---p b21a8000 00:00 0 
b21a9000-b2229000 rwxp b21a9000 00:00 0 
b2229000-b222c000 ---p b2229000 00:00 0 
b222c000-b22aa000 rwxp b222c000 00:00 0 
b22aa000-b22ad000 ---p b22aa000 00:00 0 
b22ad000-b232b000 rwxp b22ad000 00:00 0 
b232b000-b232e000 ---p b232b000 00:00 0 
b232e000-b23ac000 rwxp b232e000 00:00 0 
b23ac000-b23b3000 r-xs 00000000 03:05 974582     /usr/lib/gconv/gconv-modules.cache
b23b3000-b23e6000 r-xp 00000000 03:05 1006766    /usr/lib/locale/en_CA.utf8/LC_CTYPE
b23e6000-b23e9000 ---p b23e6000 00:00 0 
b23e9000-b2467000 rwxp b23e9000 00:00 0 
b2467000-b246a000 ---p b2467000 00:00 0 
b246a000-b24e8000 rwxp b246a000 00:00 0 
b24e8000-b24e9000 ---p b24e8000 00:00 0 
b24e9000-b257b000 rwxp b24e9000 00:00 0 
b257b000-b2596000 rwxp b257b000 00:00 0 
b2596000-b2598000 rwxp b2596000 00:00 0 
b2598000-b25b4000 rwxp b2598000 00:00 0 
b25b4000-b25b5000 rwxp b25b4000 00:00 0 
b25b5000-b25b6000 rwxp b25b5000 00:00 0 
b25b6000-b25b9000 rwxp b25b6000 00:00 0 
b25b9000-b25d4000 rwxp b25b9000 00:00 0 
b25d4000-b25da000 rwxp b25d4000 00:00 0 
b25da000-b25f4000 rwxp b25da000 00:00 0 
b25f4000-b2606000 rwxp b25f4000 00:00 0 
b2606000-b267f000 rwxp b2606000 00:00 0 
b267f000-b281f000 rwxp b267f000 00:00 0 
b281f000-b467f000 rwxp b281f000 00:00 0 
b467f000-b4eef000 r-xs 00000000 03:05 1237675    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/charsets.jar
b4eef000-b4f04000 r-xs 00000000 03:05 1237674    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/jce.jar
b4f04000-b4f89000 r-xs 00000000 03:05 1237673    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/jsse.jar
b4f89000-b4ff2000 rwxp b4f89000 00:00 0 
b4ff2000-b7608000 r-xs 00000000 03:05 1237626    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/rt.jar
b7608000-b7617000 r-xp 00000000 03:05 1237571    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libzip.so
b7617000-b7619000 rwxp 0000e000 03:05 1237571    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libzip.so
b7619000-b763a000 r-xp 00000000 03:05 1237570    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjava.so
b763a000-b763c000 rwxp 00020000 03:05 1237570    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libjava.so
b763c000-b7647000 r-xp 00000000 03:05 1237569    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libverify.so
b7647000-b7648000 rwxp 0000b000 03:05 1237569    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/libverify.so
b7648000-b7651000 r-xp 00000000 03:05 438445     /lib/tls/i686/cmov/libnss_files-2.4.so
b7651000-b7653000 rwxp 00008000 03:05 438445     /lib/tls/i686/cmov/libnss_files-2.4.so
b7653000-b765b000 r-xp 00000000 03:05 438449     /lib/tls/i686/cmov/libnss_nis-2.4.so
b765b000-b765d000 rwxp 00007000 03:05 438449     /lib/tls/i686/cmov/libnss_nis-2.4.so
b765d000-b7664000 r-xp 00000000 03:05 438441     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7664000-b7666000 rwxp 00006000 03:05 438441     /lib/tls/i686/cmov/libnss_compat-2.4.so
b7666000-b7678000 r-xp 00000000 03:05 438439     /lib/tls/i686/cmov/libnsl-2.4.so
b7678000-b767a000 rwxp 00011000 03:05 438439     /lib/tls/i686/cmov/libnsl-2.4.so
b767a000-b767c000 rwxp b767a000 00:00 0 
b767c000-b767f000 r-xp 00000000 03:05 632817     /usr/lib/libgmodule-2.0.so.0.1200.4
b767f000-b7680000 rwxp 00002000 03:05 632817     /usr/lib/libgmodule-2.0.so.0.1200.4
b7680000-b7688000 rwxs 00000000 03:05 1139370    /tmp/hsperfdata_boris/27693
b7688000-b76ac000 r-xp 00000000 03:05 438436     /lib/tls/i686/cmov/libm-2.4.so
b76ac000-b76ae000 rwxp 00023000 03:05 438436     /lib/tls/i686/cmov/libm-2.4.so
b76ae000-b7a1a000 r-xp 00000000 03:05 1249251    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/libjvm.so
b7a1a000-b7a39000 rwxp 0036b000 03:05 1249251    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client/libjvm.so
b7a39000-b7e50000 rwxp b7a39000 00:00 0 
b7e50000-b7f7d000 r-xp 00000000 03:05 438428     /lib/tls/i686/cmov/libc-2.4.so
b7f7d000-b7f7f000 r-xp 0012c000 03:05 438428     /lib/tls/i686/cmov/libc-2.4.so
b7f7f000-b7f81000 rwxp 0012e000 03:05 438428     /lib/tls/i686/cmov/libc-2.4.so
b7f81000-b7f85000 rwxp b7f81000 00:00 0 
b7f85000-b7f87000 r-xp 00000000 03:05 438434     /lib/tls/i686/cmov/libdl-2.4.so
b7f87000-b7f89000 rwxp 00001000 03:05 438434     /lib/tls/i686/cmov/libdl-2.4.so
b7f89000-b7f98000 r-xp 00000000 03:05 438454     /lib/tls/i686/cmov/libpthread-2.4.so
b7f98000-b7f9a000 rwxp 0000f000 03:05 438454     /lib/tls/i686/cmov/libpthread-2.4.so
b7f9a000-b7f9c000 rwxp b7f9a000 00:00 0 
b7f9c000-b7f9d000 r-xp 00000000 03:05 1006767    /usr/lib/locale/en_CA.utf8/LC_IDENTIFICATION
b7f9d000-b7f9f000 r-xs 00000000 03:05 1249269    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext/dnsns.jar
b7f9f000-b7fa5000 r-xp 00000000 03:05 1237562    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/native_threads/libhpi.so
b7fa5000-b7fa6000 rwxp 00006000 03:05 1237562    /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/native_threads/libhpi.so
b7fa6000-b7fa7000 rwxp b7fa6000 00:00 0 
b7fa7000-b7fa8000 r-xp b7fa7000 00:00 0 
b7fa8000-b7faa000 rwxp b7fa8000 00:00 0 
b7faa000-b7fc3000 r-xp 00000000 03:05 405622     /lib/ld-2.4.so
b7fc3000-b7fc5000 rwxp 00018000 03:05 405622     /lib/ld-2.4.so
bfb56000-bfb59000 ---p bfb56000 00:00 0 
bfb59000-bfd56000 rwxp bfb59000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -Djava.library.path=/usr/lib/jni:/usr/lib -Dgnu.gcj.runtime.VMClassLoader.library_control=never -Dazureus.install.path=/home/boris/.azureus
java_command: org.gudy.azureus2.ui.swt.Main
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=boris
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/i386:/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/../lib/i386:/usr/lib/jni
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x325bd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x325bd0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x28a010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: SIG_IGN, sa_mask[0]=0x00001000, sa_flags=0x10000000
SIGILL: [libjvm.so+0x28a010], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x28c460], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x28be90], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
libc:glibc 2.4 NPTL 2.4 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.55 0.45 0.27

CPU:total 1 (cores per cpu 1, threads per core 1) family 6 model 13 stepping 6, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 1034976k(136456k free), swap 2096408k(2091460k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_08-b03) for linux-x86, built on Jul 11 2006 09:55:52 by java_re with gcc 3.2.1-7a (J2SE release)


```

---

### Post by parradux on 2006-10-29
anyone?

---

### Post by akniss on 2006-10-30
FROM:  [http://www.ubuntuforums.org/showthread.php?t=283364](http://www.ubuntuforums.org/showthread.php?t=283364)
- Azureus from the repositories is broken
* Bug report : [https://launchpad.net/distros/ubuntu...eus/+bug/57875](https://launchpad.net/distros/ubuntu...eus/+bug/57875)
* Workaround : [http://ubuntuforums.org/showthread.p...hlight=azureus](http://ubuntuforums.org/showthread.p...hlight=azureus)

If you are using Edgy, there are known issues with Azureus.  If you are not using edgy, disregard this post.

---

### Post by randomi on 2006-10-30
I had the same issues. I installed it from the backports and it worked just fine.

---

### Post by anywebloco on 2006-11-13
What worked for me is deleting (rm -r) the .azureus directory in $user

---

