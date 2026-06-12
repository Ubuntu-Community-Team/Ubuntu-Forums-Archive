---
title: "[SOLVED] Problems with shared libraries"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Mittens on 2007-08-20
Hi all,

I'm a Linux beginner running a fresh install of Ubuntu Desktop 7.04 on a 32-bit PC.

One of the added programs I've just installed needs libraries that apparently aren't part of the main Ubuntu install (I get this kind of error message: "libpng.so.3: cannot open shared object file: no such file or directory").

One recommendation from the makers of the software is to "load an rpm that includes the PNG library" onto my system, and I don't know how to go about doing this with Ubuntu.  My googling suggests that I might be able to set the library up by installing something called "Feisty", which includes "libpng12-0", a library that seems appropriate here.

Is there an easy way for a beginner to install a shared PNG library on Ubuntu, and is there a way to ensure that software already installed will be able to find the library?  Thanks!

Mittens

---

### Post by lambros on 2007-08-20
The file "libpng.so.3" is part of the package "libpng3", which is in the Universe repository.  You'll have to enable the "Universe" repositories, they are not enabled by default.  You can do that from inside Synaptic Package Manager (go to System->Administration).  Then you should be able to find and install the "libpng3" package.

You don't need to do anything else afterwards.  That will install the shared library into your system, where your applications will automatically find it.

Regarding Ubuntu "Feisty" - it's just another name for version 7.04, which you're already running.

Good luck!
Lambros

---

### Post by schorsch on 2007-08-20
> **Mittens said:**
> Hi all,

I'm a Linux beginner running a fresh install of Ubuntu Desktop 7.04 on a 32-bit PC.

One of the added programs I've just installed needs libraries that apparently aren't part of the main Ubuntu install (I get this kind of error message: "libpng.so.3: cannot open shared object file: no such file or directory").

One recommendation from the makers of the software is to "load an rpm that includes the PNG library" onto my system, and I don't know how to go about doing this with Ubuntu.  My googling suggests that I might be able to set the library up by installing something called "Feisty", which includes "libpng12-0", a library that seems appropriate here.

Is there an easy way for a beginner to install a shared PNG library on Ubuntu, and is there a way to ensure that software already installed will be able to find the library?  Thanks!

Mittens
Hi, Ubuntu 7.04 is also called Feisty so you do not have to install again :-)
rpm's (Redhat Package Management) are used with linux distributions like SuSE or Redhat; every Debian based system uses packages that end with .deb. So stop looking for an rpm-file. You can convert rpm's into deb's but that will be another lesson in the future :-)
Right at the moment, just click:

System --> Administration --> Synaptic Package Manager

Then, after you typed your password, the program will open. Use the "Search" button to search for:

libpng

After that you are presented with six packages; choose "libpng12" and "libpng12-dev", right-click and choose "Mark for installation". When this is done, press apply ... 

Perhaps we will have to create a link to get your software running, but we will see ...

EDIT: libpng12 supersedes libpng3 so perhaps it is already installed and we have to create only a link ....

---

### Post by Mittens on 2007-08-20
Hi lambros and schorsch,

Thanks for the advice!  I installed libpng3, and this appears to have solved my problem (my software is now executing properly).

schorsch: I didn't see your advice regarding libpng12 until too late.  If I were to go back and install libpng12-deb, would this cause problems?

Mittens

---

### Post by schorsch on 2007-08-20
Hmm, I don't know ... perhaps ... but this should be fixed when you type in a terminal:
```
ln -s /usr/lib/libpng12.so /usr/lib/libpng.so.3
```
With this command you create a so called link from /usr/lib/libpng.so.3 to /usr/lib/libpng12.so.
Just think of your windows desktop: Every icon is normally just a shortcut to an application. Here /usr/lib/libpng.so.3 will be shortcut to /usr/lib/libpng12.so. And if it fails you can reinstall the package libpng3 again, don't worry ;-)

---

### Post by Mittens on 2007-08-20
Sounds good, schorsch!  Since the program is currently running fine, I'll stick with libpng3 for the moment, but will try upgrading to libpng-12 in the near future.

Thanks for your help!!!  :)

---

### Post by schorsch on 2007-08-20
Glad to hear that your application is running now. If everything is working for you I would not touch a running system. If there are some applications that will ask for the updated library in the future I would update then but not now. You can always start a new thread here if you have forgotten what I told you today.. :-)
Could you please mark this thread as solved then? This can be done via the "Thread Tools" link in the upper right corner ....

---

