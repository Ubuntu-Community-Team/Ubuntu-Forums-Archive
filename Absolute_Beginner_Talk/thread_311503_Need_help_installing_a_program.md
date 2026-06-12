---
title: "Need help installing a program"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by lucid on 2006-12-03
Hi,

I'm having trouble installing a program. As it isn't in the repositories I'm trying to use the install script that comes with.  From the Readme file:

"The archive (compressed with TAR and BZIP2) contains the source code and all necessary data files. The source code provided in this version has been adapted for Linux and might slighly differ from the Windows version. It has also been modified to use Qt3 (standard on Linux). So to compile it, you will need Qt3 development files."

I've installed the qt3 files through the repositories. The script stalls with make: command not found.

Any suggestions? :)

---

### Post by taurus on 2006-12-03
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```
That would install make, gcc, and a few other files you need to build something from source!

---

### Post by aysiu on 2006-12-03
Can you say what program it is?

---

### Post by lucid on 2006-12-03
Thanks for the reply. :)

The program is called Dragonflame and is found at [http://www.jrrvf.com/hisweloke/sindar/df20linux.html](http://www.jrrvf.com/hisweloke/sindar/df20linux.html)

It dates to 2004, so perhaps its age is a factor.

I've installed the build-essential and the scrip ran. Unfortunately it seemed to run a whole bunch of errors and ended with this:

QT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/in clude/qt3 -o moc_searchinterface.o moc_searchinterface.cpp
/usr/share/qt3/bin/moc sentenceline.h -o moc_sentenceline.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -D QT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/in clude/qt3 -o moc_sentenceline.o moc_sentenceline.cpp
In file included from sentenceline.h:22,
                 from moc_sentenceline.cpp:11:
centralwidget.h:32:19: error: qlist.h: No such file or directory
centralwidget.h:88: warning: unused parameter ‘built’
make[1]: *** [moc_sentenceline.o] Error 1
make[1]: Target `first' not remade because of errors.
make[1]: Leaving directory `/home/dragonflame_2-0_gnulinux/src'
make: *** [sub-src] Error 2
make: Target `first' not remade because of errors.
make: Leaving directory `/home/dragonflame_2-0_gnulinux'

---

### Post by aysiu on 2006-12-03
The webpage mentioned something about KDevelop3 > The archive (compressed with TAR and BZIP2) contains the source code, the Makefile, the kdevelop3 project, all necessary data files, and even a binary executable.

If you wish to rebuild the executable, the project can be opened with kdevelop3. This might not be necessary (make -k should also compile everything correctly). The source code provided in this version has been adapted for Linux and might slighly differ from the Windows version (code merging is postponed to a later release). It has also been modified to use Qt3 (standard on Linux). To recompile it, you will therefore also need the "qt3-dev" package (whereas "qt3" is sufficient to run the executable). I know it says it's not *necessary*, but that may be worth trying.

I wish I could be more help, but I don't compile apps from source.

---

### Post by sardion on 2006-12-03
You need to install the following packages:

sudo aptitude install libqt3-compat-headers libqt4-dev


I know this because I went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and did a search packages by contents and looked for qlist.h which is the missing file that caused the error.

Whenever you try to compile from source you are going to need -dev packages (which are the C code files to interface with the various libraries).  Basically, just try to compile stuff and if you a missing file error then go to packages.ubuntu.com and search for the file you need.

---

### Post by Sef on 2006-12-03
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

