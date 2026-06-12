---
title: "Getting 32 to work on 64?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by bhudda on 2006-11-18
Hello! I have a 32 bit application that i would like to install, but I can't as I am on a 64 bit system. I am using Edgy, and I want to install this game actually...[Panda Go](http://panda-igs.joyjoy.net/English/glgo/download.html) So I was wondering on how to do two things....

1. How do you force install something? What does that mean anyway? What does it do? And how would I do it for this particular app?

2. I heard you can compile the app yourself if you have the source...how do you do that? I think the source is located [Here](http://panda-igs.joyjoy.net/English/glgo/downloads/src/). So how do you install and compile using the source?

Thanks for all the help!

~b

---

### Post by ReaderRat on 2006-11-18
You should be able to run 32-bit apps on a 64-bit system. You cannot do it the other way 'round. I am not familiar with a "forced install".

---

### Post by bhudda on 2006-11-18
> **ReaderRat said:**
> You should be able to run 32-bit apps on a 64-bit system. You cannot do it the other way 'round. I am not familiar with a "forced install".

Yea, I know it SHOULD work, but it wont let me install it...it gives me an error along the lines of "package architecture (i386) does not match system (amd64)" and then it just stops and doesn't continue the install. How do I force it to install is the question...

~b

---

### Post by bhudda on 2006-11-18
Well I got it to force install using the --force-architecture command...but now I have no idea how to run it...lol. I am starting to get the hang of this thing.

EDIT: Ok got it to start...alsmot....with typing "glGo" in the command line...but it give me this error.

```
glGo: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

What do I do with this?

~b

---

### Post by wayward on 2006-11-25
I just made glGo run on my amd64 Edgy and here's a short how-to.

[LIST=1]

[*]**Download and install 32-bit library packages:**

These packages contain libraries deemed necessary for legacy purposes, i.e. to allow binary packages not yet ported to AMD64 to run.  They do *not* contain every single library you can imagine, only the essential ones, and we shall deal with that in the next step.
[LIST]
[*]ia32-libs
[*]ia32-libs-gtk
[*]ia32-libs-sdl
[/LIST]
```
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-sdl
```

[*]**Download extra 32-bit library packages:**

These packages contain additional 32-bit libraries that *glGo* links against.

[LIST]
[*]libsdl-image1.2_1.2.5-2_i386.deb
[*]libsdl-ttf1.2_1.2.2-7_i386.deb
[*]libsdl-ttf2.0-0_2.0.8-2_i386.deb
[*]python2.4_2.4.4~c1-0ubuntu1_i386.deb
[/LIST]

Store these *.deb* files in a directory of your choosing and go there.

You can download them from [http://packages.ubuntu.com/edgy]("http://packages.ubuntu.com/edgy"), just make sure that you download the 32-bit package:

[IMG]http://img145.imageshack.us/img145/4254/screenshotjm7.jpg[/IMG]


[*]**Install additional 32-bit libraries:**

Each of these newly-downloaded packages contains one important dynamic library (and one link to it) that we'll now extract into the */lib32* directory:
```
mkdir /tmp/foo; for i in *.deb; do dpkg --extract $i /tmp/foo; done; mv /tmp/foo/usr/lib/lib* /lib32/; rm -rf /tmp/foo
```

[*]**Try running glGo**

Chances are it won't work for you at once since I've had some 32-bit libraries already installed.  If you get a message such as:

*glGo: error while loading shared libraries: _libXXX_: cannot open shared object file: No such file or directory*

then follow these steps:

[INDENT]
[LIST=a]
[*]**Determine which package that library comes from:**

  ```
$ dpkg --search _libXXX_
  **pkgXXX**: /usr/lib/libXXX
```

  [*]**Download and install *pkgXXX*:**

Go back to [http://packages.ubuntu.com/edgy]("http://packages.ubuntu.com/edgy"), download the 32-bit package **pkgXXX** and install it with
```
mkdir /tmp/foo; dpkg --extract pkgXXX.deb /tmp/foo; mv /tmp/foo/usr/lib/lib* /lib32/; rm -rf /tmp/foo
```

  [*]**Repeat step 4 until glGo runs**
[/LIST]
[/INDENT]

[*]**Post here your success/failure/resolution status.**
[/LIST]

---

