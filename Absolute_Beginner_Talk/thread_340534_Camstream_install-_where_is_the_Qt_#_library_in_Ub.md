---
title: "Camstream install- where is the Qt # library in Ubuntu"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-01-17
Hi,
Need a little help please.
I'm trying to install Camstream [http://www.smcc.demon.nl/camstream/](http://www.smcc.demon.nl/camstream/)
and following the install instructions,  i need the following:

"The Qt library can be downloaded from [http://www.trolltech.com/](http://www.trolltech.com/) and several mirrors. Any version of 2.3.0 or higher will do."  (except i can't find the download - just QT/X11 open source Which is a whole collection of tutorials, programs and examples)

I believe in KDE this is already installed - where?
In Ubuntu installed/not installed? 
I tried installing everything to do with qt3 in synaptic, but i need to know where the Qt library is....

A[B][I] common problem is that Linux distributors place the Qt libraries at the weirdest places... The configure script checks the most common directories, but can't really test them all. So, if configure complains it can't locate the Qt libraries, you must first set the QTDIR environment variable (this is a requirement anyhow). So, if your Qt libraries are placed in, for example, /usr/lib/qt-2.3.0, try this:

	# QTDIR=/usr/lib/qt-2.3.0
	# export QTDIR
	# ./configure [options]

This is also the location where the uic User Interface Compiler and moc pre-processor are supposed to be. If not, make sure these can be found in your PATH![/I][/B]

.[I][B]..... "Another source of confusion is that often the library is present, but not the header files. It turns out that some distributors (Red Hat, SuSe) split the Qt package in two parts: just the library, and the header files and development tools. On your system only the library is installed (this appears to be the default), which is enough to run programs but not to compile them!

In that case you have to install the 'qt-dev' package as well. For example, if you installed the qt-3.0.3 rpm on Red Hat, you must install qt-devel-3.0.3 too. Of course the version numbers have to match! The package name may be slightly different for different systems............"[/B][/I]

Anyone helpme out here? please.

---

### Post by stoer on 2007-01-17
!!!!!!!!
Darn !!!!!!

Found it just with synaptic, no need for the hard way ](*,)   ](*,)

---

### Post by FamuLinux on 2007-01-19
> **stoer said:**
> Hi,
Need a little help please.
I'm trying to install Camstream [http://www.smcc.demon.nl/camstream/](http://www.smcc.demon.nl/camstream/)
and following the install instructions,  i need the following:

"The Qt library can be downloaded from [http://www.trolltech.com/](http://www.trolltech.com/) and several mirrors. Any version of 2.3.0 or higher will do."  (except i can't find the download - just QT/X11 open source Which is a whole collection of tutorials, programs and examples)

I believe in KDE this is already installed - where?
In Ubuntu installed/not installed? 
I tried installing everything to do with qt3 in synaptic, but i need to know where the Qt library is....

A[B][I] common problem is that Linux distributors place the Qt libraries at the weirdest places... The configure script checks the most common directories, but can't really test them all. So, if configure complains it can't locate the Qt libraries, you must first set the QTDIR environment variable (this is a requirement anyhow). So, if your Qt libraries are placed in, for example, /usr/lib/qt-2.3.0, try this:

	# QTDIR=/usr/lib/qt-2.3.0
	# export QTDIR
	# ./configure [options]

This is also the location where the uic User Interface Compiler and moc pre-processor are supposed to be. If not, make sure these can be found in your PATH![/I][/B]

.[I][B]..... "Another source of confusion is that often the library is present, but not the header files. It turns out that some distributors (Red Hat, SuSe) split the Qt package in two parts: just the library, and the header files and development tools. On your system only the library is installed (this appears to be the default), which is enough to run programs but not to compile them!

In that case you have to install the 'qt-dev' package as well. For example, if you installed the qt-3.0.3 rpm on Red Hat, you must install qt-devel-3.0.3 too. Of course the version numbers have to match! The package name may be slightly different for different systems............"[/B][/I]

Anyone helpme out here? please.

My trouble with Qt started because I have an Ralink wireless chipset in my laptop. Qt is required to compile the latest kernel module and GUI config utility. Long story short, the easiest thing to do is go through Synaptics and search for 'qt'. Scroll through the results and install basically everything that begins with qt3-[apps-dev,designer,dev-tools,doc]. This fixed my problem

---

### Post by stoer on 2007-01-19
Thanks...
took me a while but got there in the end!
:)

---

