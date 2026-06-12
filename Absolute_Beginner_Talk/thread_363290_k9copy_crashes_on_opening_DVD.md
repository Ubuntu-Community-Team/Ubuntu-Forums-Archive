---
title: "k9copy crashes on opening DVD"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Statik on 2007-02-16
Hi all,

I'm trying to backup some of my DVDs so that they don't get destroyed when the kids scratch the m putting in their DVDs. I've heard that k9copy is a good way to do this. I just installed it through synaptic and it fails when I hit OPEN on the menu. The crash message backtrace is as follows. I'm not good at reading these so I don't know what's wrong:
```

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
[Thread debugging using libthread_db enabled]
[New Thread -1240234320 (LWP 32720)]
[KCrash handler]
#6  0x08064e26 in QValueList<QString>::clear ()
#7  0x08079966 in QValueListPrivate<KIO::UDSAtom>::~QValueListPrivate ()
#8  0xb6963957 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb69643fc in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb72663b9 in KAction::activated () from /usr/lib/libkdeui.so.4
#11 0xb72a3c02 in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#12 0xb736c29d in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#13 0xb736c561 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#14 0xb6963957 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb6ceff44 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#16 0xb69838ea in QSignal::activate () from /usr/lib/libqt-mt.so.3
#17 0xb6a89fd3 in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#18 0xb726f3ce in KPopupMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.4
#19 0xb699a729 in QWidget::event () from /usr/lib/libqt-mt.so.3
#20 0xb68fab88 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb68fcd46 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb70acdb2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb688d3fd in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#24 0xb688bd3f in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#25 0xb688a14c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#26 0xb68a1320 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#27 0xb691525e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#28 0xb691506e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#29 0xb68fc731 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#30 0x08059b77 in QValueListPrivate<QString>::~QValueListPrivate ()
#31 0xb617c8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#32 0x080577e1 in ?? ()

```

Can anyone help?

Statik

---

### Post by spydirweb on 2007-05-08
I use k9copy for nearly the same reason, and I too have similar crashes on discs that seem to be in poor condition.  Some will even start to copy fine but eventually crash, while others will copy just fine.  I've tried a few other apps like dvdshrink and dvd95.  dvdshrink's command line is ok if you just want the movie itself, but I like k9copy's ability to basically just shrink the video files, keeping the menus, extras, alternate languages/subtitles, etc.  dvd95 has yet to work for me, and dvdshrink's gui interface is a little confusing.  K9Copy just works, when it works.

Is it constantly crashing like this, no matter the DVD?  If not, is it also just the quality of the disc you're using?  I have a dvd-rom/cd burner and a dvd burner.  Usually it's original in dvdrom/cd burner, blank in dvd burner, but every so often when it doesn't work like that it will work if i only use the dvd burner.  If you can you might want to give that a shot.

I'm not sure what causes my problems exactly, I think it's related to KDE libs somehow failing to read the discs for some reason, considering I can always find another way to copy them.  Give dvdshrink a shot, it's not to bad, really.

---

### Post by berteh on 2007-06-25
K9copy version 1.0.4 works great (e.g., will copy menus, shrink to fit on dvd correctly, etc.), however version 1.0.2 which is in the dapper repositories still had some bugs for me, I got 1.0.4 working from source without too much hassle following these instructions:

[http://ubuntuforums.org/showpost.php?p=1098581&postcount=12](http://ubuntuforums.org/showpost.php?p=1098581&postcount=12)

---

