---
title: "i found a program on the internet.  need help installing."
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-02-02
[http://ktoon.toonka.com/]("http://ktoon.toonka.com/")

i want to install this but i don't know how to do it.  i downloaded and unzipped to my desktop and read the install instructions:

> 
Installing and Running KToon 2D Animation Toolkit

Before you begin, you need Qt version 3.3.2 or later to be installed.

First, download the source tarball from [http://ktoon.toonka.com/modules.php?op=modload&name=Downloads](http://ktoon.toonka.com/modules.php?op=modload&name=Downloads).

Unpack it into your desired location and go into the uncompressed directory:
  $ tar xvfz ktoon-0.7.3.tar.gz
  $ cd ktoon/

Generate a Makefile that has options according to your Qt distribution:
  $ qmake ktoon.pro

Compile the KToon's source code:
  $ make

And finally, run the application from the current directory:
  $ ./bin/ktoon

If you want to save disk space, remove the object files:
  $ make clean


it seems like it would be easy.  but i don't know how to navigate in the terminal.

also, is there a better place to unzip it to?

---

### Post by JNowka on 2006-02-02
Do you have qt downloaded and installed?

if not you can easily download it from packages.ubuntu.com
[http://packages.ubuntu.com/breezy/devel/qt3-designer](http://packages.ubuntu.com/breezy/devel/qt3-designer)

though depending on your KDE version and/or updated files could result in a couple hours of downloading

---

### Post by insub2 on 2006-02-02
[QUOTE=JNowka]Do you have qt downloaded and installed?

if not you can easily download it from packages.ubuntu.com
[http://packages.ubuntu.com/breezy/devel/qt3-designer](http://packages.ubuntu.com/breezy/devel/qt3-designer)

though depending on your KDE version and/or updated files could result in a couple hours of downloading[/QUOTE]


how would i check to see if i have QT?

i've done all the updates for ubuntu.

---

### Post by az on 2006-02-02
Install the libqt3-mt-dev package

---

### Post by aysiu on 2006-02-02
[QUOTE=insub2]it seems like it would be easy.  but i don't know how to navigate in the terminal.[/QUOTE] [quote=azz]Install the libqt3-mt-dev package[/quote] In other words, go to Applications > Accessories > Terminal and type ```
sudo apt-get update
sudo apt-get install libqt3-mt-dev
```

---

### Post by insub2 on 2006-02-02
now what?

---

### Post by rawhead on 2006-04-29
Hi all

I newbie in linux / ubuntu , so i got question too :) . What packages KToon-ver 08 needs? And how i install those on ubuntu?

---

