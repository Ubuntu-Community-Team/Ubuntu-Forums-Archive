---
title: "Difficutly compiling HYDROGEN 0.9.3"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by grimace on 2007-05-01
OK...I've been using Synaptic to install for 18 months.... it's nice and simple.  But now I'm looking to install the latest version of HYDROGEN which doesn't appear in Synaptic.  I downloaded the source files, navigated to the directory, typed "./configure" and ran (into) the following problem...


~/hydrogen-0.9.3$ ./configure


-----------------------------------------------------------------
Starting Hydrogen 0.9.3 configuration...
-----------------------------------------------------------------


checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for egrep... grep -E
checking whether gcc needs -traditional... no

--- Checking for QT Libs ----------------------------------------
checking whether QTDIR environment variable is set... no
configure: WARNING: QTDIR must be properly set.
 * Searching for Qt library
   |-> searching QT in /usr/share/qt *** Not found ***
   |-> searching QT in /usr/share/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt3 *** Not found ***
   |-> searching QT in /usr/lib/qt-3.1 *** Not found ***
configure: WARNING: Qt library not found. Maybe QTDIR isn't properly set.
checking for qmake... no
configure: error: qmake not found in current PATH. Maybe QT development environment isn't available (qt3-devel).



Can anyone help get me past this minor setback?  I tried digging around in Synaptic for QT3 libs and was at a loss for what exactly I need to continue with the config...

---

### Post by stump138 on 2007-05-01
the version you can currently get is qt4 there are several libs for it including..

libqt4-core
libqt4-debug
libqt4-gui
libqt4-qt3support
libqt4-sql
qt4-designer
qt4-dev-tools
qt4-doc
qt4-qtconfig

you can get all of these via aptitude :)

---

### Post by rax_m on 2007-05-01
Hi. 

From my understanding the QT libraries are used for all KDE applications.. 
I did a quick search through synaptic and found qt3-dev-tools  which looks like it might be the libararies you need for compilation. 

You could always give it a try and uninstall it if it doesn't make a difference. 

Cheers
Rax

---

### Post by grimace on 2007-05-01
Got IT  !!! Thanks all!!!

---

### Post by MolotovHearts on 2007-10-26
I just got connection to the internet from ubuntu (finally) and I'm now trying to install hydrogen. 

I think I am now in a similar problem to the previous person except i get this:

:~/hydrogen-0.9.3$ ./configure

> -----------------------------------------------------------------
Starting Hydrogen 0.9.3 configuration...
-----------------------------------------------------------------


checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


so i thought the next thing to do would be to type: config.log but i then got:

> bash: config.log: command not found


Could anyone help, by showing me where I should go next? I haven't used Synaptec before, is it something that is recommended i use?

Thanks.

---

### Post by MolotovHearts on 2007-10-27
Don't worry about it, I was able to work everything out myself to install hydrogen. 

I also installed ardour, but I'm getting a Jack error, so I'm gonna have to check that out now.

---

