---
title: "compile .tar.gz"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by declanf6656 on 2008-03-22
how do i turn .tar.gz files into .deb files? or how do i compile or whatever .tar.gz files?

---

### Post by rsambuca on 2008-03-22
Basically the steps are:

1.  Extract the .tar.gz
2.  ./configure
3.  make
4.  sudo make install

Having said that, usually it is much easier to go directly from a .deb file, or use Synaptic Package Manager if it is in the repositories.  What is the package you are trying to install with this method?

Here is a [good site for your reference]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually"), if you can't find the package in the repositories.

---

### Post by declanf6656 on 2008-03-22
ummm a game, i found one in a deb file but it's not the latest version so i can't play online. [www.pokerth.net](www.pokerth.net) is the site the game is on. what do you mean by those 4 steps?

---

### Post by rsambuca on 2008-03-22
Did you try the linux binary installer?  That should be a one click installation.

---

### Post by declanf6656 on 2008-03-23
whats that?

---

### Post by Perfect Storm on 2008-03-23
```
cd ~/Desktop
wget http://downloads.sourceforge.net/pokerth/PokerTH-0.6.1-linux.zip?use_mirror=osdn
unzip PokerTH-0.6.1-linux.zip
cd PokerTH-0.6.1-linux
./pokerth.sh
```

should do it.

---

### Post by declanf6656 on 2008-03-23
does that work with other things aswell?

---

### Post by Perfect Storm on 2008-03-23
No. .tar.gz is just like a .zip file. It can contains everything. This one contains the files and a script that you need to run (./pokerth.sh) which launch the game in that folder.

---

### Post by declanf6656 on 2008-03-23
is there a way to turn them into .deb files?

---

### Post by Perfect Storm on 2008-03-23
That requires a bit of knowledge and patience to learn. I recommend one step at the time.


If so you need to grab the source codes, compile (make compiling scripts if they aren't available), build, make up some .deb scripts.

Other than that it's more safty to run software that comes outside Ubuntu repo in your home.

---

### Post by quinnten83 on 2008-03-23
i read on a local ubuntu forum that you can install the program checkinstall and by replacing the "make install" step with "check install" it creates a .deb.
I haven't tried it as I am too chicken to mess about with my system (I need it to be stable).

---

### Post by declanf6656 on 2008-03-23
how do i compile? sorry im a bit of a slow learner

---

### Post by Perfect Storm on 2008-03-23
Download the source to your Desktop and unpack it.

cd <into its folder>
ls -a


what's the output?




checkinstall makes a fake .deb - it can't solve dependencies etc. it used for quick uninstall of compiled applications.

---

### Post by declanf6656 on 2008-03-23
ok ive downloaded the program i want (hamachi) i unpacked it on the desktop, i opened terminal and navigated into the folder, i typed ls -a and it said no such command. what do i do?

---

### Post by Perfect Storm on 2008-03-23
it a lower case L not I


Edit:

Here's from the readme file of thte sourcelist:
> Requirements
============

To compile PokerTH you need following libs: 

Linux:
- Qt version >= 4.3.1  --> [http://trolltech.com/](http://trolltech.com/)
- libcrypt (e.g. version 0.9.7)  --> [http://www.openssl.org/](http://www.openssl.org/)
- libboost_thread, libboost_filesystem, libboost_datetime, libboost_program_options
  (version >= 1.34.1)  --> [http://www.boost.org/](http://www.boost.org/)
- libSDL_mixer, libSDL --> [http://www.libsdl.org/](http://www.libsdl.org/)

Windows:
see docs/build_vc_windows.txt




Basic Installation
==================

Linux:

  1. Type "cd path/to/the/sources". Then do for example "/usr/qt/4/bin/qmake pokerth.pro" to configure the makefile for your system.
     Pay attention that the QTDIR environment varialbe points to Qt4 not Qt3. For example QTDIR=/usr/qt/4.
     You can set this variable typing: "export QTDIR=/usr/qt/4"

  2. Type "make" to compile the package.

  3. Become root (typing "su") and type "make install" to install the program binary.

First make sure you have installed all the required libs and their devs/headers. Also get build-essential and checkinstall

---

### Post by declanf6656 on 2008-03-23
here is what happened

thanks but the first thing you suggested worked for poker TH

---

### Post by Perfect Storm on 2008-03-23
Thought you're going for the poker game?

---

### Post by declanf6656 on 2008-03-23
sorry for the confusion but the first thing you suggested worked for the poker game

---

### Post by Perfect Storm on 2008-03-23
ok, first thing first. When compiling something you need the basic tools for that. In ubuntu there's a meta-package which do that - build-essential. install it.

Next read the readme files to see what the devs writes (special compiling methode, libs etc.)

---

### Post by declanf6656 on 2008-03-23
sorry i noticed there was a readme, i typed make install but it said permission denied. this is the only account. what do i do?

---

### Post by Perfect Storm on 2008-03-23
It says it needs root/admin.

use **sudo** infront of the command.

---

### Post by declanf6656 on 2008-03-23
ok thanks now how do i do this?

	Run 'hamachi-init' to generate crypto identity (any account).

	Run 'hamachi start' to launch Hamachi daemon.

	Run 'hamachi login' to put the daemon online and to create an account.

	Run 'hamachi join <network>' to join the network.

	Run 'hamachi go-online <network>' to go online in the network.

	Run 'hamachi list' to list network members and their status.

---

### Post by Perfect Storm on 2008-03-23
Tried running them via terminal?
I'm saying this because I don't know that application.

---

### Post by declanf6656 on 2008-03-23
how do i run something via terminal?

---

### Post by Perfect Storm on 2008-03-23
just type in the command it says - that should do it.

---

### Post by Perfect Storm on 2008-03-23
Please don't hijack this thread. Start a new one.

---

### Post by linuxtoindia on 2008-03-23
please help..

---

