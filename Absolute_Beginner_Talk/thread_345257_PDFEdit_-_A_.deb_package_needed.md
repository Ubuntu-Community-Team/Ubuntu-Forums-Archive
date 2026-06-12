---
title: "PDFEdit - A .deb package needed"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2007-01-24
Hi, Guys!

I have tried to compile, and install the program PDFEdit, without success.
I have looked at the forums here and on other sites and many have the same problem.

My skills aren't sufficient to troubleshoot package creation and I am wondering if someone who is "geeky" enough to tackle this problem would like to make a .deb package for Ubuntu for the rest of us mere mortals?

It is an area in the repositories that seems to be lacking, and the cost of buying Adobe Acrobat is nothing short of ursury.

I know that KWriter can open and edit .PDF files but PDFEdit goes way beyond this.

Any takers?

Regards,
Roger :cool:

---

### Post by housam on 2007-01-24
Try to install it through Automatix2

Neglect it.

I've got it wrong , I thought Adobe reader

---

### Post by ramjet_1953 on 2007-01-24
bump

---

### Post by doundounba on 2007-01-30
Hi all,

I also want to try pdfedit, so I gave this a go.  The bad news is: checkinstall chokes for some reason, so I am unable to create a .deb package.  The good news is: the software does compile for me (Kubuntu Edgy).  But more bad news: once built and installed, it doesn't run for me. :(

If you want to try it, once you've you've got the source downloaded and unpacked, here's what you do:

- Make sure you've got what it takes to compile stuff:
> 
$ sudo apt-get install checkinstall build-essential


- Install stuff that pdfedit needs (the boost libraries and doxygen):
> 
$ sudo apt-get install bcp doxygen

- Set the path for QT:
> 
$ export QTDIR=/usr/share/qt3


- Build and install:
> 
$ ./configure
$ make
$ sudo make install


Or instead of "sudo make install", try "sudo checkinstall -D".  This is what I get on that:
> 
make[2]: Leaving directory `/home/pascal/software/pdfedit-0.2.4/src/utils'
cd kernel && qmake && make staticlib
Segmentation fault
make[1]: *** [kernel] Error 139
make[1]: Leaving directory `/home/pascal/software/pdfedit-0.2.4/src'
make: *** [src] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


And when I try to run the thing, I get:
> 
2:GUI:settings.cc:initSettings:121: No settings found - pdfeditrc

Fatal Error!
Missing item in config:
gui/items/MainMenu
QTextCodec::~QTextCodec() called by application


Can anyone take this any further?

---

### Post by Joe_CoT on 2007-01-31
> And when I try to run the thing, I get:
```
 2:GUI:settings.cc:initSettings:121: No settings found - pdfeditrc

Fatal Error!
Missing item in config:
gui/items/MainMenu
QTextCodec::~QTextCodec() called by application
```
Can anyone take this any further?

It can't access pdfeditrc. You'll notice if you run it with sudo, it works fine. Do the following:
```
sudo chmod -R +r /usr/local/share/pdfedit/*
```

And it will work fine. It looks kinda clunky, but it looks like it works.

---

### Post by padeco on 2007-01-31
hi there,

that was an interesting point: 

> sudo chmod -R +r /usr/local/share/pdfedit/*

i did as suggested above, and it works. the pdfedit command line brings up the program. however, there is still the error message:

> ~$ pdfedit
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


thanks,
padeco

---

### Post by Joe_CoT on 2007-01-31
> i did as suggested above, and it works. the pdfedit command line brings up the program. however, there is still the error message:

I wouldn't worry about it all that much. Try running gedit from a command line; see how many errors you get :D

What concerns me much more is how useless the program seems to be; it gives complete access to the pdf's raw DOM, but what good is that? The gui tools just plain stink.

All I want is *something* to let me edit pdf bookmarks and things like that.

---

### Post by doundounba on 2007-01-31
> 
sudo chmod -R +r /usr/local/share/pdfedit/*


Thanks Joe_CoT!  Very odd that make install would copy those files and not set permissions properly on them.  Anyway, after chmod-ing, it works fine for me as well.

padeco: I also get the BadDevice errors, but I've learned to kind-of ignore them, as they happen whenever I launch programs from the command line and they don't seem to affect anything. I *think* they first showed up after I upgraded to dapper...

There's some documentation for pdfedit here, BTW: 
[http://pdfedit.petricek.net/pdfedit.user_doc]("http://pdfedit.petricek.net/pdfedit.user_doc")

---

### Post by kuukie on 2007-02-12
BUMP.

As a student with over two thousand pdf pages to go through each semester something to annotate/tag/correct them is badly needed.

How can Linux even be considered in academia without something as simple as this?

Same sad story about PDF viewers still. Get used to PDF, it's here to stay (and been ISO'd recently iirc).

---

### Post by aysiu on 2007-02-12
Not sure, but [this thread](http://www.ubuntuforums.org/showthread.php?t=330543) might help.

---

### Post by meborc on 2007-02-12
> **kuukie said:**
> BUMP.

As a student with over two thousand pdf pages to go through each semester something to annotate/tag/correct them is badly needed.

How can Linux even be considered in academia without something as simple as this?

Same sad story about PDF viewers still. Get used to PDF, it's here to stay (and been ISO'd recently iirc).

hmm... and i though that pdf is kind of like doc... i mean isn't it under somekind of patent protection? ... isn't that the case it is so hard to make/edit pdf files BOTH in windows and in linux?...

or am i wrong completely :D

---

### Post by ramjet_1953 on 2007-02-20
Hi, Guys!

I finally found a deb package that worked for me.
Try this link!

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

Regards,
Roger :cool:

---

### Post by kuukie on 2007-02-26
Thanks ramjet, that worked for me, too! pdfedit as such is quite sluggish though, but at least it doesn't crash like it did with Klik.

Okular in KDE4 looks quite promising, but it's still half a year until KDE4 will be released :/

So, for the time being I suppose I'll have to make do with Adobe Reader in VirtualBox/Windows XP. Seeing that VirtualBox can even be run on pretty crappy hardware from the late 90s (given there's enough RAM), I guess we should all stop complaining about not having a certain application (yet) in Linux ;)

---

### Post by ahmatti on 2007-03-16
> **ramjet_1953 said:**
> Hi, Guys!

I finally found a deb package that worked for me.
Try this link!

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

Regards,
Roger :cool:

Thanks! That worked for me too :)

---

