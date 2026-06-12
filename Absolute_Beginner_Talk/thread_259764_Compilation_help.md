---
title: "Compilation help"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by abelIAN on 2006-09-17
I need to install the Klusters application ([http://klusters.sourceforge.net/](http://klusters.sourceforge.net/)) onto Ubuntu Dapper, installed on a Macbook. I have tried to compile it, but I can't get to the make stage because I don't have all the tools available. Unfortunately, the problem is cryptically, "Can't find X includes. Please check your installation and add the correct paths!" What X includes do I need?

Thanks, everyone.

---

### Post by Najand on 2006-09-17
Try to install build-essential and then try again:
```

sudo aptitude install build-essential

```
There is a PPC version so there is no problem with filesystem architecture.

---

### Post by abelIAN on 2006-09-17
I've installed build-essentials. And I've gotten past the "X includes" problem by installing kdelibs4. But, I can't make or make install, because there are some errors. Here is the terminal readout:

```
make  all-recursive
make[1]: Entering directory `/home/fahim/Desktop/klusters-1.6.1'
Making all in doc
make[2]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/doc'
Making all in .
make[3]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/doc'
Making all in en
make[3]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/doc/en'
Making all in Images
make[4]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/doc/en/Images'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/doc/en/Images'
make[4]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/doc/en'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/doc/en'
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/doc/en'
make[2]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/doc'
Making all in po
make[2]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/po'
Making all in src
make[2]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/src'
Making all in cursors
make[3]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/src/cursors'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src/cursors'
Making all in icons
make[3]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/src/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src/icons'
make[3]: Entering directory `/home/fahim/Desktop/klusters-1.6.1/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../src/cursors -I../src/icons -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include/libxml2  -DQT_THREAD_SUPPORT  -D_REENTRANT -pedantic -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT klusters.o -MD -MP -MF ".deps/klusters.Tpo" -c -o klusters.o klusters.cpp; \
        then mv -f ".deps/klusters.Tpo" ".deps/klusters.Po"; else rm -f ".deps/klusters.Tpo"; exit 1; fi
sortabletable.h:75: warning: unused parameter ‘nbOfRows’
sortabletable.h:75: warning: unused parameter ‘nbOfColumns’
data.h:690: warning: unused parameter ‘nbSampleSpikes’
data.h:690: warning: unused parameter ‘nbTimeFrameSpikes’
viewwidget.h:92: warning: unused parameter ‘dimensionX’
viewwidget.h:92: warning: unused parameter ‘dimensionY’
viewwidget.h:98: warning: unused parameter ‘clusterId’
viewwidget.h:98: warning: unused parameter ‘active’
viewwidget.h:106: warning: unused parameter ‘clusterId’
viewwidget.h:106: warning: unused parameter ‘active’
viewwidget.h:113: warning: unused parameter ‘clusterId’
viewwidget.h:113: warning: unused parameter ‘active’
viewwidget.h:122: warning: unused parameter ‘fromClusters’
viewwidget.h:122: warning: unused parameter ‘clusterId’
viewwidget.h:122: warning: unused parameter ‘active’
viewwidget.h:130: warning: unused parameter ‘clusterId’
viewwidget.h:130: warning: unused parameter ‘active’
viewwidget.h:138: warning: unused parameter ‘fromClusters’
viewwidget.h:138: warning: unused parameter ‘active’
viewwidget.h:146: warning: unused parameter ‘clusterId’
viewwidget.h:146: warning: unused parameter ‘active’
viewwidget.h:161: warning: unused parameter ‘modifiedClusters’
viewwidget.h:161: warning: unused parameter ‘active’
viewwidget.h:161: warning: unused parameter ‘isModifiedByDeletion’
viewwidget.h:171: warning: unused parameter ‘modifiedClusters’
viewwidget.h:171: warning: unused parameter ‘active’
viewwidget.h:181: warning: unused parameter ‘printPainter’
viewwidget.h:181: warning: unused parameter ‘metrics’
viewwidget.h:181: warning: unused parameter ‘whiteBackground’
correlationview.h:148: warning: unused parameter ‘selectedMode’
correlationview.h:200: warning: unused parameter ‘isModifiedByDeletion’
klusters.h:145: warning: unused parameter ‘event’
klusters.h:791: warning: unused parameter ‘incldef’
klusters.h:799: warning: unused parameter ‘message’
./dataprovider.h:48: warning: unused parameter ‘startTime’
./dataprovider.h:48: warning: unused parameter ‘endTime’
./dataprovider.h:48: warning: unused parameter ‘initiator’
./dataprovider.h:48: warning: unused parameter ‘startTimeInRecordingUnits’
klustersdoc.h:701: error: ISO C++ forbids declaration of ‘AutoSaveThread’ with no type
klustersdoc.h:701: error: expected ‘;’ before ‘*’ token
klusters.cpp: In member function ‘void KlustersApp::initActions()’:
klusters.cpp:142: warning: ‘showToolbar’ is deprecated (declared at /usr/include/kde/kstdaction.h:501)
klusters.cpp: In member function ‘virtual void KlustersApp::customEvent(QCustomEvent*)’:
klusters.cpp:1046: warning: ‘upload’ is deprecated (declared at /usr/include/kde/kio/netaccess.h:161)
klusters.cpp: At global scope:
klusters.cpp:1635: warning: unused parameter ‘id’
klusters.cpp: In member function ‘void KlustersApp::renameActiveDisplay()’:
klusters.cpp:2540: warning: ‘getText’ is deprecated (declared at /usr/include/kde/klineeditdlg.h:98)
make[3]: *** [klusters.o] Error 1
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1'
make: *** [all] Error 2

```

---

### Post by Najand on 2006-09-17
Well, why are you trying to install it from source when there is a debian package available... You can find it at [http://sourceforge.net/project/showfiles.php?group_id=101834&package_id=109302](http://sourceforge.net/project/showfiles.php?group_id=101834&package_id=109302)
klusters_1.6.1-1_i386.deb
Download it and use:
```

sudo dpkg -i klusters_1.6.1-1_i386.deb

```
From the directory it is located in.

---

### Post by abelIAN on 2006-09-17
By the way, I got the idea to install kdelibs4 by trying to install the Klusters .deb package. The strange thing is that I still can't install the .deb package because "Dependency is not satisfiable."

---

### Post by Najand on 2006-09-17
Do you have a name? I mean when it errors it comes with a name.

---

### Post by Najand on 2006-09-17
> **abelIAN said:**
> By the way, I got the idea to install kdelibs4 by trying to install the Klusters .deb package. The strange thing is that I still can't install the .deb package because "Dependency is not satisfiable." 

Do you have a name? When it errors, it comes up with the a name. However, if it has been installed broken, using 
```

sudo aptitude reinstall PACKAGENAME

```
will install all needed dependencies.

---

### Post by abelIAN on 2006-09-17
The package is named klusters_1.6.1-1_i386.deb, and the dependency is kdelibs4 (which is installed). I can't seem to install using aptitude reinstall. I've tried putting the file name by itself, preceded by the directories, and by cd'ing into the directory, but none of these methods work. Using make, there are several errors, which I'll relist:
```
klustersdoc.h:701: error: ISO C++ forbids declaration of ‘AutoSaveThread’ with no type
klustersdoc.h:701: error: expected ‘;’ before ‘*’ token
klusters.cpp: In member function ‘void KlustersApp::initActions()’:
klusters.cpp:142: warning: ‘showToolbar’ is deprecated (declared at /usr/include/kde/kstdaction.h:501)
klusters.cpp: In member function ‘virtual void KlustersApp::customEvent(QCustomEvent*)’:
klusters.cpp:1046: warning: ‘upload’ is deprecated (declared at /usr/include/kde/kio/netaccess.h:161)
klusters.cpp: At global scope:
klusters.cpp:1635: warning: unused parameter ‘id’
klusters.cpp: In member function ‘void KlustersApp::renameActiveDisplay()’:
klusters.cpp:2540: warning: ‘getText’ is deprecated (declared at /usr/include/kde/klineeditdlg.h:98)
make[3]: *** [klusters.o] Error 1
make[3]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fahim/Desktop/klusters-1.6.1'
make: *** [all] Error 2

```

There are also several unused parameter warnings, but these may not be fatal.

---

### Post by Najand on 2006-09-17
Hmm, use:
```

sudo aptitude search kluster

```
to search for its name.

---

### Post by abelIAN on 2006-09-17
Well, I get back:

```
c   klusters                        - A powerful and easy-to-use graphical clust
```

I'll try to install it. What does c mean? By the way, simply using sudo apt-get install klusters does not seem to work:

```
Reading package lists... Done
Building dependency tree... Done
Package klusters is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package klusters has no installation candidate

```

---

### Post by Najand on 2006-09-17
First, use "sudo dpkg -i FILENAME"
and after having depencencies error,
use "sudo aptitude reinstall klusters"
to get rid of dependencies.

---

### Post by abelIAN on 2006-09-17
This only removes Klusters:
```
fahim@fahim-macbook:~$ sudo dpkg -i /home/fahim/Desktop/klusters_1.6.1-1_i386.deb
Selecting previously deselected package klusters.
(Reading database ... 98457 files and directories currently installed.)
Unpacking klusters (from .../klusters_1.6.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of klusters:
 klusters depends on kdelibs4 (>= 4:3.1.4); however:
  Package kdelibs4 is not installed.
 klusters depends on libqt3c102-mt (>= 3:3.2.1); however:
  Package libqt3c102-mt is not installed.
 klusters depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing klusters (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 klusters
fahim@fahim-macbook:~$ sudo aptitude reinstall klusters_1.6.1-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "klusters_1.6.1-1_i386.deb"
The following packages are BROKEN:
  klusters
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  klusters: Depends: kdelibs4 (>= 4:3.1.4) which is a virtual package.
            Depends: libqt3c102-mt (>= 3:3.2.1) which is a virtual package.
            Depends: xlibs (> 4.1.0) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
klusters

Score is -301

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  klusters
The following packages will be REMOVED:
  klusters
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1720kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 98530 files and directories currently installed.)
Removing klusters ...

```

---

