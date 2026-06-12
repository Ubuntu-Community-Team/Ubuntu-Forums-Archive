---
title: "AmaroK crashes"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by mm405416 on 2007-12-12
Hey all, this has been happening for a few days now. I'm running Gutsy: I'll try and start up amarok, I'll get the splash, and the icon will appear in notifications on my bar, however whenever I click on that icon, it disappears and kmail pops up to send a crash report. The only things I've done in recent memory are remove DVDShrink and replace it with K9DVD remove DeeVeeDee and replace it with ManDVD, install some language tutoring programs, (Landrill, Kanatest), switchout gnomescreensaver for xscreensaver, and install emerald. 

the crash report is as follows


Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. Information describing the crash is below, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.


The information below is to help the developers identify the problem, please do not modify it.



```
======== DEBUG INFORMATION  =======
Version:    1.4.7
Engine:     xine-engine
Build date: Sep  3 2007
CC version: 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)
KDElibs:    3.5.7
Qt:         3.3.7
TagLib:     1.4.0
CPU count:  1
NDEBUG:     true
==== file `which amarokapp` =======
/usr/bin/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1262151968 (LWP 10860)]
[New Thread -1311282288 (LWP 10881)]
[New Thread -1302889584 (LWP 10880)]
[New Thread -1266566256 (LWP 10879)]
[New Thread -1274958960 (LWP 10878)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c1414b in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d451 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb7b85b0b in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
#5  0xb7b869ed in CollectionView::renderView () from /usr/lib/libamarok.so.0
#6  0xb7b9893c in CollectionView::qt_invoke () from /usr/lib/libamarok.so.0
#7  0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb62751aa in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb7b73110 in BrowserBar::browserActivated () from /usr/lib/libamarok.so.0
#10 0xb7b73727 in BrowserBar::showHideBrowser () from /usr/lib/libamarok.so.0
#11 0xb7b74222 in BrowserBar::polish () from /usr/lib/libamarok.so.0
#12 0xb62ae0dd in QWidget::show () from /usr/lib/libqt-mt.so.3
#13 0xb62aacbf in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#14 0xb62ae0f0 in QWidget::show () from /usr/lib/libqt-mt.so.3
#15 0xb74c2bbd in KSystemTray::minimizeRestore () from /usr/lib/libkdeui.so.4
#16 0xb74d178e in KSystemTray::activateOrHide () from /usr/lib/libkdeui.so.4
#17 0xb74d194d in KSystemTray::toggleActive () from /usr/lib/libkdeui.so.4
#18 0xb752e593 in KSystemTray::mousePressEvent () from /usr/lib/libkdeui.so.4
#19 0xb62ab644 in QWidget::event () from /usr/lib/libqt-mt.so.3
#20 0xb7e0b6fe in Amarok::TrayIcon::event () from /usr/lib/libamarok.so.0
#21 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#22 0xb620dcae in QApplication::notify () from /usr/lib/libqt-mt.so.3
#23 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#24 0xb619e27d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#25 0xb619cee2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0xb619afcc in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#27 0xb61b21a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#28 0xb6226140 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb620d704 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#30 0xb620d72f in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#31 0xb7dd22e1 in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
#32 0xb7dd2ce4 in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
#33 0xb7b9e61d in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
#34 0xb7b6c36a in App::continueInit () from /usr/lib/libamarok.so.0
#35 0xb7b6c9d8 in App::qt_invoke () from /usr/lib/libamarok.so.0
#36 0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#37 0xb66008ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#38 0xb6294842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#39 0xb629c258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#40 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb620d91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb619e209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#44 0xb61fe53b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#45 0xb61b2d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#46 0xb62261ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0xb6225fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0xb620d699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0x0804bfc2 in ?? ()
#50 0xbfe6a540 in ?? ()
#51 0xbfe6a6d4 in ?? ()
#52 0x0806a5a6 in ?? ()
#53 0x0806a595 in ?? ()
#54 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6c1414b in ?? () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x0804d451 in Amarok::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7b85b0b in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#5  0xb7b869ed in CollectionView::renderView () from /usr/lib/libamarok.so.0
No symbol table info available.
#6  0xb7b9893c in CollectionView::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#7  0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#8  0xb62751aa in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#9  0xb7b73110 in BrowserBar::browserActivated () from /usr/lib/libamarok.so.0
No symbol table info available.
#10 0xb7b73727 in BrowserBar::showHideBrowser () from /usr/lib/libamarok.so.0
No symbol table info available.
#11 0xb7b74222 in BrowserBar::polish () from /usr/lib/libamarok.so.0
No symbol table info available.
#12 0xb62ae0dd in QWidget::show () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#13 0xb62aacbf in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#14 0xb62ae0f0 in QWidget::show () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#15 0xb74c2bbd in KSystemTray::minimizeRestore () from /usr/lib/libkdeui.so.4
No symbol table info available.
#16 0xb74d178e in KSystemTray::activateOrHide () from /usr/lib/libkdeui.so.4
No symbol table info available.
#17 0xb74d194d in KSystemTray::toggleActive () from /usr/lib/libkdeui.so.4
No symbol table info available.
#18 0xb752e593 in KSystemTray::mousePressEvent () from /usr/lib/libkdeui.so.4
No symbol table info available.
#19 0xb62ab644 in QWidget::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#20 0xb7e0b6fe in Amarok::TrayIcon::event () from /usr/lib/libamarok.so.0
No symbol table info available.
#21 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#22 0xb620dcae in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#23 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#24 0xb619e27d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#25 0xb619cee2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#26 0xb619afcc in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#27 0xb61b21a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#28 0xb6226140 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#29 0xb620d704 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#30 0xb620d72f in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#31 0xb7dd22e1 in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#32 0xb7dd2ce4 in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#33 0xb7b9e61d in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#34 0xb7b6c36a in App::continueInit () from /usr/lib/libamarok.so.0
No symbol table info available.
#35 0xb7b6c9d8 in App::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#36 0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#37 0xb66008ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#38 0xb6294842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#39 0xb629c258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#40 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#41 0xb620d91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#42 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#43 0xb619e209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#44 0xb61fe53b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#45 0xb61b2d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#46 0xb62261ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#47 0xb6225fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#48 0xb620d699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#49 0x0804bfc2 in ?? ()
No symbol table info available.
#50 0xbfe6a540 in ?? ()
No symbol table info available.
#51 0xbfe6a6d4 in ?? ()
No symbol table info available.
#52 0x0806a5a6 in ?? ()
No symbol table info available.
#53 0x0806a595 in ?? ()
No symbol table info available.
#54 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 5 (Thread -1274958960 (LWP 10878)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c108fc in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb335ad3f in ?? () from /usr/lib/libxine.so.1
#3  0x085da080 in ?? ()
#4  0x085da068 in ?? ()
#5  0xb401a388 in ?? ()
#6  0xb401a3a8 in ?? ()
#7  0x1746a096 in ?? ()
#8  0xb401a390 in ?? ()
#9  0x085da080 in ?? ()
#10 0xb401a388 in ?? ()
#11 0x0006df02 in ?? ()
#12 0x00000000 in ?? ()
Thread 4 (Thread -1266566256 (LWP 10879)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c10676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb336991a in ?? () from /usr/lib/libxine.so.1
#3  0x085f3c50 in ?? ()
#4  0x085f3c38 in ?? ()
#5  0xb481b354 in ?? ()
#6  0xb481b390 in ?? ()
#7  0xb6c1f000 in ?? ()
#8  0xb6c092de in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb33698fd in ?? () from /usr/lib/libxine.so.1
#10 0xb3395480 in ?? () from /usr/lib/libxine.so.1
#11 0x085f3c30 in ?? ()
#12 0x085f3c38 in ?? ()
#13 0x085f5950 in ?? ()
#14 0xb336ca17 in ?? () from /usr/lib/libxine.so.1
#15 0x085f3c38 in ?? ()
#16 0x00000000 in ?? ()
Thread 3 (Thread -1302889584 (LWP 10880)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c10676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb335e52c in ?? () from /usr/lib/libxine.so.1
#3  0x0871f89c in ?? ()
#4  0x0871f884 in ?? ()
#5  0x00000000 in ?? ()
Thread 2 (Thread -1311282288 (LWP 10881)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c10676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb336ed44 in xine_event_wait () from /usr/lib/libxine.so.1
#3  0x08569070 in ?? ()
#4  0x08727b80 in ?? ()
#5  0x00000001 in ?? ()
#6  0xb336edd0 in ?? () from /usr/lib/libxine.so.1
#7  0x08727b80 in ?? ()
#8  0x08569070 in ?? ()
#9  0x08727b84 in ?? ()
#10 0xb6c1bff4 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#11 0x00000000 in ?? ()
Thread 1 (Thread -1262151968 (LWP 10860)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6c1414b in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d451 in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb7b85b0b in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
#5  0xb7b869ed in CollectionView::renderView () from /usr/lib/libamarok.so.0
#6  0xb7b9893c in CollectionView::qt_invoke () from /usr/lib/libamarok.so.0
#7  0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb62751aa in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb7b73110 in BrowserBar::browserActivated () from /usr/lib/libamarok.so.0
#10 0xb7b73727 in BrowserBar::showHideBrowser () from /usr/lib/libamarok.so.0
#11 0xb7b74222 in BrowserBar::polish () from /usr/lib/libamarok.so.0
#12 0xb62ae0dd in QWidget::show () from /usr/lib/libqt-mt.so.3
#13 0xb62aacbf in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#14 0xb62ae0f0 in QWidget::show () from /usr/lib/libqt-mt.so.3
#15 0xb74c2bbd in KSystemTray::minimizeRestore () from /usr/lib/libkdeui.so.4
#16 0xb74d178e in KSystemTray::activateOrHide () from /usr/lib/libkdeui.so.4
#17 0xb74d194d in KSystemTray::toggleActive () from /usr/lib/libkdeui.so.4
#18 0xb752e593 in KSystemTray::mousePressEvent () from /usr/lib/libkdeui.so.4
#19 0xb62ab644 in QWidget::event () from /usr/lib/libqt-mt.so.3
#20 0xb7e0b6fe in Amarok::TrayIcon::event () from /usr/lib/libamarok.so.0
#21 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#22 0xb620dcae in QApplication::notify () from /usr/lib/libqt-mt.so.3
#23 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#24 0xb619e27d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#25 0xb619cee2 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0xb619afcc in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#27 0xb61b21a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#28 0xb6226140 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb620d704 in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#30 0xb620d72f in QApplication::processEvents () from /usr/lib/libqt-mt.so.3
#31 0xb7dd22e1 in ScanController::initIncremental ()
   from /usr/lib/libamarok.so.0
#32 0xb7dd2ce4 in ScanController::ScanController ()
   from /usr/lib/libamarok.so.0
#33 0xb7b9e61d in CollectionDB::scanModifiedDirs ()
   from /usr/lib/libamarok.so.0
#34 0xb7b6c36a in App::continueInit () from /usr/lib/libamarok.so.0
#35 0xb7b6c9d8 in App::qt_invoke () from /usr/lib/libamarok.so.0
#36 0xb6274893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#37 0xb66008ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#38 0xb6294842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#39 0xb629c258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#40 0xb620baf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#41 0xb620d91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#42 0xb72efca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#43 0xb619e209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#44 0xb61fe53b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#45 0xb61b2d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#46 0xb62261ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#47 0xb6225fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#48 0xb620d699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#49 0x0804bfc2 in ?? ()
#50 0xbfe6a540 in ?? ()
#51 0xbfe6a6d4 in ?? ()
#52 0x0806a5a6 in ?? ()
#53 0x0806a595 in ?? ()
#54 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================
```

---

### Post by mm405416 on 2007-12-12
MORE INFORMATION:
I seems I can right click on the icon and hit restore.  That allows me to bring up amaroK, and after that, I can click on just about everything, it seems to only crash when I hit collection.  Hopefully someone can offer a little guidance or explanation?

---

### Post by itsjustarumour on 2007-12-12
Hmmm, the only thing I can suggest is using Synaptic to reinstall DVDShrink and DeeVeeDee, just in case there was a dependency error somewhere and something got removed that shouldn't have been removed...

---

### Post by mm405416 on 2007-12-12
Ok, I tried reinstalling the software (incidentally,  I was wrong about the names before, DeVeDe was correct but the other was dvd::rip) this did not assist me, amaroK is still crashing.  I'm going to try messing with some settings and report if that gets me anywhere.

---

### Post by mm405416 on 2007-12-12
still nothing, I'm really not sure where to go

---

### Post by Whiffle on 2007-12-12
My amarok was doing funny things before I installed slackware, I think it might have had something to do with an update from about a week or so ago, but xine (which is what amarok uses to play music, at least on mine) was acting up and wouldn't play anything.  Any app that also uses xine (like kaffeine) wouldn't work either...you might poke around and see what you can come up with on xine.

---

### Post by monte48lowes on 2007-12-12
I had a similar issue with Amarok a while back. Somehow the collection database got corrupted. I closed Amarok and deleted the database. Then when I restarted amarok, I had to rescan my collection. End result? Amarok started working.

Mike

The collection database is located:

> .kde/share/apps/amarok/collection.db

---

### Post by mm405416 on 2007-12-13
hey! this seems to have worked! huge thanks to you sir (or possibly ma'am)!

---

