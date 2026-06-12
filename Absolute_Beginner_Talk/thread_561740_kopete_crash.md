---
title: "kopete crash"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Red-Shield on 2007-09-27
kopete has been crashing and i have no idea why it was working here is the report and i am new to linux but must say it KICKS WINDOWS ASSSSSSS please help: SIGSEGV signal 11:confused:


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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1232811808 (LWP 11713)]
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
#6  0xb7553b63 in QGListIterator::QGListIterator ()
   from /usr/lib/libqt-mt.so.3
#7  0xb643e970 in KWalletD::wallets () from /usr/lib/kde3/kded_kwalletd.so
#8  0xb6441983 in KWalletD::doTransactionOpen ()
   from /usr/lib/kde3/kded_kwalletd.so
#9  0xb644b382 in KWalletD::processTransactions ()
   from /usr/lib/kde3/kded_kwalletd.so
#10 0xb644b887 in KWalletD::qt_invoke () from /usr/lib/kde3/kded_kwalletd.so
#11 0xb725788b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb75e37b0 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#13 0xb727781e in QSignal::activate () from /usr/lib/libqt-mt.so.3
#14 0xb727f234 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#15 0xb71eea60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#16 0xb71f088f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#17 0xb78f6c32 in KApplication::notify () from /usr/lib/libkdecore.so.4
#18 0xb71811e9 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#19 0xb71e14ab in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#20 0xb7195d25 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#21 0xb7209136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#22 0xb7208f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#23 0xb71f0609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#24 0xb671b9e8 in kdemain () from /usr/lib/libkdeinit_kded.so
#25 0xb7f74464 in kdeinitmain () from /usr/lib/kde3/kded.so
#26 0x0804e6bf in ?? ()
#27 0x00000001 in ?? ()
#28 0x0807e450 in ?? ()
#29 0x00000001 in ?? ()
#30 0x00000000 in ?? ()

---

### Post by nonewmsgs on 2007-10-15
uninstall it find the .kopete folder and delete it and reinstall and it should work.  at least if it was working properly before....
otherwise try gaim.
welcome and glad you like it :)

---

