---
title: "How do I install things without apt-get?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-21
I want to learn how to install things old-school, without apt-get.

Why? 'Cause it feels like writing "fix my PC" when I use the apt-get, it just does everything for me.

The only thing I succeded installing without apt-get was TeamSpeak, and it used a Windows-like interface for the installer.

---

### Post by Zelut on 2005-06-21
Man, after years of fighting with programs to install manually I love apt-get.  It makes things a breeze to install & uninstall... but if you really want to.

If you want to install from source you'll need to:
1. download the source packages.
2. You then extract them (using archive manager or command line)
3. run sudo ./configure in the extracted directory to configure the program to your system & find any dependencies / missing packages (also install those by hand if needed)
4.run sudo ./make & sudo ./make install

It isn't always terribly hard but you run into a lot more problems than just using apt-get.

1. if you need a package for dependency you'll need to install those too.  apt-get does that automatically
2. packages installed manually will not automatically add themselves to your gnome-panel bar.  You'll have to do that manually as well editing the .desktop file in /etc/applications/

I hope I dont sound too pessimistic... I just really appreciate apt-get after living without it.

---

### Post by SGC on 2005-06-21
If you want something in between apt-get and compiling from the source, then use .deb packages. 

All you need to do is **dpkg -i PACKAGE_NAME.deb** and the package will be installed , but before doing that you need to install all the package's dependencies.

---

### Post by Trojan1313 on 2005-06-21
[QUOTE=SGC]If you want something in between apt-get and compiling from the source, then use .deb packages. 

All you need to do is **dpkg -i PACKAGE_NAME.deb** and the package will be installed , but before doing that you need to install all the package's dependencies.[/QUOTE]
 Perhaps I too will appreciate apt-get more when I've tried the manual install. :)
So first line is:
sudo ./configure
sudo ./make
sudo ./make install

And the dot is the path to the files?
For example /mydir/makefile would have the dot /mydir/ ?

---

### Post by UbuWu on 2005-06-21
If you install checkinstall (sudo apt-get checkinstall) and replace sudo make install with sudo checkinstall, it is very easy to remove your program afterwards. You can then just remove it with apt-get or synaptic.

---

### Post by estel on 2005-06-21
Placing a . in front of the file name makes it look for that file in the directory that you're currently browsed in. Otherwise it'll look for a command of that name in /bin or something silly whereas you just want it to run a program in the local directory.

---

### Post by Trojan1313 on 2005-06-21
[QUOTE=estel]Placing a . in front of the file name makes it look for that file in the directory that you're currently browsed in. Otherwise it'll look for a command of that name in /bin or something silly whereas you just want it to run a program in the local directory.[/QUOTE]
 So a click on the browser that displayes the dir I want to use followed by a click on the terminal means . will be what I want? :)

---

### Post by az on 2005-06-21
Try Slackware.

---

### Post by Trojan1313 on 2005-06-21
...why?

EDIT:
kamine@ubuntu:~/Desktop/lmx-mice$ sudo ./configure
Password:
sudo: ./configure: command not found

What's wrong here? =/

---

### Post by poofyhairguy on 2005-06-21
[QUOTE=Trojan1313]...why?

EDIT:
kamine@ubuntu:~/Desktop/lmx-mice$ sudo ./configure
Password:
sudo: ./configure: command not found

What's wrong here? =/[/QUOTE]


If you want to do things the old fashion way, you need to install some things with apt-get first.

> sudo apt-get install build-essential

Even though personally I use Ubuntu to avoid the source files!

---

### Post by Trojan1313 on 2005-06-21
And what if there aren't any binaries? Like in this case. :)

---

### Post by cwaldbieser on 2005-06-21
It is a standard convention that the author(s) of the software include the files README and INSTALL in the root folder of their source distribution.  You should always read these first, as they usually mention any particular quirks you need to be aware of when trying to build and install the software.  In a majority of cases, the steps are:

```
$ ./configure
$ make
$ sudo make install
```

In the majority of cases, only the installation step should be done as root.  Also, in a lot of cases, you are going to get errors during one of the steps because you forgot to set some environment variable, or you don't have library headers installed, or something of that nature.

The configure step uses checks out your system and creates a makefile for you based on when you have libraries and header files installed on your system.  "configure" is just the name of a script.  By convention, it is called configure.  In theory, the script could be called anything.  In practice, it is called "configure" most of the time.  It will give you errors if it can't find something it expects.

The make step runs the makefile.  This builds the software from source in many cases.  For example, C programs could be compiled.  All sorts of build tools can be launched from make.  Many of them will tend to transform source documents into some sort of binary.

The last step installs the software on your system.  This will need root permissions if it tries to install in /usr/local/bin (which is a common default), because only root has write permissions on those directories.

I have seen different source packages that use different tool-chains, though.  It always pays to read the README first.

---

### Post by Trojan1313 on 2005-06-21
Say I want to install /home/kamine/Desktop/lmx-mice, how do I do this?

---

### Post by cwaldbieser on 2005-06-21
Truth to tell, I have no idea what lmx-mice is supposed to be.  After a quick Google, I found a tarball that had a makefile and some source files in it, but no docs describing what the software was supposed to do.

If it were an executable program, then to manually "install" it, you would just move the program to someplace in your path.  To install it system wide, that would normally be somewhere like /usr/local/bin.  If it were a shared library, then maybe /usr/local/lib.

If there isn't any documentation, then it can be really hard to figure out what you're supposed to do with any piece of software.

---

### Post by POET250 on 2005-06-22
alright I have not even had the linux installed a week and have been trying to find/load drivers  and install programs like opera and have failed miserably.  I have the  .deb folder for opera sitting on my desktop but when I try to dpkg -i it it 
     
"poet250@ubuntu:~$ sudo dpkg -i /home/poet250/Desktop/opera-static_8.01-20050615.1-qt_en_i386.deb
(Reading database ... 62564 files and directories currently installed.)
Preparing to replace opera-static 8.01-20050615.1 (using .../opera-static_8.01-20050615.1-qt_en_i386.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (8.01-20050615.1) ..."

on me and doesn't install  ](*,) 
all help much appreciated

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=cwaldbieser]Truth to tell, I have no idea what lmx-mice is supposed to be.  After a quick Google, I found a tarball that had a makefile and some source files in it, but no docs describing what the software was supposed to do.

If it were an executable program, then to manually "install" it, you would just move the program to someplace in your path.  To install it system wide, that would normally be somewhere like /usr/local/bin.  If it were a shared library, then maybe /usr/local/lib.

If there isn't any documentation, then it can be really hard to figure out what you're supposed to do with any piece of software.[/QUOTE]
It's a driver for Logitech's MX-series. In other words, a mouse driver. :)

---

### Post by POET250 on 2005-06-22
yea i've been trying to find drivers for my mx 1000 from logitech

---

### Post by cvogel on 2005-06-22
It is good to know how to install stuff without the .deb packages or the binaries... compiling source is something you'll have to do when working with daily compiled drivers and stuff.. Even though most of what you want can be found on Synaptic, you'll come across things you'll need to compile sooner or later...like the latest madwifi drivers for wireless adapters.  Make sure you install the linux-headers for your kernel as well as those build-essential tools.

---

### Post by POET250 on 2005-06-22
well it would be nice to be able to install .deb packages but i have not found a place that explains the process.  and i miss the forward and back buttons on my mx 1000 mouse (makes surfing the web easier)

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=POET250]well it would be nice to be able to install .deb packages but i have not found a place that explains the process.  and i miss the forward and back buttons on my mx 1000 mouse (makes surfing the web easier)[/QUOTE]

Then you want this howto:

[http://www.ubuntuforums.org/showthread.php?t=28374&highlight=button](http://www.ubuntuforums.org/showthread.php?t=28374&highlight=button)

---

### Post by POET250 on 2005-06-23
seems i fudged it good since trying to get my forward and back buttons.  X server will not start and i'm not sure how to fix it.  i have a good guess at how i screwed it up but don't know how to fix it.

i screwed up this step- I made a script file called "mouse.sh", like the following, and put it in "Sessions">"start programs" on Gnome. Don't forget to make it executable (chmod +x mouse)

#!/bin/sh
exec xmodmap -e "pointer = 1 2 3 6 7 4 5 8 9" &
exec imwheel -k -b "67" &
exec $REALSTARTUP

i added that section of code directly into the start programs tab within the sessions manager from the system portion of the bar at the top of the screen

please help

---

### Post by jensyt on 2005-06-23
[QUOTE=POET250]alright I have not even had the linux installed a week and have been trying to find/load drivers  and install programs like opera and have failed miserably.  I have the  .deb folder for opera sitting on my desktop but when I try to dpkg -i it it 
     
"poet250@ubuntu:~$ sudo dpkg -i /home/poet250/Desktop/opera-static_8.01-20050615.1-qt_en_i386.deb
(Reading database ... 62564 files and directories currently installed.)
Preparing to replace opera-static 8.01-20050615.1 (using .../opera-static_8.01-20050615.1-qt_en_i386.deb) ...
Unpacking replacement opera-static ...
Setting up opera-static (8.01-20050615.1) ..."

on me and doesn't install  ](*,) 
all help much appreciated[/QUOTE]

What happens as of this point, exactly? Does it finish?

---

### Post by POET250 on 2005-06-23
no jenst it goes from setting up opera static to a new input line it sucks like that

---

