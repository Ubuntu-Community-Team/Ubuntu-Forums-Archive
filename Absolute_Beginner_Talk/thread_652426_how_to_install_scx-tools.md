---
title: "how to install scx-tools ???"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Biggy on 2007-12-28
hi 

i download scx-tools from [http://sourceforge.net/project/showfiles.php?group_id=206325]("http://sourceforge.net/project/showfiles.php?group_id=206325")


but can't install in ubuntu gutsy 7.10 , compile required how to compile ??

help plzz

---

### Post by taurus on 2007-12-28
Here is something for you to look over.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Biggy on 2007-12-28
make: `scx-recorder' is up to date.

any idea ????

---

### Post by taurus on 2007-12-28
Can you at least provide a little more info?  So you unpacked the tar.gz file, ran a ./configure, then make next?  Now, you just have to install it with 

```
sudo make install
```

---

### Post by Biggy on 2007-12-28
the followin intructions are ::

To compile this program run following commands:

$ qmake -project "LIBS += -lQtNetwork -lasound"
$ qmake
$ make

---

### Post by taurus on 2007-12-28
It doesn't say anything else after the make command?  Can you post the whole README or the INSTALL?

---

### Post by Biggy on 2007-12-28
This directory contains Skype Call Recorder for Linux (SCX Recorder).

The SCX Recorder is free software.  See the file COPYING
for copying permission.
Copyright (c) 2007 Andrei Borovsky <anb@symmetrica.net>

Files xmessages.cpp, xmessages.h, apiapplication.cpp, apiapplication.h 
may be modified and redistributed free of charge anrd without restriction
as long as their original copyright notices are preserved.

System Requirements

	Skype client
	Qt library 4.x
	ALSA sound system with asoundlib.h header file installed.

To compile this program run following commands:

$ qmake -project "LIBS += -lQtNetwork -lasound"
$ qmake
$ make

If you have both Qt 4.x and Qt 3.x installed, make sure you are using qmake that comes with Qt 4.x

There is compile script in this directory that does all this for you.

In order to install the program just copy the executable file named scx-recorder anywhere you want.
The excutable is self-contained and doesn't require any additional setup.
Start your Skype client and then start the SCX Recorder.
The dialog box will appear informing you that another program (scx-recorder) wants to connect to Skype.
Click the Yes button. Now you are ready to record your Skype calls.

---

### Post by taurus on 2007-12-28
I am looking at it on my machine right now.  Do you have qmake on your machine?   Any error message when you ran the first command from a terminal?

```
qmake -project "LIBS += -lQtNetwork -lasound"
```

---

### Post by Biggy on 2007-12-28
ok i ran the first command  < qmake -project "LIBS += -lQtNetwork -lasound" > in terminal and nothing hapen..

i ran < qmake > and give error :

WARNING: Failure to find: 2-1.9.92/gb.qt/src/CMenu.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CMessage.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CMouse.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CMovieBox.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CPanel.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CPicture.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CPictureBox.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CProgress.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CRadioButton.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CScreen.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CScrollBar.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CScrollView.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CSlider.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CSpinBox.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CSplitter.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CTabStrip.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CTextArea.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CTextBox.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CTrayIcon.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CTreeView.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CWatch.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CWatcher.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CWidget.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/CWindow.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/main.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/qtxembed.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt/src/x11.c
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt.kde/src/CApplication.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt.kde/src/CArrowButton.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt.kde/src/CColorBox.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt.kde/src/CDialog.cpp
WARNING: Failure to find: Gambas
WARNING: Failure to find: 2-1.9.92/gb.qt.kde/src/CURLLabel.cpp
etc....

---

### Post by taurus on 2007-12-28
Did you install "Qt library 4.x" since that is where the error message is generated?

---

