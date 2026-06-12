---
title: "Need help with Aptana"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-11-03
I have just downloaded and installed Aptana (the Web IDE) from [www.aptana.com](www.aptana.com)

How do I start aptana, though?

---

### Post by amohanty on 2006-11-04
[http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux#Instructions_for_Ubuntu_users:](http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux#Instructions_for_Ubuntu_users:)

HTH
AM

---

### Post by aam-aadmi on 2006-11-04
I have done that extra bit too. So instalation is complete. But I am having trouble starting aptana. Do I need to include the directory ~/Aptana in my PATH variables? Typing "aptana" in the terminal gives a "command not found" response.

---

### Post by Ecthelion on 2006-11-04
I know I once had a similar problem (I think)

You can try this
```
sudo locate -u
locate aptana
```
Which will update your 'locate' and then tell you where als files called 'aptana' are.

Of course you can use any search engine.

The point is, locate 'aptana'
(it probably is it in your ~/aptana )

then just go to the folder where that file is
and do
```
./aptana
```

--Hope this helps

---

### Post by Ecthelion on 2006-11-04
> The point is, locate 'aptana'

I mean the file aptana not a dir called that...
(the file is probably in the dir)

Just to be clear

---

### Post by aam-aadmi on 2006-11-04
I located the file aptana in the following directory: ~/Aptana. Then when I go to ~/Aptana and type 
```
./aptana
```
I get the following error message:
```
An error has occurred. See the log file ~/aptana/workspace/.metadata/.log
```
I looked at that file but could not understand anything in that. Any ideas?

---

### Post by Ecthelion on 2006-11-04
> I looked at that file but could not understand anything in that. Any ideas?

Maybe post that log...

I don't think I could help but there surely are some guys on this forum who can

---

### Post by amohanty on 2006-11-04
As ecthelion suggested please post the logs. we could then help you about it.

AM

---

### Post by aam-aadmi on 2006-11-04
Here is the contents of the log file:

```
!SESSION 2006-11-04 12:08:15.227 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.4.2_09
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  #VM Runtime Configuration File
Command-line arguments:  -os linux -ws gtk -arch x86 #VM Runtime Configuration File

!ENTRY com.aptana.ide.rcp.main 1 0 2006-11-04 12:08:21.526
!MESSAGE (Build 0.2.6.11923) Bound to port 9980

!ENTRY org.eclipse.osgi 2 1 2006-11-04 12:08:28.75
!MESSAGE NLS missing message: FileExplorerView_FilesToDirectory in: com.aptana.ide.core.ui.views.fileexplorer.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-04 12:08:28.76
!MESSAGE NLS missing message: FileExplorerView_toTemporaryWorkFile in: com.aptana.ide.core.ui.views.fileexplorer.messages

!ENTRY com.aptana.ide.core.ui 1 0 2006-11-04 12:08:34.773
!MESSAGE (Build 0.2.6.11923) Connected to database aptanaDB 

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:08:38.272
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:08:38.275
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:08:38.277
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:08:38.279
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2006-11-04 12:08:38.531
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)]
	at org.eclipse.swt.SWT.error(SWT.java:2968)
	at org.eclipse.swt.browser.Browser.<init>(Browser.java:130)
	at com.aptana.ide.core.ui.views.browser.BrowserView.createPartControl(Unknown Source)
	at com.aptana.ide.core.ui.views.scriptable.GenericScriptableView.createPartControl(Unknown Source)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:305)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:180)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:552)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:283)
	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:512)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:126)
	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)
	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:391)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1102)
	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1051)
	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1256)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:576)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:528)
	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:485)
	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:230)
	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:813)
	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2201)
	at org.eclipse.ui.internal.WorkbenchWindow$5.run(WorkbenchWindow.java:2356)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:69)
	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2338)
	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:681)
	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:669)
	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1282)
	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1223)
	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:706)
	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1034)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1636)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:367)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:143)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY com.aptana.ide.core.ui 1 0 2006-11-04 12:08:38.908
!MESSAGE (Build 0.2.6.11923) Database shut down normally 
!SESSION 2006-11-04 12:09:24.307 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.4.2_09
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  #VM Runtime Configuration File
Command-line arguments:  -os linux -ws gtk -arch x86 #VM Runtime Configuration File

!ENTRY com.aptana.ide.rcp.main 1 0 2006-11-04 12:09:25.680
!MESSAGE (Build 0.2.6.11923) Bound to port 9980

!ENTRY org.eclipse.osgi 2 1 2006-11-04 12:09:28.952
!MESSAGE NLS missing message: FileExplorerView_FilesToDirectory in: com.aptana.ide.core.ui.views.fileexplorer.messages

!ENTRY org.eclipse.osgi 2 1 2006-11-04 12:09:28.953
!MESSAGE NLS missing message: FileExplorerView_toTemporaryWorkFile in: com.aptana.ide.core.ui.views.fileexplorer.messages

!ENTRY com.aptana.ide.core.ui 1 0 2006-11-04 12:09:31.382
!MESSAGE (Build 0.2.6.11923) Connected to database aptanaDB 

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:09:32.706
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:09:32.709
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:09:32.711
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.ui.workbench 4 0 2006-11-04 12:09:32.713
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:151)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:101)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1021)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1045)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1026)
	at org.eclipse.swt.widgets.Widget.releaseWidget(Widget.java:932)
	at org.eclipse.swt.widgets.Control.releaseWidget(Control.java:2395)
	at org.eclipse.swt.widgets.Scrollable.releaseWidget(Scrollable.java:313)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:948)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Widget.releaseResources(Widget.java:927)
	at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:942)
	at org.eclipse.swt.widgets.Composite.releaseWidget(Composite.java:947)
	at org.eclipse.swt.widgets.Canvas.releaseWidget(Canvas.java:132)
	at org.eclipse.swt.widgets.Decorations.releaseWidget(Decorations.java:472)
	at org.eclipse.swt.widgets.Shell.releaseWidget(Shell.java:1590)
	at org.eclipse.swt.widgets.Widget.dispose(Widget.java:403)
	at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1532)
	at org.eclipse.swt.widgets.Display.release(Display.java:2620)
	at org.eclipse.swt.graphics.Device.dispose(Device.java:212)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2006-11-04 12:09:32.793
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)]
	at org.eclipse.swt.SWT.error(SWT.java:2968)
	at org.eclipse.swt.browser.Browser.<init>(Browser.java:130)
	at com.aptana.ide.core.ui.views.browser.BrowserView.createPartControl(Unknown Source)
	at com.aptana.ide.core.ui.views.scriptable.GenericScriptableView.createPartControl(Unknown Source)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:305)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:180)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:552)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:283)
	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:512)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:126)
	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:268)
	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:391)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1102)
	at org.eclipse.ui.internal.PartStack.setSelection(PartStack.java:1051)
	at org.eclipse.ui.internal.PartStack.showPart(PartStack.java:1256)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:576)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:528)
	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:485)
	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:230)
	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:813)
	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2201)
	at org.eclipse.ui.internal.WorkbenchWindow$5.run(WorkbenchWindow.java:2356)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:69)
	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2338)
	at org.eclipse.ui.internal.WorkbenchWindow.busyOpenPage(WorkbenchWindow.java:681)
	at org.eclipse.ui.internal.Workbench.busyOpenWorkbenchWindow(Workbench.java:669)
	at org.eclipse.ui.internal.Workbench.doOpenFirstTimeWindow(Workbench.java:1282)
	at org.eclipse.ui.internal.Workbench.openFirstTimeWindow(Workbench.java:1223)
	at org.eclipse.ui.internal.WorkbenchConfigurer.openFirstTimeWindow(WorkbenchConfigurer.java:190)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:706)
	at org.eclipse.ui.internal.Workbench.init(Workbench.java:1034)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:1636)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:367)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:143)
	at com.aptana.ide.rcp.AbstractIDEApplication.run(Unknown Source)
	at com.aptana.ide.rcp.Application.run(Unknown Source)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:226)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY com.aptana.ide.core.ui 1 0 2006-11-04 12:09:32.847
!MESSAGE (Build 0.2.6.11923) Database shut down normally 

```

---

### Post by amohanty on 2006-11-04
From the log:
> [g.eclipse.swt.SWTError: No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)]/QUOTE]

Did you do this as mentioned in the aptana site:
[QUOTE]sudo apt-get install mozilla

export MOZILLA_FIVE_HOME=/usr/lib/mozilla

AM

---

### Post by aam-aadmi on 2006-11-05
Yes I had done the following

```
sudo apt-get install mozilla
export MOZILLA_FIVE_HOME=/usr/lib/mozilla
```

But this did not work. So I added the last line 
```
export MOZILLA_FIVE_HOME=/usr/lib/mozilla
``` 
to the ~/.bashrc file and now it works. I think one needs to do that to add directories to the PATH. Anyway, thanks for the help.

---

### Post by amohanty on 2006-11-05
Gald it worked for you

---

