---
title: "How do I install ristretto-0.0.16 on Xubuntu?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-15
Can I ask another question?

I tried to install ristretto-0.0.16. However, the configure gives me:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I have gcc on Xubuntu. I don't know why it doesn't work.

---

### Post by jordanmthomas on 2008-02-15
You don't appear to have any compiler installed
```
sudo apt-get install build-essential
```
You still won't be able to finish the installation with just this, but you can get farther and find out what else you need to install.

---

### Post by incen on 2008-02-15
You're right. I have this error:

```
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for intltool >= 0.31... 0.37.0 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... no
configure: error: GNU gettext tools not found; required for intltool 
```

---

### Post by incen on 2008-02-19
I posted this thread a few days ago. However, I still don't have the solution to it. Can anyone help me?

I was hoping to have a better image viewer in my Xubuntu and this one was suggested by a friend here. However, I had hard time installing it. Or is there a better one recommended?
Thanks! :)

---

### Post by Michelexub on 2008-02-22
Hi incen,
I had the same problem and I went a bit further.

Use synatptics and check that you have the packages:
gettext
gettext-base

After I have installed those packages, I reran ./configure and had the following error:
"
checking for pkg-config... no
*** The pkg-config utility could not be found on your system.
*** Make sure it is in your path, or set the PKG_CONFIG
*** environment variable to the full path to pkg-config.
*** You can download pkg-config from the freedesktop.org
*** software repository at
***
***    [http://www.freedesktop.org/software/pkgconfig](http://www.freedesktop.org/software/pkgconfig)
***
"

I will try to install pkg-config and see what happens next...

---

### Post by Michelexub on 2008-02-22
I have installed the package pkg-config using synaptics and now I have the following message in the terminal:

> 
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.22
checking for libexif >= 0.6.0... not found
*** The required package libexif was not found on your system.
*** Please install libexif (atleast version 0.6.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.


The package libexif does not exist, I found only libexif12.
Any help will be very appreciated.

---

### Post by psyBSD on 2008-02-23
You need libexif-dev, a package which contains the development headers for libexif. (it will pull the correct library aswell).

You also need the following packages:

- libgtk2.0-dev[1]
- libthunar-vfs-1-dev[2]
- libdbus-glib-1-dev[3]
- libxfce4util-dev[4]
- libxfcegui4-dev[5]

When you have these packages installed, ristretto should compile like a charm.

(PS. you might want to install 0.0.17)



[0] [http://packages.ubuntu.com/gutsy/libexif-dev](http://packages.ubuntu.com/gutsy/libexif-dev)
[1] [http://packages.ubuntu.com/gutsy/libgtk2.0-dev](http://packages.ubuntu.com/gutsy/libgtk2.0-dev)
[2] [http://packages.ubuntu.com/gutsy/libthunar-vfs-1-dev](http://packages.ubuntu.com/gutsy/libthunar-vfs-1-dev)
[3] [http://packages.ubuntu.com/gutsy/libdbus-glib-1-dev](http://packages.ubuntu.com/gutsy/libdbus-glib-1-dev)
[4] [http://packages.ubuntu.com/gutsy/libxfce4util-dev](http://packages.ubuntu.com/gutsy/libxfce4util-dev)
[5] [http://packages.ubuntu.com/gutsy/libxfcegui4-dev](http://packages.ubuntu.com/gutsy/libxfcegui4-dev)

---

### Post by Michelexub on 2008-02-23
Thanks a lot.
I've followed your suggestion and it worked.

But why should I need all those packages to install a plugin/small application is beyond me :confused:

---

### Post by psyBSD on 2008-02-23
Ok, let me explain.

**- libexif**
> **From Ubuntu Pkg-repo's:**
Most digital cameras produce EXIF files, which are JPEG files with extra tags that contain information about the image. The EXIF library allows you to parse an EXIF file and read the data from those tags.

Ristretto uses this library to extract additional information about images containing EXIF data. Some images provide information about how they should be rotated based on the orientation of the digital camera.
Ristretto auto-rotates these images based on this information.


**- libgtk2.0**
> **From Ubuntu Pkg-repo's:**
The GTK+ is a multi-platform toolkit for creating graphical user interfaces. Offering a complete set of widgets, the GTK+ is suitable for projects ranging from small one-off tools to complete application suites.

Ristretto uses gtk to build it's graphical user interface. Without this, you won't have an image viewer.


**- libthunar-vfs-1-2**
> **From Ubuntu Pkg-repo's:**
This package contains a library for virtual file system abstraction. It's used by thunar, the file manager of Xfce 4.4

Ristretto uses thunar-vfs to gather information about the files you want to open. Information about wether it is an image or some random file for example. Or to convert path's to uri's etc...


**- libdbus-glib-1**
> **From Ubuntu Pkg-repo's:**
D-Bus is a message bus, used for sending messages between applications. Conceptually, it fits somewhere in between raw sockets and CORBA in terms of complexity.

This package provides the GLib-based shared library for applications using the GLib interface to D-Bus.

The developer of ristretto was to lazy to write his own file-properties dialog. In return, he has chosen to let thunar handle this. Ristretto uses glib-dbus to tell thunar over the dbus message-bus that a properties-dialog should be displayed.


**- libxfce4util4**
> **From Ubuntu Pkg-repo's:**
This package contains libxfce4util4, the basic utility function library for Xfce4. If you intend to run Xfce4, you need this library.

Libxfce4util comes with utilities for reading .desktop-style files. Called XfceRc. XfceRc is used to read and write the ristretto-configuration-file. ~/.config/ristretto/ristrettorc


**- libxfcegui4**
> **From Ubuntu Pkg-repo's:**
This package contains a library which provides the very basic GUI functions used by the Xfce4 desktop suite. If you intend to run Xfce4, then you need to install this package.

libxfcegui4 provides several gtk-widgets which are used across xfce. ristretto uses these widgets to provide a consistent interface with the rest of xfce.


When you use xfce, all these libraries are already used by some component or another, so ristretto does not provide you with a massive memory footprint there. But to compile ristretto from source, you need the development-packages. These are packages with additional files required by the compiler and linker to build ristretto for you.

---

