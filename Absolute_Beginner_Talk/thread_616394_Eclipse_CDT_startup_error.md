---
title: "Eclipse CDT startup error?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by iKevin on 2007-11-18
Hi All

I just installed eclipse + eclipse-cdt to work on some projects in "C" and I am running 7.10.  When I start eclipse, I get these error messages shown below in the welcome panel.  Do you guys have any thoughts on where to start to resolve this issue?  I did notices that eclipse is version 3.2.2 and the CDT plugin is version 3.1.X.  Perhaps they are not compatible.

Thanks
Kevin



java.lang.ClassNotFoundException: org.eclipse.core.runtime.Plugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:402)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:347)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:83)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at org.eclipse.core.runtime.Platform.getPlugin(Platform.java:737)
   at org.eclipse.core.internal.preferences.legacy.InitLegacyPreferences.init(InitLegacyPreferences.java:43)
   at org.eclipse.core.internal.preferences.PreferenceServiceRegistryHelper.applyRuntimeDefaults(PreferenceServiceRegistryHelper.java:146)
   at org.eclipse.core.internal.preferences.PreferencesService.applyRuntimeDefaults(PreferencesService.java:337)
   at org.eclipse.core.internal.preferences.DefaultPreferences.applyRuntimeDefaults(DefaultPreferences.java:162)
   at org.eclipse.core.internal.preferences.DefaultPreferences.loadDefaults(DefaultPreferences.java:231)
   at org.eclipse.core.internal.preferences.DefaultPreferences.load(DefaultPreferences.java:227)
   at org.eclipse.core.internal.preferences.EclipsePreferences.create(EclipsePreferences.java:307)
   at org.eclipse.core.internal.preferences.EclipsePreferences.internalNode(EclipsePreferences.java:543)
   at org.eclipse.core.internal.preferences.DefaultPreferences.node(DefaultPreferences.java:149)
   at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.getDefaultPreferences(PreferenceForwarder.java:138)
   at org.eclipse.core.internal.preferences.legacy.PreferenceForwarder.getString(PreferenceForwarder.java:644)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadTheme(IntroModelRoot.java:255)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadChildren(IntroModelRoot.java:172)
   at org.eclipse.ui.internal.intro.impl.model.AbstractIntroContainer.getChildren(AbstractIntroContainer.java:76)
   at org.eclipse.ui.internal.intro.impl.model.IntroModelRoot.loadModel(IntroModelRoot.java:145)
   at org.eclipse.ui.internal.intro.impl.model.loader.BaseExtensionPointManager.loadModel(BaseExtensionPointManager.java:93)
   at org.eclipse.ui.internal.intro.impl.model.loader.ExtensionPointManager.loadCurrentModel(ExtensionPointManager.java:60)
   at org.eclipse.ui.internal.intro.impl.model.loader.ExtensionPointManager.getCurrentModel(ExtensionPointManager.java:72)
   at org.eclipse.ui.intro.config.CustomizableIntroPart.init(CustomizableIntroPart.java:151)
   at org.eclipse.ui.internal.ViewIntroAdapterPart.init(ViewIntroAdapterPart.java:156)
   at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:305)
   at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:197)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.Perspective.showView(Perspective.java:1675)
   at org.eclipse.ui.internal.WorkbenchPage.busyShowView(WorkbenchPage.java:987)
   at org.eclipse.ui.internal.WorkbenchPage.access$13(WorkbenchPage.java:968)
   at org.eclipse.ui.internal.WorkbenchPage$13.run(WorkbenchPage.java:3514)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3511)
   at org.eclipse.ui.internal.WorkbenchPage.showView(WorkbenchPage.java:3487)
   at org.eclipse.ui.internal.WorkbenchIntroManager.createIntro(WorkbenchIntroManager.java:172)
   at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:119)
   at org.eclipse.ui.internal.WorkbenchWindow.restoreState(WorkbenchWindow.java:1988)
   at org.eclipse.ui.internal.Workbench.doRestoreState(Workbench.java:2873)
   at org.eclipse.ui.internal.Workbench.access$14(Workbench.java:2821)
   at org.eclipse.ui.internal.Workbench$19.run(Workbench.java:1697)
   at org.eclipse.ui.internal.Workbench.runStartupWithProgress(Workbench.java:1437)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1695)
   at org.eclipse.ui.internal.Workbench.access$12(Workbench.java:1666)
   at org.eclipse.ui.internal.Workbench$17.run(Workbench.java:1545)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.ui.internal.Workbench.restoreState(Workbench.java:1489)
   at org.eclipse.ui.internal.WorkbenchConfigurer.restoreState(WorkbenchConfigurer.java:183)
   at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:702)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1101)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1863)
   at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:422)
   at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
   at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:95)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

---

### Post by NeilPayne on 2008-02-22
Hi,
I also fell foul of this one but hit lucky and found this thread: [http://www.mail-archive.com/debian-java@lists.debian.org/msg12021.html]("http://www.mail-archive.com/debian-java@lists.debian.org/msg12021.html"). Appears to indicate it's an upstream problem (Bug#432541) with Debian. There is a workaround suggested further down the thread which worked for me and that's to install eclipse.rcp.gcj. Hope this helps.
Neil.

---

