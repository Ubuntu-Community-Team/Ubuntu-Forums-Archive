---
title: "Installing Mutella"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Slorginvader on 2007-07-27
Hey, I tried to install Mutella (a p2p programthingie)
You have to install it with the ./configure stuff... (I'm not so experienced with this way of installing)
Anyway after the ./configure You have to typ make (as for as I know)
But I did get a (long) error:
> slorg@TaMSc:~/mutella-0.4.5$ make
make  all-recursive
make[1]: Map '/home/slorg/mutella-0.4.5' wordt binnengegaan
Making all in mutella
make[2]: Map '/home/slorg/mutella-0.4.5/mutella' wordt binnengegaan
Making all in docs
make[3]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt binnengegaan
Making all in en
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs/en' wordt binnengegaan
make[4]: Er hoeft niets gedaan te worden voor 'all'.
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs/en' wordt verlaten
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt binnengegaan
make[4]: Er hoeft niets gedaan te worden voor 'all-am'.
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt verlaten
make[3]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt verlaten
make[3]: Map '/home/slorg/mutella-0.4.5/mutella' wordt binnengegaan
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT uilocalsocket.o -MD -MP -MF ".deps/uilocalsocket.Tpo" -c -o uilocalsocket.o uilocalsocket.cpp; \
        then mv -f ".deps/uilocalsocket.Tpo" ".deps/uilocalsocket.Po"; else rm -f ".deps/uilocalsocket.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT gnumarkedfiles.o -MD -MP -MF ".deps/gnumarkedfiles.Tpo" -c -o gnumarkedfiles.o gnumarkedfiles.cpp; \
        then mv -f ".deps/gnumarkedfiles.Tpo" ".deps/gnumarkedfiles.Po"; else rm -f ".deps/gnumarkedfiles.Tpo"; exit 1; fi
gnumarkedfiles.cpp:127:2: let op: #warning MGnuMarkedFiles::RemoveFile() needs an update
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT uitextmode.o -MD -MP -MF ".deps/uitextmode.Tpo" -c -o uitextmode.o uitextmode.cpp; \
        then mv -f ".deps/uitextmode.Tpo" ".deps/uitextmode.Po"; else rm -f ".deps/uitextmode.Tpo"; exit 1; fi
uitextmode.cpp:814:46: let op: trigraph ??' genegeerd, gebruikt -trigraphs om ondersteuning aan te zetten
uitextmode.cpp:822:46: let op: trigraph ??' genegeerd, gebruikt -trigraphs om ondersteuning aan te zetten
uitextmode.cpp:864:45: let op: trigraph ??' genegeerd, gebruikt -trigraphs om ondersteuning aan te zetten
uitextmode.cpp:1080:110: let op: trigraph ??/ genegeerd, gebruikt -trigraphs om ondersteuning aan te zetten
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -D_REENTRANT -D_MIT_POSIX_THREADS -g  -O0 -MT sha1.o -MD -MP -MF ".deps/sha1.Tpo" -c -o sha1.o sha1.c; \
        then mv -f ".deps/sha1.Tpo" ".deps/sha1.Po"; else rm -f ".deps/sha1.Tpo"; exit 1; fi
cc1: let op: command line option "-fno-check-new" is valid for C++/ObjC++ but not for C
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT sha1thread.o -MD -MP -MF ".deps/sha1thread.Tpo" -c -o sha1thread.o sha1thread.cpp; \
        then mv -f ".deps/sha1thread.Tpo" ".deps/sha1thread.Po"; else rm -f ".deps/sha1thread.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT gnuwordhash.o -MD -MP -MF ".deps/gnuwordhash.Tpo" -c -o gnuwordhash.o gnuwordhash.cpp; \
        then mv -f ".deps/gnuwordhash.Tpo" ".deps/gnuwordhash.Po"; else rm -f ".deps/gnuwordhash.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT gnulogcentre.o -MD -MP -MF ".deps/gnulogcentre.Tpo" -c -o gnulogcentre.o gnulogcentre.cpp; \
        then mv -f ".deps/gnulogcentre.Tpo" ".deps/gnulogcentre.Po"; else rm -f ".deps/gnulogcentre.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT asyncdns.o -MD -MP -MF ".deps/asyncdns.Tpo" -c -o asyncdns.o asyncdns.cpp; \
        then mv -f ".deps/asyncdns.Tpo" ".deps/asyncdns.Po"; else rm -f ".deps/asyncdns.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT gnuwebcache.o -MD -MP -MF ".deps/gnuwebcache.Tpo" -c -o gnuwebcache.o gnuwebcache.cpp; \
        then mv -f ".deps/gnuwebcache.Tpo" ".deps/gnuwebcache.Po"; else rm -f ".deps/gnuwebcache.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT uiterminal.o -MD -MP -MF ".deps/uiterminal.Tpo" -c -o uiterminal.o uiterminal.cpp; \
        then mv -f ".deps/uiterminal.Tpo" ".deps/uiterminal.Po"; else rm -f ".deps/uiterminal.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT uiremote.o -MD -MP -MF ".deps/uiremote.Tpo" -c -o uiremote.o uiremote.cpp; \
        then mv -f ".deps/uiremote.Tpo" ".deps/uiremote.Po"; else rm -f ".deps/uiremote.Tpo"; exit 1; fi
uiremote.cpp:689:6: let op: #warning generate error page here
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT asyncproxysocket.o -MD -MP -MF ".deps/asyncproxysocket.Tpo" -c -o asyncproxysocket.o asyncproxysocket.cpp; \
        then mv -f ".deps/asyncproxysocket.Tpo" ".deps/asyncproxysocket.Po"; else rm -f ".deps/asyncproxysocket.Tpo"; exit 1; fi
asyncproxysocket.cpp:660:4: let op: #warning GetHostByName() call with no locking!
asyncproxysocket.cpp:911:2: let op: #warning I Guess This Will Fail On Bin Endian
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT messages.o -MD -MP -MF ".deps/messages.Tpo" -c -o messages.o messages.cpp; \
        then mv -f ".deps/messages.Tpo" ".deps/messages.Po"; else rm -f ".deps/messages.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT lineinput.o -MD -MP -MF ".deps/lineinput.Tpo" -c -o lineinput.o lineinput.cpp; \
        then mv -f ".deps/lineinput.Tpo" ".deps/lineinput.Po"; else rm -f ".deps/lineinput.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT rcobject.o -MD -MP -MF ".deps/rcobject.Tpo" -c -o rcobject.o rcobject.cpp; \
        then mv -f ".deps/rcobject.Tpo" ".deps/rcobject.Po"; else rm -f ".deps/rcobject.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT event.o -MD -MP -MF ".deps/event.Tpo" -c -o event.o event.cpp; \
        then mv -f ".deps/event.Tpo" ".deps/event.Po"; else rm -f ".deps/event.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -D_REENTRANT -D_MIT_POSIX_THREADS -g  -O0 -MT term_help.o -MD -MP -MF ".deps/term_help.Tpo" -c -o term_help.o term_help.c; \
        then mv -f ".deps/term_help.Tpo" ".deps/term_help.Po"; else rm -f ".deps/term_help.Tpo"; exit 1; fi
cc1: let op: command line option "-fno-check-new" is valid for C++/ObjC++ but not for C
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT mprintf.o -MD -MP -MF ".deps/mprintf.Tpo" -c -o mprintf.o mprintf.cpp; \
        then mv -f ".deps/mprintf.Tpo" ".deps/mprintf.Po"; else rm -f ".deps/mprintf.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -D_REENTRANT -D_MIT_POSIX_THREADS -g  -O0 -MT readline4fix.o -MD -MP -MF ".deps/readline4fix.Tpo" -c -o readline4fix.o readline4fix.c; \
        then mv -f ".deps/readline4fix.Tpo" ".deps/readline4fix.Po"; else rm -f ".deps/readline4fix.Tpo"; exit 1; fi
cc1: let op: command line option "-fno-check-new" is valid for C++/ObjC++ but not for C
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT asyncfile.o -MD -MP -MF ".deps/asyncfile.Tpo" -c -o asyncfile.o asyncfile.cpp; \
        then mv -f ".deps/asyncfile.Tpo" ".deps/asyncfile.Po"; else rm -f ".deps/asyncfile.Tpo"; exit 1; fi
asyncfile.cpp:201:3: let op: #warning This requires no requests to be sent before OPEN or ATTACH competes
asyncfile.cpp:271:5: let op: #warning call error notifiers here!!!
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT tstring.o -MD -MP -MF ".deps/tstring.Tpo" -c -o tstring.o tstring.cpp; \
        then mv -f ".deps/tstring.Tpo" ".deps/tstring.Po"; else rm -f ".deps/tstring.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT dir.o -MD -MP -MF ".deps/dir.Tpo" -c -o dir.o dir.cpp; \
        then mv -f ".deps/dir.Tpo" ".deps/dir.Po"; else rm -f ".deps/dir.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT inifile.o -MD -MP -MF ".deps/inifile.Tpo" -c -o inifile.o inifile.cpp; \
        then mv -f ".deps/inifile.Tpo" ".deps/inifile.Po"; else rm -f ".deps/inifile.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT property.o -MD -MP -MF ".deps/property.Tpo" -c -o property.o property.cpp; \
        then mv -f ".deps/property.Tpo" ".deps/property.Po"; else rm -f ".deps/property.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT byteorder.o -MD -MP -MF ".deps/byteorder.Tpo" -c -o byteorder.o byteorder.cpp; \
        then mv -f ".deps/byteorder.Tpo" ".deps/byteorder.Po"; else rm -f ".deps/byteorder.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT mui.o -MD -MP -MF ".deps/mui.Tpo" -c -o mui.o mui.cpp; \
        then mv -f ".deps/mui.Tpo" ".deps/mui.Po"; else rm -f ".deps/mui.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT gnusearch.o -MD -MP -MF ".deps/gnusearch.Tpo" -c -o gnusearch.o gnusearch.cpp; \
        then mv -f ".deps/gnusearch.Tpo" ".deps/gnusearch.Po"; else rm -f ".deps/gnusearch.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT mthread_unix.o -MD -MP -MF ".deps/mthread_unix.Tpo" -c -o mthread_unix.o mthread_unix.cpp; \
        then mv -f ".deps/mthread_unix.Tpo" ".deps/mthread_unix.Po"; else rm -f ".deps/mthread_unix.Tpo"; exit 1; fi
mthread_unix.cpp:147:1: let op: "_GNU_SOURCE" opnieuw gedefinieerd
<commandolijn>:1:1: let op: dit is de locatie van de eerdere definitie
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT asyncsocket.o -MD -MP -MF ".deps/asyncsocket.Tpo" -c -o asyncsocket.o asyncsocket.cpp; \
        then mv -f ".deps/asyncsocket.Tpo" ".deps/asyncsocket.Po"; else rm -f ".deps/asyncsocket.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT controller.o -MD -MP -MF ".deps/controller.Tpo" -c -o controller.o controller.cpp; \
        then mv -f ".deps/controller.Tpo" ".deps/controller.Po"; else rm -f ".deps/controller.Tpo"; exit 1; fi
controller.cpp:460:4: let op: #warning add a proper knownDB entry
gnushare.h:67: fout: ISO C++ forbids declaration of ‘MShareThread’ with no type
gnushare.h:67: fout: expected ‘;’ before ‘*’ token
make[3]: *** [controller.o] Fout 1
make[3]: Map '/home/slorg/mutella-0.4.5/mutella' wordt verlaten
make[2]: *** [all-recursive] Fout 1
make[2]: Map '/home/slorg/mutella-0.4.5/mutella' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/slorg/mutella-0.4.5' wordt verlaten
make: *** [all] Fout 2


So I tried to do the make install step anyway, that didn't work so I tried this again (in Root)

And I got the error again (only shorter):
> root@TaMSc:/home/slorg/mutella-0.4.5# make
make  all-recursive
make[1]: Map '/home/slorg/mutella-0.4.5' wordt binnengegaan
Making all in mutella
make[2]: Map '/home/slorg/mutella-0.4.5/mutella' wordt binnengegaan
Making all in docs
make[3]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt binnengegaan
Making all in en
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs/en' wordt binnengegaan
make[4]: Er hoeft niets gedaan te worden voor 'all'.
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs/en' wordt verlaten
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt binnengegaan
make[4]: Er hoeft niets gedaan te worden voor 'all-am'.
make[4]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt verlaten
make[3]: Map '/home/slorg/mutella-0.4.5/mutella/docs' wordt verlaten
make[3]: Map '/home/slorg/mutella-0.4.5/mutella' wordt binnengegaan
if g++ -DHAVE_CONFIG_H -I. -I. -I..  -I/usr/local/include  -D_REENTRANT -D_MIT_POSIX_THREADS -fno-exceptions -fno-check-new     -g  -O0 -MT controller.o -MD -MP -MF ".deps/controller.Tpo" -c -o controller.o controller.cpp; \
        then mv -f ".deps/controller.Tpo" ".deps/controller.Po"; else rm -f ".deps/controller.Tpo"; exit 1; fi
controller.cpp:460:4: let op: #warning add a proper knownDB entry
gnushare.h:67: fout: ISO C++ forbids declaration of ‘MShareThread’ with no type
gnushare.h:67: fout: expected ‘;’ before ‘*’ token
make[3]: *** [controller.o] Fout 1
make[3]: Map '/home/slorg/mutella-0.4.5/mutella' wordt verlaten
make[2]: *** [all-recursive] Fout 1
make[2]: Map '/home/slorg/mutella-0.4.5/mutella' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/slorg/mutella-0.4.5' wordt verlaten
make: *** [all] Fout 2
root@TaMSc:/home/slorg/mutella-0.4.5# 


Does anybody knows what to do? :confused:

ps. the terminal is in dutch, I hope you'll understand the error anyway....

---

### Post by Blutack on 2007-07-27
What is wrong with the version in the repos?  Is it too old?
If not run sudo apt-get install mutella

---

### Post by Slorginvader on 2007-07-28
Anyway, I ran sudo apt-get install mutella in the terminal (first sudo to become root than the other stuff)
That succesfully worked, but what know?

---

