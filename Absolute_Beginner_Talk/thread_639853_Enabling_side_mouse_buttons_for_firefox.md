---
title: "Enabling side mouse buttons for firefox"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by computernub1 on 2007-12-13
How do I get the side mouse buttons to be a back/forward button for firefox browser? Thank you so much in advance!

---

### Post by skrribble on 2007-12-13
what kind of mouse do you have?
have your tried using the program btnx?
find btnx here [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)
install btnx and btnx-config
then go through to make it recognize your buttons, and then set them to Alt+Left and Alt+Right

---

### Post by drumstick on 2008-01-04
I did this and it worked for me. Only problem is when I use the mouse button I have designated for going forward a page (Alt+Right), it moves forward a page and brings up a context menu that is exactly like the one that is shown when you right click on a program in the taskbar.

Any ideas how to fix this? I haven't been able to figure it out.

---

### Post by daou on 2008-01-04
> **drumstick said:**
> I did this and it worked for me. Only problem is when I use the mouse button I have designated for going forward a page (Alt+Right), it moves forward a page and brings up a context menu that is exactly like the one that is shown when you right click on a program in the taskbar.

Any ideas how to fix this? I haven't been able to figure it out.

You need to make a few small changes to your xorg.conf to fix it. It is described in the btnx [manual's troubleshooting section 12.2.1]("http://www.ollisalonen.com/btnx/man/x868.html#AEN1052")

The most important value is the Protocol, and the Device option might need to be changed as well.

---

### Post by silverhammermba on 2008-01-10
Hey, I'm trying to do this as well and running into trouble. I installed btnx fine but btnx-config isn't working. Before I can make the install file, it says I have to run ./configure but then it gives me this
```
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.10.11) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
I searched synaptic and couldn't find any packages for gtk+-2.0

---

### Post by erginemr on 2008-01-10
I believe you need to install the development package for gtk2 to be able to compile it, which should be something like libgtk2.0-dev (hint: synaptic).

---

### Post by silverhammermba on 2008-01-10
Alright, I installed a couple more packages and got the make command to work. But now make install is giving me problems. Really ugly problems.
```
max@apotheosis:~/Desktop/btnx-config-0.4.6$ make install
Making install in intl
make[1]: Entering directory `/home/max/Desktop/btnx-config-0.4.6/intl'
if { test "btnx-config" = "gettext-runtime" || test "btnx-config" = "gettext-tools"; } \
           && test 'no' = yes; then \
          /bin/mkdir -p /usr/lib /usr/include; \
          /usr/bin/install -c -m 644 libintl.h /usr/include/libintl.h; \
          @LIBTOOL@ --mode=install \
            /usr/bin/install -c -m 644 libintl.a /usr/lib/libintl.a; \
          if test "@RELOCATABLE@" = yes; then \
            dependencies=`sed -n -e 's,^dependency_libs=\(.*\),\1,p' < /usr/lib/libintl.la | sed -e "s,^',," -e "s,'\$,,"`; \
            if test -n "$dependencies"; then \
              rm -f /usr/lib/libintl.la; \
            fi; \
          fi; \
        else \
          : ; \
        fi
if test "btnx-config" = "gettext-tools" \
           && test 'no' = no \
           && test yes != no; then \
          /bin/mkdir -p /usr/lib; \
          @LIBTOOL@ --mode=install \
            /usr/bin/install -c -m 644 libgnuintl.a /usr/lib/libgnuintl.a; \
          rm -f /usr/lib/preloadable_libintl.so; \
          /usr/bin/install -c -m 644 /usr/lib/libgnuintl.so /usr/lib/preloadable_libintl.so; \
          @LIBTOOL@ --mode=uninstall \
            rm -f /usr/lib/libgnuintl.a; \
        else \
          : ; \
        fi
if test 'no' = yes; then \
          test yes != no || /bin/mkdir -p /usr/lib; \
          temp=/usr/lib/t-charset.alias; \
          dest=/usr/lib/charset.alias; \
          if test -f /usr/lib/charset.alias; then \
            orig=/usr/lib/charset.alias; \
            sed -f ref-add.sed $orig > $temp; \
            /usr/bin/install -c -m 644 $temp $dest; \
            rm -f $temp; \
          else \
            if test yes = no; then \
              orig=charset.alias; \
              sed -f ref-add.sed $orig > $temp; \
              /usr/bin/install -c -m 644 $temp $dest; \
              rm -f $temp; \
            fi; \
          fi; \
          /bin/mkdir -p /usr/share/locale; \
          test -f /usr/share/locale/locale.alias \
            && orig=/usr/share/locale/locale.alias \
            || orig=./locale.alias; \
          temp=/usr/share/locale/t-locale.alias; \
          dest=/usr/share/locale/locale.alias; \
          sed -f ref-add.sed $orig > $temp; \
          /usr/bin/install -c -m 644 $temp $dest; \
          rm -f $temp; \
        else \
          : ; \
        fi
if test "btnx-config" = "gettext-tools"; then \
          /bin/mkdir -p /usr/share/gettext/intl; \
          /usr/bin/install -c -m 644 VERSION /usr/share/gettext/intl/VERSION; \
          /usr/bin/install -c -m 644 ChangeLog.inst /usr/share/gettext/intl/ChangeLog; \
          dists="COPYING.LIB-2.0 COPYING.LIB-2.1 Makefile.in config.charset locale.alias ref-add.sin ref-del.sin export.h gmo.h gettextP.h hash-string.h loadinfo.h plural-exp.h eval-plural.h localcharset.h lock.h relocatable.h xsize.h printf-args.h printf-args.c printf-parse.h wprintf-parse.h printf-parse.c vasnprintf.h vasnwprintf.h vasnprintf.c os2compat.h libgnuintl.h.in bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c hash-string.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y plural-exp.c localcharset.c lock.c relocatable.c langprefs.c localename.c log.c printf.c version.c osdep.c os2compat.c intl-exports.c intl-compat.c"; \
          for file in $dists; do \
            /usr/bin/install -c -m 644 ./$file \
                            /usr/share/gettext/intl/$file; \
          done; \
          chmod a+x /usr/share/gettext/intl/config.charset; \
          dists="plural.c"; \
          for file in $dists; do \
            if test -f $file; then dir=.; else dir=.; fi; \
            /usr/bin/install -c -m 644 $dir/$file \
                            /usr/share/gettext/intl/$file; \
          done; \
          dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c COPYING.LIB-2 gettext.h libgettext.h plural-eval.c libgnuintl.h libgnuintl.h_vms Makefile.vms libgnuintl.h.msvc-static libgnuintl.h.msvc-shared Makefile.msvc"; \
          for file in $dists; do \
            rm -f /usr/share/gettext/intl/$file; \
          done; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/home/max/Desktop/btnx-config-0.4.6/intl'
Making install in src
make[1]: Entering directory `/home/max/Desktop/btnx-config-0.4.6/src'
make[2]: Entering directory `/home/max/Desktop/btnx-config-0.4.6/src'
test -z "/usr/sbin" || /bin/mkdir -p "/usr/sbin"
  /usr/bin/install -c 'btnx-config' '/usr/sbin/btnx-config'
/usr/bin/install: cannot create regular file `/usr/sbin/btnx-config': Permission denied
make[2]: *** [install-sbinPROGRAMS] Error 1
make[2]: Leaving directory `/home/max/Desktop/btnx-config-0.4.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/max/Desktop/btnx-config-0.4.6/src'
make: *** [install-recursive] Error 1
```

Sorry for the huge copy, paste but I have no idea what's going on.

---

### Post by daou on 2008-01-10
Install as root: sudo make install

---

### Post by silverhammermba on 2008-01-10
Ugh, well I feel stupid. The installation guide in the source folder doesn't specify that you have to install as root but the online guide (which I read) does. Thanks, though.

---

