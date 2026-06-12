---
title: "two questions"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by purple unichorn on 2006-10-20
_First question:_ [SIZE=5]UK kebourd layout
[SIZE=3]i recenty installed kubuntu-desktop on my ubuntu 6.06 and i have have to type in uk layot(eg when i go to type @ i type " istead).
i can't find how to change to US layout.
_[SIZE=2]second question:[/SIZE]_[SIZE=2] [SIZE=5]Installing from source
[SIZE=3]i just downloaded a game called damonin and i have been extremy confused by it's install howto,
can someone please tell me what this means:
[http://www.daimonin.net/modules.php?op=modload&name=phpWiki&file=index&pagename=Source%20Client%20Install](http://www.daimonin.net/modules.php?op=modload&name=phpWiki&file=index&pagename=Source%20Client%20Install)

[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by purple unichorn on 2006-10-20
particually with the bit after un-tar

---

### Post by podunk on 2006-10-20
For the keyboard, at the top of your screen
System>Preferences>Keyboard>Layouts

For compiling you might give this page a go, there are several things you need to do before you start:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Every time I've compiled a game which calls for sdl it's turned into a pain. set aside a nice chunk of time for this. Good learning experience ahead. :-)

---

### Post by mthaddon on 2006-10-20
So "tar -zxvf PATH_TO_TGZFILE" basically means to "unzip" the file (z - gzip compression, x - extract, v - verify, or print output, f - we're dealing with  a file).

./configure
make
make install

This is your basic instructions for installing from source. Before you go any further, you'll need to install the "build-essential" package - this is a "meta-package" which installs everything you need to compile programs from source. It's not included in the default install because most of the things you're installing are from ".deb" files - pre-compiled binaries that are packaged by the nice folks at Ubuntu.

The first part is basically a pre-check, or configuration which verifies that you have the appropriate libraries/binaries installed. This is a shell script which you can look at with "less configure" or any text editor. The developers will generate it so that if, for instance, their application requires a specific version of sdl, it will confirm you have that. If not, you will receive an error message from the configure script. Typically you can solve any errors by searching apt for a package that matches (so, for instance "sudo apt-cache search sdl") and installing any -dev packages. 

The second part "make" actually builds all the binaries using (typically) gcc. 

The third part "make install" copies the binaries, libraries, documentation and any configuration files to the correct locations. You will probably need to do this as root ("sudo make install"), as it will be copying files to system folders that normal users don't have write access to.

If you're seeing specific error messages, try posting those and we'll see what we can do.

Thanks, Tom

---

