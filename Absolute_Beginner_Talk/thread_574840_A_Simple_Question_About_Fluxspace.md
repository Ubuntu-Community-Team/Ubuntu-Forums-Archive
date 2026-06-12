---
title: "A Simple Question About Fluxspace"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2007-10-13
Hi,

I am trying to install fluxspace.

I do "./configure" and it comes out OK.

Then, I do "sudo checkinstall" and it gives me this:
```
nav@box:~/Desktop/fluxspace-0.4.0_alpha$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@box ]
1 -  Summary: [ fluxspace ]
2 -  Name:    [ fluxspace ]
3 -  Version: [ 0.4.0_alpha ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ fluxspace-0.4.0_alpha ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/nav/Desktop/fluxspace-0.4.0_alpha/src'
Making install in FbTk
make[2]: Entering directory `/home/nav/Desktop/fluxspace-0.4.0_alpha/src/FbTk'
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..  -Wall    -g -O2    -MT Menu.lo -MD -MP -MF ".deps/Menu.Tpo" -c -o Menu.lo Menu.cc; \
        then mv -f ".deps/Menu.Tpo" ".deps/Menu.Plo"; else rm -f ".deps/Menu.Tpo"; exit 1; fi
rm: cannot remove `': Is a directory
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -Wall -g -O2 -MT Menu.lo -MD -MP -MF .deps/Menu.Tpo -c Menu.cc  -fPIC -DPIC -o .libs/Menu.o
Menu.cc: In member function 'void FbTk::Menu::update(int)':
Menu.cc:496: error: no matching function for call to 'FbTk::FbPixmap::FbPixmap(FbTk::FbPixmap)'
make[2]: *** [Menu.lo] Error 1
make[2]: Leaving directory `/home/nav/Desktop/fluxspace-0.4.0_alpha/src/FbTk'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/nav/Desktop/fluxspace-0.4.0_alpha/src'
make: *** [install-recursive] Error 1

```

I have tried installing the Tk-dev and the Tcl-dev packages but to no avail.

Thanks,
Van

---

### Post by Pumalite on 2007-10-13
[http://sourceforge.net/docman/display_doc.php?docid=16036&group_id=76737](http://sourceforge.net/docman/display_doc.php?docid=16036&group_id=76737)

---

### Post by NavmaN on 2007-10-13
I installed all the build dependencies and I still get the same problem. Were you referring to a specefic section in the readme that I maybe missed?

I would really appreciate it if you could be a little more specific; I'm still sort of a noob. :)

Thanks

---

### Post by Pumalite on 2007-10-13
That's probably the best link on the subject. I've never done it myself.

---

