---
title: "Problems with Java"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2007-07-15
I'm a 64-bit Ubuntu Feisty user who uses 32-bit Firefox with 32-bit java.  In the past this has worked fine but now for some reason Java web starts are not working for [Aevum Obscurum](http://www.aevumobscurum.com/) ( a java-based strategy game that has worked fine in the past on Ubuntu) and everytime I go to a place on the internet that uses Java, firefox32 crashes.  

Below are some details and logs for reference.  I have tried using Java 6 off Sun's website, Java 6 (32-bit) from the repositories, and Java 5 (32-bit) from the repositories.  Nothing is working for me. :confused:

Here's the log of firefox32 crashing when I went to a java-based chatroom:

> 
fatsheep:~$ firefox32
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:27343): Gtk-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.
Fontconfig warning: line 32: unknown element "cachedir"
Fontconfig warning: line 33: unknown element "cachedir"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 18: invalid match target "scan"

(firefox-bin:27343): Gtk-WARNING **: Locale not supported by C library.
Using the fallback 'C' locale.
Fontconfig warning: line 32: unknown element "cachedir"
Fontconfig warning: line 33: unknown element "cachedir"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 18: invalid match target "scan"
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: Failed to load Pango module '/usr/lib32/pango/1.5.0/modules/pango-basic-fc.so' for id 'BasicScriptEngineFc'

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory

(firefox-bin:27343): Pango-WARNING **: /usr/lib32/pango/1.5.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Fontconfig warning: line 32: unknown element "cachedir"
Fontconfig warning: line 33: unknown element "cachedir"
Fontconfig warning: "/etc/fonts/conf.d/80-delicious.conf", line 18: invalid match target "scan"
PLUGIN ERROR
************
Java process caught exception: java.lang.ExceptionInInitializerError


java.lang.ExceptionInInitializerError
at sun.plugin.JavaRunTime.initEnvironment(JavaRunTime.java:60)
at sun.plugin.navig.motif.Plugin.doit(Plugin.java:130)
at sun.plugin.navig.motif.Plugin.start(Plugin.java:103)
Caused by: java.lang.NullPointerException
at sun.awt.X11GraphicsEnvironment.registerFontPropertiesFonts(X11GraphicsEnvironment.java:627)
at sun.java2d.SunGraphicsEnvironment.initTerminalNames(SunGraphicsEnvironment.java:1127)
at sun.java2d.SunGraphicsEnvironment.initCompositeFonts(SunGraphicsEnvironment.java:859)
at sun.java2d.SunGraphicsEnvironment.access$300(SunGraphicsEnvironment.java:53)
at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:201)
at java.security.AccessController.doPrivileged(Native Method)
at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:85)
at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:163)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
at java.lang.reflect.Constructor.newInstance(Constructor.java:274)
at java.lang.Class.newInstance0(Class.java:308)
at java.lang.Class.newInstance(Class.java:261)
at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
at java.awt.Window.init(Window.java:231)
at java.awt.Window.<init>(Window.java:275)
at java.awt.Frame.<init>(Frame.java:401)
at java.awt.Frame.<init>(Frame.java:366)
at sun.plugin.AppletViewer.<clinit>(AppletViewer.java:105)
... 3 more
Java process: caught exception from sun.plugin.navig.motif.Plugin.start
Exception in thread "main" java.lang.NullPointerException
at sun.awt.X11GraphicsEnvironment.registerFontPropertiesFonts(X11GraphicsEnvironment.java:627)
at sun.java2d.SunGraphicsEnvironment.initTerminalNames(SunGraphicsEnvironment.java:1127)
at sun.java2d.SunGraphicsEnvironment.initCompositeFonts(SunGraphicsEnvironment.java:859)
at sun.java2d.SunGraphicsEnvironment.access$300(SunGraphicsEnvironment.java:53)
at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:201)
at java.security.AccessController.doPrivileged(Native Method)
at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:85)
at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:163)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
at java.lang.reflect.Constructor.newInstance(Constructor.java:274)
at java.lang.Class.newInstance0(Class.java:308)
at java.lang.Class.newInstance(Class.java:261)
at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:62)
at java.awt.Window.init(Window.java:231)
at java.awt.Window.<init>(Window.java:275)
at java.awt.Frame.<init>(Frame.java:401)
at java.awt.Frame.<init>(Frame.java:366)
at sun.plugin.viewer.LifeCycleManager.destroyCachedAppletPanels(LifeCycleManager.java:229)
at sun.plugin.navig.motif.Plugin.onExit(Plugin.java:409)
at sun.plugin.navig.motif.Plugin.doit(Plugin.java:399)
at sun.plugin.navig.motif.Plugin.start(Plugin.java:103)
INTERNAL ERROR on Browser End: Could not read ack from child process
System error?:: Resource temporarily unavailable 

And when I try to run Aevum Obscurum, it tells me I can't connect to the server (if I am using the stand alone version) or if I am using the web start it just says it can not run the application and gives me this error:

> IO exception ([http://www.aevumobscurum.com/original/webstart/RequiredWebstartRunner.version):](http://www.aevumobscurum.com/original/webstart/RequiredWebstartRunner.version):) java.net.UnknownHostException: [www.aevumobscurum.com](www.aevumobscurum.com)

Help would be greatly appreciated.

---

### Post by kknd on 2007-07-15
Looks like the host aren't up or you have internet problems. Nothing about your instalation.

Well, thats my opinion.

---

### Post by fatsheep on 2007-07-15
> **kknd said:**
> Looks like the host aren't up or you have internet problems. Nothing about your instalation.

Well, thats my opinion.

I have internet access (I'm using the same computer to post this right now) and the game is working fine for everyone else, the server is up and the creator of the game has informed me that there were about other people online when I posted [this message asking for help](http://www.multiplayerhub.com/board/viewtopic.php?p=12596#12596).  So I just can't see how it's an internet problem or a problem with the game.

---

### Post by kknd on 2007-07-15
That exception that was throw because a connection could not be done, and its rare to the JVM stop working at random.

I can't use applets too (your game uses Java web Start, a different thing). For some reason, they crash on firefox (under kommander, its normal).

Edit.: I opened the game without problems here. All 32 bits system.

---

### Post by fatsheep on 2007-07-16
> **kknd said:**
> That exception that was throw because a connection could not be done, and its rare to the JVM stop working at random.

I can't use applets too (your game uses Java web Start, a different thing). For some reason, they crash on firefox (under kommander, its normal).

Edit.: I opened the game without problems here. All 32 bits system.

Go to about:plugins (type it into the address bar) and scroll down to the Java plugin.  Here's what it says for mine:

> 
Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

What does it say for your java plugin?

---

