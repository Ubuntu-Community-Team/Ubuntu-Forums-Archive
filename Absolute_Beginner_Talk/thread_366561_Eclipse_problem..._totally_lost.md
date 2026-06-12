---
title: "Eclipse problem... totally lost"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by KsR on 2007-02-21
hello all

I'm using Edgy eft and i installed eclipse using the ubuntuguide [HTML]http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Java_Integrated_Development_Environment_.28Eclipse.29[/HTML]

my java -version is
```
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing
```

and I am working on a Intel P4 with 512 Ram

I previously installed  Java 1,6 and was having problems using eclipse with it, so a removed java 1.6 and reinstalled Jdk 5(again using the ubuntuguide).  I configured eclipse for jdk 5 again but it wouldn't launch anymore(from the terminal as well).  
Annoyed with everything... I completely removed eclipse(using aptitude remove command) and also  Jdk 5.  I then reinstalled everything again(using the ubuntuguide) but still eclipse wont launch.  The error message asks to check the log file.  I opened the log file but have no idea what it means :confused: 
here is the log file:
```
!SESSION 2007-02-21 11:30:02.689 -----------------------------------------------
eclipse.buildId=M20060921-0945
java.version=1.5.0_08
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-02-21 11:30:05.687
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 11:30:05.688
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 11:30:05.689
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-02-21 11:30:05.689
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-02-21 11:30:05.739
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (8).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:160)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:498)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:468)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:427)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:410)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2357)
	at java.lang.Class.getConstructor0(Class.java:2671)
	at java.lang.Class.newInstance0(Class.java:321)
	at java.lang.Class.newInstance(Class.java:303)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	... 60 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2357)
	at java.lang.Class.getConstructor0(Class.java:2671)
	at java.lang.Class.newInstance0(Class.java:321)
	at java.lang.Class.newInstance(Class.java:303)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:160)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:498)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:468)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:427)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:410)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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

!ENTRY org.eclipse.osgi 4 0 2007-02-21 11:30:05.742
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (66).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:160)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:498)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:468)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:427)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:410)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	... 31 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:160)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:498)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:468)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:427)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:410)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
	at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:86)
	at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:409)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:188)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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

!ENTRY org.eclipse.osgi 4 0 2007-02-21 11:30:05.816
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException: Plug-in org.eclipse.ui.ide was unable to load class org.eclipse.ui.internal.ide.IDEApplication.
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.throwException(RegistryStrategyOSGI.java:165)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:149)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
	at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1245)
	at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:147)
	at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:759)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:51)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:74)
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

```

quite a lengthy one.. 
sorry for the long post but I thought of giving every detail.
please help.. I'm totally lost and really want to get this working as soon as possible
thanks....

---

### Post by mizar001 on 2007-02-21
Not sure, but i suggest you to install a clean version of eclipse without downloading it from repositories.

Go the the ibm website and download a clean eclipse version for linux. You only have to put it in a folder of your choice and launch the eclipse bash script. Remember to edit this script to make the eclipse use the preferred jre.

If all fail try also 

$> eclipse -clean 

As other infos, my eclipse3.2 works perfectly with java6.

Recurring to repositories to install eclipse is not the best choice, and you could realize that when you'll need of different eclipse distros (like modified workspaces for php, python and server enhanced plugins).

---

### Post by KsR on 2007-02-21
Thanks a lot.. i'll try that .. i downloaded both jdk6 and eclipse 3.2 separately :)

---

