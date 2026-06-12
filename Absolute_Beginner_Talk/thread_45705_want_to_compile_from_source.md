---
title: "want to compile from source"
date: 2005-07-01
forum: Absolute Beginner Talk
---

### Post by JulianYorke on 2005-07-01
Hey new linux user here, I want to compile programs from source, I have read up on how to do this, but I want to practice it becasue I really like Ubuntu and want to get acquainted with it.  Anyway I am looking for suggestions for good programs (anything really) to download and compilre from source.  Your help is appreciated.  Thanks

---

### Post by Kvark on 2005-07-01
After you download for example a tar.gz file containing source code, just type:

sudo alien --install /path/file.tar.gz

and then you're done.

But it's easier to just use the synaptic package manager. It leads to less problems and you will be using synaptic in 99% of the cases so better get used to that one first.

---

### Post by FLeiXiuS on 2005-07-01
[QUOTE=JulianYorke]Hey new linux user here, I want to compile programs from source, I have read up on how to do this, but I want to practice it becasue I really like Ubuntu and want to get acquainted with it.  Anyway I am looking for suggestions for good programs (anything really) to download and compilre from source.  Your help is appreciated.  Thanks[/QUOTE]
1st, lets make sure your repositories are updated.  Follow the guide here: [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

Compile whatever you want thats not already a deb, or perhaps is a deb but is missing something that you DO want.

All you have to do is have the currect libraries to do so.

```
$ sudo apt-get install build-essential
```

Those should get you started.  After this then it's time to compile the source.  Extract the source file then move to the folder created.  

The 'configure' script will be your baby.  You can enter 
```
$ ./configure --help
```
To get a full list of what you can change.  Or you can accept the defaults.

```
$ ./configure; make; make install
```
That will install configure and then install to the defaults according to the configure script.  You may encounter errors.  For instance it may tell you that you need flex.  Ok simple, so find flex and install it.  
```
$ sudo apt-get install flex
```
There as simple as that.  Now just ./configure again.  And make sure nothing else is missing.  If all goes well!  Head on to 'make' then 'sudo makeinstall'.  Goodluck mate.

Oh and, instead of using 'sudo make install' you can install a nifty little program called checkinstall which will do that process for you, plus it'll create a debian binary do you can unistall and reinstall much much easier.  When you compile from source things go all over the place.  And they leave you with no uninstall script unless the developer included a 'make uninstall'.  Some don't.  So use this tip wisley.

To install checkinstall do the following
```
$ sudo apt-get install checkinstall
```

So now that you've seen a jist, time to scare you a bit.  :-)  Recently I had to compile gaim with perl extension support.  YAY me!   So I downloaded the source gaim-1.3.1.tar.gz.  Now off for an adventure.
```
$ tar -zxvf gaim-1.3.1.tar.gz
$ cd gaim-1.3.1
$ ./configure --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/gaim --srcdir=. --disable-maintainer-mode --disable-nas --disable-nss --enable-perl --disable-silc --with-zephyr=/usr CC=cc CFLAGS=-g -Wall -O2 CXXFLAGS=-g -Wall -O2 CXX=g++
$ make
$ sudo checkinstall

```
There that wasn't so bad was it :-P.  Of course I had to edit the configure script a bit since; well gaims perl API wasn't to "up to date".  Still working on getting it fully functional.  Theres a jist, good luck soldier.

---

### Post by FLeiXiuS on 2005-07-01
[QUOTE=Kvark]After you download for example a tar.gz file containing source code, just type:

sudo alien --install /path/file.tar.gz

and then you're done.

But it's easier to just use the synaptic package manager. It leads to less problems and you will be using synaptic in 99% of the cases so better get used to that one first.[/QUOTE]

I would avoid using this method well since, you don't get the full excitement of compiling from source (customization, optimization)  All your doing is agreeing with defaults as what most deb packages would use.  Your not optimizing nor customizing anything.

---

### Post by JulianYorke on 2005-07-01
Thanks Ill try it out \\:D/

---

### Post by Kvark on 2005-07-01
[QUOTE=FLeiXiuS]I would avoid using this method well since, you don't get the full excitement of compiling from source (customization, optimization)  All your doing is agreeing with defaults as what most deb packages would use.  Your not optimizing nor customizing anything.[/QUOTE]

Yeah if you find it fun to fool around then you will need something more complicated then alien.

---

### Post by FLeiXiuS on 2005-07-01
[QUOTE=Kvark]Yeah if you find it fun to fool around then you will need something more complicated then alien.[/QUOTE]

It's not fulling around...it's compiling to meet your needs or to optimize it to your PC.

---

