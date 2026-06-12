---
title: "package missing"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-19
Hi 

I-m trying to install some packages and after *sudo apt-get install xlibmesa-glu-dev*

I got this:

[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xlibmesa-glu-dev[/I]

Do you have any sugestions?

I really need some help here.

---

### Post by patrick295767 on 2005-10-19
[QUOTE=bmarilena]Hi 

I-m trying to install some packages and after *sudo apt-get install xlibmesa-glu-dev*

I got this:

[I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xlibmesa-glu-dev[/I]

Do you have any sugestions?

I really need some help here.[/QUOTE]



[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=xlibmesa&searchon=names&subword=1&version=stable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=xlibmesa&searchon=names&subword=1&version=stable&release=all)

---

### Post by patrick295767 on 2005-10-19
[www.debian.org](www.debian.org)
then search for ur package ...
    
download it !
  
then sudo dpkg -i package.deb
   
Let us know about ur progress !

Patrick295767
__________
u can have info maybe there :
[http://www.ubuntuforums.org/showthread.php?t=64557&page=3](http://www.ubuntuforums.org/showthread.php?t=64557&page=3)

---

### Post by bmarilena on 2005-10-19
I downloaded... but the install command is not working... should the package be on a speciffic location?

---

### Post by bmarilena on 2005-10-19
After several attempts... finnaly i got this : [I]
sudo dpkg -i xlibmesa-glu-dev_4.3.0.dfsg.1-14sarge1_i386.deb
Selecting previously deselected package xlibmesa-glu-dev.
(Reading database ... 59889 files and directories currently installed.)
Unpacking xlibmesa-glu-dev (from xlibmesa-glu-dev_4.3.0.dfsg.1-14sarge1_i386.deb) ...
dpkg: dependency problems prevent configuration of xlibmesa-glu-dev:
 xlibmesa-glu-dev depends on xlibmesa-glu (= 4.3.0.dfsg.1-14sarge1); however:
  Package xlibmesa-glu is not installed.
 xlibmesa-glu-dev depends on xlibmesa-gl-dev | libgl-dev; however:
  Package xlibmesa-gl-dev is not installed.
  Package libgl-dev is not installed.
dpkg: error processing xlibmesa-glu-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xlibmesa-glu-dev[/I]

and after: 
*sudo dpkg -i xlibmesa-glu_4.3.0.dfsg.1-14sarge1_i386.deb*

I got this: 
[I]Selecting previously deselected package xlibmesa-glu.
dpkg: regarding xlibmesa-glu_4.3.0.dfsg.1-14sarge1_i386.deb containing xlibmesa-glu:
 xlibmesa-glu conflicts with libglu1
  libglu1-mesa provides libglu1 and is installed.
dpkg: error processing xlibmesa-glu_4.3.0.dfsg.1-14sarge1_i386.deb (--install):
 conflicting packages - not installing xlibmesa-glu
Errors were encountered while processing:
 xlibmesa-glu_4.3.0.dfsg.1-14sarge1_i386.deb
[/I]

What should I do next?

---

### Post by devmage on 2005-10-23
I am having the exact same problem as Marilena.  For reference, I'm trying to install Wine by source, over Ubuntu 5.10 on an AMD64 arch (since only x86 binaries seem to exist).  Any and all help on getting these dependencies worked out would be great.

---

