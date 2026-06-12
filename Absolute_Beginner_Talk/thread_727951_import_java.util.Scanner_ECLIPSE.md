---
title: "import java.util.Scanner ECLIPSE"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by nick937 on 2008-03-18
Eclipse  tells me that:
```

Severity and Description	Path	Resource	Location	Creation Time	Id
Scanner cannot be resolved to a type	Lab17b	Lab17.java	line 8	1205850539546	244

```
I was using JRE 1.5, now I updated to JRE 1.6 to see if it would fix it... no luck
and when I start up Eclipse, it opens my project and gives me this:

```

Unable to create this part due to an internal error. Reason for the failure: An exception was thrown during initialization

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
   at org.eclipse.core.internal.preferences.EclipsePreferences.node(EclipsePreferences.java:662)
   at org.eclipse.core.internal.preferences.PreferencesService.getNodes(PreferencesService.java:588)
   at org.eclipse.core.internal.preferences.PreferencesService.getString(PreferencesService.java:635)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.getLineDelimiterPreference(TextFileBufferManager.java:645)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.createEmptyDocument(TextFileBufferManager.java:300)
   at org.eclipse.core.internal.filebuffers.ResourceTextFileBuffer.initializeFileBufferContent(ResourceTextFileBuffer.java:268)
   at org.eclipse.core.internal.filebuffers.ResourceFileBuffer.create(ResourceFileBuffer.java:242)
   at org.eclipse.core.internal.filebuffers.TextFileBufferManager.connect(TextFileBufferManager.java:108)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.createFileInfo(TextFileDocumentProvider.java:561)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.createFileInfo(CompilationUnitDocumentProvider.java:909)
   at org.eclipse.ui.editors.text.TextFileDocumentProvider.connect(TextFileDocumentProvider.java:482)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitDocumentProvider.connect(CompilationUnitDocumentProvider.java:1069)
   at org.eclipse.ui.texteditor.AbstractTextEditor.doSetInput(AbstractTextEditor.java:3063)
   at org.eclipse.ui.texteditor.StatusTextEditor.doSetInput(StatusTextEditor.java:173)
   at org.eclipse.ui.texteditor.AbstractDecoratedTextEditor.doSetInput(AbstractDecoratedTextEditor.java:1512)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.internalDoSetInput(JavaEditor.java:2371)
   at org.eclipse.jdt.internal.ui.javaeditor.JavaEditor.doSetInput(JavaEditor.java:2344)
   at org.eclipse.jdt.internal.ui.javaeditor.CompilationUnitEditor.doSetInput(CompilationUnitEditor.java:1428)
   at org.eclipse.ui.texteditor.AbstractTextEditor$5.run(AbstractTextEditor.java:2396)
   at org.eclipse.jface.operation.ModalContext.runInCurrentThread(ModalContext.java:369)
   at org.eclipse.jface.operation.ModalContext.run(ModalContext.java:313)
   at org.eclipse.jface.window.ApplicationWindow$1.run(ApplicationWindow.java:763)
   at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
   at org.eclipse.jface.window.ApplicationWindow.run(ApplicationWindow.java:760)
   at org.eclipse.ui.internal.WorkbenchWindow.run(WorkbenchWindow.java:2283)
   at org.eclipse.ui.texteditor.AbstractTextEditor.internalInit(AbstractTextEditor.java:2414)
   at org.eclipse.ui.texteditor.AbstractTextEditor.init(AbstractTextEditor.java:2441)
   at org.eclipse.ui.internal.EditorManager.createSite(EditorManager.java:842)
   at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:583)
   at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:372)
   at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:566)
   at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:263)
   at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1474)
   at org.eclipse.ui.internal.EditorManager$5.run(EditorManager.java:1008)
   at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:37)
   at org.eclipse.core.runtime.Platform.run(Platform.java:858)
   at org.eclipse.ui.internal.EditorManager.restoreState(EditorManager.java:1003)
   at org.eclipse.ui.internal.WorkbenchPage.restoreState(WorkbenchPage.java:2843)
   at org.eclipse.ui.internal.WorkbenchWindow.restoreState(WorkbenchWindow.java:1936)
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

```

Please help me, I really need to work on my homework

I am using Hardy Heron 64bit btw

---

### Post by superprash2003 on 2008-03-18
incase you are in a hurry.. just save your java code in a text editor as helloworld.java or whatever.. then go to the terminal

To compile you can type:  javac helloworld.java  
To run you can type:  java helloworld

---

### Post by kpkeerthi on 2008-03-18
You may remove your eclipse 'Workspace' folder and try again. If it did not help, just install eclipse from [www.eclipse.org]("http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.3.2-200802211800/eclipse-SDK-3.3.2-linux-gtk.tar.gz") and see if the problem goes away.

You just have to download, extract it to a folder and cd to it and launch ./eclipse.

---

### Post by chessercizes on 2008-03-18
you probably already checked this, but you're compiling to 5.0 / 6.0 compliant settings right?

Like if you go to Window -- Preferences

and then expand "Java", and then click on compiler. And then look at the Compiler Compliance Level.

hopefully that helps

good luck!!

---

### Post by nick937 on 2008-03-18
Thank you all for your help, I removed eclipse completely and downloaded it from the site. and it now works correctly

---

### Post by drubin on 2008-03-18
> I was using JRE 1.5, now I updated to JRE 1.6 to see if it would fix it... no luck
and when I start up Eclipse, it opens my project and gives me this:


I know you said it worked:) glad, but i noticed that you said  JRE that is java run time environment. to compile/build java applications you need JDK java development kit.

Did you have the JDK installed just by the way?

---

### Post by nick937 on 2008-03-18
Ya, I had JDK installed.. I could still compile programs ... I had been using eclipse like this for weeks because my professor alwsay gave us programs that took input from files and not the keyboard so it worked fine. The only problem I had was when I had to make a program that used the scanner class...

---

### Post by drubin on 2008-03-18
> The only problem I had was when I had to make a program that used the scanner class...

Scanner class came out in jdk1.4 though.

---

### Post by nick937 on 2008-03-18
> **rubinboy said:**
> Scanner class came out in jdk1.4 though.

hmmm, im not sure, I installed Hardy about a month or so ago.. and installed Eclipse and java through synaptic package manager.. so i dont see why I would have an old version of JDK

---

### Post by drubin on 2008-03-19
I stand to be corrected. 
[http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html) 
It was since jdk1.5. 

(Why are they given out 1.5 when 1.6 is stable?)

---

