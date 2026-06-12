---
title: "Adept Manager Error won't start"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by cutiger95 on 2007-12-22
New install and Adept Manager hangs up when starting with the following message

"Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself."

This is after a fresh boot and log-in.  No-one else is on the machine and I have not used the package manager.  

Very strange.

---

### Post by NeoLithium on 2007-12-22
When you first log in, a little popup appears and you can start downloading the updates.  If that is running, you don't be able to run Adept until after hte updates have installed.

---

### Post by cutiger95 on 2007-12-22
I don't have a pop-up when I log-in.  Is there anyway to see if there is actually anything running?

---

### Post by NeoLithium on 2007-12-22
Generally you can see the update manager icon in the system tray.  If there's no updates running, I'd suggest a quick reboot and try once again before opening any other programs once again.

---

### Post by cutiger95 on 2007-12-22
That is what I tried and it doesn't seem to work, on about the 6th reboot already.  There is no update icon in the bar nor adept package icon.  That's why I am so confused.  

It's almost like something is half started somewhere if that makes any sense at all.

---

### Post by spiderbatdad on 2007-12-22
try ```
sudo dpkg --configure -a
``` maybe this will fix the package that is hung up.

---

### Post by cutiger95 on 2007-12-22
Here is the Backtrace of the error:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[New Thread -1235810624 (LWP 8380)]
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
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb65cb875 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb65cd201 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb67d76e0 in __gnu_cxx::__verbose_terminate_handler ()
   from /usr/lib/libstdc++.so.6
#10 0xb67d4f65 in ?? () from /usr/lib/libstdc++.so.6
#11 0xb67d4fa2 in std::terminate () from /usr/lib/libstdc++.so.6
#12 0xb67d50ca in __cxa_throw () from /usr/lib/libstdc++.so.6
#13 0x0812b916 in ?? ()
#14 0x0812be8a in ?? ()
#15 0x0812bee8 in ?? ()
#16 0x0812c735 in ?? ()
#17 0x0812a22d in ?? ()
#18 0x08114379 in ?? ()
#19 0x080951ed in ?? ()
#20 0x0807378d in ?? ()
#21 0x0807408e in ?? ()
#22 0xb6e1b893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb71a78ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0xb6e3b842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0xb6e43258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#26 0xb6db2af0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#27 0xb6db491f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0xb7578ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#29 0xb6d45209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#30 0xb6da553b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#31 0xb6d59d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#32 0xb6dcd1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0xb6dccfde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0xb6db4699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x0806f75e in ?? ()
#36 0xb65b7050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0806f401 in ?? ()

---

### Post by cutiger95 on 2007-12-22
Spider Thanks that appears to have fixed the issue.  Not sure what it was but something was hung up.

---

