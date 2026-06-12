---
title: "Trouble Installing Zend Sudio 5.5"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by online_lie on 2007-12-14
Hello everyone, I am attempting to install Zend Studio on Ubuntu Gutsy Gibbon. When i run "./ZendStudio-5_5_0.bin" I recieve the following message:


> Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

'SWING' UI not supported by VM.  Reverting to AWT.
Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.UnsatisfiedLinkError: /tmp/install.dir.13561/Linux/resource/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
        [INDENT]
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.load0(Unknown Source)
        at java.lang.System.load(Unknown Source)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
[/INDENT]
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)


I have no idea what is going on... any suggestions would be greatly appreciated.

Thanks,
Nick

---

### Post by toddward on 2007-12-14
Just gonna ask the one quick question...have you installed the Java?  If so, which version do you have installed?

---

### Post by online_lie on 2007-12-15
I have sun java 6  installed. This is a work machine, i may actually have a 64bit processor in there, that may be causing some of the issues.

---

