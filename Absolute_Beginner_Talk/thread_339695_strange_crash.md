---
title: "strange crash"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-16
Hi, I have been having a lot of strange program closures recently. ie. they just close with no warning. Programs most susceptible to this have been firefox, nebeans and amarok. Can anybody make any sense of the content which I found in the terminal?

Memtest completes with no errors and PSU has just been replaced.

```
Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] Bad page state in process 'java'

Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] page:c10affa0 flags:0x80000000 mapping:00000000 mapcount:-2097152 count:0

Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] Trying to fix it up, but a reboot is needed

Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] Backtrace:

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.536000] Bad page state in process 'apport'

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.536000] page:c1147fa0 flags:0x80000004 mapping:00000000 mapcount:-2097152 count:0

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.536000] Trying to fix it up, but a reboot is needed

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.536000] Backtrace:

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.584000] Bad page state in process 'apport'

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.584000] page:c1417fa0 flags:0x80000004 mapping:00000000 mapcount:-2097152 count:0

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.584000] Trying to fix it up, but a reboot is needed

Message from syslogd@tom-desktop at Tue Jan 16 10:59:29 2007 ...
tom-desktop kernel: [17185847.584000] Backtrace:

Message from syslogd@tom-desktop at Tue Jan 16 10:59:34 2007 ...
tom-desktop kernel: [17185852.364000] Bad page state in process 'apport-gtk'

Message from syslogd@tom-desktop at Tue Jan 16 10:59:34 2007 ...
tom-desktop kernel: [17185852.364000] page:c1297fa0 flags:0x80000000 mapping:00000000 mapcount:-2097152 count:0

Message from syslogd@tom-desktop at Tue Jan 16 10:59:34 2007 ...
tom-desktop kernel: [17185852.364000] Trying to fix it up, but a reboot is needed

Message from syslogd@tom-desktop at Tue Jan 16 10:59:34 2007 ...
tom-desktop kernel: [17185852.364000] Backtrace:
```

---

### Post by kidders on 2007-01-16
Hi there,

These errors are fairly serious I'm afraid :-( ...

> **tommy1987 said:**
> ```
Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] Bad page state in process 'java'
```This one is memory-related. A "page" is a chunk of memory that's being swapped between actual RAM and virtual RAM. It's tempting to wonder whether your RAM or swap partition(s) have physical errors in them.

> **tommy1987 said:**
> ```
Message from syslogd@tom-desktop at Tue Jan 16 10:28:58 2007 ...
tom-desktop kernel: [17184016.012000] Trying to fix it up, but a reboot is needed
```Afaik this is part of a kernel oops. Basically, the software driving the operating system itself encounters a set of circumstances it can't make any sense of, and tries to patch up the mess. This message is to let you know it can't be sure it was successful. Continuing to use your computer without rebooting can lead to very odd behaviour.

If your computer is working properly, these are errors that you should never see. They can happen...

[LIST]
[*]If your RAM is damaged.
[*]If your CPU is making mistakes, eg because it's overheating.
[*]Perhaps if you're using a kernel not designed for your processor architecture?
[/LIST]

The apps you mentioned will tend to do an awful lot of paging, so perhaps that's the cause of your problem. If it were me, I would:

[LIST=1]
[*]Check my RAM and swap partitions for errors.
[*]Try to deliberately cause these errors a few times, to see if I can spot a pattern.
[*]Then, try to *avoid* causing them, maybe by scaling down my CPU speed, removing bad RAM, disabling swap space, installing a different kernel ... whatever you think might help.
[/LIST]

Once you pin down the cause of the problem, fixing it should be easy. :-)

---

### Post by tommy1987 on 2007-01-16
Thats very helpful, Thanks a lot.

Two questions, how sure should I be that memory is not the problem since memtest gives me no errors? Would reformatting my swap partition eliminate an option?

---

### Post by kidders on 2007-01-16
> **tommy1987 said:**
> How sure should I be that memory is not the problem since memtest gives me no errors? Would reformatting my swap partition eliminate an option?Yeah, I just noticed that sentence in your o/p. In a way, your successful memtest is a little discouraging!!

Faulty swap is less likely to be the problem, but you can check by scanning the surface of the partition, which is not quite the same thing as re-formatting it. You could also try deactivating all your swap, and seeing if you can still deliberately provoke the paging errors.

One thing I'm curious about is how hard your PC is working around the time it craps out on you. If CPU usage is high for a sustained period around the appearance of the error messages, it might be worth thinking about heat-related problems.

Sorry I'm being so vague about your problem ... it's a tough one to deal with. :-(

Although my instinct is to gravitate towards hardware-related faults, it is still possible that your kernel is the problem. What motherboard/CPU do you have? What's the output of "uname -a"? (Perhaps there is a known issue that you can avoid by upgrading/downgrading your kernel.)

**Edit:** Afaik, you can take memtest's verdict as gospel.

**Edit:** Have you added any new hardware lately, other than your PSU? Maybe a PCI card, PCMCIA card, etc.?

---

### Post by tommy1987 on 2007-01-17
How do I disable swap? I think that will be worth a go.

The CPU is not working hard at all when crashes have occured before. E.g It has just happened with Opera and the only other thing working is Democracy Player.

Heat I am pretty sure is not the problem, the case is well ventilated and has extra fans, nothing is overclocked.

I have an Athlon 2200xp and Asus A7N8X Deluxe 2 Motherboard.

Output of uname -a

Linux tom-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

There was the addition of a wireless card (netgear). Could that be the problem?

---

### Post by kidders on 2007-01-17
Hi there,

If you think disabling swap is worth a shot, you can use the **swapoff** command to dismount a swap partition. Be a little wary though ... without any virtual memory, your PC may do some odd things (like inexplicably kill processes) when it runs out of RAM, in a desperate effort to acquire some!

> **tommy1987 said:**
> I have an Athlon 2200xp and Asus A7N8X Deluxe 2 Motherboard.

Output of uname -a

Linux tom-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/LinuxI'm no kernel expert, but I'll try to establish whether there's any possibility you've fallen victim to a bug of some sort. Thanks.

> **tommy1987 said:**
> There was the addition of a wireless card (netgear). Could that be the problem?You would *think* you should be able to add hardware without having to worry about upsetting your kernel! All the same, any recent changes would make me suspicious. :-|

---

### Post by tommy1987 on 2007-01-17
I have some more information which may be of use to  the diagnosis of this problem.

I was using the system, there were several apps running and suddenly the whole system crashed, the mouse still moved around but clicking didnt work. I tried the three finger salute and even that didnt work, I had to reset it with the button!

Also, when restarting the system, I get a audible message saying system failed memory test. Memtest does complete with no errors though. Then the following message was proudly displayed:

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built in shell (ash)

/bin/sh: can't access tty: job control turned off
(initramfs)

Am currently reverting to windows until I determine the problem, If I find similar problems in Windows then I know there is something wrong with my hardware which I suspect anyway.
EDIT: Windows is producing some strange problems also (EG When downloading firefox setup and trying to run it, it tells me it is corrupt before even extracting it! .. Very Strange?)

I know I will have to reinstall Ubuntu but its getting to be a major headache now! I have had this problem before of the crash and then this message forcing me to reinstall it.

Thanks for all the help, more is greatly appreciated!

Tom

---

### Post by kidders on 2007-01-17
I haven't been able to find anything that might suggest you're falling victim to some sort of known bug in the Linux kernel. :-(

> Also, when restarting the system, I get a audible message saying system failed memory test.Odd! I wonder if false positives from memtest are common. :-k (Makes you wonder!)

In any case, a process of elimination should tell you which chips (or slots) are faulty.

---

### Post by tommy1987 on 2007-01-17
I will give this a go. Last time this happened, I went through exactly the same thing. Ran memtest but there were loads of errors and I found the offending slot of RAM (Produced loads of errors). Then I had no errors, so I thought it was sorted, obviously not :mad:

Anyway, I'll post the outcome

---

### Post by tommy1987 on 2007-01-17
just tried to install netbeans in windows and I enclose the log of why the install failed, it may wield some information about what is faulty...

```

(17-Jan-2007 13:43:31), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, sysDir: C:\
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Total (not necessarily on one disk when tempdir is redirected) Mbytes = 534
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, RequiredBytesTable: RequiredBytesTable: {C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp	50000000
C:\Program Files\Java\jre1.6.0	80000000
C:\Program Files\Java\jdk1.6.0	250000000
C:\	55000000
C:\Program Files\Common Files	125000000}
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.UnpackJarsAction, dbg, getRequiredBytes nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.StorageBuilderAction, dbg, getRequiredBytes nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.StorageBuilderAction, dbg, getRequiredBytes tempPath: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.StorageBuilderAction, dbg, Total (not necessarily on one disk when tempdir is redirected) Mbytes = 30
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.StorageBuilderAction, dbg, RequiredBytesTable: RequiredBytesTable: {C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp	16000000
C:\Program Files\netbeans-5.5	16000000}
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter ENTER
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter PRE_INSTALL PANEL
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, Size of NetBeans: 86
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, Adjusted size of J2SE: 336
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, summaryPreInstallMsg:'$L(org.netbeans.installer.Bundle,Product.displayName) $L(org.netbeans.installer.Bundle,PreviewPanel.previewInstallMessage)<br>C:\Program Files\netbeans-5.5<br><br>$L(org.netbeans.installer.Bundle,JDK.shortName) $L(org.netbeans.installer.Bundle,PreviewPanel.previewInstallMessage)<br>C:\Program Files\Java\jdk1.6.0<br><br>$L(org.netbeans.installer.Bundle,PreviewPanel.previewSize)<br>422 MB'
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, Size of NetBeans: 86
(17-Jan-2007 13:43:31), Install, org.netbeans.installer.NbSummaryPanel, dbg, Adjusted size of J2SE: 336
(17-Jan-2007 13:43:32), Install, com.installshield.product.actions.UninstallerJVMResolution, dbg.jvm, searching for a JVM
(17-Jan-2007 13:43:32), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, executing launcher to resolve JVM
(17-Jan-2007 13:43:32), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, waiting to read output from the launcher
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, got output from launcher. First line = 1
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, found matching JVM
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, matching JVM HOME is C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\LREA5.tmp
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32JVMServiceImpl, dbg.jvm, matching JVM file is C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\LREA9.tmp
(17-Jan-2007 13:43:33), Install, com.installshield.product.actions.UninstallerJVMResolution, dbg.jvm, resolved to JVM file: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\LREA9.tmp with JVM_HOME = C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\LREA5.tmp
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Files (files): free=58240632 total=66715648
(17-Jan-2007 13:43:33), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Files (files)
(17-Jan-2007 13:43:41), Install, com.installshield.product.actions.Files, err, java.util.zip.ZipException: incorrect data check
STACK_TRACE: 17
java.util.zip.ZipException: incorrect data check
	at com.installshield.boot.streamhandler.ISInflaterInputStream.read(Unknown Source)
	at java.io.FilterInputStream.read(Unknown Source)
	at com.installshield.product.actions.Files.copy(Unknown Source)
	at com.installshield.product.actions.Files.copyFileWithFileService(Unknown Source)
	at com.installshield.product.actions.Files.copyFilesPayload(Unknown Source)
	at com.installshield.product.actions.Files.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)

(17-Jan-2007 13:43:41), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Files (files): free=57831016 total=66715648
(17-Jan-2007 13:43:41), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Post Install Fixup Action (fixup): free=57699960 total=66715648
(17-Jan-2007 13:43:41), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Post Install Fixup Action (fixup)
(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, dbg, install, support is com.installshield.product.ProductActionSupport@964130 ...
(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, dbg, nbInstallDir is C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, dbg, jdkHome = C:\Program Files\Java\jdk1.6.0
(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, dbg, create file: C:\Program Files\netbeans-5.5\nb5.5\config\productid content: 'NBJDK'
(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, err, java.io.FileNotFoundException: C:\Program Files\netbeans-5.5\nb5.5\config\productid (The system cannot find the path specified)
STACK_TRACE: 25
java.io.FileNotFoundException: C:\Program Files\netbeans-5.5\nb5.5\config\productid (The system cannot find the path specified)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at java.io.FileWriter.<init>(Unknown Source)
	at com.installshield.wizard.service.file.PureJavaFileServiceImpl.writeAsciiFile(Unknown Source)
	at com.installshield.wizard.service.file.PureJavaFileServiceImpl.createAsciiFile(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.wizard.service.file.GenericFileService.createAsciiFile(Unknown Source)
	at org.netbeans.installer.PostInstallFixupAction.install(PostInstallFixupAction.java:118)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)

(17-Jan-2007 13:43:41), Install, org.netbeans.installer.PostInstallFixupAction, dbg, create file: C:\Program Files\netbeans-5.5\nb5.5\var\license_accepted
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, patching C:\Program Files\netbeans-5.5\etc\netbeans.conf
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, err, java.io.FileNotFoundException: C:\Program Files\netbeans-5.5\etc\netbeans.conf (The system cannot find the path specified)
STACK_TRACE: 25
java.io.FileNotFoundException: C:\Program Files\netbeans-5.5\etc\netbeans.conf (The system cannot find the path specified)
	at java.io.FileInputStream.open(Native Method)
	at java.io.FileInputStream.<init>(Unknown Source)
	at java.io.FileInputStream.<init>(Unknown Source)
	at java.io.FileReader.<init>(Unknown Source)
	at com.installshield.wizard.service.file.PureJavaFileServiceImpl.readAsciiFile(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at com.installshield.wizard.service.LocalImplementorProxy.invoke(Unknown Source)
	at com.installshield.wizard.service.AbstractService.invokeImpl(Unknown Source)
	at com.installshield.wizard.service.file.GenericFileService.readAsciiFile(Unknown Source)
	at org.netbeans.installer.PostInstallFixupAction.addJDKHomeToIDEConfigFile(PostInstallFixupAction.java:265)
	at org.netbeans.installer.PostInstallFixupAction.install(PostInstallFixupAction.java:139)
	at com.installshield.product.service.product.PureJavaProductServiceImpl.installProductAction(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.getResultForProductAction(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitComponent(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitInstallableComponents(Unknown Source)
	at com.installshield.product.service.product.InstallableObjectVisitor.visitProductBeans(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$InstallProduct.install(Unknown Source)
	at com.installshield.product.service.product.PureJavaProductServiceImpl$Installer.execute(Unknown Source)
	at com.installshield.wizard.service.AsynchronousOperation.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)

(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, deleting C:\Program Files\netbeans-5.5\bin\netbeans.cmd
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, cannot find C:\Program Files\netbeans-5.5\bin\runideopenvms.com
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, cannot find C:\Program Files\netbeans-5.5\bin\macosx_launcher.dmg
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, cannot find C:\Program Files\netbeans-5.5\bin\runideos2.cmd
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, deleting C:\Program Files\netbeans-5.5\bin\netbeans
(17-Jan-2007 13:43:42), Install, org.netbeans.installer.PostInstallFixupAction, dbg, cannot find C:\Program Files\netbeans-5.5\_uninst\nb-uninstall.template
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Post Install Fixup Action (fixup): free=57167328 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Desktop Icon (desktopicon): free=56970960 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Desktop Icon (desktopicon)
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Desktop Icon (desktopicon): free=56516512 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Desktop Icon (programsmenu): free=56320128 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Desktop Icon (programsmenu)
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Desktop Icon (programsmenu): free=55992832 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Files (bean117): free=55927376 total=66715648
(17-Jan-2007 13:43:42), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Files (bean117)
(17-Jan-2007 13:43:46), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Files (bean117): free=58440344 total=66715648
(17-Jan-2007 13:43:46), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Install J2sdk Action (bean3): free=58304520 total=66715648
(17-Jan-2007 13:43:46), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Install J2sdk Action (bean3)
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, $D(common): C:\Program Files\Common Files
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, $D(install): C:\Program Files
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, jreInstallDir: C:\Program Files\Java\jre1.6.0
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Tempdir: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, createInstallScriptJDKWindows ENTER
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, findJDKWindowsInstaller installDirFile: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, findJDKWindowsInstaller JDK installer found: jdk-6-fcs-bin-b105-windows-i586-29_nov_2006.exe
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, # # # # # # # #
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Start Invoking JDK installer: cmdArray -> [C:\Program Files\netbeans-5.5\_uninst\custom-install-jdk.bat]
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, doProgress -> true
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, cmdArray -> [C:\Program Files\netbeans-5.5\_uninst\custom-install-jdk.bat]
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:46), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:47), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:47), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:48), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:48), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:49), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:49), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:50), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:50), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:52), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:52), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:53), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:53), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:54), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 0 perc = 0
(17-Jan-2007 13:43:54), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0  MODIFIED!!!
(17-Jan-2007 13:43:55), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0 NOT created yet
(17-Jan-2007 13:43:57), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0 NOT created yet
(17-Jan-2007 13:43:59), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 2539 perc = 0
(17-Jan-2007 13:43:59), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\COPYRIGHT  MODIFIED!!!
(17-Jan-2007 13:44:00), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 932331 perc = 0
(17-Jan-2007 13:44:00), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\bin\msvcr71.dll  MODIFIED!!!
(17-Jan-2007 13:44:02), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 8447324 perc = 2
(17-Jan-2007 13:44:02), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\db\lib\derby.jar  MODIFIED!!!
(17-Jan-2007 13:44:03), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 31467783 perc = 9
(17-Jan-2007 13:44:03), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\jre\lib\sdk.jsse.pack  MODIFIED!!!
(17-Jan-2007 13:44:05), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 69942235 perc = 21
(17-Jan-2007 13:44:05), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.pack  MODIFIED!!!
(17-Jan-2007 13:44:06), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 71427674 perc = 22
(17-Jan-2007 13:44:06), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\jre\lib\deploy\splash.jpg  MODIFIED!!!
(17-Jan-2007 13:44:07), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 81459935 perc = 25
(17-Jan-2007 13:44:07), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\jre\lib\ext\localedata.pack  MODIFIED!!!
(17-Jan-2007 13:44:09), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 84700354 perc = 26
(17-Jan-2007 13:44:09), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\jre\lib\charsets.jar  MODIFIED!!!
(17-Jan-2007 13:44:10), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 96955899 perc = 30
(17-Jan-2007 13:44:11), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.jar  MODIFIED!!!
(17-Jan-2007 13:44:12), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 99609653 perc = 31
(17-Jan-2007 13:44:12), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.jar  MODIFIED!!!
(17-Jan-2007 13:44:14), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 109227061 perc = 34
(17-Jan-2007 13:44:14), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.jar  MODIFIED!!!
(17-Jan-2007 13:44:16), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 128261173 perc = 40
(17-Jan-2007 13:44:16), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.jar  MODIFIED!!!
(17-Jan-2007 13:44:17), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 130978702 perc = 40
(17-Jan-2007 13:44:17), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\lib\tools.jar  MODIFIED!!!
(17-Jan-2007 13:44:18), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 136640406 perc = 42
(17-Jan-2007 13:44:19), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\demo\jfc\SwingSet2\src\TreeDemo.java  MODIFIED!!!
(17-Jan-2007 13:44:20), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 136932534 perc = 42
(17-Jan-2007 13:44:20), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\demo\jvmti\agent_util\src  MODIFIED!!!
(17-Jan-2007 13:44:22), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 140549895 perc = 43
(17-Jan-2007 13:44:22), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\demo\plugin\jfc\SwingSet2\src\OptionPaneDemo.java  MODIFIED!!!
(17-Jan-2007 13:44:24), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 145212458 perc = 45
(17-Jan-2007 13:44:24), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\jnlp\raf\src\randomFile.java  MODIFIED!!!
(17-Jan-2007 13:44:25), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 151352344 perc = 47
(17-Jan-2007 13:44:25), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:26), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 153511884 perc = 47
(17-Jan-2007 13:44:26), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:28), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 172760462 perc = 53
(17-Jan-2007 13:44:30), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\src.zip  MODIFIED!!!
(17-Jan-2007 13:44:31), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 156920450 perc = 49
(17-Jan-2007 13:44:31), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:33), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 156920450 perc = 49
(17-Jan-2007 13:44:33), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:34), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 162530210 perc = 50
(17-Jan-2007 13:44:34), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, 
------------------------------  Command Print  -----------------------
Command: 
C:\Program Files\netbeans-5.5\_uninst\custom-install-jdk.bat
Command Output:

Command Error:

Return Status: 0
------------------------------------------------------------------------

(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Return status: 0
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, in progress stop
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, interrupting ProgressThread 
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, ProgressThread interrupted
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, Finishing
(17-Jan-2007 13:44:35), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, active Threads -> 10
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, createInstallScriptJREWindows ENTER
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, findJREWindowsInstaller JRE installer found: C:\Program Files\Common Files\Java\Update\Base Images\jdk1.6.0.b105\patch-jdk1.6.0.b105\jre.msi
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:@echo off
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET DRIVE=C:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET LOGFILE="C:\Program Files\netbeans-5.5\_uninst\install-jre.log"
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET JRE_INSTALLER_LOCATION="C:\Program Files\Common Files\Java\Update\Base Images\jdk1.6.0.b105\patch-jdk1.6.0.b105"
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET JRE_MSI_PROJECT=jre.msi
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET TMP=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:SET TEMP=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:%DRIVE%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:cd %JRE_INSTALLER_LOCATION%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:echo Installing JRE... > %LOGFILE%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:if not exist %JRE_MSI_PROJECT% goto nosetup
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:start /w msiexec.exe /qn /i %JRE_MSI_PROJECT% IEXPLORER=1 MOZILLA=1
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:set EXITCODE=%ERRORLEVEL%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:echo Finished Installing JRE... >> %LOGFILE%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:goto end
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line::nosetup
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:	echo ERROR: jre installer not found >> %LOGFILE%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:	exit 1
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line::end
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, JRE line:	exit %EXITCODE%
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, # # # # # # # #
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Start Invoking JRE installer: cmdArray -> [C:\Program Files\netbeans-5.5\_uninst\custom-install-jre.bat]
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, doProgress -> true
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, cmdArray -> [C:\Program Files\netbeans-5.5\_uninst\custom-install-jre.bat]
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 170093186 perc = 53
(17-Jan-2007 13:44:36), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:38), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 170093186 perc = 53
(17-Jan-2007 13:44:38), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:39), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, installed size = 170093186 perc = 53
(17-Jan-2007 13:44:39), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, StatusDetailThread-> C:\Program Files\Java\jdk1.6.0\sample\webservices\EbayServer\index.html  MODIFIED!!!
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, 
------------------------------  Command Print  -----------------------
Command: 
C:\Program Files\netbeans-5.5\_uninst\custom-install-jre.bat
Command Output:

Command Error:

Return Status: 1603
------------------------------------------------------------------------

(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Return status: 1603
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, in progress stop
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, interrupting ProgressThread 
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, ProgressThread interrupted
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction$ProgressThread, dbg, Finishing
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, active Threads -> 10
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, Error occured while installing [1603] -> C:\Program Files\netbeans-5.5\_uninst\custom-install-jre.bat
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, err, Error occured while installing [1603] -> C:\Program Files\netbeans-5.5\_uninst\custom-install-jre.bat
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.InstallJ2sdkAction, dbg, J2SE installation took: (ms) 54531
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Install J2sdk Action (bean3): free=55935384 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Unpack Jars Action (unpackJarsAction): free=55776512 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Unpack Jars Action (unpackJarsAction)
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.UnpackJarsAction, dbg, nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.UnpackJarsAction, dbg, uninstDir: C:\Program Files\netbeans-5.5\_uninst
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.UnpackJarsAction, err, # # # # # # # #
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.UnpackJarsAction, err, Fatal error: Cannot find jar catalog file: C:\Program Files\netbeans-5.5\_uninst\packedjars.xml
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Unpack Jars Action (unpackJarsAction): free=55638768 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Files (bean51): free=55563512 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Files (bean51)
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Files (bean51): free=55355568 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory before installing Storage Builder Action (storageBuilderAction): free=55242552 total=66715648
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, msg1, installing Storage Builder Action (storageBuilderAction)
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, uninstDir: C:\Program Files\netbeans-5.5\_uninst
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, jdkHome: C:\Program Files\Java\jdk1.6.0
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, TempPath: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, Created temporary dir for SB: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\mdrtmpdir
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, err, # # # # # # # #
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, err, Fatal error: Cannot create destination directory for Storage Builder.
(17-Jan-2007 13:44:40), Install, org.netbeans.installer.StorageBuilderAction, dbg, Deleted temporary dir for SB: C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\mdrtmpdir
(17-Jan-2007 13:44:40), Install, com.installshield.wizard.platform.win32.Win32ProductServiceImpl, dbg.install, JVM memory after installing Storage Builder Action (storageBuilderAction): free=55029800 total=66715648
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, uid: 274c5407c4fa26908310cb5c1c550000
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, Key -> Software\Microsoft\Windows\CurrentVersion\Uninstall
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, First match with UID keyNames[0]: 274c5407c4fa26908310cb5c1c5500001954585185 UninstallString: C:\Program Files\netbeans-5.5\_uninst\uninstaller.exe
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, strippedValue: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, Second match with UninstallString. Modify/Add Keys.
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, Adding value -> Software\Microsoft\Windows\CurrentVersion\Uninstall\C:\Program Files\netbeans-5.5\bin\netbeans.exe
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.PostInstallWizardAction, dbg, Adding value -> Software\Microsoft\Windows\CurrentVersion\Uninstall\C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter ENTER
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter nbInstallDir: C:\Program Files\netbeans-5.5
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter POST_INSTALL PANEL
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter exitCode: -200
(17-Jan-2007 13:44:43), Install, org.netbeans.installer.NbSummaryPanel, dbg, queryEnter INSTALLATION FAILED

```

This is exactly the same thing as happened when I tried to install it in ubuntu, I only managed to install it successfully through trying several times until it worked. I am sure it would be the same in Windows but I want to use Ubuntu!

Tom

---

### Post by hoges on 2007-01-17
I was just thinking that maybe you bumped something when you installed the wireless card. Is it internal? I gather from your posts that you tracked down the offending ram stick.

Could it be possible that you bumped a hdd cable out of place, or that the hdd itself is damaged? Would explain the inability to find files. Maybe run a scandisk in windows if you can.

Overheating motherboard? Blocked fan?

To be honest, i have very little idea what's wrong, I'm just throwing out hardware suggestions in the hope that it'll help

cheers
hoges

---

### Post by tommy1987 on 2007-01-17
Have just performed a series of memtests, and the results are somewhat strange.

I have three slots on my motherboard, each memory module in its slot by itself produces around 20-30 errors! This would seem to indicate that all three modules are faulty.

They are manufactured by Crucial so this is highly unlikely. Am I right in thinking this is more likely to be a motherboard problem? 

Im at my wits end and am tempted to go and buy a mobo+cpu combo and have done with it. Can my RAM (if it is faulty) in any way damage my new gear (should I buy it?).

Thanks, Tom

---

### Post by tommy1987 on 2007-01-17
I have found a new CPU AMD Sempron 4000+ 64bit and Motherboard, Do you think it would be worth my while to purchase these and try the RAM in the new motherboard. Surely three modules of crucial RAM cant all fail at once?

Perhaps, most importantly, is it possible for RAM if it is faulty to damage a motherboard?

---

### Post by kidders on 2007-01-18
Sorry... I fell behind on this thread a little! :-(

I would be very nervous about recommending something that will cost you money. :-? I suppose there seem to be three potential problems here:

[LIST=1]
[*]*All* your RAM could be faulty, which would really only be possible if your PSU is broken or inappropriate, I think.
[*]Your RAM slots could be dusty or damaged. I once encountered RAM-related trouble after I removed and re-inserted the RAM on an old PC. It turned out that all the dust lying around inside the box got into the memory slots when I removed the chips ... a couple of lungfulls of air solved the problem.
[*]Your motherboard may be dying. Again, it's hard to see how this could have happened unless your PSU is at fault.
[/LIST]

It would be ideal if you could try your RAM in another box. If it worked, I would think about replacing the PSU and motherboard ... just to be safe. Hopefully someone will post a less radical response before you spend too much money, but tbh, I feel doubtful. :-|

**Edit:** Oops... I forgot to mention that your o/p says you replaced your PSU recently. Does that fit the timeline? Just to be safe, I suppose I should check that you know how do discharge static from your body before messing around inside your box, and that you can tell a suitable PSU from an unsuitable one. Most people know all that already, but I just want to be sure!

**Edit:** This thread is really nasty. :-( My heart sinks whenever I see one of these, that can't just be solved with a command or two on a console.

---

### Post by psycosmyth on 2007-01-18
ok, this will take a tangent but I had simular issues when I first installed Edgy. I could not get the same apps you mentioned to stay up, they just close without warning. I reinstalled and no love again. I then installed Xubuntu and got amarok to behave but Firefox freeked. I had some of the same errors too. I gave up and began to kill all mozilla libs and installed opera and all the media codecs in terminal. I have no clue as to what happened other than several paths for some libs got broken. My RAM was good but overwhelmed. I have no firefox but I have no Gnome either. KDE/XFCE apps are easier on my little processor anyway.

---

### Post by tommy1987 on 2007-01-18
Some new information can be observed here: 
[http://www.freeimagehosting.net/image.php?0640cbad65.jpg](http://www.freeimagehosting.net/image.php?0640cbad65.jpg)

They are the results of my extensive afternoon of memory testing today ;-)
Basically, the total number of errors appears first followed by the test number and in brackets the number of errors if >=1.

I can establish from this that 

1. Each memory displays inconsistent results even in another slot
2. There is definitely something not right somewhere

Can my CPU FSB affect anything because I am currently running my AMD 2200+ at 100Mhz FSB, is this right?

My thoughts having done this test are to go out and buy a new motherboard CPU combo and then hope the memory isnt faulty. From talking to a friend with experience with working with hardware he says failure of crucial RAM is extremely rare and would think it near impossible for 3 to die at once.

Help is massively appreciated before I bite the bullet and buy the new gear!

Tom

---

### Post by ciscosurfer on 2007-01-18
> **tommy1987 said:**
> Some new information can be observed here: 
[http://www.freeimagehosting.net/image.php?0640cbad65.jpg](http://www.freeimagehosting.net/image.php?0640cbad65.jpg)

They are the results of my extensive afternoon of memory testing today ;-)
Basically, the total number of errors appears first followed by the test number and in brackets the number of errors if >=1.

I can establish from this that 

1. Each memory displays inconsistent results even in another slot
2. There is definitely something not right somewhere

Can my CPU FSB affect anything because I am currently running my AMD 2200+ at 100Mhz FSB, is this right?

My thoughts having done this test are to go out and buy a new motherboard CPU combo and then hope the memory isnt faulty. From talking to a friend with experience with working with hardware he says failure of crucial RAM is extremely rare and would think it near impossible for 3 to die at once.

Help is massively appreciated before I bite the bullet and buy the new gear!

TomMay I ask what you PSU is rated at?  Are you sure it's pumping out enough wattage to handle all of your components?

I would also suggest the following:[LIST=1]
[*]Open your case up (take static discharge precautions of course) and make sure all components are lined up where they need to be, no loose cables, reseat your RAM (and clean the RAM slots before reseating the RAM).
[*]While you have you case open, check for faulty capacitors, blown capacitors (they will look like they have bulged towards the top, or may be completely busted altogether).
[*]If you think the problem may be associated to the addition of your wireless card (I don't think it is, but it doesn't hurt to check), then remove the card and then try to reproduce the errors you were having before.  Do they still appear?
[*]Try using the bootable floppy version of Memtest86, which can be found here: [http://www.memtest86.com/](http://www.memtest86.com/) or try the regular version as well: [http://www.memtest.org/](http://www.memtest.org/) you might also try DocMemory here: [http://www.simmtester.com/page/products/doc/docinfo.asp](http://www.simmtester.com/page/products/doc/docinfo.asp) or GoldMemory here: [http://www.goldmemory.cz/screen.php](http://www.goldmemory.cz/screen.php)
[*]Download and use (in Windows) the Windows Memory Diagnostic tool: [http://oca.microsoft.com/en/windiag.asp](http://oca.microsoft.com/en/windiag.asp)
[*]In Windows, look in your Device Manager for any inconsistencies, errors, driver malfunctions, etc.
[*]Again, make sure your new PSU can handle your computer's components...if it is underrated in regards to your computer's specs, you're bound to get multiple errors, over and over and over, ad nauseum.  And, it will prevent you from fully utilizing and using your computer.  In addition, an underrated (read: low wattage output) PSU can cause permanent damage to your system's components, this includes but certainly is not limited to your RAM (read: motherboard).
[*]If everything checks out above, then give your box a quick hug, reboot 'er, and see if she gives you any love![/LIST]

---

### Post by tommy1987 on 2007-01-18
I will try what has been suggested and thank you for your help.

PSU is unlikely to be the problem since, was using a 350W PSU before fine and the new PSU is 550W. They are both quality branded ones.

---

### Post by tommy1987 on 2007-01-18
Other memory tests still produce multiple errors, I am thinking the motherboard is at fault here more and more. I have had it for three years but can't see why one day it would just decide to die on me. Let alone all 3 RAM slots!

---

### Post by tommy1987 on 2007-01-19
Have tried memory in the board from another computer which works fine and this still gives me the errors although not as many, How do you interpret that? When I booted into Windows using this new RAM I tried to download firefox again and it still said it was corrupted! Hence the problems were reoccurring.

---

### Post by ciscosurfer on 2007-01-19
> **tommy1987 said:**
> Have tried memory in the board from another computer which works fine and this still gives me the errors although not as many, How do you interpret that? When I booted into Windows using this new RAM I tried to download firefox again and it still said it was corrupted! Hence the problems were reoccurring.Sounds to me like your motherboard has had it.  Incidentally, when you boot up, do you hear a whining or a hissing noise coming from the case?

---

### Post by tommy1987 on 2007-01-20
I hear no hissing noise or anything but te BIOS has gone all funny now, when I go into it on bootup it wont let me do anything even move to another option?!

I hope that is the case to be honest. Have ordered new components now including new motherboard and processor. I really hope it all works when I put it all together. 

Will let you guys know, thanks for all the help, hopefully that is the end of it.

---

### Post by tommy1987 on 2007-01-26
New motherboard and CPU arrived today, set it all up and everything appears fine!
Just letting you guys know the outcome.

Thanks for all the help and support!

---

### Post by kidders on 2007-01-26
I hope everything goes well for you! Post back if you run into any trouble.

---

