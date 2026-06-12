---
title: "problem with compiling kydpdict"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by johny_ on 2007-11-14
Hello:)

I'm pretty new to this forum, but I've already stumbled across some thread before, so just saying a Hello to all those people who help:)

My problem regards a compilation of a dictionary layout, the main version is for windows but a linux clon exist as well.

These are steps i've taken so far:

Just downloaded the sources, untared them cd to the dir and runed "./configure", which firstly failed screaming out about wrong QT dir.

I runed it then in this way > /configure --with-qt-includes=/usr/include/qt3/ --with-qt-libraries=/usr/lib/qt3/, and....waaaa it worked and created the makefile.

Now however, when I invoke "make"

johny@johny-laptop:/usr/src/kydpdict-0.6.5$ make
make -C src
make[1]: Wej&#347;cie do katalogu `/usr/src/kydpdict-0.6.5/src'
Creating dependency information
gcc -MM -MG  -I/usr/include/qt3/ kdynamictip.cpp kydpconfig.cpp kydpdict.cpp main.cpp ydpdictionary.cpp ydpconfigure.cpp dock_widget.cpp > .depend
make[2]: Wej&#347;cie do katalogu `/usr/src/kydpdict-0.6.5/src'
g++ -c main.cpp -I/usr/include/qt3/ -g -O2 -Wall -DVERSION=\"0.6.5\" -DLOCALEDIR=\"/usr/local/share/kydpdict\"
g++ -c kydpconfig.cpp -I/usr/include/qt3/ -g -O2 -Wall -DVERSION=\"0.6.5\" -DKYDPDATADIR=\"/usr/local/share/kydpdict/\"
g++ -c kdynamictip.cpp -I/usr/include/qt3/ -g -O2 -Wall -DVERSION=\"0.6.5\"
g++ -c kydpdict.cpp  -I/usr/include/qt3/ -g -O2 -Wall -DVERSION=\"0.6.5\"
dock_widget.h:23: error: ISO C++ forbids declaration of &#8216;TrayHint&#8217; with no type
dock_widget.h:23: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
make[2]: *** [kydpdict.o] B&#322;&#261;d 1
make[2]: Opuszczenie katalogu `/usr/src/kydpdict-0.6.5/src'
make[1]: *** [all] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/usr/src/kydpdict-0.6.5/src'
make: *** [all] B&#322;&#261;d 2

It fails with the error above:(

Some translation to the output;)

"Opuszczenie katalogu" means "leaving dir"
"B&#322;ad" means error
"Wejscie do katalogu" means "entering dir"

I know that there will be people who will understand without a problem the output above, the translation was for them "saying" me to go to my local language support team or forum..

I myself, don't know neither C , nor C++ enough for finding out what's wrong..

Here is the makefile

PACKAGE_NAME=kydpdict
PACKAGE_VERSION=0.6.5
CC=gcc
CXX=g++
CXXFLAGS=-g -O2 -Wall -DVERSION=\"$(PACKAGE_VERSION)\"
MOC=/usr/bin/moc
LUPDATE=/usr/bin/lupdate
LRELEASE=/usr/bin/lrelease
QT_LIB=-lqt-mt
QT_LIBS=-L/usr/lib/qt3/
QT_INCLUDE=-I/usr/include/qt3/
X_CFLAGS=
X_LIBS=
X_LIB=-lX11
HAVE_X11=yes
prefix=/usr/local
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
datadir=${prefix}/share

LOCALEDIR=$(datadir)/$(PACKAGE_NAME)
KYDPDATADIR=$(datadir)/$(PACKAGE_NAME)/

# Do not touch below and above this line

OBJECTS = kdynamictip.cpp kydpconfig.cpp kydpdict.cpp main.cpp ydpdictionary.cpp ydpconfigure.cpp

OOBJECTS = main.o kydpconfig.o kdynamictip.o kydpdict.o ydpdictionary.o ydpdictionary.moc.o \
    ydpconfigure.o ydpconfigure.moc.o kydpdict.moc.o

ifeq ($(HAVE_X11),yes)
OBJECTS  += dock_widget.cpp
OOBJECTS += dock_widget.o dock_widget.moc.o
endif

ifeq (.depend,$(wildcard .depend))
all :     kydpdict translation
include .depend
else
all:    depend
    @$(MAKE) all
endif

main.o:
        $(CXX) -c main.cpp $(QT_INCLUDE) $(CXXFLAGS) -DLOCALEDIR=\"$(LOCALEDIR)\"

kydpdict.moc.o: kydpdict.h
        $(MOC) kydpdict.h -o kydpdict.moc.cpp
        $(CXX) -c kydpdict.moc.cpp $(QT_INCLUDE) $(CXXFLAGS)

kydpdict.o:
        $(CXX) -c kydpdict.cpp $(X_CFLAGS) $(QT_INCLUDE) $(CXXFLAGS)

ydpdictionary.o: tips.h
        $(CXX) -c ydpdictionary.cpp $(QT_INCLUDE) $(CXXFLAGS)

ydpdictionary.moc.o: ydpdictionary.h
        $(MOC) ydpdictionary.h -o ydpdictionary.moc.cpp
        $(CXX) -c ydpdictionary.moc.cpp $(QT_INCLUDE) $(CXXFLAGS)

ydpconfigure.o:
        $(CXX) -c ydpconfigure.cpp $(QT_INCLUDE) $(CXXFLAGS)

ydpconfigure.moc.o: ydpconfigure.h
        $(MOC) ydpconfigure.h -o ydpconfigure.moc.cpp
        $(CXX) -c ydpconfigure.moc.cpp $(QT_INCLUDE) $(CXXFLAGS)

kydpconfig.o:
        $(CXX) -c kydpconfig.cpp $(QT_INCLUDE) $(CXXFLAGS) -DKYDPDATADIR=\"$(KYDPDATADIR)\"

kdynamictip.o:
        $(CXX) -c kdynamictip.cpp $(QT_INCLUDE) $(CXXFLAGS)

ifeq ($(HAVE_X11),yes)
dock_widget.o:
        $(CXX) -c dock_widget.cpp $(X_CFLAGS) $(QT_INCLUDE) $(CXXFLAGS)

dock_widget.moc.o: dock_widget.h
        $(MOC) dock_widget.h -o dock_widget.moc.cpp
        $(CXX) -c dock_widget.moc.cpp $(QT_INCLUDE) $(CXXFLAGS)
endif

kydpdict:     $(OOBJECTS)
        $(CXX) $(OOBJECTS) $(QT_LIBS) $(QT_LIB) $(X_LIBS) $(X_LIB) $(CXXFLAGS) -o kydpdict

translation: kydpdict.pro
    $(LUPDATE) kydpdict.pro
    $(LRELEASE) kydpdict.pro

install: kydpdict
        install -s -m 755 kydpdict $(DESTDIR)$(bindir)
        install -m 755 -d $(DESTDIR)$(LOCALEDIR)
        install -m 755 -d $(DESTDIR)$(KYDPDATADIR)
        install -m 644 kydpdict_pl.qm $(DESTDIR)$(LOCALEDIR)

clean:
        -rm *.o *.moc.cpp *.qm .depend
        -rm kydpdict

distclean: clean
        -rm Makefile

depend dep:    $(OBJECTS:.o=.cpp)
    @echo "Creating dependency information"
    $(CC) -MM -MG $(X_CFLAGS) $(QT_INCLUDE) $^ > .depend


I think it's the case of configure and the libraries paths I've put intoit, but how come it hadn't failed before?:?

I'd be really greatfull for any help and info on the issue

---

