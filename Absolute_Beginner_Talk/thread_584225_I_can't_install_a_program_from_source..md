---
title: "I can't install a program from source."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Dirty Soap on 2007-10-20
I am trying to install WebKit. I run ```
bzip2 -cd WebKit-r26750.tar.bz2 | tar xvf -
``` to unpack it.

Then cd WebKit-r26750 to change to it's directory.

Then ./configure did not work, I received ```
bash: ./configure: No such file or directory
```

So I moved on to make, received ```
make[1]: *** [tmp/JSAttrCustom.o] Error 1
make[1]: Leaving directory `/home/ant/WebKit/WebKitBuild/Release/WebCore'
make: *** [sub-WebCore-make_default-ordered] Error 2
``` at the end of it.

I also have no INTSALL, README, nor configure files.

---

### Post by Maestro23 on 2007-10-20
To install from source, you first need "build-essential" installed.

> sudo apt-get install build-essential

*There was no Installation documentation on the site where you got the program?

---

### Post by Frak on 2007-10-20
WebKit is a program for OS X.

---

### Post by Dirty Soap on 2007-10-20
I already have build-essentials.

And is it? I just figured since it's in sourcecode, I can install it in Linux.

---

### Post by Maestro23 on 2007-10-20
> **Frak said:**
> WebKit is a program for OS X.

Wow... Answers that question.:popcorn:

---

### Post by Dirty Soap on 2007-10-20
But I also have another sourcecode (for FretsOnFire), with the same problems.

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> I already have build-essentials.

And is it? I just figured since it's in sourcecode, I can install it in Linux.

Aren't there QT builds of WebKit that have been ported?

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> But I also have another sourcecode (for FretsOnFire), with the same problems.


[http://sourceforge.net/project/downloading.php?groupname=fretsonfire&filename=FretsOnFire-1.2.512-linux.tar.gz&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=fretsonfire&filename=FretsOnFire-1.2.512-linux.tar.gz&use_mirror=osdn)

Did you install from there? Or did you try and compile the OSX version?

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> Aren't there QT builds of WebKit that have been ported?
You mean this? [http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/](http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/)

I still get an error when i run "QTDIR=/usr/share/qt4/ WebKit/WebKitTools/Scripts/build-webkit"

---

### Post by RomeReactor on 2007-10-20
Hi. If you're looking Epiphany-Webkit, maybe [this thread]("http://ubuntuforums.org/showthread.php?p=3541156") can be of help.

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> [http://sourceforge.net/project/downloading.php?groupname=fretsonfire&filename=FretsOnFire-1.2.512-linux.tar.gz&use_mirror=osdn](http://sourceforge.net/project/downloading.php?groupname=fretsonfire&filename=FretsOnFire-1.2.512-linux.tar.gz&use_mirror=osdn)

Did you install from there? Or did you try and compile the OSX version?
Oh, I definitely got the Linux version.

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> You mean this? [http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/](http://mondaybynoon.com/2007/04/23/installing-and-running-webkit-in-linux-using-qt/)

I still get an error when i run "QTDIR=/usr/share/qt4/ WebKit/WebKitTools/Scripts/build-webkit"

I meant this:

 apt-cache search webkit
libqtwebkit-dev - Web content engine library for Qt - Development files
libqtwebkit0d - Web content engine library for Qt
libqtwebkit0d-dbg - Web content engine library for Qt - Debugging symbols
libwebkitgdk-dev - Web content engine library for Gtk+ - Development files
libwebkitgdk0d - Web content engine library for Gtk+
libwebkitgdk0d-dbg - Web content engine library for Gtk+ - Debugging symbols
paste-common - common files for paste modules
python-pastewebkit - port/reimplementation of Webware WebKit in WSGI and Paste


But i don't know if they are the same thing. I did see this: [http://dot.kde.org/1152645965/](http://dot.kde.org/1152645965/) from back in July of last year.

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> Oh, I definitely got the Linux version.

The best way to get help with compile errors is to cut/paste the errors.

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> The best way to get help with compile errors is to cut/paste the errors.
```
:~$ cd FretsOnFire
:~/FretsOnFire$ ./configure
bash: ./configure: No such file or directory
:~/FretsOnFire$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> ```
:~$ cd FretsOnFire
:~/FretsOnFire$ ./configure
bash: ./configure: No such file or directory
:~/FretsOnFire$ make
make: *** No targets specified and no makefile found.  Stop.
```

Okay, so what are the contents of the FretsOnFire directory?

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> I meant this:

 apt-cache search webkit
libqtwebkit-dev - Web content engine library for Qt - Development files
libqtwebkit0d - Web content engine library for Qt
libqtwebkit0d-dbg - Web content engine library for Qt - Debugging symbols
libwebkitgdk-dev - Web content engine library for Gtk+ - Development files
libwebkitgdk0d - Web content engine library for Gtk+
libwebkitgdk0d-dbg - Web content engine library for Gtk+ - Debugging symbols
paste-common - common files for paste modules
python-pastewebkit - port/reimplementation of Webware WebKit in WSGI and Paste


But i don't know if they are the same thing. I did see this: [http://dot.kde.org/1152645965/](http://dot.kde.org/1152645965/) from back in July of last year.
Would I download all of them?

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> Okay, so what are the contents of the FretsOnFire directory?
```
:~/FretsOnFire$ ls -a
.                      libvorbisfile.so.3           pygame.key.so
..                     libvorbis.so.0               pygame.mixer_music.so
_amanith.so            _locale.so                   pygame.mixer.so
array.so               math.so                      pygame.mouse.so
binascii.so            md5.so                       pygame.movie.so
_bisect.so             mmap.so                      pygame.overlay.so
bz2.so                 multiarray.so                pygame.rect.so
collections.so         numpy.core._dotblas.so       pygame.rwobject.so
copying.txt            numpy.core.multiarray.so     pygame.sndarray.so
cPickle.so             numpy.core.scalarmath.so     pygame.surface.so
cStringIO.so           numpy.core._sort.so          pygame.surfarray.so
_ctypes.so             numpy.core.umath.so          pygame.surflock.so
_curses.so             numpy.fft.fftpack_lite.so    pygame.time.so
data                   numpy.lib._compiled_base.so  pygame.transform.so
datetime.so            numpy.linalg.lapack_lite.so  PyOpenGL-3.0.0a6.egg-info
fcntl.so               numpy.random.mtrand.so       _random.so
FretsOnFire            _numpy.so                    readline.so
FretsOnFire.bin        ogg._ogg.so                  readme.txt
grp.so                 ogg.vorbis.so                select.so
_heapq.so              operator.so                  sha.so
_imaging.so            psyco._psyco.so              _socket.so
itertools.so           pygame.base.so               _ssl.so
libamanith.so.1        pygame.cdrom.so              strop.so
libblas.so.3           pygame.constants.so          struct.so
libffi.so.4            pygame.display.so            termios.so
libg2c.so.0            pygame.draw.so               time.so
liblapack.so.3         pygame.event.so              umath.so
libogg.so.0            pygame.fastevent.so          _weakref.so
libpython2.4.so.1.0    pygame.font.so               xml.parsers.pyexpat.so
libSDL_mixer-1.2.so.0  pygame.imageext.so           xml.parsers.sgmlop.so
libSDL_ttf-2.0.so.0    pygame.image.so              zlib.so

```

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> ```
:~/FretsOnFire$ ls -a
.                      libvorbisfile.so.3           pygame.key.so
..                     libvorbis.so.0               pygame.mixer_music.so
_amanith.so            _locale.so                   pygame.mixer.so
array.so               math.so                      pygame.mouse.so
binascii.so            md5.so                       pygame.movie.so
_bisect.so             mmap.so                      pygame.overlay.so
bz2.so                 multiarray.so                pygame.rect.so
collections.so         numpy.core._dotblas.so       pygame.rwobject.so
copying.txt            numpy.core.multiarray.so     pygame.sndarray.so
cPickle.so             numpy.core.scalarmath.so     pygame.surface.so
cStringIO.so           numpy.core._sort.so          pygame.surfarray.so
_ctypes.so             numpy.core.umath.so          pygame.surflock.so
_curses.so             numpy.fft.fftpack_lite.so    pygame.time.so
data                   numpy.lib._compiled_base.so  pygame.transform.so
datetime.so            numpy.linalg.lapack_lite.so  PyOpenGL-3.0.0a6.egg-info
fcntl.so               numpy.random.mtrand.so       _random.so
FretsOnFire            _numpy.so                    readline.so
FretsOnFire.bin        ogg._ogg.so                  readme.txt
grp.so                 ogg.vorbis.so                select.so
_heapq.so              operator.so                  sha.so
_imaging.so            psyco._psyco.so              _socket.so
itertools.so           pygame.base.so               _ssl.so
libamanith.so.1        pygame.cdrom.so              strop.so
libblas.so.3           pygame.constants.so          struct.so
libffi.so.4            pygame.display.so            termios.so
libg2c.so.0            pygame.draw.so               time.so
liblapack.so.3         pygame.event.so              umath.so
libogg.so.0            pygame.fastevent.so          _weakref.so
libpython2.4.so.1.0    pygame.font.so               xml.parsers.pyexpat.so
libSDL_mixer-1.2.so.0  pygame.imageext.so           xml.parsers.sgmlop.so
libSDL_ttf-2.0.so.0    pygame.image.so              zlib.so

```

If it were me and I was trying to install and run software that was not in the repositories (available on Synaptic, Adept, apt-get) I would read the documentation on the website where I downloaded the software from.

[http://fretsonfire.sourceforge.net/documentation/source/](http://fretsonfire.sourceforge.net/documentation/source/)

Looks like it's right there.

---

### Post by Maestro23 on 2007-10-20
> **llamakc said:**
> If it were me and I was trying to install and run software that was not in the repositories (available on Synaptic, Adept, apt-get) I would read the documentation on the website where I downloaded the software from.

[http://fretsonfire.sourceforge.net/documentation/source/](http://fretsonfire.sourceforge.net/documentation/source/)

Looks like it's right there.

Dang, I was too slow.  Just googled that up myself.:)

---

### Post by llamakc on 2007-10-20
My Beer-Fu is strong tonight.

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> If it were me and I was trying to install and run software that was not in the repositories (available on Synaptic, Adept, apt-get) I would read the documentation on the website where I downloaded the software from.

[http://fretsonfire.sourceforge.net/documentation/source/](http://fretsonfire.sourceforge.net/documentation/source/)

Looks like it's right there.
Oh, I didn't see that. Sorry for wasting your time.

---

### Post by llamakc on 2007-10-20
It's no waste of time. Somebody else will see this (possibly searching for Frets On Fire) and know what to do. Good luck. Oh, and I do not know what you need to install when it comes to WebKit. I'm unfamiliar with it or its uses.

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> It's no waste of time. Somebody else will see this (possibly searching for Frets On Fire) and know what to do. Good luck. Oh, and I do not know what you need to install when it comes to WebKit. I'm unfamiliar with it or its uses.
I'll just do this:

apt-cache search webkit
libqtwebkit-dev - Web content engine library for Qt - Development files
libqtwebkit0d - Web content engine library for Qt
libqtwebkit0d-dbg - Web content engine library for Qt - Debugging symbols
libwebkitgdk-dev - Web content engine library for Gtk+ - Development files
libwebkitgdk0d - Web content engine library for Gtk+
libwebkitgdk0d-dbg - Web content engine library for Gtk+ - Debugging symbols
paste-common - common files for paste modules
python-pastewebkit - port/reimplementation of Webware WebKit in WSGI and Paste

And thanks.

---

### Post by llamakc on 2007-10-20
> **Dirty Soap said:**
> I'll just do this:

apt-cache search webkit
libqtwebkit-dev - Web content engine library for Qt - Development files
libqtwebkit0d - Web content engine library for Qt
libqtwebkit0d-dbg - Web content engine library for Qt - Debugging symbols
libwebkitgdk-dev - Web content engine library for Gtk+ - Development files
libwebkitgdk0d - Web content engine library for Gtk+
libwebkitgdk0d-dbg - Web content engine library for Gtk+ - Debugging symbols
paste-common - common files for paste modules
python-pastewebkit - port/reimplementation of Webware WebKit in WSGI and Paste

And thanks.

That just searches for packages with 'webkit'. They may not all be needed. What is your actual need for WebKit? Are you developing with it?

---

### Post by Dirty Soap on 2007-10-20
> **llamakc said:**
> That just searches for packages with 'webkit'. They may not all be needed. What is your actual need for WebKit? Are you developing with it?
I just wanted to experiment with it because its used by Safari.

---

### Post by Frak on 2007-10-20
> **Dirty Soap said:**
> I just wanted to experiment with it because its used by Safari.
Experiment with KHTML, you won't believe how close they are (WebKit is 100% based off of KHTML)

---

