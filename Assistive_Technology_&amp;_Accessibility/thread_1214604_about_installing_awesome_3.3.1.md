---
title: "about installing awesome 3.3.1"
date: 2009-07-16
forum: Assistive Technology &amp; Accessibility
---

### Post by skyalone on 2009-07-16
hello everyone!  my version  is 9.04  . when i install  awesome and type make in that file it shows as follow:
Running cmake…
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git -> /usr/bin/git
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc -> /usr/bin/luadoc
-- convert -> /usr/bin/convert
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- checking for modules 'glib-2.0;cairo;x11;pango>=1.19.3;pangocairo>=1.19.3;xcb-randr;xcb-xtest;xcb-xinerama;xcb-event>=0.3.4;xcb-aux>=0.3.0;xcb-atom>=0.3.0;xcb-keysyms>=0.3.4;xcb-icccm>=0.3.3;xcb-image>=0.3.0;xcb-property>=0.3.0;cairo-xcb;libstartup-notification-1.0>=0.10;xproto>=7.0.15;imlib2;libxdg-basedir>=1.0.0'
--   package 'xcb-xtest' not found
--   package 'libstartup-notification-1.0>=0.10' not found
--   package 'xproto>=7.0.15' not found
--   package 'libxdg-basedir>=1.0.0' not found
CMake Error at /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:270 (message):
  A required package was not found
Call Stack (most recent call first):
  /usr/share/cmake-2.6/Modules/FindPkgConfig.cmake:322 (_pkg_check_modules_internal)
  awesomeConfig.cmake:134 (pkg_check_modules)
  CMakeLists.txt:15 (include)


CMake Error at awesomeConfig.cmake:157 (message):
Call Stack (most recent call first):
  CMakeLists.txt:15 (include)


-- Configuring incomplete, errors occurred!
make: *** [cmake] Error 1










i just want to know what else packages should i need to install      thank a lot:D

---

### Post by regala on 2009-07-16
> **skyalone said:**
> hello everyone!  my version  is 9.04  . when i install  awesome and type make in that file it shows as follow:
Running cmake&#8230;
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git -> /usr/bin/git
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc -> /usr/bin/luadoc
-- convert -> /usr/bin/convert
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found


> 
-- checking for modules 'glib-2.0;cairo;x11;pango>=1.19.3;pangocairo>=1.19.3;xcb-randr;xcb-xtest;xcb-xinerama;xcb-event>=0.3.4;xcb-aux>=0.3.0;xcb-atom>=0.3.0;xcb-keysyms>=0.3.4;xcb-icccm>=0.3.3;xcb-image>=0.3.0;xcb-property>=0.3.0;cairo-xcb;libstartup-notification-1.0>=0.10;xproto>=7.0.15;imlib2;libxdg-basedir>=1.0.0'
--   package 'xcb-xtest' not found


for this you WOULD need whatever it is some libxcb*-*-dev packages at versions >=0.3.3, which will be available only on Karmic (9.10) or if someone is willing to make them, you would need backports, but, in this very case, it may mean building backports for a lotta packages (libx11-* for sure, and maybe a bunch in X)

> 
--   package 'libstartup-notification-1.0>=0.10' not found



ditto, this version is available only starting Karmic => need to do a backport.

> 

--   package 'xproto>=7.0.15' not found
--   package 'libxdg-basedir>=1.0.0' not found



yep, that's it: need to backport a big bunch of what X.Org is in Karmic.



> 
i just want to know what else packages should i need to install      thank a lot:D


sorry, but it won't be that easy. You will HAVE to build new several packages before that. and IIRC, you would then have to rebuild all the other packages that depend upon the X stack: every single graphical application.

in fact, the simplest (and most likely the only) way would be to upgrade to Karmic, which I wouldn't advise anyone to doing :)

---

