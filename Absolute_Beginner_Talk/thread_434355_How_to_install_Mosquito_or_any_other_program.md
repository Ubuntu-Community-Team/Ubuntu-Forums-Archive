---
title: "How to install Mosquito or any other program???"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-05-05
So, I downloaded this Mosquito thing, wich is supposed to be a window manager. I downloaded a tar.gz file and extracted the files to a directory mosquito.

In the terminal I did "CD mosquito" to go to that especific directory. 

By typing LS I got the following output:

BUGS               INSTALL               Popupmenu.cpp
Colors.h           install-sh            Popupmenu.h
Configfile.cpp     kill.xpm              PopupmenuItem.cpp
Configfile.h       Main.cpp              PopupmenuItem.h
config.h.in        Makefile              popup.xpm
configure          Makefile.in           README
configure.in       Manager.cpp           resize.xpm
COPYING            Manager.h             Rootpopupmenu.cpp
Dock.cpp           mcon.c                Rootpopupmenu.h
Dock.h             Misc.cpp              Signalhandler.cpp
Dockpopupmenu.cpp  Misc.h                Signalhandler.h
Dockpopupmenu.h    mosquito              tile.xpm
Eventhandler.cpp   Mosquito.h            TODO
Eventhandler.h     mosquitorc            Vscreen.cpp
Fonts.h            Mwindow.cpp           Vscreen.h
iconify.xpm        Mwindow.h             xcalccolor.c
Iconpopupmenu.cpp  Mwindowpopupmenu.cpp  xgetkeycode.c
Iconpopupmenu.h    Mwindowpopupmenu.h


I  see an Install file and an install-sh file. But how on earth do I install the damned thing???

---

### Post by taurus on 2007-05-05
What does INSTALL say?

```
more INSTALL
```
Hit space bar for the next 24 lines.

However, it's more or less something a long the line of

```
sudo aptitude update
sudo aptitude install  checkinstall **build-essential**  <-- you need this package if you want to build anything from source!
./configure
make
sudo checkinstall
```

---

### Post by supersonicdarky on 2007-05-05
what is the difference between **make install** and **checkinstall**?

---

### Post by picpak on 2007-05-05
> **supersonicdarky said:**
> what is the difference between **make install** and **checkinstall**?

make install just throws all of the files into the system; checkinstall puts the files into a .deb package which you can install and maintain through Synaptic.

---

### Post by Ganda_Melga on 2007-05-06
> **taurus said:**
> What does INSTALL say?

```
more INSTALL
```
Hit space bar for the next 24 lines.

However, it's more or less something a long the line of

```
sudo aptitude update
sudo aptitude install  checkinstall **build-essential**  <-- you need this package if you want to build anything from source!
./configure
make
sudo checkinstall
```


Negative negative! Several errors along the process, too much text to place here. Ends with this message:

:~/mosquito$ ./configure
configure: error: can not find sources in . or ..
melga@melga-desktop:~/mosquito$ ./ configure
bash: ./: é uma directoria
melga@melga-desktop:~/mosquito$ make
gcc -I/usr/X11R6/include -L/usr/X11R6/lib -Wall mcon.c -o mcon -lX11 -lm
mcon.c: In function &#8216;main&#8217;:
mcon.c:17: warning: implicit declaration of function &#8216;exit&#8217;
mcon.c:17: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
mcon.c:67: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
mcon.c:97: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
mcon.c:125: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
mcon.c:135: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
/usr/bin/ld: impossível encontrar -lX11
collect2: ld returned 1 exit status
make: *** [all] Error 1
melga@melga-desktop:~/mosquito$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Mosquitopack 
>> eof   
>> EOF
>>                                  

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values: 

0 -  Maintainer: [ root@melga-desktop ]
1 -  Summary: [ Mosquitopack ]
2 -  Name:    [ mosquito ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ mosquito ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

melga@melga-desktop:~/mosquito$

---

### Post by taurus on 2007-05-06
Post

```
cd ~/mosquito
ls -la
```

---

### Post by Ganda_Melga on 2007-05-06
> **taurus said:**
> Post

```
cd ~/mosquito
ls -la
```

I don't get it. It just gives a list of files. I've searching  the net looking for tutorials on how to install programs, but those I read didn't helped a bit.

---

### Post by taurus on 2007-05-06
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Ganda_Melga on 2007-05-06
> **taurus said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)



Thanks a lot! I will read it carefully.

---

