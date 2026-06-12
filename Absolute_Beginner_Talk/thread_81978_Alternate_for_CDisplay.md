---
title: "Alternate for CDisplay"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by the_purulent on 2005-10-25
I used a program in windows for viewing comic books that were stored in .cbr files.  The program was called CDisplay.  Anyone know of a linux alternative that can load images from zip archives?  Right now I use GQview but I have to unzip all the files to view them first, which is a huge pain.

---

### Post by the_purulent on 2005-10-26
bump!

---

### Post by jrw6 on 2005-10-26
What you want is [Comical]("http://comical.sourceforge.net/").  You'll have to compile it yourself, but it's pretty good.  Don't forget to apt-get zip unzip, rar and unrar so it can open those file types.

EDIT:  I noticed the links on their homepage are leading to error pages.  Try [here]("http://sourceforge.net/project/showfiles.php?group_id=98800&package_id=105837").

---

### Post by the_purulent on 2005-10-27
Awesome! This is perfect.  Thanks you
I may need a little help compiling, if so I'll come back and bug you again.

---

### Post by the_purulent on 2005-10-29
So I have the .tar.gz source file now...  but I am very new to compiling programs... I know it has to be turned into a .deb and then installed but I don't know how to do it :(
Any help would be greatly appreciated.

---

### Post by thinhlegolas on 2005-10-29
Uncompress your tar file, go to the directory to read the README or INSTALL file... usually the standard procedure is 
1) ./configure
2) make
3) make install

Hope that helps

---

### Post by the_purulent on 2005-10-29
The readme has no instructions in it for installation...

---

### Post by thinhlegolas on 2005-10-29
How doing step 1->3 as above, it should be the standard procedure

---

### Post by the_purulent on 2005-10-29
```

root@lordpurulent:/home/clayton/My Downloads/comical# sudo ./configure
sudo: ./configure: command not found

root@lordpurulent:/home/clayton/My Downloads/comical# sudo make
sudo: make: command not found

root@lordpurulent:/home/clayton/My Downloads/comical# sudo make install
sudo: make: command not found

```

Do I need to have some development or 'make' libraries or something installed first?

---

### Post by thinhlegolas on 2005-10-29
try comical 4.0, other versions don't have ./configure
[http://prdownloads.sourceforge.net/comical/comical-0.4.tar.gz?use_mirror=switch](http://prdownloads.sourceforge.net/comical/comical-0.4.tar.gz?use_mirror=switch)

More help is here [http://www.sketchyorigins.com/comics/showthread.php?t=6496](http://www.sketchyorigins.com/comics/showthread.php?t=6496)
:)

---

### Post by the_purulent on 2005-10-29
```

root@lordpurulent:/home/clayton/My Downloads# cd comical-0.4
root@lordpurulent:/home/clayton/My Downloads/comical-0.4# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
root@lordpurulent:/home/clayton/My Downloads/comical-0.4# make
bash: make: command not found
root@lordpurulent:/home/clayton/My Downloads/comical-0.4# sudo make install
sudo: make: command not found
root@lordpurulent:/home/clayton/My Downloads/comical-0.4# sudo make
sudo: make: command not found
root@lordpurulent:/home/clayton/My Downloads/comical-0.4# sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

Now I get this... and make will not work afterwards...

---

### Post by thinhlegolas on 2005-10-30
Sorry, been busy the whole day

Since you're compiling the program from source, you need to have C compiler and C++ compiler and some more...

Use Synaptic, install gcc, c++, g++ ...

---

### Post by Mustard on 2005-10-30
Make sure you install the 'build-essential' package.

```
sudo apt-get install build-essential
```

---

### Post by the_purulent on 2005-10-30
```

onfig
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking wxWindows version... ./configure: line 8238: wx-config: command not found
not found
configure: error: wxWindows is required. Try --with-wx-config.
root@lordpurulent:/home/clayton/My Downloads/comical-0.4#

```

Now I get this lol  I've installed all of the packages you suggested...

---

### Post by Mustard on 2005-10-30
Type in terminal

```
apt-cache search wxWindows
```

...and take a punt on which package or packages you need to install to fulfil your missing dependency.

---

### Post by the_purulent on 2005-10-31
Ok, I finally got a make file, but when i try to make I get another problem:

```

root@lordpurulent:/home/clayton/My Downloads/comical-0.4# sudo make
Making all in src
make[1]: Entering directory `/home/clayton/My Downloads/comical-0.4/src'
g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"comical\" -DVERSION=\"0.4\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -I. -I.    -Wall -g -fexceptions -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D_LARGEFILE_SOURCE=1 -DNO_GCC_PRAGMA  -Wall -g -fexceptions -Wall -g -fexceptions -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D_LARGEFILE_SOURCE=1 -DNO_GCC_PRAGMA -c ComicalApp.cpp
ComicalApp.cpp: In constructor &#8216;MainFrame::MainFrame(const wxString&, const wxPoint&, const wxSize&, long int)&#8217;:
ComicalApp.cpp:64: error: no matching function for call to &#8216;wxLogWindow::wxLogWindow(MainFrame* const, const char [12], bool, bool)&#8217;
/usr/include/wx-2.6/wx/generic/logg.h:124: note: candidates are: wxLogWindow::wxLogWindow(const wxLogWindow&)
/usr/include/wx-2.6/wx/generic/logg.h:94: note:                 wxLogWindow::wxLogWindow(wxWindow*, const wxChar*, bool, bool)
ComicalApp.cpp:67: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;void wxLogVerbose(const wxChar*, ...)&#8217;
ComicalApp.cpp:115: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;void wxLogVerbose(const wxChar*, ...)&#8217;
ComicalApp.cpp:117: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;void wxLogVerbose(const wxChar*, ...)&#8217;
ComicalApp.cpp: At global scope:
ComicalApp.cpp:124: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:125: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:126: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:127: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:128: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:129: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:130: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:131: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp:144: error: invalid static_cast from type &#8216;void (MainFrame::*)()&#8217; to type &#8216;void (wxEvtHandler::*)(wxCommandEvent&)&#8217;
ComicalApp.cpp: In member function &#8216;void MainFrame::OnAbout(wxCommandEvent&)&#8217;:
ComicalApp.cpp:155: error: conversion from &#8216;const char [1]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
ComicalApp.cpp:158: error: conversion from &#8216;const char [1]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
ComicalApp.cpp:158: error: conversion from &#8216;const char [9]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
ComicalApp.cpp: In member function &#8216;void MainFrame::OnOpen()&#8217;:
ComicalApp.cpp:175: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;wxString wxFileSelector(const wxChar*, const wxChar*, const wxChar*, const wxChar*, const wxChar*, int, wxWindow*, int, int)&#8217;
ComicalApp.cpp: In member function &#8216;bool MainFrame::OpenFile(wxString)&#8217;:
ComicalApp.cpp:195: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".CBR"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp:195: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".RAR"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp:197: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".CBZ"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp:197: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".ZIP"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp:199: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".CBB"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp:199: error: ambiguous overload for &#8216;operator==&#8217; in &#8216;wxString::Upper() const() == ".BZ2"&#8217;
/usr/include/wx-2.6/wx/string.h:1409: note: candidates are: bool operator==(const wxString&, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1413: note:                 bool operator==(const wxChar*, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1447: note:                 bool operator==(const wxString&, const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:1482: note:                 bool operator==(wxChar, const wxString&) <near match>
/usr/include/wx-2.6/wx/string.h:1483: note:                 bool operator==(const wxString&, wxChar) <near match>
/usr/include/wx-2.6/wx/longlong.h:906: note:                 bool operator==(long int, const wxLongLong&) <near match>
/usr/include/wx-2.6/wx/longlong.h:919: note:                 bool operator==(long unsigned int, const wxULongLong&) <near match>
ComicalApp.cpp: In member function &#8216;void MainFrame::OnGoTo()&#8217;:
ComicalApp.cpp:248: error: ambiguous overload for &#8216;operator=&#8217; in &#8216;message = "Enter a page number from 0 to "&#8217;
/usr/include/wx-2.6/wx/string.h:626: note: candidates are: wxString& wxString::operator=(int) <near match>
/usr/include/wx-2.6/wx/string.h:845: note:                 wxString& wxString::operator=(wxChar) <near match>
/usr/include/wx-2.6/wx/string.h:859: note:                 wxString& wxString::operator=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.6/wx/string.h:610: note:                 wxString& wxString::operator=(const wxString&) <near match>
ComicalApp.cpp:249: error: conversion from &#8216;const char [5]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
ComicalApp.cpp:249: error: conversion from &#8216;const char [11]&#8217; to &#8216;const wxString&#8217; is ambiguous
/usr/include/wx-2.6/wx/string.h:642: note: candidates are: wxString::wxString(wxChar, size_t) <near match>
/usr/include/wx-2.6/wx/string.h:632: note:                 wxString::wxString(int) <near match>
ComicalApp.cpp: In member function &#8216;void MainFrame::OnFull(wxCommandEvent&)&#8217;:
ComicalApp.cpp:258: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;void wxLogVerbose(const wxChar*, ...)&#8217;
ComicalApp.cpp:259: error: cannot convert &#8216;const char*&#8217; to &#8216;const wxChar*&#8217; for argument &#8216;1&#8217; to &#8216;void wxLogVerbose(const wxChar*, ...)&#8217;
make[1]: *** [ComicalApp.o] Error 1
make[1]: Leaving directory `/home/clayton/My Downloads/comical-0.4/src'
make: *** [all-recursive] Error 1

```

This is alot of work :) But interesting to try for the first time.  And it will be worth it in the end I hope lol
Thanks for all the help guys.

---

### Post by Moonbuzz on 2005-10-31
Sorry I didn't get here before all this...

There's a small and quite nice program called [Comix]("http://comix.sourceforge.net/"). It's fairly good, slightly less features than CDisplay, but it does the job right, and with the 1.4 version, I can easily recommend it (it didn't save preferences in previous versions).

No need to compile, btw, the tar.bz file can be extracted, and placed anywhere you wish (home folder, or wherever you want to run your program from). Just place the Python script file "comix" somewhere in your path (ex. /usr/local/bin/ - you'll need sudo to do this) and make sure it is executable before you run it (chmod +x). Place comix.desktop (might be shown as "Comix") in /usr/local/share/applications/ and comix.png in /usr/local/share/pixmaps/.

---

### Post by the_purulent on 2005-10-31
That sounds alot easier to me :)
I'll give that a shot when I get thome. Thanks!

---

### Post by Shampyon on 2006-10-04
THREAD NECROMANCY!

I figured it's better to add to an established thread (even one over a year old) rather than create a new one.

The Windows version of CDisplay usually works fine, and Comix is a great alternative. A few minutes ago, though, I found a shell script that provides a cbr reader:

[http://www.shii.org/linux](http://www.shii.org/linux)

Hope it's of use to someone!

---

### Post by PCFascist on 2007-06-27
comix worked great for me. I would also suggest installing unrar from apt-get.

This should be part of the Ubuntu supported packages....

---

### Post by ogiso_akpolokpolo on 2008-05-07
Thanks for the heads-up jrw6! Comical is exactly what I was looking for in a linux alternative to CDisplay

---

### Post by mburner21 on 2008-06-11
Comix is now available from the application servers, make sure you have the unrar package

---

