---
title: "java error in ubuntu7.10"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by mokkai on 2008-04-09
just now i installed ubuntu7.10
and installed sun-java5-jre

when i start my eclipse 
it giving  log error below 
 
!SESSION 2008-04-09 21:12:10.706 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_13
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_IN
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2008-04-09 21:12:12.034
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/pkthegreat/aptana/configuration/org.eclipse.osgi/bundles/75/1/.cp/libswt-pi-gtk-3236.so: Can't load IA 32-bit .so on a AMD 64-bit platform
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:993)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:436)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at com.aptana.ide.rcp.AbstractIDEApplication.createDisplay(AbstractIDEApplication.java:152)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(AbstractIDEApplication.java:89)
	at com.aptana.ide.rcp.Application.run(Application.java:43)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

---

### Post by jken146 on 2008-04-09
If I were you I'd uninstall sun-java5-jre and install sun-java6-jre.

---

### Post by mokkai on 2008-04-09
now thats is fine .....
ooo.. thank you so much ....

---

