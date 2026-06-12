---
title: "Help With qpspmanager Please!"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Jeordy on 2007-10-29
I read through all the posts on this forum about this already and have been talkin with Frak, but so far nothin, and he went to bed... Here is my command prompt after following the directions::
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ qmake
WARNING: Failure to find: src/mainwindow.h
WARNING: Failure to find: src/optionsmanager.h
WARNING: Failure to find: src/applicationsmanager.h
WARNING: Failure to find: src/optionswidget.h
WARNING: Failure to find: src/qpspmanager.h
WARNING: Failure to find: src/videosmanager.h
WARNING: Failure to find: src/videoswidget.h
WARNING: Failure to find: src/applicationswidget.h
WARNING: Failure to find: src/backupsmanager.h
WARNING: Failure to find: src/backupswidget.h
WARNING: Failure to find: src/isoswidget.h
WARNING: Failure to find: src/pspapplication.h
WARNING: Failure to find: src/firmwares.h
WARNING: Failure to find: src/filemanager.h
WARNING: Failure to find: src/qpspmanagerexception.h
WARNING: Failure to find: src/qpspmanagerpbpexception.h
WARNING: Failure to find: src/which.h
WARNING: Failure to find: src/encodevideodialog.h
WARNING: Failure to find: src/addisodialog.h
WARNING: Failure to find: src/isocompressor.h
WARNING: Failure to find: src/psxconverter.h
WARNING: Failure to find: src/videojob.h
WARNING: Failure to find: src/video.h
WARNING: Failure to find: src/videooptions.h
WARNING: Failure to find: src/videojobmanager.h
WARNING: Failure to find: src/isosmanager.h
WARNING: Failure to find: src/savegame.h
WARNING: Failure to find: src/pspendian.h
WARNING: Failure to find: src/fsusage.h
WARNING: Failure to find: src/helpwidget.h
WARNING: Failure to find: src/main.cpp
WARNING: Failure to find: src/mainwindow.cpp
WARNING: Failure to find: src/optionsmanager.cpp
WARNING: Failure to find: src/applicationsmanager.cpp
WARNING: Failure to find: src/optionswidget.cpp
WARNING: Failure to find: src/qpspmanager.cpp
WARNING: Failure to find: src/videosmanager.cpp
WARNING: Failure to find: src/videoswidget.cpp
WARNING: Failure to find: src/applicationswidget.cpp
WARNING: Failure to find: src/backupswidget.cpp
WARNING: Failure to find: src/isoswidget.cpp
WARNING: Failure to find: src/backupsmanager.cpp
WARNING: Failure to find: src/pspapplication.cpp
WARNING: Failure to find: src/filemanager.cpp
WARNING: Failure to find: src/isosmanager.cpp
WARNING: Failure to find: src/qpspmanagerexception.cpp
WARNING: Failure to find: src/qpspmanagerpbpexception.cpp
WARNING: Failure to find: src/video.cpp
WARNING: Failure to find: src/encodevideodialog.cpp
WARNING: Failure to find: src/isocompressor.cpp
WARNING: Failure to find: src/psxconverter.cpp
WARNING: Failure to find: src/addisodialog.cpp
WARNING: Failure to find: src/videojob.cpp
WARNING: Failure to find: src/pspendian.cpp
WARNING: Failure to find: src/videojobmanager.cpp
WARNING: Failure to find: src/savegame.cpp
WARNING: Failure to find: src/helpwidget.cpp
WARNING: Failure to find: src/whichunix.cpp
WARNING: Failure to find: src/fsusageunix.cpp
WARNING: Failure to find: src/mainwindow.ui
WARNING: Failure to find: src/optionswidget.ui
WARNING: Failure to find: src/videoswidget.ui
WARNING: Failure to find: src/applicationswidget.ui
WARNING: Failure to find: src/backupswidget.ui
WARNING: Failure to find: src/isoswidget.ui
WARNING: Failure to find: src/encodevideo.ui
WARNING: Failure to find: src/addiso.ui
WARNING: Failure to find: src/helpwidget.ui
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ make
Makefile:403: warning: overriding commands for target `obj/mainwindow.o'
Makefile:265: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:406: warning: overriding commands for target `obj/optionswidget.o'
Makefile:274: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:409: warning: overriding commands for target `obj/videoswidget.o'
Makefile:283: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:412: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:286: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:415: warning: overriding commands for target `obj/backupswidget.o'
Makefile:289: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:418: warning: overriding commands for target `obj/isoswidget.o'
Makefile:292: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:427: warning: overriding commands for target `obj/helpwidget.o'
Makefile:340: warning: ignoring old commands for target `obj/helpwidget.o'
make: *** No rule to make target `src/mainwindow.ui', needed by `ui/mainwindow.h'.  Stop.
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ sudo make
Makefile:403: warning: overriding commands for target `obj/mainwindow.o'
Makefile:265: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:406: warning: overriding commands for target `obj/optionswidget.o'
Makefile:274: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:409: warning: overriding commands for target `obj/videoswidget.o'
Makefile:283: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:412: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:286: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:415: warning: overriding commands for target `obj/backupswidget.o'
Makefile:289: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:418: warning: overriding commands for target `obj/isoswidget.o'
Makefile:292: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:427: warning: overriding commands for target `obj/helpwidget.o'
Makefile:340: warning: ignoring old commands for target `obj/helpwidget.o'
make: *** No rule to make target `src/mainwindow.ui', needed by `ui/mainwindow.h'.  Stop.
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ sudo make install
Makefile:403: warning: overriding commands for target `obj/mainwindow.o'
Makefile:265: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:406: warning: overriding commands for target `obj/optionswidget.o'
Makefile:274: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:409: warning: overriding commands for target `obj/videoswidget.o'
Makefile:283: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:412: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:286: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:415: warning: overriding commands for target `obj/backupswidget.o'
Makefile:289: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:418: warning: overriding commands for target `obj/isoswidget.o'
Makefile:292: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:427: warning: overriding commands for target `obj/helpwidget.o'
Makefile:340: warning: ignoring old commands for target `obj/helpwidget.o'
make: Nothing to be done for `install'.
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ $ ./bin/QPSPManager
bash: $: command not found
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ ./bin/qpspmanager
bash: ./bin/qpspmanager: No such file or directory
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ qmake
WARNING: Failure to find: src/mainwindow.h
WARNING: Failure to find: src/optionsmanager.h
WARNING: Failure to find: src/applicationsmanager.h
WARNING: Failure to find: src/optionswidget.h
WARNING: Failure to find: src/qpspmanager.h
WARNING: Failure to find: src/videosmanager.h
WARNING: Failure to find: src/videoswidget.h
WARNING: Failure to find: src/applicationswidget.h
WARNING: Failure to find: src/backupsmanager.h
WARNING: Failure to find: src/backupswidget.h
WARNING: Failure to find: src/isoswidget.h
WARNING: Failure to find: src/pspapplication.h
WARNING: Failure to find: src/firmwares.h
WARNING: Failure to find: src/filemanager.h
WARNING: Failure to find: src/qpspmanagerexception.h
WARNING: Failure to find: src/qpspmanagerpbpexception.h
WARNING: Failure to find: src/which.h
WARNING: Failure to find: src/encodevideodialog.h
WARNING: Failure to find: src/addisodialog.h
WARNING: Failure to find: src/isocompressor.h
WARNING: Failure to find: src/psxconverter.h
WARNING: Failure to find: src/videojob.h
WARNING: Failure to find: src/video.h
WARNING: Failure to find: src/videooptions.h
WARNING: Failure to find: src/videojobmanager.h
WARNING: Failure to find: src/isosmanager.h
WARNING: Failure to find: src/savegame.h
WARNING: Failure to find: src/pspendian.h
WARNING: Failure to find: src/fsusage.h
WARNING: Failure to find: src/helpwidget.h
WARNING: Failure to find: src/main.cpp
WARNING: Failure to find: src/mainwindow.cpp
WARNING: Failure to find: src/optionsmanager.cpp
WARNING: Failure to find: src/applicationsmanager.cpp
WARNING: Failure to find: src/optionswidget.cpp
WARNING: Failure to find: src/qpspmanager.cpp
WARNING: Failure to find: src/videosmanager.cpp
WARNING: Failure to find: src/videoswidget.cpp
WARNING: Failure to find: src/applicationswidget.cpp
WARNING: Failure to find: src/backupswidget.cpp
WARNING: Failure to find: src/isoswidget.cpp
WARNING: Failure to find: src/backupsmanager.cpp
WARNING: Failure to find: src/pspapplication.cpp
WARNING: Failure to find: src/filemanager.cpp
WARNING: Failure to find: src/isosmanager.cpp
WARNING: Failure to find: src/qpspmanagerexception.cpp
WARNING: Failure to find: src/qpspmanagerpbpexception.cpp
WARNING: Failure to find: src/video.cpp
WARNING: Failure to find: src/encodevideodialog.cpp
WARNING: Failure to find: src/isocompressor.cpp
WARNING: Failure to find: src/psxconverter.cpp
WARNING: Failure to find: src/addisodialog.cpp
WARNING: Failure to find: src/videojob.cpp
WARNING: Failure to find: src/pspendian.cpp
WARNING: Failure to find: src/videojobmanager.cpp
WARNING: Failure to find: src/savegame.cpp
WARNING: Failure to find: src/helpwidget.cpp
WARNING: Failure to find: src/whichunix.cpp
WARNING: Failure to find: src/fsusageunix.cpp
WARNING: Failure to find: src/mainwindow.ui
WARNING: Failure to find: src/optionswidget.ui
WARNING: Failure to find: src/videoswidget.ui
WARNING: Failure to find: src/applicationswidget.ui
WARNING: Failure to find: src/backupswidget.ui
WARNING: Failure to find: src/isoswidget.ui
WARNING: Failure to find: src/encodevideo.ui
WARNING: Failure to find: src/addiso.ui
WARNING: Failure to find: src/helpwidget.ui
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ make
Makefile:403: warning: overriding commands for target `obj/mainwindow.o'
Makefile:265: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:406: warning: overriding commands for target `obj/optionswidget.o'
Makefile:274: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:409: warning: overriding commands for target `obj/videoswidget.o'
Makefile:283: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:412: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:286: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:415: warning: overriding commands for target `obj/backupswidget.o'
Makefile:289: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:418: warning: overriding commands for target `obj/isoswidget.o'
Makefile:292: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:427: warning: overriding commands for target `obj/helpwidget.o'
Makefile:340: warning: ignoring old commands for target `obj/helpwidget.o'
make: *** No rule to make target `src/mainwindow.ui', needed by `ui/mainwindow.h'.  Stop.
jeordy@Jeffery:~/Desktop/qpspmanager-2.0.2/src$ sudo make install
Makefile:403: warning: overriding commands for target `obj/mainwindow.o'
Makefile:265: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:406: warning: overriding commands for target `obj/optionswidget.o'
Makefile:274: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:409: warning: overriding commands for target `obj/videoswidget.o'
Makefile:283: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:412: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:286: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:415: warning: overriding commands for target `obj/backupswidget.o'
Makefile:289: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:418: warning: overriding commands for target `obj/isoswidget.o'
Makefile:292: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:427: warning: overriding commands for target `obj/helpwidget.o'
Makefile:340: warning: ignoring old commands for target `obj/helpwidget.o'
make: Nothing to be done for `install'.

if you can help, it would be much aprichiated, i wanted to get this workin b4 i went to bed =P

---

### Post by Jeordy on 2007-10-29
bump... somone please help

---

