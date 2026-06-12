---
title: "Do i need to reinstall ubuntu"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by natman on 2007-05-04
Hi,
I use linux for a little bit of practice programming in C++, i used kdevelope and then upgraded to feisty and now every time i try to open a template project or my own .cpp the program just crashes
( i ran backtrace and got this
[HTML](no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 47782103622448 (LWP 5927)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#5  0x00002b7519706d70 in PartController::createEditorPart ()
   from /usr/lib/libkdevshell.so.0
#6  0x00002b7519709c93 in PartController::editDocumentInternal ()
   from /usr/lib/libkdevshell.so.0
#7  0x00002b75259557df in AppWizardPart::openFilesAfterGeneration ()
   from /usr/lib/kde3/libkdevappwizard.so
#8  0x00002b752595586b in AppWizardPart::qt_invoke ()
   from /usr/lib/kde3/libkdevappwizard.so
#9  0x00002b751b7c1e0b in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#10 0x00002b751b7c287c in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#11 0x00002b7519714e34 in ProjectManager::slotLoadProject ()
   from /usr/lib/libkdevshell.so.0
#12 0x00002b7519715110 in ProjectManager::qt_invoke ()
   from /usr/lib/libkdevshell.so.0
#13 0x00002b751b7c1ce2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#14 0x00002b751bb2fec9 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#15 0x00002b751b7e0e37 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#16 0x00002b751b7e7e6a in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#17 0x00002b751b75d1d6 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#18 0x00002b751b75ef65 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0x00002b751ae707a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#20 0x00002b751b6efcc2 in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0x00002b751b750490 in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#22 0x00002b751b7043ef in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#23 0x00002b751b77670b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#24 0x00002b751b776513 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#25 0x00002b751b75ec9c in QApplication::exec () from /usr/lib/libqt-mt.so.3
#26 0x000000000040780b in ?? ()
#27 0x00002b751a0ee8e4 in __libc_start_main () from /lib/libc.so.6
#28 0x0000000000406fc9 in ?? ()
#29 0x00007fff91613798 in ?? ()
#30 0x0000000000000000 in ?? ()
[/HTML]

Is there a problem with my kubuntu or is kdevelope just srewed up? Should i chance reinstalling?

---

### Post by ronocdh on 2007-05-05
If you haven't yet found a workaround, I would recommend you reinstall. Personally I always install freshly from a CD when upgrading to a new version; I usually use the alternate CD, too. By backing up your Home directory you can ensure you'll keep all your documents and most of your settings, too. Good luck!

---

