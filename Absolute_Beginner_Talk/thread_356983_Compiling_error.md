---
title: "Compiling error"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by treehouse on 2007-02-09
So I'm trying to get Xpertmud to work. I tried to alien an rpm, but it crashes so I'm compiling from source. All the dependencies are satisfied, and I was told it'll run on gnome as long as I have the KDE libs installed. ./configure worked just fine, then I tried to make:

```

nick@nick-desktop:~/Desktop/xpertmud-3.1preview1$ sudo make
Password:
make  all-recursive
make[1]: Entering directory `/home/nick/Desktop/xpertmud-3.1preview1'
Making all in qextmdi
make[2]: Entering directory `/home/nick/Desktop/xpertmud-3.1preview1/qextmdi'
Making all in src
make[3]: Entering directory `/home/nick/Desktop/xpertmud-3.1preview1/qextmdi/src'
source='qextmdichildarea.cpp' object='qextmdichildarea.lo' libtool=yes \
        depfile='.deps/qextmdichildarea.Plo' tmpdepfile='.deps/qextmdichildarea.TPlo' \
        depmode=gcc3 /bin/sh ../../admin/depcomp \
        /bin/sh ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../qextmdi/include -I../../qextmdi/res -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -Wall -pedantic -Wno-long-long -g -DKDE_NO_COMPAT -DQT_NO_COMPAT  -c -o qextmdichildarea.lo `test -f 'qextmdichildarea.cpp' || echo './'`qextmdichildarea.cpp
../../qextmdi/include/qextmdidefines.h:91: error: extra ';'
make[3]: *** [qextmdichildarea.lo] Error 1
make[3]: Leaving directory `/home/nick/Desktop/xpertmud-3.1preview1/qextmdi/src'make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nick/Desktop/xpertmud-3.1preview1/qextmdi'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/Desktop/xpertmud-3.1preview1'
make: *** [all] Error 2
nick@nick-desktop:~/Desktop/xpertmud-3.1preview1$

```

I have no idea what these errors mean. Could anyone point me in the right direction?

---

### Post by mvaniersel on 2007-02-09
> 
../../qextmdi/include/qextmdidefines.h:91: error: extra ';'

This looks like an ordinary syntax error. Did you perhaps edit the file by accident? Could you paste qextmdidefines.h here, or at least the part around line 91?

---

### Post by treehouse on 2007-02-09
I didn't touch it.

Full file:
```

//----------------------------------------------------------------------------
//    filename             : qextmdidefines.h
//----------------------------------------------------------------------------
//    Project              : Qt MDI extension
//
//    begin                : 07/1999       by Szymon Stefanek as part of kvirc
//                                         (an IRC application)
//    changes              : 09/1999       by Falk Brettschneider to create an
//                                         stand-alone Qt extension set of
//                                         classes and a Qt-based library
//
//    copyright            : (C) 1999-2000 by Falk Brettschneider
//                                         and
//                                         Szymon Stefanek (stefanek@tin.it)
//    email                :  gigafalk@geocities.com (Falk Brettschneider)
//----------------------------------------------------------------------------
//
//----------------------------------------------------------------------------
//
//    This program is free software; you can redistribute it and/or modify
//    it under the terms of the GNU Library General Public License as
//    published by the Free Software Foundation; either version 2 of the
//    License, or (at your option) any later version.
//
//----------------------------------------------------------------------------
#ifndef _MDIDEFINES_H_
#define _MDIDEFINES_H_

#include <qglobal.h>

#define QEXTMDI_MDI_CHILDFRM_SEPARATOR 2
#define QEXTMDI_MDI_CHILDFRM_BORDER 3
#define QEXTMDI_MDI_CHILDFRM_DOUBLE_BORDER 6
#define QEXTMDI_MDI_CHILDFRM_MIN_WIDTH 130

//----------------------------------------------------------------------------
namespace QextMdi
{
   /** extent Qt events
      @see QCustomEvent, QEvent::User 
      <PRE>
      bool
      B_MyWidget::event( QEvent* e) {
         if( e->type() == QEvent::Type(QEvent::User + int(QextMdi::EV_Move))) {
            ...
         }
         ...
      }
      </PRE>
   */
   enum EventType {
      EV_Move=1,
      EV_DragBegin,
      EV_DragEnd,
      EV_ResizeBegin,
      EV_ResizeEnd
   };

   /**
   * During @ref QextMdiMainFrm::addWindow the enum AddWindowFlags is used to determine how the view is initialy being added to the MDI system
   */
   enum AddWindowFlags {
      /**
      * standard is: show normal, attached, visible, document view (not toolview). Maximize, Minimize, Hide adds
      * appropriately. Detach adds a view that appears toplevel, ToolWindow adds the view as tool view.
      * That means it is stay-on-top and toplevel. UseQextMDISizeHint should use the restore geometry of the
      * latest current top childframe but is not supported yet.
      */
      StandardAdd = 0,
      Maximize    = 1,
      Minimize    = 2,
      Hide        = 4,
      Detach      = 8,
      ToolWindow  = 16,
      UseQextMDISizeHint = 32
   };

   enum FrameDecor {
      Win95Look = 0,
      KDE1Look  = 1,
      KDE2Look  = 2,
      KDE2LaptopLook = 3
   };

   enum MdiMode {
      ToplevelMode   = 0,
      ChildframeMode = 1,
      TabPageMode    = 2
   };

}; //namespace


//----------------------------------------------------------------------------
#ifndef _DLL_IMP_EXP_MSG_
#   define _DLL_IMP_EXP_MSG_
#endif

#if defined(_OS_WIN32_) || defined(Q_OS_WIN32)
  /* QT linked libraries compiled with MSVC */
#  ifdef MAKEDLL_QEXTMDI
    /* for building qextmdi */
#   ifdef _DLL_IMP_EXP_MSG_
#     ifdef _DEBUG
#      pragma message ("  exporting C++ class to debug lib...")
#      else
#      pragma message ("  exporting C++ class to release lib...")
#      endif
#    endif
#    define DLL_IMP_EXP_QEXTMDICLASS  __declspec(dllexport)
#  else
    /* for including headers of qextmdi */
#    ifdef _DLL_IMP_EXP_MSG_
#      ifdef _DEBUG
#      pragma message ("  importing C++ class from qextmdi debug lib...")
#      else
#      pragma message ("  importing C++ class from qextmdi release lib...")
#      endif
#    endif
#    define DLL_IMP_EXP_QEXTMDICLASS  __declspec(dllimport)
#  endif
#else
#  define DLL_IMP_EXP_QEXTMDICLASS
#endif

#undef DLL_IMP_EXP_QEXTMDICLASS
#define DLL_IMP_EXP_QEXTMDICLASS

#endif //_MDIDEFINES_H_

```

Line 91 is:

*}; //namespace*

deleting the semicolon should make it work then?

---

### Post by po0f on 2007-02-09
treehouse,

[quote=treehouse]deleting the semicolon should make it work then?[/quote]

Yes.

---

### Post by treehouse on 2007-02-09
More frustration...I deleted it, did it again, deleted semicolons from a couple more files before a roablock. Then I found the svn had a newer version. Config goes smoothly and all goes well until I get another error I don't have any idea how to fix:

```

*** Warning: Linking the shared library libxmperlinterpreter.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portabl e!
make[5]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud/scriptin g/perl'
make[4]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud/scriptin g/perl'
Making all in python
make[4]: Entering directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud/scripti ng/python'
no ./createCallbacks.py ./sysinit_py.in < ../GuiScriptingBindings.h > AutoSysini t.py
/bin/sh: no: command not found
make[4]: *** [AutoSysinit.py] Error 127
make[4]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud/scriptin g/python'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud/scriptin g'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud/xpertmud'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/xpertmud/trunk/xpertmud'
make: *** [all] Error 2

```

Synaptic doesn't mention anything called 'no' I can install, so I assume it's a syntax error right off the bat, and I'm not sure what Error 127 means.

---

### Post by mvaniersel on 2007-02-09
Hmmm, that semicolon there is not necessary but it shouldn't give an error either. 

This build system seems very complicated. I recommend contacting the author directly.

---

### Post by po0f on 2007-02-09
mvaniersel,

The [project page](http://xpertmud.sourceforge.net/) hasn't been updated since early 2004.  :)


treehouse.

You might want to look into alternatives to this program.  It looks like this project is dead.

---

### Post by treehouse on 2007-02-09
Thanks for trying to help. I found a patched deb in the bowels of the internet.

---

### Post by Hiko96786 on 2007-05-11
Aloha,
    Where did you find the .deb? I would like to get this loaded as well. I am running it now through a VM in Windows. I also installed all the dependencies required and downloaded the latest svn but it dies during the make - Makefile.dist because the automake is the wrong version. 
Mahalo
Hiko

---

### Post by treehouse on 2008-04-15
Sorry to bump an ancient thread, but I never knew that Hiko had posted to it. The solution I found can be found [here](http://forums.achaea.com/index.php?s=&showtopic=28706&view=findpost&p=788232).

> 
add this to your /etc/apt/sources.list:
CODE
deb [http://www.informatik.uni-freiburg.de/~mechnich/dapper](http://www.informatik.uni-freiburg.de/~mechnich/dapper) ./

then:
CODE
sudo apt-get update && sudo apt-get install xpertmud


I am running edgy here at work and feisty at home. It works on both, even though they aren't dapper. Works great. Be sure to have perl/ruby installed if you intend to use the perl/ruby engine (obviously). I only use the perl engine though, not sure about ruby.

[http://www.informatik.uni-freiburg.de/~mechnich](http://www.informatik.uni-freiburg.de/~mechnich) also has information about patches so it will compile correctly on debian/ubuntu, etc.


I haven't payed attention to see if there are any updates, but I believe the dapper version is still functioning well, even if you can't get a more up to date version.

---

### Post by Hiko96786 on 2008-04-15
treehouse,
    Cool. I haven't really messed with it since then. I got svn access to the source and got it to compile under Fiest Fawn but it always got a segfault so I sort of walked away from the whole thing. Xpertmud was very cool for the btech muxes but I just couldn't get it to work right. I am thinking that when Hardy Heron comes out I will install it and try to rebuild it again.
Mahalo,
Edward

---

