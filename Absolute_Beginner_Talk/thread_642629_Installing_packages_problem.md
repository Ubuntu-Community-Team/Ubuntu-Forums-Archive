---
title: "Installing packages problem"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-12-16
Heya, Ive been able to get by untill now downloading packages through other means. But when I get to tar type packages that I need to use codes, it doesnt seem to work. Itll ask me to use the ./configure, which I use, but it comes back with no directory. Could you tell me what Im doing wrong? Ill give you one of the error messages.
marlon@marlon-laptop:~$ tar -zxf fung-calc-1.3.2b.tar.gz
tar: fung-calc-1.3.2b.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
marlon@marlon-laptop:~$ cd fung-calc-1.3.2b
bash: cd: fung-calc-1.3.2b: No such file or directory
marlon@marlon-laptop:~$ cd ~/fung-calc-1.3.2b
bash: cd: /home/marlon/fung-calc-1.3.2b: No such file or directory
marlon@marlon-laptop:~$ ./configure
bash: ./configure: No such file or directory
marlon@marlon-laptop:~$ ./configure fung-calc-1.3.2b
bash: ./configure: No such file or directory
marlon@marlon-laptop:~$ cd ~/Desktop
marlon@marlon-laptop:~/Desktop$ ./configure
bash: ./configure: No such file or directory
marlon@marlon-laptop:~/Desktop$ ./configure fung-calc-1.3.2b
bash: ./configure: No such file or directory
marlon@marlon-laptop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
marlon@marlon-laptop:~/Desktop$ fung-calc-1.3.2b
bash: fung-calc-1.3.2b: command not found
marlon@marlon-laptop:~/Desktop$ fung-calc-1.3.2b
bash: fung-calc-1.3.2b: command not found
marlon@marlon-laptop:~/Desktop$ fung-calc-1.3.2b make install
bash: fung-calc-1.3.2b: command not found
marlon@marlon-laptop:~/Desktop$ 
I tried it many times in many different ways. I kept the item on my desktop. Could you tell me what Im doing wrong, help will be much appreciated.

---

### Post by lamalex on 2007-12-16
you can't untar a file that's not there. you need to need to be on the desktop to untar it. You can do either of these two things
```
cd Desktop/
tar -xzvf fung-calc-1.3.2b.tar.gz

``` and then the rest OR
```

tar -xzvf Desktop/fung-calc-1.3.2b.tar.gz

``` and then the rest

---

### Post by lamalex on 2007-12-16
Just for completeness, here's an explanation. When you open a terminal you see
```
yourname@hostname~$
```
the ~ is shorthand for the directory /home/<yourname>. if you type ```
pwd
```it will output /home/<yourname>. pwd is the command that prints your full path, the expanded version of ~. The file you're looking for is on your desktop, /home/<yourname>/Desktop or ~/Desktop. tar cannot open a file if it's not there. from your home directory, tar could not find you archive since it was on the desktop. You then need to change directories (cd) to the desktop to untar it. To check if a file is there, use ```
ls -l
``` and look for it, if it's not there, then your path is wrong or the file just doesn't exist. I hope this helps you understand the terminal a little bit better.

---

### Post by thelatinist on 2007-12-16
Unless you saved the archive to your home folder, you will need to specify the complete path to the archive.

If the file is on your desktop, for example, use the following commands:

```
sudo mkdir ~/src
cd ~/src
tar xvfz ~/Desktop/program_name.tar.gz
./configure
make
make install
make clean

```

---

### Post by Marfish on 2007-12-17
I tried some of your suggestions, but I still came up with error messages.
marlon@marlon-laptop:~$ sudo mkdir ~/Desktop
mkdir: cannot create directory `/home/marlon/Desktop': File exists
marlon@marlon-laptop:~$ cd ~/Desktop
marlon@marlon-laptop:~/Desktop$ tar xvfz ~Desktop/fung-calc-1.3.2b.tar.gz
tar: ~Desktop/fung-calc-1.3.2b.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
marlon@marlon-laptop:~/Desktop$ tar -xzvf Desktop/fung-calc-1.3.2b.tar.gz
tar: Desktop/fung-calc-1.3.2b.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
marlon@marlon-laptop:~/Desktop$

---

### Post by RomeReactor on 2007-12-17
Hi. If the file is in your desktop:
```
cd Desktop
```
then:
```
tar -xzvf fung-calc-1.3.2b.tar.gz
```

If the file is **not** in your desktop, you need to navigate to the correct directory using **cd**; an easier way to do all this is to move the file to your home folder, so you don't have to navigate anywhere after launching the terminal.

---

### Post by Marfish on 2007-12-17
Okay, I tried it again and managed to unpackage it. Now what do I do? I cant seem to configure or install it.
marlon@marlon-laptop:~/Desktop$ tar -xzvf fung-calc-1.3.2b.tar.gz
fung-calc-1.3.2b/
fung-calc-1.3.2b/admin/
fung-calc-1.3.2b/admin/ChangeLog
fung-calc-1.3.2b/admin/compile
fung-calc-1.3.2b/admin/config.guess
fung-calc-1.3.2b/admin/config.sub
fung-calc-1.3.2b/admin/depcomp
fung-calc-1.3.2b/admin/install-sh
fung-calc-1.3.2b/admin/ltcf-c.sh
fung-calc-1.3.2b/admin/ltcf-cxx.sh
fung-calc-1.3.2b/admin/ltcf-gcj.sh
fung-calc-1.3.2b/admin/ltconfig
fung-calc-1.3.2b/admin/ltmain.sh
fung-calc-1.3.2b/admin/missing
fung-calc-1.3.2b/admin/mkinstalldirs
fung-calc-1.3.2b/admin/ylwrap
fung-calc-1.3.2b/admin/CVS/
fung-calc-1.3.2b/admin/CVS/Root
fung-calc-1.3.2b/admin/CVS/Repository
fung-calc-1.3.2b/admin/CVS/Entries
fung-calc-1.3.2b/admin/CVS/Tag
fung-calc-1.3.2b/admin/Doxyfile.am
fung-calc-1.3.2b/admin/Doxyfile.global
fung-calc-1.3.2b/admin/Makefile.common
fung-calc-1.3.2b/admin/acinclude.m4.in
fung-calc-1.3.2b/admin/am_edit
fung-calc-1.3.2b/admin/conf.change.pl
fung-calc-1.3.2b/admin/config.pl
fung-calc-1.3.2b/admin/configure.in.bot.end
fung-calc-1.3.2b/admin/configure.in.min
fung-calc-1.3.2b/admin/cvs-clean.pl
fung-calc-1.3.2b/admin/cvs.sh
fung-calc-1.3.2b/admin/debianrules
fung-calc-1.3.2b/admin/detect-autoconf.sh
fung-calc-1.3.2b/admin/libtool.m4.in
fung-calc-1.3.2b/admin/new-libtool.m4.in
fung-calc-1.3.2b/admin/new-ltmain.sh
fung-calc-1.3.2b/admin/old-libtool.m4.in
fung-calc-1.3.2b/admin/old-ltcf-c.sh
fung-calc-1.3.2b/admin/old-ltcf-cxx.sh
fung-calc-1.3.2b/admin/old-ltcf-gcj.sh
fung-calc-1.3.2b/admin/old-ltconfig
fung-calc-1.3.2b/admin/old-ltmain.sh
fung-calc-1.3.2b/README
fung-calc-1.3.2b/AUTHORS
fung-calc-1.3.2b/COPYING
fung-calc-1.3.2b/ChangeLog
fung-calc-1.3.2b/INSTALL
fung-calc-1.3.2b/Makefile.am
fung-calc-1.3.2b/Makefile.in
fung-calc-1.3.2b/NEWS
fung-calc-1.3.2b/TODO
fung-calc-1.3.2b/acinclude.m4
fung-calc-1.3.2b/aclocal.m4
fung-calc-1.3.2b/config.h.in
fung-calc-1.3.2b/configure
fung-calc-1.3.2b/configure.in
fung-calc-1.3.2b/fung-calc.spec.in
fung-calc-1.3.2b/samplegraphs.fgc
fung-calc-1.3.2b/stamp-h.in
fung-calc-1.3.2b/subdirs
fung-calc-1.3.2b/configure.files
fung-calc-1.3.2b/Fung_calc.kdevelop
fung-calc-1.3.2b/Makefile.cvs
fung-calc-1.3.2b/Doxyfile
fung-calc-1.3.2b/Makefile.dist
fung-calc-1.3.2b/configure.in.in
fung-calc-1.3.2b/src/
fung-calc-1.3.2b/src/icons.h
fung-calc-1.3.2b/src/Makefile.am
fung-calc-1.3.2b/src/Makefile.in
fung-calc-1.3.2b/src/main.cpp
fung-calc-1.3.2b/src/fung-calc.desktop
fung-calc-1.3.2b/src/polargraph.xpm
fung-calc-1.3.2b/src/glfunctiongraph.xpm
fung-calc-1.3.2b/src/qMakefile
fung-calc-1.3.2b/src/statplot.xpm
fung-calc-1.3.2b/src/glcylindricalgraph.xpm
fung-calc-1.3.2b/src/parametricgraph.xpm
fung-calc-1.3.2b/src/functiongraph.xpm
fung-calc-1.3.2b/src/densityplot.xpm
fung-calc-1.3.2b/src/glpolargraph.xpm
fung-calc-1.3.2b/src/libfungcalc/
fung-calc-1.3.2b/src/libfungcalc/cartesian3dcoord.h
fung-calc-1.3.2b/src/libfungcalc/cylindricalcoord.h
fung-calc-1.3.2b/src/libfungcalc/expression.h
fung-calc-1.3.2b/src/libfungcalc/fungmath.h
fung-calc-1.3.2b/src/libfungcalc/fungpainter.h
fung-calc-1.3.2b/src/libfungcalc/fungparser.h
fung-calc-1.3.2b/src/libfungcalc/fungvector.h
fung-calc-1.3.2b/src/libfungcalc/polarcoord.h
fung-calc-1.3.2b/src/libfungcalc/rectcoord.h
fung-calc-1.3.2b/src/libfungcalc/statinfo.h
fung-calc-1.3.2b/src/libfungcalc/sphericalcoord.h
fung-calc-1.3.2b/src/libfungcalc/animator.h
fung-calc-1.3.2b/src/libfungcalc/commongraph.h
fung-calc-1.3.2b/src/libfungcalc/Makefile.am
fung-calc-1.3.2b/src/libfungcalc/Makefile.in
fung-calc-1.3.2b/src/libfungcalc/fungmath.cpp
fung-calc-1.3.2b/src/libfungcalc/animator.cpp
fung-calc-1.3.2b/src/libfungcalc/fungpainter.cpp
fung-calc-1.3.2b/src/libfungcalc/statinfo.cpp
fung-calc-1.3.2b/src/libfungcalc/rectcoord.cpp
fung-calc-1.3.2b/src/libfungcalc/polarcoord.cpp
fung-calc-1.3.2b/src/libfungcalc/fungvector.cpp
fung-calc-1.3.2b/src/libfungcalc/fungparser.cpp
fung-calc-1.3.2b/src/libfungcalc/expression.cpp
fung-calc-1.3.2b/src/libfungcalc/cartesian3dcoord.cpp
fung-calc-1.3.2b/src/libfungcalc/sphericalcoord.cpp
fung-calc-1.3.2b/src/libfungcalc/cylindricalcoord.cpp
fung-calc-1.3.2b/src/libfungcalc/commongraph.cpp
fung-calc-1.3.2b/src/libfungcalc/fparser/
fung-calc-1.3.2b/src/libfungcalc/fparser/fparser.hh
fung-calc-1.3.2b/src/libfungcalc/fparser/Makefile.am
fung-calc-1.3.2b/src/libfungcalc/fparser/Makefile.in
fung-calc-1.3.2b/src/libfungcalc/fparser/fparser.cc
fung-calc-1.3.2b/src/libfungcalc/fparser/fparser.txt
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/arclengthfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/definiteintegralfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/distancefunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/intersectionfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/mathfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/maximumfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/minimumfunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/zerofunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/meanvaluefunction.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/Makefile.am
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/Makefile.in
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/zerofunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/minimumfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/maximumfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/intersectionfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/arclengthfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/mathfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/distancefunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/definiteintegralfunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/meanvaluefunction.cpp
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/mathfunctionimplementor.h
fung-calc-1.3.2b/src/libfungcalc/mathfunctions/mathfunctionimplementor.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/
fung-calc-1.3.2b/src/libfungcalc/2D/basicgraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/expressiongraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/functiongraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/graphevent.h
fung-calc-1.3.2b/src/libfungcalc/2D/parametricgraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/polargraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/statplotgraph.h
fung-calc-1.3.2b/src/libfungcalc/2D/densityplot.h
fung-calc-1.3.2b/src/libfungcalc/2D/plotmodule.h
fung-calc-1.3.2b/src/libfungcalc/2D/whiskerplot.h
fung-calc-1.3.2b/src/libfungcalc/2D/scatterplot.h
fung-calc-1.3.2b/src/libfungcalc/2D/frequencyplot.h
fung-calc-1.3.2b/src/libfungcalc/2D/Makefile.am
fung-calc-1.3.2b/src/libfungcalc/2D/Makefile.in
fung-calc-1.3.2b/src/libfungcalc/2D/statplotgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/polargraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/parametricgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/graphevent.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/basicgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/functiongraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/expressiongraph.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/densityplot.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/plotmodule.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/whiskerplot.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/frequencyplot.cpp
fung-calc-1.3.2b/src/libfungcalc/2D/scatterplot.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/
fung-calc-1.3.2b/src/libfungcalc/3D/glbasicgraph.h
fung-calc-1.3.2b/src/libfungcalc/3D/glfunctiongraph.h
fung-calc-1.3.2b/src/libfungcalc/3D/glgraphevent.h
fung-calc-1.3.2b/src/libfungcalc/3D/glexpressiongraph.h
fung-calc-1.3.2b/src/libfungcalc/3D/glparametricgraph.h
fung-calc-1.3.2b/src/libfungcalc/3D/glpolargraph.h
fung-calc-1.3.2b/src/libfungcalc/3D/Makefile.am
fung-calc-1.3.2b/src/libfungcalc/3D/Makefile.in
fung-calc-1.3.2b/src/libfungcalc/3D/glparametricgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glfunctiongraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glbasicgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glpolargraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glexpressiongraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glcylindricalgraph.cpp
fung-calc-1.3.2b/src/libfungcalc/3D/glcylindricalgraph.h
fung-calc-1.3.2b/src/libfungcalcui/
fung-calc-1.3.2b/src/libfungcalcui/Makefile.am
fung-calc-1.3.2b/src/libfungcalcui/Makefile.in
fung-calc-1.3.2b/src/libfungcalcui/graph.cpp
fung-calc-1.3.2b/src/libfungcalcui/fungcolorbutton.cpp
fung-calc-1.3.2b/src/libfungcalcui/commongraphmain.cpp
fung-calc-1.3.2b/src/libfungcalcui/interface.cpp
fung-calc-1.3.2b/src/libfungcalcui/graphtypeinfo.h
fung-calc-1.3.2b/src/libfungcalcui/usage.ui
fung-calc-1.3.2b/src/libfungcalcui/mainwindowtype.h
fung-calc-1.3.2b/src/libfungcalcui/fungcolorbutton.h
fung-calc-1.3.2b/src/libfungcalcui/animationparamsdialog.ui.h
fung-calc-1.3.2b/src/libfungcalcui/interface.ui
fung-calc-1.3.2b/src/libfungcalcui/valuedialog.ui.h
fung-calc-1.3.2b/src/libfungcalcui/newgraphdialog.ui
fung-calc-1.3.2b/src/libfungcalcui/graph.h
fung-calc-1.3.2b/src/libfungcalcui/fungxmlhandler.cpp
fung-calc-1.3.2b/src/libfungcalcui/commongraphmain.h
fung-calc-1.3.2b/src/libfungcalcui/printertype.h
fung-calc-1.3.2b/src/libfungcalcui/newgraphdialog.ui.h
fung-calc-1.3.2b/src/libfungcalcui/zoomfactordialog.ui
fung-calc-1.3.2b/src/libfungcalcui/valuedialog.ui
fung-calc-1.3.2b/src/libfungcalcui/fungxmlhandler.h
fung-calc-1.3.2b/src/libfungcalcui/animationparamsdialog.ui
fung-calc-1.3.2b/src/libfungcalcui/zoomfactordialog.ui.h
fung-calc-1.3.2b/src/libfungcalcui/interface.ui.h
fung-calc-1.3.2b/src/libfungcalcui/2D/
fung-calc-1.3.2b/src/libfungcalcui/2D/Makefile.am
fung-calc-1.3.2b/src/libfungcalcui/2D/Makefile.in
fung-calc-1.3.2b/src/libfungcalcui/2D/basicgraphmain.cpp
fung-calc-1.3.2b/src/libfungcalcui/2D/expressiongraphmain.cpp
fung-calc-1.3.2b/src/libfungcalcui/2D/dummy.h
fung-calc-1.3.2b/src/libfungcalcui/2D/functiongraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/2D/polargraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/2D/parametricgraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/2D/dummy.cpp
fung-calc-1.3.2b/src/libfungcalcui/2D/statplotgraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/2D/statplotgraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/2D/expressiongraphmain.h
fung-calc-1.3.2b/src/libfungcalcui/2D/basicgraphmain.h
fung-calc-1.3.2b/src/libfungcalcui/2D/polargraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/2D/functiongraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/2D/densityplotmain.ui
fung-calc-1.3.2b/src/libfungcalcui/2D/parametricgraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/2D/densityplotmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/3D/
fung-calc-1.3.2b/src/libfungcalcui/3D/Makefile.am
fung-calc-1.3.2b/src/libfungcalcui/3D/Makefile.in
fung-calc-1.3.2b/src/libfungcalcui/3D/glbasicgraphmain.cpp
fung-calc-1.3.2b/src/libfungcalcui/3D/dummy.h
fung-calc-1.3.2b/src/libfungcalcui/3D/dummy.cpp
fung-calc-1.3.2b/src/libfungcalcui/3D/glfunctiongraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/3D/glpolargraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/3D/glfunctiongraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/3D/glcylindricalgraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/3D/glcylindricalgraphmain.ui
fung-calc-1.3.2b/src/libfungcalcui/3D/glpolargraphmain.ui.h
fung-calc-1.3.2b/src/libfungcalcui/3D/glbasicgraphmain.h
fung-calc-1.3.2b/src/translations/
fung-calc-1.3.2b/src/translations/Makefile.am
fung-calc-1.3.2b/src/translations/Makefile.in
fung-calc-1.3.2b/src/translations/fung-calc.es.qm
fung-calc-1.3.2b/src/translations/fung-calc.es.ts
fung-calc-1.3.2b/src/mimetypes/
fung-calc-1.3.2b/src/mimetypes/Makefile.am
fung-calc-1.3.2b/src/mimetypes/Makefile.in
fung-calc-1.3.2b/src/mimetypes/x-fgc.desktop
fung-calc-1.3.2b/src/icons/
fung-calc-1.3.2b/src/icons/Makefile.am
fung-calc-1.3.2b/src/icons/Makefile.in
fung-calc-1.3.2b/src/icons/hi16-app-fung_calc.png
fung-calc-1.3.2b/src/icons/hi32-app-fung_calc.png
fung-calc-1.3.2b/src/icons/hi48-app-fung_calc.png
fung-calc-1.3.2b/src/icons/hi64-app-fung_calc.png
fung-calc-1.3.2b/contrib/
fung-calc-1.3.2b/contrib/Makefile.am
fung-calc-1.3.2b/contrib/Makefile.in
fung-calc-1.3.2b/contrib/fung-calc.ebuild
fung-calc-1.3.2b/docs/
fung-calc-1.3.2b/docs/Makefile.am
fung-calc-1.3.2b/docs/Makefile.in
fung-calc-1.3.2b/docs/en/
fung-calc-1.3.2b/docs/en/animationparams.png
fung-calc-1.3.2b/docs/en/animationtoolbar.png
fung-calc-1.3.2b/docs/en/credits.docbook
fung-calc-1.3.2b/docs/en/functiongraph.png
fung-calc-1.3.2b/docs/en/index.docbook
fung-calc-1.3.2b/docs/en/installation.docbook
fung-calc-1.3.2b/docs/en/introduction.docbook
fung-calc-1.3.2b/docs/en/newgraph.png
fung-calc-1.3.2b/docs/en/Makefile.am
fung-calc-1.3.2b/docs/en/Makefile.in
marlon@marlon-laptop:~/Desktop$ ./configure
bash: ./configure: No such file or directory
marlon@marlon-laptop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
marlon@marlon-laptop:~/Desktop$ make install
make: *** No rule to make target `install'.  Stop.
marlon@marlon-laptop:~/Desktop$

---

### Post by RomeReactor on 2007-12-17
The .tar.gz package extracted as a folder named **fung-calc-1.3.2b**, so you need to enter that directory and then issue the rest of the commands:
```
cd fung-calc-1.3.2b
```
```
./configure
```
```
make
```
```
sudo make install
```

Before all that, open Nautilus and go in that folder to see if you can find a README or INSTALL file, so you can check if you need to install dependencies before compiling.

---

### Post by Marfish on 2007-12-17
Thanks for helping me out. Really have no idea what Im doing. Right now its giving me another error report when I tried to ./configure it.
marlon@marlon-laptop:~/Desktop/fung-calc-1.3.2b$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

---

### Post by RomeReactor on 2007-12-17
Try installing build-essential before trying ./configure again:
```
sudo apt-get install build-essential
```

What are you trying to install? it would be easier to look if there's a precompiled package; you can find many programs not available in the repositories in [GetDeb]("http://www.getdeb.net/").

---

