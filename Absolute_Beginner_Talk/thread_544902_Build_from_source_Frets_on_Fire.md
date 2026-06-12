---
title: "Build from source Frets on Fire"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-09-06
I am trying to build Frets on Fire from source since it isnt in the repos and downloading the binaries does not really allow you to integrate the program into the gnome desktop enviroment. The source can be found here:
[http://downloads.sourceforge.net/fretsonfire/FretsOnFire-src-1.2.451.tar.gz?modtime=1176687361&big_mirror=0](http://downloads.sourceforge.net/fretsonfire/FretsOnFire-src-1.2.451.tar.gz?modtime=1176687361&big_mirror=0)

When I cd to the unarchived folder I do not see a configure file so I just enter 'make'. This outputs:
```
--- Building EXE
/bin/sh: c:/apps/actpython/python: not found
--- Fixing PyOpenGL
cd: 6: can't cd to dist/data
cp: cannot stat `../../data/PyOpenGL__init__.pyc': No such file or directory
        zip warning: name not matched: OpenGL/__init__.pyo

zip error: Nothing to do! (library.zip)
--- Removing useless stuff
rm: cannot remove `dist/w9xpopen.exe': No such file or directory
make: *** [dist] Error 1
```
This seems like its a makefile for Windows? Especially since theres a Makefile.unix. I tried:
```
make Makefile.unix
```
But I guess thats not really that right syntax. Could anyone please tell me what I actually should be doing in order to compile this python app?

---

### Post by Compyx on 2007-09-06
You could try
```

make -f Makefile.unix

```

I doubt this will work since whoever wrote that makefile seems to know very little about what he/she is doing (`rm` on a M$ box?).

---

### Post by mevets on 2007-09-06
You're right, they didnt do a great job.
> steve@steve-laptop:~/Desktop/FretsOnFire-src-1.2.451$ make -f Makefile.unix--- Building binary
~/src/cx_Freeze-3.0.3/FreezePython --target-dir dist --include-modules encodings.string_escape,encodings.iso8859_1,xml.sax.drivers2.drv_pyexpat,SongChoosingScene,GuitarScene,GameResultsScene src/FretsOnFire.py
/bin/sh: /home/steve/src/cx_Freeze-3.0.3/FreezePython: not found
make: *** [dist] Error 127

Is there anyway I can better integrate FoF into the system like having an entry in alt+f2 and on the debian menu using the precompiled binaries here: [http://downloads.sourceforge.net/fretsonfire/FretsOnFire-1.2.451-linux.tar.gz?modtime=1176687303&big_mirror=0?](http://downloads.sourceforge.net/fretsonfire/FretsOnFire-1.2.451-linux.tar.gz?modtime=1176687303&big_mirror=0?)

---

