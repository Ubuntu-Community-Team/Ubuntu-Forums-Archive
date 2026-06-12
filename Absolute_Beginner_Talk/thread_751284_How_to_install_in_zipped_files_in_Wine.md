---
title: "How to install in zipped files in Wine?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-04-10
I'm trying to install a C compiler for Windows into Wine from a CD but it won't install.
I think its because the files are zipped but I'm just guessing because part of the installation works fine with the example source files that are not zipped.
I have no problem installing the compiler in Wndows so its not the CD.
Has anyone run into this problem or know a solution?

---

### Post by guitarMan666 on 2008-04-10
The root of the problem is a compatability issue with Wine.  I'd make sure you are using the latest version from the Ubuntu repositories.

---

### Post by mikeyphi on 2008-04-10
As far as I know (which isn't much!) wine expects programs to have *.exe extension in order to install. Are you able to unzip the software, say on your Desktop, and then install?

---

### Post by pedro_orange on 2008-04-10
I would guess it's a problem with that particular compiler not being able to run properly within wine. 
If you're compiling generic standard C you might be better off using gcc.

You can install this by inserting your Ubuntu CD and doing the following command:

```
sudo apt-get install build-essential
```

---

### Post by garyed on 2008-04-10
I'm using Wine version .9.33
As far as gcc compiler I haven't been able to get it to work on any of my programs yet.
I get all kinds of errors that I don't get when I compile with my windows compiler.
Also this compiler has a simple interface that lets me test my source easily.
I started learning a little programming quite a few years ago in C and C++ and I'm thinking about trying it again.

---

### Post by garyed on 2008-04-10
> **mikeyphi said:**
> As far as I know (which isn't much!) wine expects programs to have *.exe extension in order to install. Are you able to unzip the software, say on your Desktop, and then install?
I think the problem is the install file is an exe but the files it installs are zip. 
That's why it stopd after partial installation & hangs when the compiler tries to install.
The files that are not zipped install O.K.

---

### Post by stchman on 2008-04-10
> **garyed said:**
> I'm trying to install a C compiler for Windows into Wine from a CD but it won't install.
I think its because the files are zipped but I'm just guessing because part of the installation works fine with the example source files that are not zipped.
I have no problem installing the compiler in Wndows so its not the CD.
Has anyone run into this problem or know a solution?

I would unzip the archives in Linux and re-burn them to a CD.

Linux does have C compilers, so unless you are programming the Windows API then just use Linux.

You can install the compiler LCC.

[http://www.cs.virginia.edu/~lcc-win32/](http://www.cs.virginia.edu/~lcc-win32/)

I use to use it on my Windows installs as it was free.

---

### Post by garyed on 2008-04-10
I noticed in my terminal when I tried to install the Windows compiler in wine it says:

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


After I exit it then shows this in the terminal:

fixme:toolhelp:InterruptUnRegister16 (0000), stub.
fixme:toolhelp:NotifyUnregister16 (0), semi-stub.


Maybe it has nothing to do with archived files.
Anyone have any ideas what thtat means?

---

### Post by pedro_orange on 2008-04-11
> **garyed said:**
> I'm using Wine version .9.33
As far as gcc compiler I haven't been able to get it to work on any of my programs yet.
I get all kinds of errors that I don't get when I compile with my windows compiler.
Also this compiler has a simple interface that lets me test my source easily.
I started learning a little programming quite a few years ago in C and C++ and I'm thinking about trying it again.

If you're getting errors compiling on linux then you're not writing standard c/c++.

If you cannot get WINE to run your compiler - why not install a virtual machine and stick Windows in it?

---

### Post by Enverex on 2008-04-11
> **guitarMan666 said:**
> The root of the problem is a compatability issue with Wine.  I'd make sure you are using the latest version from the Ubuntu repositories.

Bad idea. Use the official Wine repos from winehq.org they are far more up to date (i.e. the correct version or one behind, the Ubuntu repos are never updated after the release of the initial Ubuntu version release).

> **garyed said:**
> I'm using Wine version .9.33

If you intend to use Wine then update, you're 26 versions (!!) out of date.

> **garyed said:**
> I noticed in my terminal when I tried to install the Windows compiler in wine it says:

Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.


After I exit it then shows this in the terminal:

fixme:toolhelp:InterruptUnRegister16 (0000), stub.
fixme:toolhelp:NotifyUnregister16 (0), semi-stub.


Maybe it has nothing to do with archived files.
Anyone have any ideas what thtat means?

This means the program you're trying to run is a DOS exe which likely wont work or run well at all in Wine, use DOSBox.

---

### Post by ByteJuggler on 2008-04-11
Maybe you should rather tell us exactly what compiler you're trying to install, and/or exactly what error messages you're getting with other compilers on your source, so we can help you move over to a native Linux compiler.

If you want an IDE for your C++ work, there's many available on Linux, e.g. Eclipse, KDevelop and several other lighter weight source editors.

---

### Post by garyed on 2008-04-11
I have a compiler that came with the book  "Learn C in 21 Day"s.
It's a Borland compiler  for both Windows &t the setup.exe file runs from Windows.  If I remember right there is also A DOS compiler on the CD that can be installed through DOS but it won't install when I manually call the .exe either.
I've upgraded to the newer version of Wine but it didn't help.
I did find that what I'm experiencing is considered a bug in Wine when installing a DOS program.
they recommend using  wineconsole <*.exe>   to install but it still didn't work for me.

 The Borland compiler will do either C or C++ so maybe thats why I can't get GCC to compile. I tried G++ & that didn't compile either. One of the errors  I get is the #include files are missing.

---

### Post by ByteJuggler on 2008-04-11
> **garyed said:**
> I have a compiler that came with the book  "Learn C in 21 Day"s.
It's a Borland compiler  for both Windows &t the setup.exe file runs from Windows.  If I remember right there is also A DOS compiler on the CD that can be installed through DOS but it won't install when I manually call the .exe either.
I've upgraded to the newer version of Wine but it didn't help.
I did find that what I'm experiencing is considered a bug in Wine when installing a DOS program.
they recommend using  wineconsole <*.exe>   to install but it still didn't work for me.

 The Borland compiler will do either C or C++ so maybe thats why I can't get GCC to compile. I tried G++ & that didn't compile either. One of the errors  I get is the #include files are missing.

Is this Borland C++ for Windows, or Borland C++ for DOS?  

Also, can you post the exact text of the error message.  It might be that there's a header file package that you had missing that needs to be installed on your system that caused the error message, and that the proper fix therefore is to install the package.  Honestly, GCC/G++ is pretty standard.  Perhaps you can post the code that you're trying to compile, if it's a small example?

Personally, I would seriously suggest you try to tackle the problems with using GCC as it'd be better for you to use an up to date/native compiler rather than an old DOS based Borland compiler (good as Borland compilers are.)

Aside: GCC also does C or C++, however, when compiling C it's invoked as "gcc" and when c++ as "g++".  Make sure you therefore use "g++" when you compile C++ on Linux/Unix.

---

### Post by garyed on 2008-04-12
Actually I got some of my C programs to compile with GCC after I took out some unneeded header files. Wow is it fast too. I need to work on my  C++ included headers.  
One of my problems is I've been mixing C & C++ code in the same program which the Borland compiler allowed so I got into a bad habbit. I'm going to have to relearn a few things before I even get started again. I've got all kinds of books but they're all pretty old,

---

