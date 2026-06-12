---
title: "Help with aMSN installation"
date: 2005-07-23
forum: Apple PPC Users
---

### Post by HOT on 2005-07-23
HI, i have found a problem installing cvs version of aMSN. First, i make aptitude cvs, after i download aMSN, etc... But whan i try to execute amsn (./amsn) it say me that i need to compile TkCximage. I try it, but ./configure doesn't find gcc compiler or that appears...

          [I]root@driade:~/msn# ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@driade:~/msn#[/I]

And the following error is in config.log:
[I]configure:1345: checking for gcc
configure:1374: result: no
configure:1425: checking for cc
configure:1454: result: no
configure:1467: checking for cc
configure:1513: result: no
configure:1566: checking for cl
configure:1595: result: no[/I] 

What can i do ? Can i compile TkCximage or that is impossible?

THANKS  ;-)

---

### Post by netrattler on 2005-07-23
You need to install the compilers for Ubuntu sudo apt-get install build-essentials

Joe

---

### Post by HOT on 2005-07-23
apt-get says me build-essentials doesn't exist o.O I have activated universe and multiverse repository.

---

### Post by HOT on 2005-07-23
Well, the build was build-essential without final "s". I begin the compilation, but now there is another error... -_-

[I]root@driade:~/msn# ./configure --with-tk=/usr/lib/tk8.4/ --with-tcl=/usr/lib/tcl8.4/
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for prefix by checking for wish... /usr/bin/wish
checking tcl build dir... using tcl library in /usr/lib/tcl8.4/
./configure: line 3006: /usr/lib/tcl8.4//tclConfig.sh: No such file or directory[/I] 

What do i make now ?  :???:

---

### Post by Thirsteh on 2005-08-07
I regret that I am unable to give you the exact name of the package you need, but do a search in Synaptic for "TCL" (it MIGHT be "TK) but try TCL first. There should be a "TCL/TK 7.*" or similarly named package (also the package should be an Ubuntu-package, you can see from the ubuntu logo on the left of the package). Now, you will need the -devel version of this package, if you select that and try to install, the binary package will be installed as well. Once again, I regret that I cannot look it up and tell you the exact name, but I'm not running Ubuntu at the moment. All best.

---

### Post by cowlip on 2005-08-28
[QUOTE=Thirsteh]I regret that I am unable to give you the exact name of the package you need, but do a search in Synaptic for "TCL" (it MIGHT be "TK) but try TCL first. There should be a "TCL/TK 7.*" or similarly named package (also the package should be an Ubuntu-package, you can see from the ubuntu logo on the left of the package). Now, you will need the -devel version of this package, if you select that and try to install, the binary package will be installed as well. Once again, I regret that I cannot look it up and tell you the exact name, but I'm not running Ubuntu at the moment. All best.[/QUOTE]

Hey this worked, I was missing the tk one...just search for it in synapitc and get the dev one of 8.4

---

