---
title: "[SOLVED] Configuring the qt3file properly"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by PmDematagoda on 2007-08-29
I just downloaded a .tar.bz2 file, I extracted it and tried running ./configure. This did not work as I got a message saying that QTDIR environment variable was not set, I looked in the readme and set the QTDIR manually.

I tried running ./configure again and got this output:
```

configure: QMAKESPEC environment variable is not set - default will be used.
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking boost/smart_ptr.hpp usability... no
checking boost/smart_ptr.hpp presence... no
checking for boost/smart_ptr.hpp... no
configure: error: You need boost library to compile PDFedit
```

Obviously I can't continue with the installation, does anyone know why this happens?:confused:

---

### Post by dwhitney67 on 2007-08-30
It would appear at first glance that you need to install the boost libraries onto your system to be able to build whatever version of Qt that you have downloaded.

To get the boost libraries:

[FONT="Courier New"]$ sudo apt-get install boost-devel[/FONT]

If that does not work, then try:

[FONT="Courier New"]$ sudo apt-get install libboost-dev[/FONT]

I've seen references to both of these when doing a Google search.  I'm not sure which is correct.

---

### Post by PmDematagoda on 2007-08-30
Now it's telling me that I need boost iostreams library to compile it. Does anyone know where to find these?:confused:

---

### Post by dwhitney67 on 2007-08-31
Answer:   [http://www.google.com](http://www.google.com)




or
[FONT="Courier New"]
$ sudo apt-get install boost*-dev[/FONT]

---

### Post by PmDematagoda on 2007-08-31
Nope nothing, it says the package doesn't exist.:(

---

### Post by schorsch on 2007-08-31
```
sudo apt-get install libboost-iostreams-dev
```

---

### Post by PmDematagoda on 2007-08-31
Okay (sigh) after that I get another problem:-
```

Trying qmake: /usr/share/qt3/bin/qmake ... not valid
Trying qmake: qmake ... not valid
Trying qmake: qmake-qt3 ... not valid
Trying qmake: /usr/bin/qmake ... not valid
Trying qmake: /usr/lib/qt3/bin/qmake ... not valid
Failed to find qmake from QT3!
```

This is just the last part of the very long output and if anyone needs the whole output just ask me.
Really sorry for acting like a first-class noob but this is the first time i'm using a .tar.bz2 file to install programs, anyone tells me I can get it through the repositories I'm just saying I just want to know as much about linux as possible.

Now that you got through the boring speech let me end by saying I would appreciate any help.:lolflag:

---

### Post by schorsch on 2007-08-31
```
sudo apt-get install qt3-dev-tools
```

---

### Post by PmDematagoda on 2007-08-31
Thanks a lot for your help schorsch and dwhitney67 but now I hit a new obstacle:confused:,(The program i'm trying to install is pdfedit), when I type in the command "make" the process ends with this output:-

```
QOutputDevPixmap.cpp:26:21: error: qpixmap.h: No such file or directory
QOutputDevPixmap.cpp:27:20: error: qimage.h: No such file or directory
QOutputDevPixmap.h:40: error: &#8216;QImage&#8217; does not name a type
QOutputDevPixmap.h:43: error: &#8216;QImage&#8217; does not name a type
QOutputDevPixmap.cpp: In constructor &#8216;QOutputDevPixmap::QOutputDevPixmap(Guchar*)&#8217;:
QOutputDevPixmap.cpp:40: error: class &#8216;QOutputDevPixmap&#8217; does not have any field named &#8216;m_image&#8217;
QOutputDevPixmap.cpp: In member function &#8216;virtual void QOutputDevPixmap::endPage()&#8217;:
QOutputDevPixmap.cpp:63: error: &#8216;m_image&#8217; was not declared in this scope
QOutputDevPixmap.cpp:79: error: &#8216;m_image&#8217; was not declared in this scope
QOutputDevPixmap.cpp:79: error: &#8216;uchar&#8217; was not declared in this scope
QOutputDevPixmap.cpp:79: error: expected primary-expression before &#8216;)&#8217; token
QOutputDevPixmap.cpp:79: error: &#8216;QImage&#8217; has not been declared
QOutputDevPixmap.cpp:79: error: &#8216;QImage&#8217; was not declared in this scope
make[2]: *** [QOutputDevPixmap.o] Error 1
make[2]: Leaving directory `/home/pramod/pdfedit-0.3.2/src/kpdf-kde-3.3.2'
make[1]: *** [qoutputdevices] Error 2
make[1]: Leaving directory `/home/pramod/pdfedit-0.3.2/src'
make: *** [src] Error 2

```

Do you know the solution to this? I can give you the whole output if you want.

---

### Post by schorsch on 2007-08-31
Where did you get the source file from? Perhaps I can do a parallel install ...

---

### Post by PmDematagoda on 2007-08-31
Here's the link. Hope you have better luck with it than I did.

[http://sourceforge.net/project/showfiles.php?group_id=177354](http://sourceforge.net/project/showfiles.php?group_id=177354)

---

### Post by schorsch on 2007-08-31
BTW: If you do not mind to use a slightly older version of pdfedit I just build a .deb-package from an .rpm-package via alien for 32 bit architecture (pdfedit_0.3.1-44.4_i386.deb).

---

### Post by PmDematagoda on 2007-08-31
Thanks a lot that would be great help!!:)

By the way if it's not too much trouble for you, could you just post the method by which you installed Alien and compiled the .deb package?

---

### Post by schorsch on 2007-08-31
First you have to install the package alien:
```
sudo apt-get install alien
```
After that you have to find the rpm. I found it [here]("http://software.opensuse.org/search")
The last step is also simple:
```
sudo alien pdfedit-0.3.1-43.4.i586.rpm
sudo dpkg -i pdfedit_0.3.1-44.4_i386.deb
```
That's all! You will find the icon under "Applications --> Office" when running Gnome.

... and I am still getting the same errors as you ....

---

### Post by schorsch on 2007-08-31
Finally I got it compiled from the sources. There were two things missing:
```
sudo ln -s /usr/include/qt3/ /usr/share/qt3/include
sudo apt-get install libqt3-mt-dev
```
After that the compilation was successful.
In the last step I did not do a "make install" as this makes it hard to remove the program if you want to. I used the follwing command instead:
```
sudo checkinstall -exclude=/bin,/lib,/usr/lib,/usr/share/qt3
```
This has the advantage that a .deb-package is created and installed and this package can be removed easily by the package manager. The command "checkinstall" is available after installing the package "checkinstall"

---

### Post by PmDematagoda on 2007-08-31
It worked, thanks a lot schorsch, I owe you one, I think the problem with the latest pdfedit is that it need KDE to work, because I saw a few files that do concern KDE, I know that even KDE applications work on gnome as well, but it doesn't seem to apply to the latest pdfedit.

Okay you proved me wrong schorsch.

---

### Post by schorsch on 2007-08-31
Glad to hear that. Could you please mark this thread as solved as this may help others, too?

---

### Post by PmDematagoda on 2007-08-31
Done and done. Amazing how this thread came to address both qt3 configuration and pdfedit installation isn't it?:lolflag:

---

### Post by dwhitney67 on 2007-08-31
PmDematagoda - I'm sure that you are find the installation of Qt to be somewhat frustrating (compliment Ubuntu for that; with Fedora Core it is a lot easier).  Are you attempting to build a particular version?  'schorsch' suggested that you get Qt from the repos using apt-get.  Is this not an option?  Are you trying to build a particular version that is not available in the repos?

Anyhow, the latest problem you are having would initially appear to be issues with the source code.  However I doubt it is.  Since the first part of your build did not appear to succeed, it is difficult to really say what the problem is.

I have built Qt-3.2.3 countless times (yes it is an ancient version) and before I can begin building the source code, it needs to be configured.  I'm sure the same applies to your version.  Did you run 'configure' before you started your exercise of building Qt??

These are the typical steps of building Qt (well, at least for Qt-3.2.3):

1. Obtain source from trolltech.com

2. Build as follows:

[FONT="Courier New"]$ tar xjvf qt-<version>.tar.bz2
$ cd qt-<version>
$ ./configure <config options>
$ make
$ sudo make install <install options>[/FONT]

With Qt-3.2.3 there is a need to specify the LD_LIBRARY_PATH during the 'make' and 'make install' phases, so in actuality the last two steps actually look like:
[FONT="Courier New"]
$ LD_LIBRARY_PATH=`pwd`/lib make
$ sudo LD_LIBRARY_PATH=`pwd`/lib make install <install options>[/FONT]

The instructions above may or may not be similar for the version you are installing.  Read carefully the **qt-<version>/INSTALL** file before proceeding with anything.

And if you continue to seek help here, at least specify what version of Qt you are trying to build and where you obtained the source package.

---

### Post by schorsch on 2007-08-31
The title of the thread is a little bit misleading. He did not want to compile QT but the application "pdfedit" ... ;-) And this worked with the version from the repos.

---

### Post by PmDematagoda on 2007-09-02
Sorry for the misleading topic guys, I wasn't sure if qt3 was a file or directory, but thanks for your advice dwhitney67 I'm sure I could use your advice later on. I sure learned a lot about installing stuff on linux thanks to you guys, thanks especially to dwhitney67 and schorsch, if you guys have any problems I will try my best to help you out.:)

P.S.I think i may have qt4 as well because I saw that directory in the same location qt3 is, will have to learn more about linux and it's ways of installing stuff.

---

