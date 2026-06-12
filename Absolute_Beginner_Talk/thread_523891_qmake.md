---
title: "qmake"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2007-08-12
i am trying to complie vivia using qmake, but when i put in qmake and make, i get these errors...do i have to somehow downgrade my version of qdesigner?

```
qmake
vivia.pro:43: Unknown test function: CONFIG
WARNING: Found potential symbol conflict of AlignSyncMarkersDialog.h (AlignSyncMarkersDialog.h) in HEADERS
WARNING: Found potential symbol conflict of ExportDialog.cpp (ExportDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of ExportDialog.h (ExportDialog.h) in HEADERS
WARNING: Found potential symbol conflict of MainWindow.cpp (MainWindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of MainWindow.h (MainWindow.h) in HEADERS
WARNING: Found potential symbol conflict of StartupDialog.cpp (StartupDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of StartupDialog.h (StartupDialog.h) in HEADERS
WARNING: Found potential symbol conflict of ErrorListDialog.cpp (ErrorListDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of ErrorListDialog.h (ErrorListDialog.h) in HEADERS
WARNING: Found potential symbol conflict of TranDurationDialog.h (TranDurationDialog.h) in HEADERS
meghan@meghan-laptop:~/vivia/src$ make
Makefile:1067: warning: overriding commands for target `.obj/ExportDialog.o'
Makefile:890: warning: ignoring old commands for target `.obj/ExportDialog.o'
Makefile:1104: warning: overriding commands for target `.obj/MainWindow.o'
Makefile:931: warning: ignoring old commands for target `.obj/MainWindow.o'
Makefile:1108: warning: overriding commands for target `.obj/StartupDialog.o'
Makefile:868: warning: ignoring old commands for target `.obj/StartupDialog.o'
Makefile:1112: warning: overriding commands for target `.obj/ErrorListDialog.o'
Makefile:894: warning: ignoring old commands for target `.obj/ErrorListDialog.o'Makefile:1259: warning: overriding commands for target `.obj/moc_AlignSyncMarkersDialog.o'
Makefile:1165: warning: ignoring old commands for target `.obj/moc_AlignSyncMarkersDialog.o'
Makefile:1262: warning: overriding commands for target `.obj/moc_ExportDialog.o'Makefile:1246: warning: ignoring old commands for target `.obj/moc_ExportDialog.o'
Makefile:1266: warning: overriding commands for target `.obj/moc_MainWindow.o'
Makefile:1253: warning: ignoring old commands for target `.obj/moc_MainWindow.o'Makefile:1269: warning: overriding commands for target `.obj/moc_StartupDialog.o'
Makefile:1240: warning: ignoring old commands for target `.obj/moc_StartupDialog.o'
Makefile:1272: warning: overriding commands for target `.obj/moc_ErrorListDialog.o'
Makefile:1249: warning: ignoring old commands for target `.obj/moc_ErrorListDialog.o'
Makefile:1275: warning: overriding commands for target `.obj/moc_TranDurationDialog.o'
Makefile:1168: warning: ignoring old commands for target `.obj/moc_TranDurationDialog.o'
Makefile:1386: warning: overriding commands for target `.obj/moc_AlignSyncMarkersDialog.cpp'
Makefile:1320: warning: ignoring old commands for target `.obj/moc_AlignSyncMarkersDialog.cpp'
Makefile:1389: warning: overriding commands for target `.obj/moc_ExportDialog.cpp'
Makefile:1374: warning: ignoring old commands for target `.obj/moc_ExportDialog.cpp'
Makefile:1392: warning: overriding commands for target `.obj/moc_MainWindow.cpp'Makefile:1380: warning: ignoring old commands for target `.obj/moc_MainWindow.cpp'
Makefile:1395: warning: overriding commands for target `.obj/moc_StartupDialog.cpp'
Makefile:1368: warning: ignoring old commands for target `.obj/moc_StartupDialog.cpp'
Makefile:1398: warning: overriding commands for target `.obj/moc_ErrorListDialog.cpp'
Makefile:1377: warning: ignoring old commands for target `.obj/moc_ErrorListDialog.cpp'
Makefile:1401: warning: overriding commands for target `.obj/moc_TranDurationDialog.cpp'
Makefile:1323: warning: ignoring old commands for target `.obj/moc_TranDurationDialog.cpp'
g++ -c -pipe -Wall -W -O2 -pipe -fomit-frame-pointer -ffast-math -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../ffmpeg-out/include -I.obj -I/usr/include/qt3 -I.obj/ -I. -I.obj/ -o .obj/Utils.o Utils.cpp
In file included from Utils.cpp:20:
Utils.h:23:18: error: QImage: No such file or directory
Utils.cpp:24:18: error: QColor: No such file or directory
Utils.cpp:25:17: error: QTime: No such file or directory
Utils.h:30: error: ‘QString’ does not name a type
Utils.h:32: error: ‘QString’ does not name a type
Utils.h:34: error: ‘QString’ does not name a type
Utils.h:40: error: ‘QImage’ does not name a type
Utils.cpp:31: error: ‘QString’ does not name a type
Utils.cpp:44: error: ‘QString’ does not name a type
Utils.cpp:56: error: ‘QString’ does not name a type
Utils.cpp: In function ‘void Utils::deleteAVPicture(AVPicture*)’:
Utils.cpp:78: error: ‘NULL’ was not declared in this scope
Utils.cpp: At global scope:
Utils.cpp:84: error: ‘QImage’ does not name a type
make: *** [.obj/Utils.o] Error 1
```

---

### Post by schorsch on 2007-08-12
Just a guess but perhaps you are missing some of the qt3 development packages. But I could not say exactly which ones.

---

### Post by milosz.galazka on 2007-08-12
Maybe just package *kde-devel*

---

### Post by irishgoth8822 on 2007-08-12
i actually looked at the devel package when i was trying to pick packages i might need to fix this, and i didnt install it because it had so many dependencies and i wasnt sure if i needed it...but im installing now, and i'll give it a shot. thanks :-)

---

### Post by irishgoth8822 on 2007-08-12
well, turns out that unfortunately, kde-devel did nothing. ive installed almost every single package that comes up when i search 'qt' or 'qmake' or 'qt3' but im getting the same exact error scripts.

---

### Post by Ashrael on 2007-11-20
qmake
vivia.pro:43: Unknown test function: CONFIG
WARNING: Found potential symbol conflict of AlignSyncMarkersDialog.h (AlignSyncMarkersDialog.h) in HEADERS
WARNING: Found potential symbol conflict of ExportDialog.cpp (ExportDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of ExportDialog.h (ExportDialog.h) in HEADERS
WARNING: Found potential symbol conflict of MainWindow.cpp (MainWindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of MainWindow.h (MainWindow.h) in HEADERS
WARNING: Found potential symbol conflict of StartupDialog.cpp (StartupDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of StartupDialog.h (StartupDialog.h) in HEADERS
WARNING: Found potential symbol conflict of ErrorListDialog.cpp (ErrorListDialog.cpp) in SOURCES
WARNING: Found potential symbol conflict of ErrorListDialog.h (ErrorListDialog.h) in HEADERS
WARNING: Found potential symbol conflict of TranDurationDialog.h (TranDurationDialog.h) in HEADERS


 same here..nothing on the vivia forum either..... 


anybody???

---

