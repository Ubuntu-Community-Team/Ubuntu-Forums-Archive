---
title: "[SOLVED] How do i make a program from source?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by plr4ever on 2007-12-22
I cannot for the life of me seem to install ANY program from source:confused:. Right now i am trying to compile glest. I have read the steps on how to make a source, but i cant get past ./configure. It isn't found in the directory. I downloaded the .run file of it, but i still want to learn how to make a source.

---

### Post by p_quarles on 2007-12-22
You probably just need the build tools:
```
sudo apt-get install build-essential
```

---

### Post by autocrosser on 2007-12-23
Take a look at the Wiki information.  [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

That should point you the right way. And also look at:  [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by plr4ever on 2007-12-23
I have build essential already. Thanks autocrosser, but i still cant get the ./configure command to work at all in this source. 

I HATE SOURCES.

God intended everything to be in .deb format.

---

### Post by p_quarles on 2007-12-23
> **plr4ever said:**
> I have build essential already. Thanks autocrosser, but i still cant get the ./configure command to work at all in this source. 

I HATE SOURCES.

God intended everything to be in .deb format.
Okay, so can you post the error output that you get after running ./configure? The problem is likely that you're missing dependencies, and a good source code package will usually give you some hints about what you're missing.

---

### Post by plr4ever on 2007-12-23
```
 bash: ./configure: No such file or directory 
```

There is no config directory? what kind of source is this!

---

### Post by autocrosser on 2007-12-23
Is it a python installer? There are a couple of types that have come about in the last few years.....I forget the other one, but it's a odd-ball one too..

Why don't you give a list of the install folder or the install instructions? Might also help if you said where you got the source & what it is.....


EDIT: I just d/l'd it from SourceForge---It uses JAM as a build prerequesite--Look at this:

2. Building and Installation 
 
2.1 Prerequesites 
The game depends on some tools and libraries to be present, before you can 
start compiling it. Here's a list of them: 
 
* normal gnu compiler and additional tools (g++ version 3.2 or later is 
  required at the moment) 
 
* perforce jam 2.5 or later (used as build tool) 
  [ftp://ftp.perforce.com/pub/jam](ftp://ftp.perforce.com/pub/jam) 
 
* X11 libraries +headers 
  [http://www.x.org](http://www.x.org) (or the older [http://www.xfree86.org](http://www.xfree86.org)) 
 
* SDL 1.2.5 or later 
  [http://www.libsdl.org](http://www.libsdl.org) 
 
* Xerces-C 
  [http://xml.apache.org/xerces-c/index.html](http://xml.apache.org/xerces-c/index.html) 
 
* OpenAL 
  [http://www.openal.org](http://www.openal.org) 
 
* Ogg 
  [http://www.xiph.org/ogg/vorbis](http://www.xiph.org/ogg/vorbis)   
 
* Vorbis 
  [http://www.vorbis.com](http://www.vorbis.com) 
 
If the configure script can't find some of the libraries, make sure that you 
also have the -dev packages installed that some distributions provide. 
At this point I'd like to thank all the authors of these helpful libraries 
that made our development easy and straightforward. 
 
2.2 Building 
 
To build and install the game use the following commands (in the top glest 
directory). 
 
cd mk/linux 
./configure 
jam 


Looks like you need some stuff to make it......

---

### Post by plr4ever on 2007-12-23
Thanks a million autocrosser, at least now i know now i wasn't being a TOTAL idiot. I read that file too, and got jam, but i think i am just going to stick with the .run file.

Ya'll are great!:guitar:

---

