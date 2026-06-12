---
title: "Problem with installation of Ktoon!"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-02-08
Hi, 

I'm trying to install Ktoon but I can't. I'v already installed qt4 and downloaded ktoon0.8.0. To install it I get this message :
>  ./build.sh -prefix /usr/lib
 *  Error: you need to run the command "./configure" first
mehdi@mehdi-desktop:~/download/ktoon$ ./configure
scripts/global: line 52: -query: command not found
scripts/global: line 65: [: too many arguments
scripts/global: line 70: -query: command not found
 *  Using Qt:
 *  Checking for aspell... no.
 *  Checking for sound... no.
 *  Checking for gif... no.
 *  Checking for ffmpeg 0.4.9... no.
 *  Checking for ming... no.

**************************************
 *  KToon is configured, if you want to clean configuration, execute 'make -f Makefile.common confclean'
**************************************

I'm following the instruction of this site: [SITE]("http://ktoon.toonka.com/documentation/index.php?title=Accesing_Source_Code_by_using_SVN")
Could you guide me please?

Thanks,

---

### Post by ramjet_1953 on 2007-02-08
Use the following link to download a deb package and then just install it by right clicking on the package in Nautilus and selecting install with debi package manager.

[http://people.debian.org/~juanma/packages/ktoon/](http://people.debian.org/~juanma/packages/ktoon/)

Regards,
Roger :cool:

---

### Post by linux-beginner on 2007-02-08
Thanks,
I'v installed it but it crashes.
> mehdi@mehdi-desktop:~$ ktoon
[Initializing DApplication]
[Initializing DConfig]
[Initializing DConfigDocument]
*********Init configuration file : "/home/mehdi/.ktoon/ktoon.cfg"
ktoon is crashing with signal 11 :(
QPixmap::fromImage: Cannot convert a null image
QCoreApplication::exec: The event loop is already running

I went to [debian site]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=396130") but didn't understand how i can solve it.
:(

---

### Post by ramjet_1953 on 2007-02-08
It looks like there is a known problem with this package.

I'm afraid you will just have to keep an eye on the site, until they post a fix.

Roger 8)

---

### Post by linux-beginner on 2007-02-08
Thanks,

---

