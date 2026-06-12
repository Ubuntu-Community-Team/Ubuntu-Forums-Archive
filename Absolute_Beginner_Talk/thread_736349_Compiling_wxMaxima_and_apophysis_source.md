---
title: "Compiling wxMaxima and apophysis source"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by djowtlawz on 2008-03-26
Hi I have these programs and only have the source for Apophysis - (Dephi7/Pascal) And I tried to configure and make wxMaxima as the instructions in its file says but I get the fowllowing messages:

```
root@BLyons:/home/brendon/Desktop/wxMaxima-0.7.4# make
Making all in src
make[1]: Entering directory `/home/brendon/Desktop/wxMaxima-0.7.4/src'
make  all-am
make[2]: Entering directory `/home/brendon/Desktop/wxMaxima-0.7.4/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DwxUSE_GUI=0 -pthread -I/usr/include/libxml2 -DPREFIX=\"/usr/local\" -g -O2 -MT CommandLine.o -MD -MP -MF ".deps/CommandLine.Tpo" -c -o CommandLine.o CommandLine.cpp; \
        then mv -f ".deps/CommandLine.Tpo" ".deps/CommandLine.Po"; else rm -f ".deps/CommandLine.Tpo"; exit 1; fi
BTextCtrl.h:26: error: expected class-name before ‘{’ token
BTextCtrl.h:31: error: expected ‘,’ or ‘...’ before ‘&’ token
BTextCtrl.h:33: error: ISO C++ forbids declaration of ‘wxPoint’ with no type
BTextCtrl.h:48: error: ‘wxKeyEvent’ has not been declared
CommandLine.h:33: error: expected ‘,’ or ‘...’ before ‘&’ token
CommandLine.h:35: error: ISO C++ forbids declaration of ‘wxPoint’ with no type
CommandLine.h:52: error: ‘wxKeyEvent’ has not been declared
CommandLine.cpp:40: error: expected ‘,’ or ‘...’ before ‘&’ token
CommandLine.cpp:42: error: ISO C++ forbids declaration of ‘wxPoint’ with no type
CommandLine.cpp: In constructor ‘CommandLine::CommandLine(wxWindow*, wxWindowID, const wxString&, int)’:
CommandLine.cpp:42: error: ‘pos’ was not declared in this scope
CommandLine.cpp:42: error: ‘size’ was not declared in this scope
CommandLine.cpp:42: error: ‘style’ was not declared in this scope
CommandLine.cpp: At global scope:
CommandLine.cpp:118: error: variable or field ‘FilterLine’ declared void
CommandLine.cpp:118: error: ‘int CommandLine::FilterLine’ is not a static member of ‘class CommandLine’
CommandLine.cpp:118: error: ‘wxKeyEvent’ was not declared in this scope
CommandLine.cpp:118: error: ‘event’ was not declared in this scope
CommandLine.cpp:119: error: expected ‘,’ or ‘;’ before ‘{’ token
CommandLine.cpp:235: error: ‘wxKeyEventHandler’ was not declared in this scope
make[2]: *** [CommandLine.o] Error 1
make[2]: Leaving directory `/home/brendon/Desktop/wxMaxima-0.7.4/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/brendon/Desktop/wxMaxima-0.7.4/src'
make: *** [all-recursive] Error 1
```

I am not sure what I am doing wrong with making wxMaxima but help would be greatly appreciated.

Apophysis:

I have PASCAL compilers but nothing seems to do the job, I have seen the section with it pointing to use WINE but that is slow, choppy and many tools are not even there. So help with compiling this would be great.

Thank You in Advance

---

### Post by mc4man on 2008-03-26
I would make sure you have these
python-wxgtk2.8 ,  python-wxtools  , python-wxaddons  , wx2.8-i18n 
and if so add
libwxgtk2.8-dev
edit: - above for wxmaxima  (before installing you may want to install repo ver. first to satisfy install /run deps  then uninstall wxmaxima before installing your built version

---

