---
title: "Installing kxdocker"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by arthurbarnhouse on 2006-07-12
Trying to install kxdocker, ./configure worked fine.  make seemed to work fine, but make install gave me this:

foy@foy-desktop:~/Desktop/kxdocker-1.0.0a$ make install kxdocker
Making install in doc
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
Making install in .
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[3]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
Making install in en
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[3]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxdocker
/usr/bin/install -c -p -m 644 index.docbook /usr/share/doc/HTML/en/kxdocker/index.docbook
/usr/bin/install: cannot remove `/usr/share/doc/HTML/en/kxdocker/index.docbook': Permission denied
make[3]: *** [install-nls] Error 1
make[3]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make: *** [install-recursive] Error 1


What went wrong?

---

### Post by angkor on 2006-07-12
Any reason you're not using apt?

```
sudo aptitude install kxdocker
```


edit: Ah, I see you are trying to install a newer version. Have you tried running make install as root, since there is a permission error in that output.

---

### Post by arthurbarnhouse on 2006-07-12
Didn't know it was on aptitude

thank you.

---

### Post by arthurbarnhouse on 2006-07-12
OK.  I tried installing it from apt.

got this:  

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Edit:  

Nevermind, it installed but it isn't showing up.  the one in the aptitude doesn't support Gnome, I don't think.  

so source it is.

How do I install from root?

---

### Post by Jucato on 2006-07-12
I think kxdocker is a KDE app that supports/uses KDE parts. I'm not really sure it will work the same way if you use it in GNOME.

Unless of course, you were actually looking for kdocker, which is a totally different program...

---

### Post by vavoem on 2006-07-12
seems like you only updated your repositories 

Did you try


sudo apt-get install kxdocker 


Or else

sudo apt-cache search docker 

to get the exact package name

---

### Post by arthurbarnhouse on 2006-07-12
"I think kxdocker is a KDE app that supports/uses KDE parts. I'm not really sure it will work the same way if you use it in GNOME."

kxdocker website says it supports GNOME.  Besides, I tried installing it in KDE and GNOME.  Same Result.

"seems like you only updated your repositories"

Nope, used sudo apt-get install kxdocker.  

The one in the repository, though, is old.  .3 old.  The one I'm trying to install now is a 1.0 release.  


This time I did "sudo make install" I got this:

foy@foy-desktop:~/Desktop/kxdocker-1.0.0a$ sudo make install
Making install in doc
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
Making install in .
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[3]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
Making install in en
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[3]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxdocker
/usr/bin/install -c -p -m 644 index.docbook /usr/share/doc/HTML/en/kxdocker/index.docbook
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxdocker
/usr/bin/install -c -p -m 644 index.cache.bz2 /usr/share/doc/HTML/en/kxdocker/
rm -f /usr/share/doc/HTML/en/kxdocker/common
ln -s /usr/share/doc/kde/HTML/en/common /usr/share/doc/HTML/en/kxdocker/common
make[3]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc/en'
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/doc'
Making install in po
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/po'
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/po'
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/po'
Making install in src
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/src'
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/src'
/bin/sh ../admin/mkinstalldirs /usr/lib
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libkxdocker.la /usr/lib/libkxdocker.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib
/bin/sh ../admin/mkinstalldirs /usr/bin
  /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  kxdocker /usr/bin/kxdocker
/bin/sh ../admin/mkinstalldirs /usr/lib/kxdocker
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libKXDesignPanther.la /usr/lib/kxdocker/libKXDesignPanther.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kxdocker
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libKXDockerFake.la /usr/lib/kxdocker/libKXDockerFake.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kxdocker
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libKXAnimator.la /usr/lib/kxdocker/libKXAnimator.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kxdocker
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libKXMouse.la /usr/lib/kxdocker/libKXMouse.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kxdocker
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  libKXCommand.la /usr/lib/kxdocker/libKXCommand.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kxdocker
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/16x16/apps
/usr/bin/install -c -p -m 644 ./hi16-app-kxdocker.png /usr/share/icons/hicolor/16x16/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/48x48/apps
/usr/bin/install -c -p -m 644 ./hi48-app-kxdocker.png /usr/share/icons/hicolor/48x48/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/32x32/apps
/usr/bin/install -c -p -m 644 ./hi32-app-kxdocker.png /usr/share/icons/hicolor/32x32/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/64x64/apps
/usr/bin/install -c -p -m 644 ./hi64-app-kxdocker.png /usr/share/icons/hicolor/64x64/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/128x128/apps
/usr/bin/install -c -p -m 644 ./hi128-app-kxdocker.png /usr/share/icons/hicolor/128x128/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/icons/hicolor/22x22/apps
/usr/bin/install -c -p -m 644 ./hi22-app-kxdocker.png /usr/share/icons/hicolor/22x22/apps/kxdocker.png
/bin/sh ../admin/mkinstalldirs /usr/share/applnk/Utilities
 /usr/bin/install -c -p -m 644 kxdocker.desktop /usr/share/applnk/Utilities/kxdocker.desktop
/bin/sh ../admin/mkinstalldirs /usr/share/apps/kxdocker
 /usr/bin/install -c -p -m 644 kxdockerui.rc /usr/share/apps/kxdocker/kxdockerui.rc
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/src'
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/src'
Making install in addons
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a/addons'
/bin/sh ../admin/mkinstalldirs /usr/include
/usr/bin/install -c -p -m 644 libkxdocker.h /usr/include
/bin/sh ../admin/mkinstalldirs /usr/share/apps/kxdocker
/usr/bin/install -c -p -m 644 kxdocker_conf.xml /usr/share/apps/kxdocker
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a/addons'
make[1]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a'
make[2]: Entering directory `/home/foy/Desktop/kxdocker-1.0.0a'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a'
make[1]: Leaving directory `/home/foy/Desktop/kxdocker-1.0.0a'

I'd swear it's saying that it's already been installed, but it isn't showing up in my applications menu.

---

### Post by arthurbarnhouse on 2006-07-12
hmm. . . well, now it does appear to be showing up.  its on my desktop at least.  but it still won't show up in my applications menu.

---

### Post by arthurbarnhouse on 2006-07-12
well. . . no not exactly.  It doesn't seem to be working right.  all it does is show the kde menu.  I can't add programs, or even get to a preferences panel for this thing.

OK.  Here's what happens when I launch kxdocker from terminal:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or rein stall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdoc](http://www.xiaprojects.com/www/prodotti/kxdoc) ker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: loading plugins...
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open sh ared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open  shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open shared ob ject file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open shared  object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open sha red object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMatrix)
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerFake.so: cannot open shared o bject file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerFake.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDockerFake.so.so: cannot open sh ared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerFake.so: cannot open shared objec t file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerFake.so.so: cannot open shared ob ject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDockerFake.so.so: cannot open shared  object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xGDocker)
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared obje ct file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared o bject file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open share d object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared object f ile: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared objec t file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open shared ob ject file: No such file or directory
kxdocker: WARNING: xeplugin_register(xCommand)
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared o bject file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open sh ared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared objec t file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared ob ject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared o bject file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open sh ared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared objec t file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared ob ject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared o bject file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open sh ared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared objec t file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared ob ject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open sha red object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared obj ect file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open sha red object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared obj ect file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared  object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open sha red object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared obj ect file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared obj ect file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shar ed object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shared o bject file: No such file or directory
kxdocker: WARNING: xeplugin_register(xAnimator)
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object  file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared obj ect file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object fil e: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared obje ct file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMouse)
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open share d object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shar ed object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open s hared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared obje ct file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared o bject file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open share d object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] xPillow
kxdocker: WARNING: Going to background...
foy@foy-desktop:~/Desktop/kxdocker-1.0.0a$ QObject::connect: Cannot connect XEPl ugin_Command::xParseTo(const QString &, int, void *) to (null)::xParse(const QSt ring &, int, void *)
foy@foy-desktop:~/Desktop/kxdocker-1.0.0a$ QObject::connect: Cannot connect XEPlugin_Command::xParseTo(const QString &, int, void *) to (null)::xParse(const QString &, int, void *)

---

### Post by michael1977 on 2006-07-26
kxdocker .37 or higher works under gnome I have it working just fine, it is a tad different to configure compared to kde but if you have never used it under kde you should have no issues.  I had an easier time because I had installed xgl compiz via the quinnstorm (beerorkid) packages which gave synaptic access to the quinn kxdocker 1.01 and all its needed files.  If you install this way you need kxdocker kxdocker-data kxdocker-configurator etc. most importantly of all the files is the panel icon file make sure you include this in the install or you wont be able to access the configurator without a terminal.  don't bother with the kxdocker-trash it won't work it is set for kde and konquerer.  

As for not showing up in menu just create an application launcher on your panel and as command put kxdocker it will start just fine.

If your aptitude install worked do the same create a launcher on your panel name it Kxdocker and for command kxdocker and it will act as a starter this could also be done in applications menu I believe.

---

### Post by nolongerlivecd on 2006-08-20
I've got KxDocker running on Kubuntu, but it hides under the bottom panel...

---

### Post by daradib on 2006-11-01
I have a similar problem. I am using Kubuntu 64-bit Edgy (though I had the same problem under Dapper before I upgraded). Kxdocker appears on the menu, but it does not start if I click it. If I run it through Konsole, I get the following result:

[HTML]cyrusjones@DARADIB:~$ kxdocker
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
ERROR: Communication problem with kxdocker, it probably crashed.[/HTML]

I really wanted to use kxdocker because it made the another computer's OS look a lot better. I have a feeling that I didn't install something I should have or I'm not that intelligent.

---

### Post by daradib on 2006-11-10
> **arthurbarnhouse said:**
> well. . . no not exactly.  It doesn't seem to be working right.  all it does is show the kde menu.  I can't add programs, or even get to a preferences panel for this thing.

OK.  Here's what happens when I launch kxdocker from terminal:


I had a similar error. Follow Wieman01's instructions at [http://www.ubuntuforums.org/showthread.php?p=1362850&highlight=file#post1362850](http://www.ubuntuforums.org/showthread.php?p=1362850&highlight=file#post1362850)

Note that, at least for me, I found the configuration in /usr/share/apps/kxdocker/.

---

