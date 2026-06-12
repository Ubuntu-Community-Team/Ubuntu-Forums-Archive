---
title: "Sun Wireless Toolkit 2.5.1EA on Linux"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by ricardor on 2007-05-09
I successfully installed the new Sun Wireless Toolkit 2.5.1 EA on my Ubuntu 6.06 Dapper system.

However, when I try to run any example MIDlet in the toolkit, it gives me this error:

java.lang.UnsatisfiedLinkError: /usr/share/WTK2.5.1EA/bin/sublime.so: Can't load IA 32-bit .so on a IA 32-bit platform
at java.lang.ClassLoader$NativeLibrary.load(Native Method)
at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
at java.lang.Runtime.load0(Runtime.java:769)
at java.lang.System.load(System.java:968)
at com.sun.kvem.Sublime.<init>(Unknown Source)
at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
at java.lang.Class.newInstance0(Class.java:350)
at java.lang.Class.newInstance(Class.java:303)
at com.sun.kvem.Lime.createLime(Unknown Source)
at com.sun.kvem.KVMBridge.<init>(Unknown Source)
at com.sun.kvem.KVMBridge.getBridge(Unknown Source)
at com.sun.kvem.midp.MIDP.run(Unknown Source)
at com.sun.kvem.environment.EmulatorInvoker.runEmulatorImpl(Unknown Source)
at com.sun.kvem.environment.EmulatorInvoker.main(Unknown Source)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
at java.lang.reflect.Method.invoke(Method.java:585)
at com.sun.kvem.environment.JVM.main(Unknown Source)

What am I doing wrong? It says I can't load an IA 32-bit .so on an IA 32-bit platform. What does that mean? I did install the x32 version of Ubuntu on my Intel machine (Inspiron B120).

Any feedback would be most appreciated.

---

