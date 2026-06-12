---
title: "Installing software qmake command"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by asgard_command on 2007-10-23
I am trying to install a program to access my Humax PVR.
These are the instructions on the website for Linux installation.
----------------------------------
Linux/Mac OS X

1. Qt 4.1.0 or newer development libraries to be installed.
2. libusb development libraries to be installed.
3. Extract project tar -xvzf humaxGui-1.00.tar.gz.
4. Open a Shell Console and navigate to the humaxGui directory.
5. Run "qmake humaxGui.pro".
6. Run "make".
7. Note: If this stage fails due to a 'Ui' error, try the command 'make compiler_uic_make_all', then re-run the 'make' command.
7. Connect USB cable between PC and PVR.
8. Run ./humaxGui from the current directory.

Notes for Linux Users

* On some distro's humaxGui will need to be run as root in order for it to connect.
* Device -> host (pvr->pc) transfers will not work with recovery mode enabled (Still under investigation, may crash the pvr).
* Lower transfer rates may be required.
* qmake may not be the correct command to run as Qt3 will probably be installed along side Qt4 (DO NOT REMOVE Qt3 FROM YOUR OS, UNLESS YOU REALLY KNOW WHAT YOU ARE DOING), some distro's have renamed it qmake4 or qmake-qt4, you will have to check (humaxGui will not compile under Qt3).
----------------------------------------

I installed qt4 development libraries and libusb

I used qmake-qt4 instead of make when I ran the final make command this is what I got,

----------------------------------------
/usr/bin/uic-qt4 ui/MainWindow.ui -o release/uic/ui_MainWindow.h
/usr/bin/uic-qt4 ui/AboutDialog.ui -o release/uic/ui_AboutDialog.h
/usr/bin/uic-qt4 ui/DeviceInfoDialog.ui -o release/uic/ui_DeviceInfoDialog.h
/usr/bin/uic-qt4 ui/FileReplaceDialog.ui -o release/uic/ui_FileReplaceDialog.h
/usr/bin/uic-qt4 ui/PrefsDialog.ui -o release/uic/ui_PrefsDialog.h
/usr/bin/uic-qt4 ui/TransferDialog.ui -o release/uic/ui_TransferDialog.h
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_SHARED -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -Iincl -Irelease/moc -Irelease/uic -o release/obj/AboutDialog.o src/AboutDialog.cpp
make: g++: Command not found
make: *** [release/obj/AboutDialog.o] Error 127
----------------------------------------

Any help appreciated, this is pretty much the last app I need to get working under Linux to never need windows again.

---

### Post by mrog on 2007-10-23
try running

apt-get install build-essential

then try installing your software again.

---

### Post by asgard_command on 2007-10-23
Worked perfect.

Thanks very much.

---

