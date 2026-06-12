---
title: "How do I install a program (in a folder) on my desktop?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by t2000kw on 2007-05-05
I am trying to install an ink-level monitor for my Canon printer. I have extracted three folders but need to install the programs and libraries (?) in them. They weren't in neat .deb packages, at least where I found them at. And Synaptics doesn't have them available.

---

### Post by tehkain on 2007-05-05
is there a Make file or a Install Readme?

---

### Post by t2000kw on 2007-05-05
Yes--there is a makefile and a readme.

**Here's the readme file:**

Inkblot - the GNOME printer ink level tool

Dependencies:

	- GNOME 2.4.x or newer
	- libinklevel ([http://libinklevel.sf.net](http://libinklevel.sf.net))
	- libieee1284 ([http://cyberelk.net/tim/libieee1284/](http://cyberelk.net/tim/libieee1284/))

Features

	- status icon indicating overall ink level status
	- dialog recording % level for black/color
	- support for separate CMYK levels where detected

Not very helpful, is it, except that it tells about the dependencies which I already knew about. And those dependencies are also in folders as well. I already used the archive manager to unzip/un-tarball them all. 

[B]
There is a makefile. [/B]Do I run a command inside the folder, put the folder somewhere else, copy the contents to a temp folder somewhere, or does it matter where I do the installation or compiling from?

---

### Post by tehkain on 2007-05-05
[http://www.cutlersoftware.com/ubuntuinstall/#source](http://www.cutlersoftware.com/ubuntuinstall/#source)

Should help yah. Scroll down to Source Package.

---

### Post by t2000kw on 2007-05-06
Here's my results with one of the source packages. It didn't work, but it might not be due to user error. Also, there may be a different way of doing this to get around the error and make it work. This is my complete terminal session. I though it was a nice shortcut to be able to drag the folder on my desktop to the terminal window. I didn't realize that Linux had evolved to that level already.

I appreciate the pointer to that particular web site, tehkain! The little video made it look easy. 
===================
terminal session below
===================

[B]

donald@donald:~$ cd '/home/donald/Desktop/libinklevel'
donald@donald:~/Desktop/libinklevel$ ./configure
bash: ./configure: No such file or directory
donald@donald:~/Desktop/libinklevel$ make
cc -Wall -O2 -fPIC -DPIC -I.   -c -o canon.o canon.c
cc -Wall -O2 -fPIC -DPIC -I.   -c -o d4lib.o d4lib.c
d4lib.c:1246: warning: \u2018clearSndBuf\u2019 defined but not used
cc -Wall -O2 -fPIC -DPIC -I.   -c -o epson_new.o epson_new.c
cc -Wall -O2 -fPIC -DPIC -I.   -c -o hp_new.o hp_new.c
cc -Wall -O2 -fPIC -DPIC -I.   -c -o libinklevel.o libinklevel.c
cc -Wall -O2 -fPIC -DPIC -I.   -c -o linux.o linux.c
linux.c:11:22: error: ieee1284.h: No such file or directory
linux.c: In function \u2018get_device_id\u2019:
linux.c:30: error: storage size of \u2018parports\u2019 isn\u2019t known
linux.c:54: warning: implicit declaration of function \u2018ieee1284_find_ports\u2019
linux.c:54: error: \u2018E1284_OK\u2019 undeclared (first use in this function)
linux.c:54: error: (Each undeclared identifier is reported only once
linux.c:54: error: for each function it appears in.)
linux.c:56: warning: implicit declaration of function \u2018ieee1284_get_deviceid\u2019
linux.c:57: error: \u2018F1284_FRESH\u2019 undeclared (first use in this function)
linux.c:30: warning: unused variable \u2018parports\u2019
make: *** [linux.o] Error 1
donald@donald:~/Desktop/libinklevel$ checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> library file for ink cartridge level checks
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ donald@donald ]
1 -  Summary: [ library file for ink cartridge level checks ]
2 -  Name:    [ libinklevel ]
3 -  Version: [ 20070506 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libinklevel ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
cc -Wall -O2 -fPIC -DPIC -I.   -c -o linux.o linux.c
linux.c:11:22: error: ieee1284.h: No such file or directory
linux.c: In function \u2018get_device_id\u2019:
linux.c:30: error: storage size of \u2018parports\u2019 isn\u2019t known
linux.c:54: warning: implicit declaration of function \u2018ieee1284_find_ports\u2019
linux.c:54: error: \u2018E1284_OK\u2019 undeclared (first use in this function)
linux.c:54: error: (Each undeclared identifier is reported only once
linux.c:54: error: for each function it appears in.)
linux.c:56: warning: implicit declaration of function \u2018ieee1284_get_deviceid\u2019
linux.c:57: error: \u2018F1284_FRESH\u2019 undeclared (first use in this function)
linux.c:30: warning: unused variable \u2018parports\u2019
make: *** [linux.o] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

donald@donald:~/Desktop/libinklevel$ [/B]

---

