---
title: "Need help to install pdfedit"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-03
I've asked once but maybe not specific enough:
[http://www.ubuntuforums.org/showthread.php?t=330035](http://www.ubuntuforums.org/showthread.php?t=330035)

I have tried to install pdfedit.
I've downloaded the sources from the pdfedit homesite. 
I guess that I'm suppose to run ./configure;make;make install (I've seen that in several places)
It appears that it needs something related to qt3 so I installed libqt3-mt-dev (and some other libqt3). It says on pdfedit homepage that it must be qt3 not qt4.
./configure runs apparently fine though one warning:

```
config.status: WARNING:  config.pro.in.in seems to ignore the --datarootdir setting
```

But now make complains (several times) about missing gmake
```
/bin/sh: gmake: not found
```
and:
```
Can't find Qt library. No QTDIR set
```
and ends with:
```
make: *** [src] Error 2
```

I'm not entirely sure what I'm doing :confused: or if I'm at all on the right track

---

### Post by bluefrog on 2007-01-03
sudo apt-get install gmake

you need to export the qtdir

export QTDIR=/usr/include/qt3                         (or something similar)
export /usr/share/qt3/:/usr/include/qt3/:$PATH  (or something similar)

James

---

### Post by fsando on 2007-01-03
It responds with:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gmake

```

---

### Post by bluefrog on 2007-01-03
use synaptic then to try to find gmake. don't know in what repository it is (universe, normal ubuntu...)

James

---

### Post by fsando on 2007-01-03
Hi bluefrog and thanks
Actually it works with the two export commands (apart from a minor typo colon instead of semicolon)
It installed fine (at least I could open it)
I don't know what it is about the missing gmake - it didn't miss it anymore ;)
cheers

---

### Post by dannyboy79 on 2007-01-03
what are you allowed to do with this software installed? I am curious because I opened a pdf that was posted on the internet and I wanted to save it to my desktop and I couldn't??? I know I can't "create a pdf" because I don't have a pdf creater installed but I figured that by having pdfreader installed I would be able to save the existing pdf that was already created and posted on the web so that I could view it locally instead of having to go that website everytime I wanted to view it. Well, I can't save it? Something about permission? Which doesn't make any sense because I have permission to the location I was trying to save it to. Maybe I need to open firefox using gksudo then go the website, then i'll be able to save it???? so I am curious if this pdf program you are talking about will help me? Any thoughts?

---

### Post by Efwis on 2007-01-03
> **fsando said:**
> It responds with:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gmake

```

for future reference, gmake is included in Build-essential. 

```
sudo apt-get install build-essential
```
Gmake is part of that system. it is not a stand alone library.

---

### Post by scubanator87 on 2007-01-17
I was having the same problems -the gmake but when i ran the export command 


```
export /usr/share/qt3/:/usr/include/qt3/:$PATH
```


then tried

```
 export /usr/share/qt3/;/usr/include/qt3/;$PATH

```

and the other two possibilites but it still give me

```
 export /usr/share/qt3/:/usr/include/qt3/:$PATH
bash: export: `/usr/share/qt3/:/usr/include/qt3/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games': not a valid identifier

```


```
 export /usr/share/qt3/;/usr/include/qt3/;$PATH
bash: export: `/usr/share/qt3/': not a valid identifier
bash: /usr/include/qt3/: is a directory
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory

```

---

### Post by po0f on 2007-01-17
scubanator87,

```
[FONT="Courier New"]$ export PATH="/usr/share/qt3:$PATH"
$ export QTDIR="/usr/include/qt3"[/FONT]
```

You might want to check to make sure those directories actually exist, though.

---

### Post by scubanator87 on 2007-01-22
thanks that worked!

---

### Post by padeco on 2007-01-28
hi there,
 
i attempted the command lines described above without any succes. the output posted below is what i get from the $sudo make

QOutputDevPixmap.cpp:25:21: error: qpixmap.h: No such file or directory
QOutputDevPixmap.cpp:26:20: error: qimage.h: No such file or directory
QOutputDevPixmap.h:40: error: ‘QImage’ does not name a type
QOutputDevPixmap.h:43: error: ‘QImage’ does not name a type
QOutputDevPixmap.cpp: In constructor ‘QOutputDevPixmap::QOutputDevPixmap(Guchar*)’:
QOutputDevPixmap.cpp:39: error: class ‘QOutputDevPixmap’ does not have any field named ‘m_image’
QOutputDevPixmap.cpp: In destructor ‘virtual QOutputDevPixmap::~QOutputDevPixmap()’:
QOutputDevPixmap.cpp:46: error: ‘free’ was not declared in this scope
QOutputDevPixmap.cpp: In member function ‘virtual void QOutputDevPixmap::endPage()’:
QOutputDevPixmap.cpp:60: error: ‘free’ was not declared in this scope
QOutputDevPixmap.cpp:61: error: ‘malloc’ was not declared in this scope
QOutputDevPixmap.cpp:62: error: ‘m_image’ was not declared in this scope
QOutputDevPixmap.cpp:78: error: ‘m_image’ was not declared in this scope
QOutputDevPixmap.cpp:78: error: ‘uchar’ was not declared in this scope
QOutputDevPixmap.cpp:78: error: expected primary-expression before ‘)’ token
QOutputDevPixmap.cpp:78: error: ‘QImage’ has not been declared
QOutputDevPixmap.cpp:78: error: ‘IgnoreEndian’ was not declared in this scope
QOutputDevPixmap.cpp:78: error: ‘QImage’ was not declared in this scope
make[2]: *** [QOutputDevPixmap.o] Error 1
make[2]: Leaving directory `/home/. . ./Programs/pdfedit-0.2.4/src/kpdf-kde-3.3.2'
make[1]: *** [qoutputdevices] Error 2
make[1]: Leaving directory `/home/. . ./Programs/pdfedit-0.2.4/src'
make: *** [src] Error 2

if anyone has any idea as to how i can overcome this problem, much appreciated.

thanks,
padeco

---

### Post by vikingdocerrado on 2007-02-21
I am experiencing the very same problem as padeco, but with version 0.2.5 of pdfedit.

Does anyone have any idea on how to solve it?

Regards.

Edit: Never mind. I used synaptic to install more qt3 libraries* and I passed that point. Then the other problem that I had (when I was trying to run the program) was solved by
```
sudo chmod -R +r /usr/local/share/pdfedit/*
```
as suggested by Joe_CoT in [http://ubuntuforums.org/showthread.php?t=345257#5]("http://ubuntuforums.org/showthread.php?t=345257#5")

* - At first I installed libqt3-compat-headers and libqt3-headers but that did not help. After that I installed libqt3-mt-dev and all that came along and it worked. :D

---

### Post by ramjet_1953 on 2007-02-21
Here's a link to a deb package that installed OK for me, after I checked the dependencies first.

[http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb](http://download.tuxfamily.org/3v1deb//pool/edgy/3v1n0/pdfedit_0.2.5-0+3v1ubuntu1_i386.deb)

Check out the attached screenshot.

Regards,
Roger :cool:

---

### Post by stmiller on 2007-08-26
Replying to an old thread, but to compile PDFedit 0.3.1 from source I had to issue these two commands:
```

export QTDIR=/usr/share/qt3/

```
(for 64bit)```

export QMAKESPEC=/usr/share/qt3/mkspecs/linux-g++-64/

```

or (for 32bit)
```

export QMAKESPEC=/usr/share/qt3/mkspecs/linux-g++-32/

```

then
```

./configure
(enter)

make
(enter)

sudo make install


```
EDIT: This is assuming you have all qt3 dev dependencies and such installed. OK hope this helps!

---

