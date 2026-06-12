---
title: "Can somebody convert this for me and also show me the steps?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by DilfATX on 2008-02-07
Is there a simple app that can convert these types of files to .deb or install them in an automated fashion.  Or is it always going to be a manual thing?  

The app I'm wanting to convert is PSP Manager for Linux

[http://superb-west.dl.sourceforge.net/sourceforge/qpspmanager/qpspmanager-2.0.2.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/qpspmanager/qpspmanager-2.0.2.tar.gz)

If somebody shows me how they did it I would be so greatfull.  

If there is a simple app that can do this I would surely love to know.  Thanks again guys for the help you give on this forum.

---

### Post by y-lee on 2008-02-07
> Is there a simple app that can convert these types of files to .deb or install them in an automated fashion. Or is it always going to be a manual thing?

Making a deb is quite involved, something I've never tried and certainly much harder than compiling source code. See [How to make a deb package.]("http://www.linuxdevices.com/articles/AT8047723203.html"). I also know of no automated way to compile source code tho I suppose one could try to write a script for it. More hassle than it is worth. :lolflag:

To compile this app first lets install the dependencies:

```
sudo apt-get install qt3-dev-tools libqt3-mt-dev
```

Uncompress your tar file in your home directory. Cd to that directory
Type these three commands into the terminal one at a time to compile this app.

```
qmake
make
sudo make install
```

*Any error messages post back here*. I got this info somewhere else but it should work. I haven't compiled this app tho i did download it and look at what was inside of it. I have no desire to compile it , don't need and I use dapper might run into weird dependency issues.

Hope this helps any questions feel free to post back here.

---

### Post by jken146 on 2008-02-07
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ibanez on 2008-02-07
What does that psp manager app do that you cant do by plugging usb cable into ubuntu?

I can do everything I need with just the cable??

---

### Post by Aquaman420 on 2008-02-07
As far as making .deb packages there is a program in the repos called "alien" that I have used several times with success.  I did a demo run with your package and it converted great for me.  Scratch that.  I don't think it did work.

---

### Post by Thelasko on 2008-02-07
Alien is for converting an binary packages for an other Linux flavors into a .deb. (like converting a Red Hat .rpm file)  It will not compile from source.  You have a few options:

1. You can try compiling from source as y-lee noted.  It will install the program on your machine but without dependency resolution (won't install any other programs your program requires to run), menus under GNOME or have an easy uninstall.  

2. Try to create your own .deb file which I don't know how to do, but I know it's not easy.  (mostly that dependency stuff again)

3. Wait for someone else to create the .deb and upload it to the repositories (it will happen eventually it's listed as a to do item on launchpad)

4. Google around to see if somebody has already created a .deb or .rpm that you can use. (at your own risk)

The hard part about using Linux is dependency resolution.  It's why people choose Debian or Ubuntu, because Synaptic handles all of that for you.  Unfortunately you won't be on the cutting edge because somebody has to sit down and work out what this program needs to run on your machine.  I recommend sitting tight until all of it is resolved by the professionals.  I have used other distributions and I have decided I can deal with slightly older software as long as I don't have to deal with dependency hell.

---

### Post by y-lee on 2008-02-07
> **Thelasko said:**
> The hard part about using Linux is dependency resolution.  It's why people choose Debian or Ubuntu, because Synaptic handles all of that for you.  Unfortunately you won't be on the cutting edge because somebody has to sit down and work out what this program needs to run on your machine.  I recommend sitting tight until all of it is resolved by the professionals.  I have used other distributions and I have decided I can deal with slightly older software as long as I don't have to deal with dependency hell.

Amen on Dependency problems, I have had some serious problems trying to resolve them compiling certain apps.

Creating a menu item in gnome is a rather minor thing. But any other dependences this program needs other than what I list above I don't know. Make or configure will usually complain about them, tho sometimes cryptically. Third party debs sometimes cause problems...ask me how i know that. :lolflag:


Waiting for an app to be added to the repos is the easiest, seldom have any problems then. But if DilfATX wishes to try to install this app we can try to help that is what these forums are for. No promises tho. Some things are beyond me it seems.

---

### Post by jw5801 on 2008-02-07
You could try using "checkinstall" instead of "make install"! checkinstall creates a crude .deb package (I don't think it worries about dependencies or anything), which you can then install using dpkg and remove again using apt or dpkg (or synaptic, even, for that matter).

---

### Post by DilfATX on 2008-02-07
> **y-lee said:**
> Making a deb is quite involved, something I've never tried and certainly much harder than compiling source code. See [How to make a deb package.]("http://www.linuxdevices.com/articles/AT8047723203.html"). I also know of no automated way to compile source code tho I suppose one could try to write a script for it. More hassle than it is worth. :lolflag:

To compile this app first lets install the dependencies:

```
sudo apt-get install qt3-dev-tools libqt3-mt-dev
```

Uncompress your tar file in your home directory. Cd to that directory
Type these three commands into the terminal one at a time to compile this app.

```
qmake
make
sudo make install
```

*Any error messages post back here*. I got this info somewhere else but it should work. I haven't compiled this app tho i did download it and look at what was inside of it. I have no desire to compile it , don't need and I use dapper might run into weird dependency issues.

Hope this helps any questions feel free to post back here.

I beleive I did get some errors..here is the output i got..

> rey@rey-desktop:/home$ cd /home/rey/qpspmanager-2.0.2
rey@rey-desktop:~/qpspmanager-2.0.2$ qmake
WARNING: Found potential symbol conflict of mainwindow.cpp (src/mainwindow.cpp) in SOURCES
WARNING: Found potential symbol conflict of mainwindow.h (src/mainwindow.h) in HEADERS
WARNING: Found potential symbol conflict of optionswidget.cpp (src/optionswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of optionswidget.h (src/optionswidget.h) in HEADERS
WARNING: Found potential symbol conflict of videoswidget.cpp (src/videoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of videoswidget.h (src/videoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of applicationswidget.cpp (src/applicationswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of applicationswidget.h (src/applicationswidget.h) in HEADERS
WARNING: Found potential symbol conflict of backupswidget.cpp (src/backupswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of backupswidget.h (src/backupswidget.h) in HEADERS
WARNING: Found potential symbol conflict of isoswidget.cpp (src/isoswidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of isoswidget.h (src/isoswidget.h) in HEADERS
WARNING: Found potential symbol conflict of helpwidget.cpp (src/helpwidget.cpp) in SOURCES
WARNING: Found potential symbol conflict of helpwidget.h (src/helpwidget.h) in HEADERS
rey@rey-desktop:~/qpspmanager-2.0.2$ make
Makefile:592: warning: overriding commands for target `obj/mainwindow.o'
Makefile:318: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:599: warning: overriding commands for target `obj/optionswidget.o'
Makefile:350: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:609: warning: overriding commands for target `obj/videoswidget.o'
Makefile:402: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:618: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:411: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:626: warning: overriding commands for target `obj/backupswidget.o'
Makefile:419: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:632: warning: overriding commands for target `obj/isoswidget.o'
Makefile:425: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:642: warning: overriding commands for target `obj/helpwidget.o'
Makefile:519: warning: ignoring old commands for target `obj/helpwidget.o'
Makefile:726: warning: overriding commands for target `obj/moc_mainwindow.o'
Makefile:652: warning: ignoring old commands for target `obj/moc_mainwindow.o'
Makefile:729: warning: overriding commands for target `obj/moc_optionswidget.o'
Makefile:664: warning: ignoring old commands for target `obj/moc_optionswidget.o'
Makefile:733: warning: overriding commands for target `obj/moc_videoswidget.o'
Makefile:684: warning: ignoring old commands for target `obj/moc_videoswidget.o'
Makefile:736: warning: overriding commands for target `obj/moc_applicationswidget.o'
Makefile:687: warning: ignoring old commands for target `obj/moc_applicationswidget.o'
Makefile:739: warning: overriding commands for target `obj/moc_backupswidget.o'
Makefile:695: warning: ignoring old commands for target `obj/moc_backupswidget.o'
Makefile:742: warning: overriding commands for target `obj/moc_isoswidget.o'
Makefile:698: warning: ignoring old commands for target `obj/moc_isoswidget.o'
Makefile:751: warning: overriding commands for target `obj/moc_helpwidget.o'
Makefile:716: warning: ignoring old commands for target `obj/moc_helpwidget.o'
Makefile:805: warning: overriding commands for target `obj/moc_mainwindow.cpp'
Makefile:754: warning: ignoring old commands for target `obj/moc_mainwindow.cpp'
Makefile:808: warning: overriding commands for target `obj/moc_optionswidget.cpp'
Makefile:763: warning: ignoring old commands for target `obj/moc_optionswidget.cpp'
Makefile:811: warning: overriding commands for target `obj/moc_videoswidget.cpp'
Makefile:772: warning: ignoring old commands for target `obj/moc_videoswidget.cpp'
Makefile:814: warning: overriding commands for target `obj/moc_applicationswidget.cpp'
Makefile:775: warning: ignoring old commands for target `obj/moc_applicationswidget.cpp'
Makefile:817: warning: overriding commands for target `obj/moc_backupswidget.cpp'
Makefile:781: warning: ignoring old commands for target `obj/moc_backupswidget.cpp'
Makefile:820: warning: overriding commands for target `obj/moc_isoswidget.cpp'
Makefile:784: warning: ignoring old commands for target `obj/moc_isoswidget.cpp'
Makefile:829: warning: overriding commands for target `obj/moc_helpwidget.cpp'
Makefile:802: warning: ignoring old commands for target `obj/moc_helpwidget.cpp'
/usr/share/qt3/bin/uic src/mainwindow.ui -o ui/mainwindow.h
uic: File generated with too recent version of Qt Designer (4.0 vs. 3.3.7)
make: *** [ui/mainwindow.h] Error 1
rey@rey-desktop:~/qpspmanager-2.0.2$ sudo make install
Makefile:592: warning: overriding commands for target `obj/mainwindow.o'
Makefile:318: warning: ignoring old commands for target `obj/mainwindow.o'
Makefile:599: warning: overriding commands for target `obj/optionswidget.o'
Makefile:350: warning: ignoring old commands for target `obj/optionswidget.o'
Makefile:609: warning: overriding commands for target `obj/videoswidget.o'
Makefile:402: warning: ignoring old commands for target `obj/videoswidget.o'
Makefile:618: warning: overriding commands for target `obj/applicationswidget.o'
Makefile:411: warning: ignoring old commands for target `obj/applicationswidget.o'
Makefile:626: warning: overriding commands for target `obj/backupswidget.o'
Makefile:419: warning: ignoring old commands for target `obj/backupswidget.o'
Makefile:632: warning: overriding commands for target `obj/isoswidget.o'
Makefile:425: warning: ignoring old commands for target `obj/isoswidget.o'
Makefile:642: warning: overriding commands for target `obj/helpwidget.o'
Makefile:519: warning: ignoring old commands for target `obj/helpwidget.o'
Makefile:726: warning: overriding commands for target `obj/moc_mainwindow.o'
Makefile:652: warning: ignoring old commands for target `obj/moc_mainwindow.o'
Makefile:729: warning: overriding commands for target `obj/moc_optionswidget.o'
Makefile:664: warning: ignoring old commands for target `obj/moc_optionswidget.o'
Makefile:733: warning: overriding commands for target `obj/moc_videoswidget.o'
Makefile:684: warning: ignoring old commands for target `obj/moc_videoswidget.o'
Makefile:736: warning: overriding commands for target `obj/moc_applicationswidget.o'
Makefile:687: warning: ignoring old commands for target `obj/moc_applicationswidget.o'
Makefile:739: warning: overriding commands for target `obj/moc_backupswidget.o'
Makefile:695: warning: ignoring old commands for target `obj/moc_backupswidget.o'
Makefile:742: warning: overriding commands for target `obj/moc_isoswidget.o'
Makefile:698: warning: ignoring old commands for target `obj/moc_isoswidget.o'
Makefile:751: warning: overriding commands for target `obj/moc_helpwidget.o'
Makefile:716: warning: ignoring old commands for target `obj/moc_helpwidget.o'
Makefile:805: warning: overriding commands for target `obj/moc_mainwindow.cpp'
Makefile:754: warning: ignoring old commands for target `obj/moc_mainwindow.cpp'
Makefile:808: warning: overriding commands for target `obj/moc_optionswidget.cpp'
Makefile:763: warning: ignoring old commands for target `obj/moc_optionswidget.cpp'
Makefile:811: warning: overriding commands for target `obj/moc_videoswidget.cpp'
Makefile:772: warning: ignoring old commands for target `obj/moc_videoswidget.cpp'
Makefile:814: warning: overriding commands for target `obj/moc_applicationswidget.cpp'
Makefile:775: warning: ignoring old commands for target `obj/moc_applicationswidget.cpp'
Makefile:817: warning: overriding commands for target `obj/moc_backupswidget.cpp'
Makefile:781: warning: ignoring old commands for target `obj/moc_backupswidget.cpp'
Makefile:820: warning: overriding commands for target `obj/moc_isoswidget.cpp'
Makefile:784: warning: ignoring old commands for target `obj/moc_isoswidget.cpp'
Makefile:829: warning: overriding commands for target `obj/moc_helpwidget.cpp'
Makefile:802: warning: ignoring old commands for target `obj/moc_helpwidget.cpp'
make: Nothing to be done for `install'.
rey@rey-desktop:~/qpspmanager-2.0.2$ 


---

### Post by y-lee on 2008-02-07
```
 I beleive I did get some errors..here is the output i got..
```

Indeed you do :confused:

From that output it appears to me you have conflicting libraries header files or something like that going on.

what version of Ubuntu are you running? It is looking like you need Qt4 to me instead of Qt3. :confused:

For future reference if make or configure or qmake give warnings no use to go any further, most likely it will not compile or if it does it won't work right. there may be exceptions to that but you usually want to stop with the first set of warnings or errors and try to figure that out.

And to make the forums easier to read wrap code tags around terminal output the ** #** button at the top of this text box :)

What version of ubuntu ya have might help us figure this out. What you need may or may not be available for your version, as qt is rather important stuff for Ubuntu and I'm not sure one should upgrade it to something not found in the repos.

Also what is the output of
```
qmake -v
```

---

### Post by y-lee on 2008-02-07
I think all those errors is the version of qmake set as default by Ubuntu. Wondering if ya have the version of qmake you need or if ya can install it and then ya gotta change a few links. If it is possible it going to be a big hassle. And i can't compile this on dapper I've done figured that out, the needed libraries are too outta date.

---

### Post by mc4man on 2008-02-07
assuming you have builds depends try - ```
qmake-qt4
``` followed by make

edit:works fine - you need qt4-dev-tools and libqt4-dev ,   you can leave your qt3 packages installed
as far as install/running don't know what you'd need  - probably a somewhat fully enabled ffmpeg
if not already installed get checkinstall - after the make go sudo checkinstall  - will make life easier with future versions

---

### Post by Thelasko on 2008-02-08
<sarcasm>Since this program is so well documented we know exactly what the problem is.</sarcasm>

Seriously, this program has no documentation.  How is anybody supposed to figure out how to compile it?  This is probably the reason there are no .deb files in the repositories.

Edit:  My point being, if we can't figure out how to get it to compile, you might have to go bug the author.

---

