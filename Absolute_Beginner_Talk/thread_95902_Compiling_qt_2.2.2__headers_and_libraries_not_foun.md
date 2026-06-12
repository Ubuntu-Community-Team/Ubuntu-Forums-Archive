---
title: "Compiling: qt 2.2.2 : headers and libraries not found? how to solve ?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-27
Compiling: qt 2.2.2 : headers and libraries not found? how to solve ?
  
Thank you very much,

 Pat'

---

### Post by patrick295767 on 2005-11-27
I found the solution:
  
You can find the Qt library (version 3.3.4) at [ftp://ftp.trolltech.com/qt/source/](ftp://ftp.trolltech.com/qt/source/)

A current copy of KDE SVN can be obtained as explained at Retrieving the source.
Installation

Unlike most compiled software, Qt is compiled in the place where it will stay instead of using a 'make install'. Please read the INSTALL instructions in the Qt package. You need to set the $QTDIR and $KDEDIR to the locations where Qt and KDE will be installed, respectively. Also, append $QTDIR/bin and $KDEDIR/bin to your $PATH and $LD_LIBRARY_PATH. Alternatively, instead of using $LD_LIBRARY_PATH, you may add your Qt and KDE library paths to /etc/ld.so.conf, but don't forget to run ldconfig as root after installing Qt and kdelibs, otherwise configure scripts will fail to find the newly installed libraries!

If your distribution sets $XDG_DATA_DIRS and/or $XDG_CONFIG_DIRS you will want to update them to include the correct $KDEDIR/share/ resp. $KDEDIR/etc/xdg/

    bunzip2 qt-x11-free-3.3.4.tar.bz2
    tar xvf qt-x11-free-3.3.4.tar
    cd qt-x11-free-3.3.4
    less INSTALL
    (Set up QTDIR, KDEDIR, PATH, LD_LIBRARY_PATH, XDG_DATA_DIRS and XDG_CONFIG_DIRS)
    cd $QTDIR
    ./configure -system-zlib -qt-gif -system-libpng \
    -system-libjpeg -plugin-imgfmt-mng -thread -no-stl \
    -no-xinerama -no-g++-exceptions
    make

---

