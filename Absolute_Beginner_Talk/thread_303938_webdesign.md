---
title: "webdesign"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by pocahontas on 2006-11-21
I loaded Aptana_setup.bin to my desktop. Ho do I use it? If I click 'open' then gedit opens with:
'can't open:is a binary file'

---

### Post by 3rdalbum on 2006-11-21
Is the file executable? To check, right-click it. Go to the Properties item, then look in the Permissions tab. Make sure all three Execute checkboxes are checked.

Then close the Properties box and double-click on the program. You will probably get a choice of what to do with the file - select Run, and if that doesn't work try Run In Terminal. If you have any more problems, please post the output from the terminal.

---

### Post by pocahontas on 2006-11-22
Yes, thanks. It seemed to be a permission error, but...Now it is installed and when I try to open it in /home/john/aptana with ./aptana an error shows saying that an error has occured and to look in de /aptana/workspace/.metafiles/.log for details. So I did and here is what's in the log:


!ENTRY org.eclipse.osgi 2006-11-22 18:02:35.298
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

!ENTRY com.aptana.ide.core.ui 1 0 2006-11-22 18:02:35.376
!MESSAGE (Build 0.2.6.11923) Database shut down normally 

I have not the slightest idea what this means, so please help me.

---

### Post by Dusibello on 2006-11-22
can't help with your original question, but if helpful someday, have you looked at nvu? pretty slick stuff for html editing....

---

### Post by pocahontas on 2006-11-24
OK I deleted aptana and loaded nvu. But,...HTML is not a problem but when I  insert some php code things went wrong.
I did tried to run it locally 
I typed in the seach field of the browser (Firefox):
  
    htpp://localhost/php/hello.php  //name of the testfile

The browser shows :
Not Found. Port 80

Maybe this can help: if i type in the terminal: php -v nothing shows up.
I'm an absolute newby in linux.Under windows I never had problems with Dreamweaver. It's frustrating!!!

---

