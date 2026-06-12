---
title: "[SOLVED] program install help"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-12-09
I have qdvdauthor installed from repositories which is version 0.1.5 but the maintainer is frequently correcting little problems with it so I'd like to install his fixes.  They however aren't in the repositories but can be accessed from sourceforge.  My question is, if I download the new version to the Desktop (as tar.gz) how do I install it over the earlier version?
thanks--this looks like it should be easy but I haven't found the answer yet!

---

### Post by thelatinist on 2007-12-09
It's fairly easy, actually.  Untar to a directory, then CD to that directory and run the following commands:

```
./configure
make
make install
```

---

### Post by flyingsolo on 2007-12-09
Thanks for your help.  However, when I do 
.configure
I get a reply:  bash: .configure: command not found
(by the way, did you mean change to the directory where the program is downloaded or change into the folder for the program?)

UPDATE: OK, figured out some of this; needed to cd to qdvdauthor-1.0.0 folder on Desktop; also needed to do: ./configure (slightly different from .configure) but then I got message to install qt dev tools; ok, did that but now get:
./configure: 425: /bin/qmake: not found
make: *** No targets specified and no makefile found.  Stop.
Problems compiling configurator application
Please report to [email]qdvdauthor@users.sf.net[/email]

..so now I'm stuck again!  Any more ideas? thanks.

---

### Post by spiderbatdad on 2007-12-09
meant cd into the directory containing the program files that was created when you extracted the package. . There isn't always a configure file, so proceed to make then sudo make install...or look for a read me or install instructions in the directory...

---

### Post by flyingsolo on 2007-12-09
thanks spiderbatdad, but as you can see from my edit above, there is a configure file but I'm running into another problem.

---

### Post by thelatinist on 2007-12-09
Sorry...that was a type-o.  It meant to say ./configure.  Have edited it.

As for your other problem, try:

```
apt-get install qmake
```

Then try again.  I'm not sure...you may need to use:

```
qmake
qmake install
```

to install it, too.  Apparantly this is a special c++ compiler for use with QT.

---

### Post by flyingsolo on 2007-12-29
Bump--I'm still trying to get an updated (current) version of qdvdauthor to work but still have this problem as noted above.  Now it is the holidays & I've got some time to 'play' with this but can't get the current version installed.

---

### Post by hyper_ch on 2007-12-29
I see you are using Dapper Drake. That came out 18 months ago. Are you sure you don't want to upgrade? There should be an updated version available now. Otherwise you could enable the backport repositories.

If you want to compile you first need some additional stuff:
```

sudo apt-get install build-essential

```
Then you can try the
```

./configure
make
sudo make install

```
steps. Maybe further packages are required.

---

### Post by flyingsolo on 2007-12-29
Actually, I should change my profile b/c I have Gutsy running on my laptop but still have Dapper on an old Desktop, my very first linux machine, that has run so well since day one!

I have the build-essential installed.  When I change to the /tmp/qdvdauthor and run ./configure I get an enormous list of errors, as follows:

> g++ -c -pipe -Wall -W -Wno-non-virtual-dtor -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
main.cpp:1:26: error: qapplication.h: No such file or directory
In file included from main.cpp:2:
.ui/configurator.h:13:22: error: qvariant.h: No such file or directory
.ui/configurator.h:14:21: error: qdialog.h: No such file or directory
.ui/configurator.h:15:22: error: qprocess.h: No such file or directory
.ui/configurator.h:16:23: error: qdatetime.h: No such file or directory
.ui/configurator.h:33: error: expected class-name before &#8216;{&#8217; token
.ui/configurator.h:34: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
.ui/configurator.h:36: error: expected &#8216;;&#8217; before &#8216;public&#8217;
.ui/configurator.h:71: error: &#8216;QString&#8217; does not name a type
.ui/configurator.h:72: error: &#8216;QString&#8217; has not been declared
.ui/configurator.h:75: error: &#8216;QString&#8217; does not name a type
.ui/configurator.h:77: error: expected `:' before &#8216;slots&#8217;
.ui/configurator.h:78: error: expected primary-expression before &#8216;virtual&#8217;
.ui/configurator.h:78: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
.ui/configurator.h:78: error: expected &#8216;;&#8217; before &#8216;virtual&#8217;
.ui/configurator.h:117: error: expected `:' before &#8216;slots&#8217;
.ui/configurator.h:118: error: expected primary-expression before &#8216;virtual&#8217;
.ui/configurator.h:118: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
.ui/configurator.h:118: error: expected &#8216;;&#8217; before &#8216;virtual&#8217;
.ui/configurator.h:121: error: ISO C++ forbids declaration of &#8216;QProcess&#8217; with no type
.ui/configurator.h:121: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
.ui/configurator.h:124: error: &#8216;QTime&#8217; does not name a type
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:6: error: &#8216;QApplication&#8217; was not declared in this scope
main.cpp:6: error: expected `;' before &#8216;a&#8217;
.ui/configurator.h:38: error: &#8216;Configurator::~Configurator()&#8217; is private
main.cpp:7: error: within this context
main.cpp:8: error: &#8216;class Configurator&#8217; has no member named &#8216;initMe&#8217;
main.cpp:8: error: &#8216;a&#8217; was not declared in this scope
main.cpp:9: error: &#8216;class Configurator&#8217; has no member named &#8216;show&#8217;
main.cpp:10: error: &#8216;lastWindowClosed&#8217; was not declared in this scope
main.cpp:10: error: &#8216;SIGNAL&#8217; was not declared in this scope
main.cpp:10: error: &#8216;quit&#8217; was not declared in this scope
main.cpp:10: error: &#8216;SLOT&#8217; was not declared in this scope
main.cpp: At global scope:
main.cpp:4: warning: unused parameter &#8216;argc&#8217;
main.cpp:4: warning: unused parameter &#8216;argv&#8217;
make: *** [.obj/main.o] Error 1
Problems compiling configurator application
Please report to [email]qdvdauthor@users.sf.net[/email]

---

### Post by hyper_ch on 2007-12-29
well, you could try the backports...

---

### Post by flyingsolo on 2007-12-29
Ok--solved my own problem (surprise,surprise!) by finding another thread addressing this.
For those who follow, check these threads:

[https://help.ubuntu.com/community/Installing_'Q'_DVD-Author#head-0fa2d9344f5d0c3a904ec4d781e2c8b42ca18953]("https://help.ubuntu.com/community/Installing_'Q'_DVD-Author#head-0fa2d9344f5d0c3a904ec4d781e2c8b42ca18953"):

[http://ubuntuforums.org/showthread.php?t=465121]("http://ubuntuforums.org/showthread.php?t=465121")

Hopefully the repositories will soon have Varol's 1.0 version which I believe he has said should be available soon (Dec 07 or Jan 08).

---

