---
title: "[SOLVED] error reinstalling eclipse"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by _sluimers_ on 2007-04-24
Due to an error that made me not being able to install a plugin I thought reinstalling eclipse might work.
Now I get this error when I'm trying to start eclipse:

```

!SESSION 2007-04-24 08:59:14.108 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.1.2 (Ubuntu 4.1.2-0ubuntu5)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2007-04-24 08:59:18.884
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-24 08:59:18.884
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-24 08:59:18.884
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2007-04-24 08:59:18.885
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2007-04-24 08:59:19.070
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (173).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   ...58 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.newInstance(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:136)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:383)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.VMClassLoader.defineClass(libgcj.so.70)
   at java.lang.ClassLoader.defineClass(libgcj.so.70)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.defineClass(DefaultClassLoader.java:161)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.defineClass(ClasspathManager.java:501)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findClassImpl(ClasspathManager.java:471)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClassImpl(ClasspathManager.java:430)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:413)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   ...61 more

!ENTRY org.eclipse.osgi 4 0 2007-04-24 08:59:19.161
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (67).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:141)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   ...29 more
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:278)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:134)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:962)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:317)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:256)
   at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:342)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(EclipseLazyStarter.java:88)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:412)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:189)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:334)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2007-04-24 08:59:19.180
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
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
   at java.lang.reflect.Method.invoke(libgcj.so.70)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.make.core_3.1.1.200703212302.jar[/email] [215] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.doc.user_3.1.1.200703212302.jar[/email] [217] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.launch_3.1.1.200703212302.jar[/email] [218] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.core.linu[/email]x_3.1.1.200703212302/ [219] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.mi.core_3.1.1.200703212302.jar[/email] [220] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt_3.1.1.200703212302.jar[/email] [221] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.ui_3.1.1.200703212302.jar[/email] [222] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.make.ui_3.1.1.200703212302.jar[/email] [224] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.297
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.mi.ui_3.1.1.200703212302.jar[/email] [226] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.ui_3.1.1.200703212302.jar[/email] [228] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.ui_3.1.1.200703212302.jar[/email] [229] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.core_3.1.1.200703212302.jar[/email] [230] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.core_3.1.1.200703212302.jar[/email] [232] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.gnu.ui_3.1.1.200703212302.jar[/email] [233] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.refactoring_3.1.1.200703212302.jar[/email] [234] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2007-04-24 08:59:19.298
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.core_3.1.1.200703212302.jar[/email] [235] was not resolved.

```


If anyone could help me fix this problem, your help would be greatly appreciated. :)

---

### Post by _sluimers_ on 2007-11-10
Solved after installing Feisty 7.10

---

