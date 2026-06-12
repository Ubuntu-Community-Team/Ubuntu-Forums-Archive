---
title: "Installing a  .gz file..."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by ReaderRat on 2006-09-24
I have just downloaded mtink-1.0.13tar.gz to my Desktop (An Epson printer ink level checker). I don't know what to do with it. I am sure there is an  easy way to install it, but I need to know where to look for instructions. I googled and got pay sites. :confused:

---

### Post by NetworkGuy on 2006-09-24
From a terminal type 
```
tar -zxvf mtink-1.0.13.tar.gz
```

That will unzip/untar the file and allow you to work with what is inside.

---

### Post by PriceChild on 2006-09-24
Try using synaptic instead, search for mtink, and install the package.

Alternatively, type the following into a terminal:```
sudo apt-get update
sudo apt-get install mtink
```
This will install the package from the ubuntu repositories and will be much quicker and easier to install.

---

### Post by Omnios on 2006-09-24
Here is a link to a basic how to to install tarballs
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)

---

### Post by ReaderRat on 2006-09-24
> **PriceChild said:**
> Try using synaptic instead, search for mtink, and install the package.

Alternatively, type the following into a terminal:```
sudo apt-get update
sudo apt-get install mtink
```
This will install the package from the ubuntu repositories and will be much quicker and easier to install.
Apt-get returned "mtink not found".
I don't know how to search in synaptic. (I tried.)

---

### Post by ReaderRat on 2006-09-24
> **Omnios said:**
> Here is a link to a basic how to to install tarballs
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)
I got this far;

ben@ben-desktop:~/Desktop$ cd mtink-1.0.13a
ben@ben-desktop:~/Desktop/mtink-1.0.13a$ ./configure
bash: ./configure: No such file or directory
ben@ben-desktop:~/Desktop/mtink-1.0.13a$ ls
CHANGE.LOG            getGimVersion.sh  Makefile.ORG        README.MacOsX
checkMotifVersion.sh  html              mtink-all.spec      server
chooser               LEGGIMI           mtink-all.spec.ORG  staticLib.sh
Configure             LESE-MICH         mtink.spec          Temak
detect                LICENCE           mtink.spec.ORG      Themes
doc                   LISEZ-MOI         OLVASS_EL           utils
etc                   mainSrc           pyink               xpm
getGimpPluginDir.sh   Makefile          README

What next?

---

### Post by andiii on 2006-09-24
make
sudo make install


or

make
sudo checkinstall


or

look what the readme says :)

---

### Post by ReaderRat on 2006-09-24
> **andiii said:**
> make
sudo make install


or

make
sudo checkinstall


or

look what the readme says :)

make didn't work, and the readme said this (which I do not understand):

This beta version is not completely tested. In order to
compile mtink you must make sure that the Motif, openMotif or
Lesstif runtime and development package are installed.

A gimp plug-ins is also provided (gimp-mtink).

An ls of files is two posts above.

---

### Post by kaens on 2006-09-24
What happened when you tried to run make?

As an alternitave to manual compilation and installation, you might try using apt-get again, execpt for issuing
```
apt-cache search mtink
``` 
to find the package you want to install.

(I just did this, and the package is mtink...so if it's not there for you, you probably need to enable some repositories - see [here](http://ubuntuguide.org/wiki/Dapper#Repositories))

---

### Post by Omnios on 2006-09-24
DId you install ?build-essencials. Its a hole bunch of standard compiler stuff.

---

### Post by bodhi.zazen on 2006-09-24
Well, I do not know if this will help, but:

Frist I would install build-essential and checkinstall.

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```.

You may need to enable your repositories first.
```
sudo gedit /etc/apt/source.list
```

Remove the # in front of the repositories.

Then it appears you already have a make file as a part of the tar ball.

Try ```
cd ~/Desktop/mtink-1.0.13a
aptitude install openmotif libmotif-dev
sudo checkinstall
```

---

### Post by ReaderRat on 2006-09-24
[quote=kaens](I just did this, and the package is mtink...so if it's not there for you, you probably need to enable some repositories - see here)[/quote]
That is what I had to do. Had to fool around with synaptic for a while, but I finally did get the program(s) installed okay. Thank you very much, I learned a lot.

---

### Post by kaens on 2006-09-26
Hey, that's what it's all about!

---

