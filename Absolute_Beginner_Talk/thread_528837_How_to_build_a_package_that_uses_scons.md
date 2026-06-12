---
title: "How to build a package that uses scons"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by punong_bisyonaryo on 2007-08-18
Hello,

Does anyone know how to build a package that uses scons?

I downloaded [Battle Tanks]("http://btanks.sourceforge.net/blog/") source, to my surprise it wasn't the usual ./configure, sudo make install fare. Readme says something about "you must use scons to build this".

Any help would be appreciated.

Thanks!

---

### Post by badactress on 2007-08-18
if it's been packaged with scons-local, there's no need for you to install anything. You should be able to cd to the battletanks folder & type : ./scons at the command prompt.

If scons-local isn't included with the source code, then you'll need to: 'apt-get install scons' first.

---

### Post by punong_bisyonaryo on 2007-08-18
Is it possible to make a deb from scons source file. By the way there was no scons-local, so I'll try installing scons first..

---

### Post by punong_bisyonaryo on 2007-08-18
Ok, forget the thing about deb for now. For now, after installing scons and running scons, I get this: ```
scons: Reading SConscript files ...
Package sigc++-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `sigc++-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sigc++-2.0' found
Package sigc++-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `sigc++-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'sigc++-2.0' found
Checking for sigc::signal1<int,int> sig in C++ library sigc-2.0... yes
Checking for XML_ParserCreate(NULL) in C library expat... no
```

I'm not very good at source files, it was hard enough with the make system before; this looks like gibberish. Do I just install sigc++.2.0? What's with the PKG_CONFIG_PATH stuff?

---

### Post by badactress on 2007-08-19
Ok! Well I'm no linux guru so I was hoping someone else would jump in & answer since we're vearing close to the edge of my knowledge!!

But yes, it sounds like you need to:

'sudo apt-get install libsigc++-2.0-0c2a'   (might already be installed)

and the development library:

'sudo apt-get install libsigc++-2.0-dev'

If they were the only errors Scons produced, then hopefully this should solve the problem!

:)

PKG_CONFIG_PATH is an evironment variable which tells the compiler which folders to look in to find any libraries a program needs to be linked to to compile. What the error message is telling you is that it can't find libsigc in any of the folders in it's list, so if the library is already installed, but it's not in the usual places the compiler would look, you need to add it's folder-location (it's directory path) to the PKG_CONFIG_PATH list so the compiler can find it. More likely though, is that libsigc simply isn't installed, so installing it should do the trick.

BTW 'Make' would produce the same error messages if it couldn't find a library it needs.. It isn't just a Scons thing!

---

### Post by punong_bisyonaryo on 2007-08-19
libsigc++-2.0-0c2a was already installed, so I only needed to install libsigc++-2.0-dev.

but it still has this error:
```
Checking for XML_ParserCreate(NULL) in C library expat... no
```
I have no idea what this means.

---

### Post by badactress on 2007-08-19
lol.. now I really am guessing..

But..

There is a library called expat that probably needs installing now. Again the standard lib might already be installed but the dev version probably isn't:

sudo apt-get install libexpat1
sudo apt-get install libexpat1-dev

:)

---

### Post by Shivad on 2007-08-22
Hi! exact the same problem, follow your steps but...

Checking for sigc::signal1<int,int> sig in C++ library sigc-2.0... yes
Checking for XML_ParserCreate(NULL) in C library expat... yes
Checking for zlibVersion() in C library z... no :confused:

Help please! :(

---

### Post by punong_bisyonaryo on 2007-08-22
> **Shivad said:**
> Hi! exact the same problem, follow your steps but...

Checking for sigc::signal1<int,int> sig in C++ library sigc-2.0... yes
Checking for XML_ParserCreate(NULL) in C library expat... yes
Checking for zlibVersion() in C library z... no :confused:

Help please! :(

I had to leave this one for while because of work. Anyway, I'm back at compiling this.

I was able to get past this by typing
```
sudo aptitude install zlib1g-dev
```

But I got stuck at
```
checking for SDL_Init(0) in C++ libary SDL... no
```

Currently looking for the right package for this.

---

### Post by punong_bisyonaryo on 2007-08-22
Installing libsdl1.2-dev worked.:)

```
sudo aptitude install libsdl1.2-dev
```

As a heads up, you'll also be needing libsdl-image1.2-dev, libopenal-dev

```
sudo aptitude install libsdl-image1.2-dev libopenal-dev
```

and then I got stuck when it asked for library vorbisfile. I tried libvorbisfile3 but didn't work.

Edit:
Didn't work when I installed libvorbisfile3, but it works when you install libvorbis-dev. It's compiling now. No problems hopefully.;)

---

### Post by Shivad on 2007-08-22
now I get a lot of stuff going on, but at the end this is what I get:  

sh: o: not found
Install file: "build/release/bt" as "bt"
scons: *** [bt] build/release/bt: No such file or directory
scons: building terminated because of errors.

I tried to install the “bt” but no good, no idea how to :confused:

---

### Post by punong_bisyonaryo on 2007-08-22
Hmmm, I have no idea...

Did you execute scons as root? sudo scons?

I hope badactress or anybody helps us out.

@Shivad, if you manage to solve it on your own, please share here your experience/problem/solutions for others to see and learn also.

---

