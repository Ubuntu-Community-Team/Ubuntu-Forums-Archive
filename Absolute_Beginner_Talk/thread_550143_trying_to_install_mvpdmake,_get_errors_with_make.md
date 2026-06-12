---
title: "trying to install mvpdmake, get errors with make"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-09-13
I'm trying to install a nice GUI app to encode video to watch it on my ipod nano (thanks to ilinux), but am having trouble getting it to work.  I run make, which seems to be fine, and finishes by telling me type "make install now", which i type, and get an error and it won't finish. here's what it says```

bman@wherewulf:~/Desktop/mvpdmake-0.4$ make install now
mkdir -p intl/po
rm -f intl/po/messages-glade.pot
rm -f intl/po/messages-python.pot
xgettext --force-po -o intl/po/messages-python.pot -L Python --from-code=utf8 *.py EPL/*.py
xgettext: MvpdMake.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/Exception.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/UI.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/Video.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext --force-po -o intl/po/messages-glade.pot -L Glade --from-code=utf8 *.glade
msgcat --force-po intl/po/messages-glade.pot intl/po/messages-python.pot -o intl/po/messages.pot
rm -f intl/po/messages-glade.pot 
rm -f intl/po/messages-python.pot
for lang in ru; do msgmerge -U intl/po/$lang.po intl/po/messages.pot; done
.... done.
for lang in ru; do mkdir -p intl/mo/$lang/LC_MESSAGES; done
for lang in ru; do msgfmt intl/po/$lang.po -o intl/mo/$lang/LC_MESSAGES/mvpdmake.mo; done
Done
Type: make install now
for lang in ru; do \
                mkdir -p /share/locale/$lang/LC_MESSAGES ; \
        done
for i in 16 22 24 32 36 48 64 72 96 128 192 ; do \
                mkdir -p /share/icons/hicolor/${i}x${i}/apps ; \
        done                                     
for i in 16 22 24 32 36 48 64 72 96 128 192 ; do \
                mkdir -p /share/icons/gnome/${i}x${i}/apps ; \
        done                                     
mkdir -p /bin
mkdir -p /lib/mvpdmake
mkdir -p /lib/mvpdmake/EPL
mkdir -p /share/applications
mkdir -p /share/mvpdmake
mkdir -p /share/icons/hicolor/scalable/apps
mkdir -p /share/icons/gnome/scalable/apps
for lang in ru; do \
                install -m 644 intl/mo/$lang/LC_MESSAGES/* \
                        /share/locale/$lang/LC_MESSAGES/ ; \
        done
install: cannot remove `/share/locale/ru/LC_MESSAGES/mvpdmake.mo': Permission denied
make: *** [install-po] Error 1
bman@wherewulf:~/Desktop/mvpdmake-0.4$ sudo make install now
Password:
mkdir -p intl/po
rm -f intl/po/messages-glade.pot
rm -f intl/po/messages-python.pot
xgettext --force-po -o intl/po/messages-python.pot -L Python --from-code=utf8 *.py EPL/*.py
xgettext: MvpdMake.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/Exception.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/UI.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext: EPL/Video.py:1: Unknown encoding "utf8". Proceeding with ASCII instead.
xgettext --force-po -o intl/po/messages-glade.pot -L Glade --from-code=utf8 *.glade
msgcat --force-po intl/po/messages-glade.pot intl/po/messages-python.pot -o intl/po/messages.pot
rm -f intl/po/messages-glade.pot 
rm -f intl/po/messages-python.pot
for lang in ru; do msgmerge -U intl/po/$lang.po intl/po/messages.pot; done
.... done.
for lang in ru; do mkdir -p intl/mo/$lang/LC_MESSAGES; done
for lang in ru; do msgfmt intl/po/$lang.po -o intl/mo/$lang/LC_MESSAGES/mvpdmake.mo; done
Done
Type: make install now
for lang in ru; do \
                mkdir -p /share/locale/$lang/LC_MESSAGES ; \
        done
for i in 16 22 24 32 36 48 64 72 96 128 192 ; do \
                mkdir -p /share/icons/hicolor/${i}x${i}/apps ; \
        done                                     
for i in 16 22 24 32 36 48 64 72 96 128 192 ; do \
                mkdir -p /share/icons/gnome/${i}x${i}/apps ; \
        done                                     
mkdir -p /bin
mkdir -p /lib/mvpdmake
mkdir -p /lib/mvpdmake/EPL
mkdir -p /share/applications
mkdir -p /share/mvpdmake
mkdir -p /share/icons/hicolor/scalable/apps
mkdir -p /share/icons/gnome/scalable/apps
for lang in ru; do \
                install -m 644 intl/mo/$lang/LC_MESSAGES/* \
                        /share/locale/$lang/LC_MESSAGES/ ; \
        done
sed -e 's/%{_prefix}/\/usr/g' site-config.in > site-config
install -m 644 site-config /lib/mvpdmake/
sed -e 's/%{_prefix}/\/usr/g' mvpdmake.in > mvpdmake
install -m 755 mvpdmake /bin/
for i in 16 22 24 32 36 48 64 72 96 128 192 ; do \
                rsvg-convert -w $i -h $i -f png \
                        -o /share/icons/hicolor/${i}x${i}/apps/mvpdmake.png \
                        mvpdmake.svg ; \
        done
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
/bin/sh: rsvg-convert: not found
make: *** [make-install-icons] Error 127

```

I assume it has something to do with rsvg-convert not being there, but I can't find it anywhere.  Any help would be great.

---

### Post by cubeist on 2007-09-13
when installing from source files there are three basic steps... well four if you include unzipping the files.

Anyway, first in the terminal move to the directory of the uncompressed files and type "./configure"  (Actually, the way I like to do it is create a new folder, then cd into that new folder and type "../configure"  This keeps things nice and clean for future reference, but is completely unnecessary)

Second, if configure runs ok (you have all the dependencies installed) then you can type "make" and the program will build itself (this may take a long time depending on the size of the program and power of your computer)

Third, assuming the make process went smoothly you can type "make install" and it will install the files in the proper places (/usr/bin, /usr/share, etc)

good luck.  post back with results

---

### Post by cubeist on 2007-09-13
oh... reread your post... perhaps you only need to run "make install" as sudo.  I am not 100% certain what the "now" command means because when you type "sudo make install" it installs the files immediately anyway...

---

### Post by xboxbman on 2007-09-13
> **cubeist said:**
> oh... reread your post... perhaps you only need to run "make install" as sudo.  I am not 100% certain what the "now" command means because when you type "sudo make install" it installs the files immediately anyway...

Sudo makes no difference.  ./configure does nothing.  Thanks for trying though.

---

### Post by cubeist on 2007-09-15
I would advise to try again from a fresh download and follow the instructions to a tee... make sure you pay attention to the output from ./configure to see what dependencies you need... then install the dependencies and do ./configure again and again until it is satisfied... then make... then sudo make install

I have installed many, many packages from source on numerous platforms over the years... it can be done! Don't give up :)


Edit - I just tried to make it and your right... it refuses to build itself.  They are using a strange make pattern...

---

### Post by olskar on 2007-10-01
If you, or someone else, still need it I have it in deb format for you

---

