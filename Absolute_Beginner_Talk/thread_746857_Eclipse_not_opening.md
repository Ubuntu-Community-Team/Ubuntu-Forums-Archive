---
title: "Eclipse not opening"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by xecure on 2008-04-05
eclipse was running fine for me, and then one day i tried to open it and it gave me this error message: ```
An error has occurred. See the log file
/home/zaki/Programming/.metadata/.log.
```did i screw up?

---

### Post by kbless7 on 2008-04-05
did you go to the log? you won't know until you actually do what it tells you

---

### Post by xecure on 2008-04-06
in my ~/Programming/.metadata folder there is only a vverson.ini file no log file. when i diectly enter the .log file in nautilus it tell me it couldn't display the file and underneath it tells me the location is not a folder

---

### Post by Nepherte on 2008-04-06
Press ctrl+h in nautilus to toggle on/off hidden files. Do you see it now?

---

### Post by harrybazeegar on 2008-04-06
can you tell us
1. where you installed eclipse
2. where your workspace directory is
3. what is this '.metadata' directory for? is it a config directory?

---

### Post by xecure on 2008-04-06
> **Nepherte said:**
> Press ctrl+h in nautilus to toggle on/off hidden files. Do you see it now?Yes I'm able to see the log now, but I'm not sure what it means. I have tried removing and re-adding eclipse once.

> **harrybazeegar said:**
> can you tell us
1. where you installed eclipse
2. where your workspace directory is
3. what is this '.metadata' directory for? is it a config directory?
i installed eclipse via the add/remove Application on the main menu. My workspace is ~/programming and the /.metadata folder was there by default, I believe Eclipse makes the directory by default.

---

### Post by xecure on 2008-04-06
here's the error in the .log file it helps:```
!SESSION 2008-04-06 23:12:47.044 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_03
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2008-04-06 23:12:49.233
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-04-06 23:12:49.234
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-04-06 23:12:49.234
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-04-06 23:12:49.234
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2008-04-06 23:12:49.736
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2008-04-06 23:12:49.752
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (37).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:1010)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /hw1/homeworkOne.java not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundException: Tree element /hw1/homeworkOne.java not found.
	at org.eclipse.core.internal.dtree.AbstractDataTree.handleNotFound(AbstractDataTree.java:257)
	at org.eclipse.core.internal.dtree.DeltaDataTree.getData(DeltaDataTree.java:585)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:50)
	at org.eclipse.core.internal.dtree.NoDataDeltaNode.asBackwardDelta(NoDataDeltaNode.java:59)
	at org.eclipse.core.internal.dtree.DataDeltaNode.asBackwardDelta(DataDeltaNode.java:47)
	at org.eclipse.core.internal.dtree.DeltaDataTree.asBackwardDelta(DeltaDataTree.java:88)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:816)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:815)
	at org.eclipse.core.internal.dtree.DeltaDataTree.reroot(DeltaDataTree.java:792)
	at org.eclipse.core.internal.watson.ElementTree.immutable(ElementTree.java:517)
	at org.eclipse.core.internal.resources.SaveManager.restore(SaveManager.java:644)
	at org.eclipse.core.internal.resources.SaveManager.startup(SaveManager.java:1299)
	at org.eclipse.core.internal.resources.Workspace.startup(Workspace.java:1883)
	at org.eclipse.core.internal.resources.Workspace.open(Workspace.java:1653)
	at org.eclipse.core.resources.ResourcesPlugin.startup(ResourcesPlugin.java:367)
	at org.eclipse.core.internal.compatibility.PluginActivator.start(PluginActivator.java:31)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(BundleContextImpl.java:991)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:985)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:966)
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
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-04-06 23:12:49.757
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
	at org.eclipse.ui.internal.ide.IDEApplication.run(IDEApplication.java:96)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)
```

---

### Post by spamalot on 2008-04-07
hello,

i have the same problem. any help would be appreciated.

!SESSION 2008-04-02 15:49:16.987 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.5.0_13
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

This is a continuation of log file /home/er/workspace/src/cpp/.metadata/.bak_9.log
Created Time: 2008-04-04 20:11:00.279

!ENTRY org.eclipse.cdt.core 4 4 2008-04-04 20:11:00.280
!MESSAGE Error
!STACK 0
java.lang.StackOverflowError
	at org.eclipse.cdt.internal.core.pdom.db.ShortString.compare(ShortString.java:202)
	at org.eclipse.cdt.internal.core.pdom.dom.PDOMNamedNode$NodeFinder.compare(PDOMNamedNode.java:85)
	at org.eclipse.cdt.internal.core.pdom.db.BTree.accept(BTree.java:226)
	at org.eclipse.cdt.internal.core.pdom.db.BTree.accept(BTree.java:195)
	at


also, if i launch from the terminal, here's what i have:

 eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
er@ubuntu:~$ sudo touch /usr/local/lib/eclipse/.eclipseextension
er@ubuntu:~$ sudo chmod 2775 /usr/local/lib/eclipse/.eclipseextension
er@ubuntu:~$ sudo chown root:staff /usr/local/lib/eclipse/.eclipseextension
er@ubuntu:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found

...and the same pb i.e. eclipse seems to start and then says "an error has occured, see .metadata log"

---

### Post by spamalot on 2008-04-07
ps:

no need to reply.

deleted .metadata listed above and now launches but file indexing gone...

---

### Post by harrybazeegar on 2008-04-07
hmm... i have installed eclipse by hand... maybe u should try the same :shrug:

---

### Post by xecure on 2008-04-07
same problem, any other ideas?

---

### Post by xecure on 2008-04-07
bump again
=/

---

### Post by harrybazeegar on 2008-04-08
Your logs tend to show that some files are missing ... or gone bad...
this could be because some files have misteriously gone kaboom

I dont really remember but your workspace is stored as a separate directory right?
copy all your projects from that directory to some other place and reinstall eclipse.

I still say you should try installing it by hand because it will give you a little more control ( at least it gave me )... that way you can control which java is being used by eclipse ( in case you have more than one version ).

BTW what version of java do you have? the one that comes with 
1. ubuntu?
2. eclipse?
3. a separately installed Sun JDK?

that could also (maybe) be a problem...

---

