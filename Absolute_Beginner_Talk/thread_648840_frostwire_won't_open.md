---
title: "frostwire won't open"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by trugreg on 2007-12-24
ubuntu 8.04 - I have been reading threads and trying things but get this - 

greg@greg-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb515f767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb515f8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb51af2ed]
#3 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/motif21/libmawt.so [0xb532b69e]
#4 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/motif21/libmawt.so [0xb52cfbe7]
#5 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/motif21/libmawt.so [0xb52cfe98]
#6 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/motif21/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb52d019f]
#7 [0xb5ca84ee]
#8 [0xb5ca0ea5]
#9 [0xb5ca0ea5]
#10 [0xb5c9e243]
#11 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so [0x620bc6d]
#12 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so [0x630a828]
#13 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so [0x620bb00]
#14 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x62619bb]
#15 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7cb996d]
#16 [0xb5ca84ee]
#17 [0xb5ca0d4d]
#18 [0xb5c9e243]
#19 /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so [0x620bc6d]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/usr/lib/frostwire/runFrostwire.sh: line 125: 10439 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by Maxtorm on 2007-12-24
According to this [http://scorreiait.wordpress.com/2007/11/21/graphical-java-programs-assertion-c-xliblock-failed/](http://scorreiait.wordpress.com/2007/11/21/graphical-java-programs-assertion-c-xliblock-failed/) it is a bug. The page has a fix too, which appears to be no more than a global substitution of FAKEEXTN for XINERAMA in libmawt.so.

---

### Post by trugreg on 2007-12-24
thank you that worked

---

### Post by trugreg on 2007-12-24
Now how do I change the title of this thread to add [SOLVED]

---

### Post by ghettosamson on 2007-12-24
I am having a similar problem. 
im running gutsy 64 bit
here is what mine says.
==================================
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_13]
Configuring environment...
Loading FrostWire:

Runtime link error - it appears that libXt got loaded before libXm,
which is not allowed.
java.lang.InternalError: libXt loaded before libXm
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:822)
        at java.lang.System.loadLibrary(System.java:993)
        at sun.font.FontManager$1.run(FontManager.java:178)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.font.FontManager.<clinit>(FontManager.java:173)
        at sun.java2d.SunGraphicsEnvironment.addDirFonts(SunGraphicsEnvironment.java:722)
        at sun.java2d.SunGraphicsEnvironment.registerFontsInDir(SunGraphicsEnvironment.java:602)
        at sun.java2d.SunGraphicsEnvironment.access$200(SunGraphicsEnvironment.java:58)
        at sun.java2d.SunGraphicsEnvironment$1.run(SunGraphicsEnvironment.java:174)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.java2d.SunGraphicsEnvironment.<init>(SunGraphicsEnvironment.java:94)
        at sun.awt.X11GraphicsEnvironment.<init>(X11GraphicsEnvironment.java:164)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
        at java.lang.Class.newInstance0(Class.java:350)
        at java.lang.Class.newInstance(Class.java:303)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at sun.awt.motif.MToolkit.<clinit>(MToolkit.java:93)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at java.awt.Toolkit$2.run(Toolkit.java:821)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
        at com.limegroup.gnutella.gui.Main.showInitialSplash(Main.java:67)
        at com.limegroup.gnutella.gui.Main.main(Main.java:39)


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_13-b05, mixed mode)

===============================
what to do?

---

### Post by Martje_001 on 2007-12-24
> **trugreg said:**
> Now how do I change the title of this thread to add [SOLVED]
[http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved](http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved)

---

### Post by Maxtorm on 2007-12-25
> **ghettosamson said:**
> im running gutsy 64 bit
here is what mine says....
Runtime link error - it appears that libXt got loaded before libXm,

According to [http://www.frostwire.com/forum/viewtopic.php?t=2563&sid=5cf0d826b69edd570c70fe766c821c5f](http://www.frostwire.com/forum/viewtopic.php?t=2563&sid=5cf0d826b69edd570c70fe766c821c5f) : > Frostwire needs the ia32 version of java. Try installing  
Code:  
sudo apt-get install ia32-sun-java6-bin

---

