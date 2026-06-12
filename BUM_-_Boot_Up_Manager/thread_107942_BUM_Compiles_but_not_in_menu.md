---
title: "BUM Compiles but not in menu"
date: 2005-12-24
forum: BUM - Boot Up Manager
---

### Post by No-Brain on 2005-12-24
I compiled the latest version of BUM from the tar ball.  I managed to get it to compile, i.e. /usr/local/bin there is a file called bum, a perl script?

It does not appear in my Gnome/Ubutu System/Admistration menu.

Can I add it manually?

If it's a perl script, why does it need to be compiled?

TIA
Roger

---

### Post by saltydog on 2005-12-27
[QUOTE=No-Brain]I compiled the latest version of BUM from the tar ball.  I managed to get it to compile, i.e. /usr/local/bin there is a file called bum, a perl script?

It does not appear in my Gnome/Ubutu System/Admistration menu.

Can I add it manually?

If it's a perl script, why does it need to be compiled?

TIA
Roger[/QUOTE]

In fact it doesn't need to be "compiled", but "built". When you run 

make && sudo make install

the Makefile provides to check if all needed dependecies are on your pc, copy the files on specific folders (there are several files, libraries are on another folder), create the desktop entry for the menu, put the translation files into the proper directories...and so on.

If you have configured it to be installed in /usr/local you can't find the menu entry in Grome! In order to have it, you should run (as reported on the web site [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html) ):

tar -xvzf bum-2.1.3.tar.gz
cd bum-2.1.3
./configure --prefix=/usr
make
sudo make install

Read the INSTALL file for configuration options.

Anyway, if you run Ubuntu Dapper or Debian testing/unstable, you can just do:

sudo apt-get install bum

If you are running Breezy,  download the latest .deb package and install it with  dpkg -i

---

### Post by No-Brain on 2005-12-27
Thanks for the reply, and the explanation.  Missed the instructions on the web site.  Just did a ./configure - Make - Make install, no switches.

I know just enough to be dangerous.

TIA
Roger

---

