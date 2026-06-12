---
title: "xine crashing in Kaffeine, Feisty, amd64"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by mikerduffy on 2007-04-24
I'm running kubuntu 7.04 amd64.
I was using opengl, but it's possible I changed that.  However, I have no idea how to check, since Kaffeine (0.8.3) crashes before I can find out (see below).

I've been watching DVDs with no problems (save the lack of subtitles) for a couple of weeks, but today that all changed.
[list]
[*]If I insert a DVD, then choose to play it in Kaffeine when the dialog pops up, Kaffeine crashes.
[*]If I open Kaffeine, then click "Settings > xine Engine Parameters", Kaffeine crashes again.
[*]Yes, I've tried multiple DVDs, all movies from Netflix.
[/list]
Here is the backtrace from the latter method of crash:
```
(no debugging symbols found)
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
[Thread debugging using libthread_db enabled]
[New Thread 47746445926176 (LWP 5563)]
[New Thread 1082132800 (LWP 5564)]
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
#5  0x00002b6cd7ef95ba in KXineWidget::getXineLog ()
   from /usr/lib/kde3/libxinepart.so
#6  0x00002b6cd7eec2bc in XinePart::slotError ()
   from /usr/lib/kde3/libxinepart.so
#7  0x00002b6cd7ef38b4 in XinePart::qt_invoke ()
   from /usr/lib/kde3/libxinepart.so
#8  0x00002b6cd18fece2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#9  0x00002b6cd18ff27d in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#10 0x00002b6cd7ef85b8 in KXineWidget::signalXineError ()
   from /usr/lib/kde3/libxinepart.so
#11 0x00002b6cd7f06bea in KXineWidget::initXine ()
   from /usr/lib/kde3/libxinepart.so
#12 0x00002b6cd7ee2f2e in XinePart::slotConfigXine ()
   from /usr/lib/kde3/libxinepart.so
#13 0x00002b6cd7ef389b in XinePart::qt_invoke ()
   from /usr/lib/kde3/libxinepart.so
#14 0x00002b6cd18fece2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#15 0x00002b6cd18ff87c in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#16 0x00002b6ccfd0ef0d in KAction::slotPopupActivated ()
   from /usr/lib/libkdeui.so.4
#17 0x00002b6ccfd0f1b3 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#18 0x00002b6cd18fece2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#19 0x00002b6cd1c6cec9 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#20 0x00002b6cd191de37 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#21 0x00002b6cd1a1da58 in QPopupMenu::mouseReleaseEvent ()
   from /usr/lib/libqt-mt.so.3
#22 0x00002b6cd1933410 in QWidget::event () from /usr/lib/libqt-mt.so.3
#23 0x00002b6cd189a1d6 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#24 0x00002b6cd189c334 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#25 0x00002b6cd061d7a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#26 0x00002b6cd182cd34 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#27 0x00002b6cd182b661 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#28 0x00002b6cd1829b0a in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#29 0x00002b6cd18403ea in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#30 0x00002b6cd18b370b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#31 0x00002b6cd18b3513 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#32 0x00002b6cd189bc9c in QApplication::exec () from /usr/lib/libqt-mt.so.3
#33 0x0000000000437b99 in ?? ()
#34 0x00002b6cd53c58e4 in __libc_start_main () from /lib/libc.so.6
#35 0x0000000000437829 in ?? ()
#36 0x00007fffdd7ca888 in ?? ()
#37 0x0000000000000000 in ?? ()

```
Hopefully, someone can tell me to change one line in a config file somewhere.

...Today, I had to boot into Windows XP to watch the DVD. :shudder:

---

### Post by mikerduffy on 2007-04-26
bump

---

### Post by watergate on 2007-05-01
I have the same problem. No one has a solution?

---

### Post by Giggity on 2007-07-26
I just started having the same problem.  As soon as I try to enter the xine Engine parameters, Kaffeine crashes.

---

### Post by puppy on 2007-07-30
yeah I've just started having the same problem - kaffeine crashes when trying to play a video or selecting one of the tabs... :confused:

---

### Post by asmoore82 on 2007-07-30
here's the quick and dirty fix.... 

all linux apps store your personal settings in hidden "dot" files in your home directory.
Usually, the name of the file/folder is the same as the name of the app but kaffeine is slightly
more complicated because its a part of the KDE suite....

anyways, I would move all of kaffeine's settings to a backup location and run it again "for the first time" to see if it works.
open a term and ...

```
~ $ mkdir .backup
~ $ mv -v .kde/share/apps/kaffeine .backup/
```

---

### Post by eldersoares on 2007-07-31
well, my problem is almost the same. i have edgy x86 and kaffeine doesnt even open... the icon keeps jumping w/ the cursor but nothing happens... i'm almost sure i havent made any changes in the system... it just started to happen at once. the solution above didnt work for me...
thanks

---

