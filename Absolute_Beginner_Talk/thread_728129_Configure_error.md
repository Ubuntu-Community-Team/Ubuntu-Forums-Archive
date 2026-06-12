---
title: "Configure error"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by kingsrook on 2008-03-18
I'm trying to install vpython on kubuntu 7.1 by following the instructions on [http://www.vpython.org/linux_download.html]("http://www.vpython.org/linux_download.html") . When I run the configure file I get this error
```
configure: error: Gtk+ is required on Unix-like systems
```
I know its something simple but I'm completely new to linux and don't know how to get GTK+ or whatever. I thought kubuntu came with that.

---

### Post by oldos2er on 2008-03-18
[http://www.vpython.org/INSTALL.html](http://www.vpython.org/INSTALL.html)

 You can install the needed packages through Synaptic Package Manager.

---

### Post by kingsrook on 2008-03-18
What packages do I need exactly? I have installed libgtkglext1, gtkglextmm 1.2.0, and libgtkmm-2.4-1c2a. Thanks

---

### Post by mc4man on 2008-03-18
your going to need the -dev packages of what you mentioned - maybe also libgtk2.0-dev, libboost-dev, ect. Possibly also boost-build (probably not)   or maybe libboost-python-dev

---

### Post by kingsrook on 2008-03-18
alright, I finally got it to configure fine, but now when I try to make it I get
```
Compiling ../../visual-3.2.9/src/arrow.cpp ...
make[1]: *** [arrow.lo] Error 1
make[1]: Leaving directory `/home/(myusername)/Desktop/build/src'
make: *** [all-recursive] Error 1
```
Is there any hope or should I stick with vpython on windows?

---

### Post by mc4man on 2008-03-18
see if there's a cvisual/build.log or something similar in your source folder, if so read thru
edit; what version of gcc, g++ are you using
re edit; it looks like it may be easier to build on hardy, for gutsy are you using this source [http://sourceforge.net/project/showfiles.php?group_id=6013](http://sourceforge.net/project/showfiles.php?group_id=6013)

---

### Post by kingsrook on 2008-03-18
There's a cvisualmodule.d file in the src folder of the source files after configuring and also a config.log. Not sure the version of gcc, how do I see that? I'm not using the one from sourceforge.net, I'm using [http://www.vpython.org/download/visual-3.2.9.tar.bz2]("http://www.vpython.org/download/visual-3.2.9.tar.bz2")

Actually I found the build.log file - here are the errors that were in it

../../visual-3.2.9/include/cvisual.h:8:47: error: boost/python/detail/wrap_python.hpp: No such file or directory
../../visual-3.2.9/include/cvisual.h:12:34: error: boost/python/tuple.hpp: No such file or directory
../../visual-3.2.9/include/cvisual.h:13:33: error: boost/python/list.hpp: No such file or directory
../../visual-3.2.9/include/displaylist.h:10:35: error: boost/python/object.hpp: No such file or directory

---

### Post by mc4man on 2008-03-18
I just now took the one from sourceforge and it compiled successfully on hardy. All the necessary packages were available in synaptic - took a little searching. Note: I didn't install python-visual.(seems to maybe cause an issue) I did install prior to build -```
 libboost-thread-dev, libcairomm-1.0-dev, libglibmm-2.4-dev, libgtkglext1-dev, libgtkglextmm-x11-dev, libgtkmm-2.4-dev, libsigc++-2.0-dev, libxmu-dev, libxmu-headers, libglade2-dev, libglademm-2.4-dev, python-cairo-dev, python2.4, python2.4-minimal, python-numpy
```  (+all depends of these, hope their spelled right)
Note: I had build-deps for mplayer and wine previously installed -you  may have some deps other than above that I already had in place
As far as gcc this is a recent install so it's just gcc, gcc-4.2, g++, g++-4.2
i'm assuming you have installed _build-essential_ 
I have to go out - will look a gutsy and post back - hardy may be your best bet

Edit: add libboost-dev to above and ck. for libpango1.0-dev
One final edit;   you really should read thru the install.txt in your source folder as to using a build folder and some other stuff relating to installing, ect. - doing the make may be only half the battle

---

### Post by kingsrook on 2008-03-18
well, I got all those libraries except I couldn't find libgtkglextmm-x11-dev and I have python2.5. I still get the same error with make. Maybe I will have to try hardy.
edit: I am using a build folder and trying to follow the intructions best I can

---

### Post by mc4man on 2008-03-19
Do you have python2.5-dev  installed ?
I had a feeling the above list was incomplete
Looking back in my install history i also see
libboost-python-dev
 python2.5-dev

---

### Post by kingsrook on 2008-03-19
Sweet! Success! I guess I just needed  libboost-python-dev, I already had python2.5-dev. Once I installed  libboost-python-dev it made without a hitch. I was able run a python script that imported the visual  module and it worked fine. Thanks allot for all the help:)

---

