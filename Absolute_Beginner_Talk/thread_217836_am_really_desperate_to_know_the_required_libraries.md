---
title: "am really desperate to know the required libraries to compile a new kernel"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-07-17
I know this doesn't deserve to be in "Absolute Beginner Talk" but still here goes: 

```

dpkg --list | grep qt
ii  libqt4-core                            4.1.2-1ubuntu1                        Qt 4 core non-GUI functionality runtime libr
ii  libqt4-dev                             4.1.2-1ubuntu1                        Qt 4 development files
ii  libqt4-gui                             4.1.2-1ubuntu1                        Qt 4 core GUI functionality runtime library
ii  libqt4-qt3support                      4.1.2-1ubuntu1                        Qt 3 compatibility library for Qt 4
ii  libqt4-sql                             4.1.2-1ubuntu1                        Qt 4 SQL database module

```

Any more libraries I need for "make xconfig" ????

Ok, so let's ignore make xconfig. I try make gconfig. 

the make file tells me 
> You need gtk+-2.0, glib-2.0 and libglade-2.0.

Very well. Open synaptic. Search for packages with gtk+ in the name. 

libgtk+2.0-directfb0
libgtk+2.0-directfb-dev

Next, search for packages with glib in the name. A whole bunch appear, so I am guessing the ones I need (which I install) are:
libglib2.0-0
libglib2.0-data
libglib2.0-dev

Now search libglade-2.0. I find it and it is already installed. Thank God. Atleast something. 

I understand Ubuntu is a newbie friendly distro, but does it mean it actually discourages people from compiling their own kernels.

---

### Post by nalmeth on 2006-07-17
What kernel are you trying to compile? Are you following a wiki or a howto?

---

### Post by teet on 2006-07-17
Sometimes when it says that you need a specific package, you actually have to install that package PLUS the development package (will probably have "-dev" or "dev" somewhere in the name) that goes along with it.  Yeah, I know it's pretty stupid, but I've found that it seems to work in situations where I'm trying to get all my dependencies taken care of.

Isn't there a custom kernel compilation guide somewhere on the forums?

-teet

edit:  [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

---

### Post by taurus on 2006-07-17
Are you trying to compile a new kernel or X because the dependencies that you showed are for X while you just need "build-essential" if you plan to build a kernel?

```

sudo apt-get install build-essential

```

---

### Post by harisund on 2006-07-18
Thanks anyway people. Tihs was what I was looking for:

[https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/16864](https://launchpad.net/distros/ubuntu/+source/qt-x11-free/+bug/16864)

---

