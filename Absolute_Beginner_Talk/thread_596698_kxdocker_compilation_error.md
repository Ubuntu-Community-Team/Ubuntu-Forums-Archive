---
title: "kxdocker compilation error"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-29
Hi,

Whenever I try to install kxdocker following this tutorial ([http://wozlabs.com/linux/kxdcfht.html](http://wozlabs.com/linux/kxdcfht.html)) after running the ./configure command successfully, 690when I run the make command this is what it says:

> ron@Apple-Macintosh:~/kxdocker-1.1.4a$ make
make  all-recursive
make[1]: Entering directory `/home/ron/kxdocker-1.1.4a'
Making all in doc
make[2]: Entering directory `/home/ron/kxdocker-1.1.4a/doc'
Making all in .
make[3]: Entering directory `/home/ron/kxdocker-1.1.4a/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ron/kxdocker-1.1.4a/doc'
Making all in en
make[3]: Entering directory `/home/ron/kxdocker-1.1.4a/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ron/kxdocker-1.1.4a/doc/en'
make[2]: Leaving directory `/home/ron/kxdocker-1.1.4a/doc'
Making all in po
make[2]: Entering directory `/home/ron/kxdocker-1.1.4a/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ron/kxdocker-1.1.4a/po'
Making all in src
make[2]: Entering directory `/home/ron/kxdocker-1.1.4a/src'
if /bin/bash ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT xgdockerfake.lo -MD -MP -MF ".deps/xgdockerfake.Tpo" \
          -c -o xgdockerfake.lo `test -f 'xgdockerfake.cpp' || echo './'`xgdockerfake.cpp; \
        then mv -f ".deps/xgdockerfake.Tpo" ".deps/xgdockerfake.Plo"; \
        else rm -f ".deps/xgdockerfake.Tpo"; exit 1; \
        fi
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libKXDockerFake.la -rpath /usr/lib/kxdocker -avoid-version -module -L/usr/share/qt3/lib -L/usr/lib    xgdockerfake.lo xgpillowfake.lo libkxdocker.la -lkio -lkdeui 
if /bin/bash ../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT xgfloater.lo -MD -MP -MF ".deps/xgfloater.Tpo" \
          -c -o xgfloater.lo `test -f 'xgfloater.cpp' || echo './'`xgfloater.cpp; \
        then mv -f ".deps/xgfloater.Tpo" ".deps/xgfloater.Plo"; \
        else rm -f ".deps/xgfloater.Tpo"; exit 1; \
        fi
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libKXAnimator.la -rpath /usr/lib/kxdocker -avoid-version -module -L/usr/share/qt3/lib -L/usr/lib    xeplugin_animator.lo xgfloater.lo libkxdocker.la 
/bin/bash ../libtool --silent --mode=link --tag=CXX g++  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libKXMouse.la -rpath /usr/lib/kxdocker -avoid-version -module -L/usr/share/qt3/lib -L/usr/lib    xeplugin_mouse.lo -lXtst libkxdocker.la 
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libKXMouse.la] Error 1
make[2]: Leaving directory `/home/ron/kxdocker-1.1.4a/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/kxdocker-1.1.4a'
make: *** [all] Error 2


I don't really know what the problem is and I can solve it.

Thnx

---

### Post by limac on 2007-10-30
Dude anyone??

---

### Post by llamakc on 2007-10-30
Looks like you didn't satisfy the dependencies that would have been in the instructions.

---

### Post by overdrank on 2007-10-30
> **limac said:**
> Dude anyone??

Hi why not try the deb file from here. 
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fkxdocker%2Fkxdocker_1.1.4a-0ubuntu2_i386.deb&md5sum=6ed0bc6420521880e310ef5715186dcb&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fkxdocker%2Fkxdocker_1.1.4a-0ubuntu2_i386.deb&md5sum=6ed0bc6420521880e310ef5715186dcb&arch=i386&type=main)
just choose a mirror close to you.

---

### Post by limac on 2007-10-30
Then what to do to run the deb file?

---

### Post by llamakc on 2007-10-30
Download the deb. Save it to your Desktop. Get that done first.

---

### Post by limac on 2007-10-30
did that already

---

### Post by limac on 2007-10-30
+ thanks to u llamck, my compilation knowledge in Ubuntu has started to develop.

---

### Post by limac on 2007-10-30
what after saving in in my desktop??

---

### Post by Maestro23 on 2007-10-30
> **limac said:**
> what after saving in in my desktop??

Right Click on it. Should have the option to **Open with GDebi Package Installer**.

If not, you can open a terminal.

> cd ~/Desktop

ls (make sure you see the .deb)

sudo dpkg -i package.deb

---

### Post by llamakc on 2007-10-30
Open the terminal. In it type the following:

```

cd ~/Desktop

```

The "~" character represents YOUR home directory (/home/ron).

Next, install it.

```

sudo dpkg -i kxdocker*.deb

```

It should be installed. You can list every file installed with that package with the command

```

dpkg -L kxdocker

```

HTH

---

### Post by limac on 2007-10-30
you are one help dude and not to forget you maestro. 

But how do I run that deb file after it is installed??

---

### Post by llamakc on 2007-10-30
> **limac said:**
> you are one help dude and not to forget you maestro. 

But how do I run that deb file after it is installed??

You won't "run" the .deb. The .deb is a packaged archive of multiple files. When you use "dpkg" to install it (which is what happens behind the scenes in Synaptic, by the way) you are telling the system that you have installed a new software, and the files are put where they belong. After that you run the PROGRAM, not the deb.

So, how do you run kxdocker? If there's a menu entry you would run it that way. In this case with kxdocker I recommend you type the keys:

ALT-F2 (the alt key and the F2 key) at the same time. This will open the "run" dialog. When THAT opens, type in 

kxdocker

and it should start up.

---

### Post by limac on 2007-10-30
nothing is happening when I type in kxdocker after pressing ALT+F2...

---

### Post by llamakc on 2007-10-30
IN the terminal type:

```

dpkg -L kxdocker


```

and cut/paste EVERYTHING it spits out.

---

### Post by limac on 2007-10-30
This is what it says:

ron@Apple-Macintosh:~$ dpkg -L kxdocker
/.
/usr
/usr/bin
/usr/bin/kxdocker
/usr/share
/usr/share/doc
/usr/share/doc/kde
/usr/share/doc/kde/HTML
/usr/share/doc/kde/HTML/en
/usr/share/doc/kde/HTML/en/kxdocker
/usr/share/doc/kde/HTML/en/kxdocker/index.docbook
/usr/share/doc/kde/HTML/en/kxdocker/index.cache.bz2
/usr/share/doc/kxdocker
/usr/share/doc/kxdocker/AUTHORS
/usr/share/doc/kxdocker/copyright
/usr/share/doc/kxdocker/changelog.Debian.gz
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/kxdocker.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/kxdocker.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/kxdocker.png
/usr/share/icons/hicolor/64x64
/usr/share/icons/hicolor/64x64/apps
/usr/share/icons/hicolor/64x64/apps/kxdocker.png
/usr/share/icons/hicolor/128x128
/usr/share/icons/hicolor/128x128/apps
/usr/share/icons/hicolor/128x128/apps/kxdocker.png
/usr/share/icons/hicolor/22x22
/usr/share/icons/hicolor/22x22/apps
/usr/share/icons/hicolor/22x22/apps/kxdocker.png
/usr/share/applnk
/usr/share/applnk/Utilities
/usr/share/applnk/Utilities/kxdocker.desktop
/usr/share/apps
/usr/share/apps/kxdocker
/usr/share/apps/kxdocker/kxdockerui.rc
/usr/share/apps/kxdocker/kxdocker_conf.xml
/usr/share/apps/kxdocker/kxdocker_conf_default.xml
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/kxdocker.1.gz
/usr/share/menu
/usr/share/menu/kxdocker
/usr/lib
/usr/lib/libkxdocker.so.0.0.40
/usr/lib/libkxdocker.la
/usr/lib/kxdocker
/usr/lib/kxdocker/libKXDesignPanther.so
/usr/lib/kxdocker/libKXDesignPanther.la
/usr/lib/kxdocker/libKXDockerFake.so
/usr/lib/kxdocker/libKXDockerFake.la
/usr/lib/kxdocker/libKXAnimator.so
/usr/lib/kxdocker/libKXAnimator.la
/usr/lib/kxdocker/libKXMouse.so
/usr/lib/kxdocker/libKXMouse.la
/usr/lib/kxdocker/libKXCommand.so
/usr/lib/kxdocker/libKXCommand.la
/usr/lib/kxdocker/libKXDockerComposite.so
/usr/lib/kxdocker/libKXDockerComposite.la
/usr/include
/usr/include/kde
/usr/include/kde/libkxdocker.h
/usr/share/doc/kde/HTML/en/kxdocker/common
/usr/lib/libkxdocker.so.0
/usr/lib/libkxdocker.so
ron@Apple-Macintosh:~$ dpkg -L kxdocker

---

### Post by llamakc on 2007-10-30
try typing this in a terminal.

```

/usr/bin/kxdocker

```

IT has to be EXACT. The Terminal shell (BASH) is case-sensitive.

---

### Post by limac on 2007-10-30
They are saying:

ron@Apple-Macintosh:~$ /usr/bin/kxdocker
ron@Apple-Macintosh:~$ WARNING: KXDocker is already running!

What? but nothing is running? Huh?

---

### Post by Maestro23 on 2007-10-30
> **llamakc said:**
> try typing this in a terminal.

```

/usr/bin/kxdocker

```

IT has to be EXACT. The Terminal shell (BASH) is case-sensitive.

Hey llamakc, If that doesn't work for him, might have to dig deeper :(

I dug this old thread up about running kxdocker on dapper.  I'm sure some will apply to the issue at hand here. Found 2 relevant threads:

[http://ubuntuforums.org/showthread.php?t=269256](http://ubuntuforums.org/showthread.php?t=269256)
[http://ubuntuforums.org/showthread.php?t=232128](http://ubuntuforums.org/showthread.php?t=232128)

---

### Post by limac on 2007-10-30
thnx for trying but no info was that helpful.....

---

### Post by llamakc on 2007-10-30
Are Desktop Effects running limac?

---

### Post by Maestro23 on 2007-10-30
> **limac said:**
> thnx for trying but no info was that helpful.....

You looked thru the info on those 2 links and already digested the info and determined that it would be of no help?

---

### Post by limac on 2007-10-30
> **Maestro23 said:**
> You looked thru the info on those 2 links and already digested the info and determined that it would be of no help?

I already looked at those links earlier yesterday and didn't do the trick for me..

---

### Post by limac on 2007-10-30
> **llamakc said:**
> Are Desktop Effects running limac?

Yeah they are on.

---

### Post by wieman01 on 2007-10-30
If KXDocker is running please move the mouse pointed to the lower end of your screen. It is probably hiding there.

There are other options if KXDocker does not compile correctly. Kooldock, Kibadock, etc. which are all in the repository.

---

### Post by limac on 2007-10-30
I tried kiba-dock, but I want to give my desktop a more macish look and kxdocker I heard wasx stable. So any further suggestions.

---

### Post by llamakc on 2007-10-30
Have you looked under your web browser to see if it's there?

---

### Post by limac on 2007-10-30
and does it anyhow have anything to do with my awn being enabled and installed??

---

### Post by limac on 2007-10-30
> **llamakc said:**
> Have you looked under your web browser to see if it's there?

only my awn running and that's it. I tried to close awn to see if anything was there but no.

---

### Post by limac on 2007-10-30
so what do i do about this??

---

### Post by limac on 2007-10-31
i do require some further assistance. So some quick help would really be appreciated.

---

