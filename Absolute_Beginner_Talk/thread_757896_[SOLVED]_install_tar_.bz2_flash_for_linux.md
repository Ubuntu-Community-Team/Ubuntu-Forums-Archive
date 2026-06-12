---
title: "[SOLVED] install tar .bz2 flash for linux"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by inter-m on 2008-04-17
I have been trying to install this package
f4l-0.2.1.tar.bz2
First I extracted it then I navigated to its dircetory and typed ./configure and get this response
```
bash: ./configure: No such file or directory
```
so I did an ls and this what I got
```
bin  callgrind.cmd  COPYING  CVS  deneme.swf  Doxyfile  f4l.kdevelop  f4l.kdevelop.pcs  f4l.kdevses  f4l.pro  Makefile  src  templates
```
as u see there is a Makefile so i type make and this is what I get
```
make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'.  Stop.

```
Im really lost here and have no clue on what to do... 

thanx in advance...

---

### Post by philinux on 2008-04-17
If you want flash for linux go here.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

---

### Post by inter-m on 2008-04-17
thanx i already have that but im trying to get is a program that make flash files... :)

---

### Post by philinux on 2008-04-17
Ah, hope someone steps up then with answer.

There's usually a readme file with instructions.

---

### Post by inter-m on 2008-04-17
ya thats what i thought but it only came with a copy file... :(

---

### Post by Bachstelze on 2008-04-17
Could you please provide a link to the archive?

---

### Post by oldos2er on 2008-04-17
> **HymnToLife said:**
> Could you please provide a link to the archive?

 It's at Sourceforge.

---

### Post by forrestcupp on 2008-04-17
Make sure you have qmake installed
```
sudo apt-get install qt3-dev-tools
```


And sourceforge is a big place.  An actual link would save some time.

---

### Post by chili555 on 2008-04-17
As well, this:```
sudo apt-get install build-essential
```Will help.

---

### Post by inter-m on 2008-04-17
i tried ./configure
```
khalaf@sumbul:~/Flash4Linux/f4l-0.2.1$ ./configure
bash: ./configure: No such file or directory

```
this is what i  got i thought to myself since i already a Makefile then there is no need for the first step correct me if im worng....

```
khalaf@sumbul:~/Flash4Linux/f4l-0.2.1$ make
cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/khalaf/Flash4Linux/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSAction.o FSAction.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSActionObject.o FSActionObject.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSBitmapFill.o FSBitmapFill.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSBoolean.o FSBoolean.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSBounds.o FSBounds.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSButton.o FSButton.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSButtonColorTransform.o FSButtonColorTransform.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSButtonEvent.o FSButtonEvent.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSButtonSound.o FSButtonSound.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSCall.o FSCall.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSCharacter.o FSCharacter.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSClipEvent.o FSClipEvent.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSColor.o FSColor.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSColorTransform.o FSColorTransform.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSCoordTransform.o FSCoordTransform.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSCurve.o FSCurve.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineButton.o FSDefineButton.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineButton2.o FSDefineButton2.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineFont.o FSDefineFont.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineFont2.o FSDefineFont2.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineImage.o FSDefineImage.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineImage2.o FSDefineImage2.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineJPEGImage.o FSDefineJPEGImage.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineJPEGImage2.o FSDefineJPEGImage2.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineJPEGImage3.o FSDefineJPEGImage3.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineMorphShape.o FSDefineMorphShape.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineMovieClip.o FSDefineMovieClip.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineObject.o FSDefineObject.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineShape.o FSDefineShape.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineShape2.o FSDefineShape2.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineShape3.o FSDefineShape3.cpp
g++ -c -pipe -w -g -D_REENTRANT  -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o FSDefineSound.o FSDefineSound.cpp
FSDefineSound.h:140: error: extra qualification ‘transform::FSDefineSound::’ on member ‘FSDefineSound’
make[1]: *** [FSDefineSound.o] Error 1
make[1]: Leaving directory `/home/khalaf/Flash4Linux/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2

```

this what i got when i did sudo make install

```
khalaf@sumbul:~/Flash4Linux/f4l-0.2.1$ sudo make install
( [ -d src/flagStonePort/transform-cxx-bsd/transform ] && cd src/flagStonePort/transform-cxx-bsd/transform ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d src/flagStonePort/transform-util-cxx/transform-util ] && cd src/flagStonePort/transform-util-cxx/transform-util ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d src ] && cd src ; grep "^qmake_all:" Makefile && make -f Makefile qmake_all; ) || true
( [ -d src/flagStonePort/transform-cxx-bsd/transform ] && cd src/flagStonePort/transform-cxx-bsd/transform ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/khalaf/.Trash/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/khalaf/.Trash/f4l-0.2.1/src/flagStonePort/transform-cxx-bsd/transform'
( [ -d src/flagStonePort/transform-util-cxx/transform-util ] && cd src/flagStonePort/transform-util-cxx/transform-util ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/khalaf/.Trash/f4l-0.2.1/src/flagStonePort/transform-util-cxx/transform-util'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/khalaf/.Trash/f4l-0.2.1/src/flagStonePort/transform-util-cxx/transform-util'
( [ -d src ] && cd src ; make -f Makefile install; ) || true
make[1]: Entering directory `/home/khalaf/.Trash/f4l-0.2.1/src'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/khalaf/.Trash/f4l-0.2.1/src
```

and ofcourse i did all of this after i installed the qmake adn build essentials...
also this is the link [http://sourceforge.net/project/showfiles.php?group_id=87799&package_id=157994&release_id=342150](http://sourceforge.net/project/showfiles.php?group_id=87799&package_id=157994&release_id=342150)

---

### Post by oldos2er on 2008-04-17
> **forrestcupp said:**
> And sourceforge is a big place.  An actual link would save some time.

 It took me about 4 seconds to get there after plugging "f4l-0.2.1.tar.bz2" into Google, fwiw.

---

### Post by chili555 on 2008-04-17
Well! That was an adventure, but I finally got it to make with no errors! I installed more qt3 packages, specifically libqt3-mt-dev and the list of dependencies that came with it. I also changed src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h in line 140 from FSDefineSound::FSDefineSound to FSDefineSound. Be sure to save and close the text editor. Run:```
make clean
make
```Sip a brew and it should work. No need to *make install.* cd to bin and do  *./f4l.* Good luck and post back if you get stuck.

---

### Post by inter-m on 2008-04-17
thanx chili its all working now... its moments like these that i really appreciate moving from windows to Linux... thanx all

---

