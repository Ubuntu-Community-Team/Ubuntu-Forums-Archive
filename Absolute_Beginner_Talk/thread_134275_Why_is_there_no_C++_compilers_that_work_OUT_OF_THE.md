---
title: "Why is there no C++ compilers that work OUT OF THE BOX."
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-02-21
Seems like everything requires me to download some sort of collection of files.. I though that was java's method?

If i'm wrong can someone redirect me to a simple compiler for C++ that works straight up?

---

### Post by jrib on 2006-02-21
g++

install the build-essential package with synaptic or just do ```
sudo apt-get install build-essential
```

I'm curious, what c++ compilers were you trying?

---

### Post by vialick on 2006-02-21
You can install GCC off the CD, just go into the package manager and select it for installation and apply.

---

### Post by systemintheglitch on 2006-02-21
but does it work "out of the box"

---

### Post by kaamos on 2006-02-21
Ubuntu must fit on one cd and putting everything in and installing it by default would bloat it to 14 cds and 10gb hard drive space. Makes little sense when stuff can be installed as easy as just "sudo apt-get install g++"

---

### Post by carlosqueso on 2006-02-21
build-essential does work "out of the box" (if by out of the box you mean right after installing with apt).  Ubuntu doesn't include it by default probably because it's aimed at non-technical users. What are you trying to do with it?

---

### Post by systemintheglitch on 2006-02-21
All i want is an ide or compiler where i can either edit or pass to it (like gcc) a freakin c++ file and it will compile and run it.. Why isnt there a simple compiler such as msvc++6? I never had to download anything for that? Why do i have to download something to get gc++ to work? Why didnt they include whatever it is i have to download with gc++?

---

### Post by systemintheglitch on 2006-02-21
For instance.. Anjuta says i need glib installed to compile anything.. Why the hell doesnt anjuta come with glib?? Why is this so complicated?

---

### Post by carlosqueso on 2006-02-21
g++ comes in the build-essential package.....you can use any text editor to edit the files.  If you install via synaptic or apt-get, it DOES install everything that you need.....if you install by downloading stuff, it doesn't because of the way that linux is put together.

---

### Post by kaamos on 2006-02-21
```
Why didnt they include whatever it is i have to download with g++?
```
I really don't see your issue here
```
sudo apt-get install g++
```
> alaisi@ubuntu:~$ g++ --help
Usage: g++ [options] file...
Options:
  -pass-exit-codes         Exit with highest error code from a phase
  --help                   Display this information
  --target-help            Display target specific command line options
  (Use '-v --help' to display command line options of sub-processes)
  -dumpspecs               Display all of the built in spec strings
  -dumpversion             Display the version of the compiler
  -dumpmachine             Display the compiler's target processor
  -print-search-dirs       Display the directories in the compiler's search path
and so on..

Also installing anjuta from synaptic pulls with it the needed libraries.

---

### Post by systemintheglitch on 2006-02-21
I installed anjuta from the add aplications menu and the second i created a project it said there was an error because i didnt have glib...

---

### Post by carlosqueso on 2006-02-21
Weird...usually apt takes care of that....try installing the libglib2.0-dev and libglib files with ```
sudo apt-get install libglib2.0-0 libglib2.0-dev
``` in a terminal.

---

### Post by systemintheglitch on 2006-02-21
That worked....

---

### Post by carlosqueso on 2006-02-21
Cool....good luck with your linux programming attempt....just curious...is Anjuta an IDE? If it is, let me know how it works for you, as I'm looking for an IDE to get me back unrusty at c++

---

### Post by cwaldbieser on 2006-02-21
[QUOTE=systemintheglitch]For instance.. Anjuta says i need glib installed to compile anything.. Why the hell doesnt anjuta come with glib?? Why is this so complicated?[/QUOTE]
OK, I think I understand what you are saying.
You are finding that when you compile a program from source in Ubuntu, you don't have all the necessary header files installed in order to compile against various libraries.

Those header files don't come installed by default, because a lot of users will never compile a program.

On Windows, you are saying that you never need to download extra header files to compile against libraries, but that is **not** entirely accurate.  It is true that MS VC++ may include some portion of that Windows Platform SDK headers included in a default installation.  However, on Ubuntu, the libraries you are trying to compile against are application libraries.  If you needed to compile against a 3rd party library in Windows, you would need to obtain a copy of their header files, too.

There is nothing g++ or any copiler can do about that-- they can include headers for standard development, but to include headers for every development package in the compiler distribution would not be practical.

---

### Post by jan on 2006-03-24
yup have the same problem, Anjuta needing glib...

---

### Post by Joshuwa on 2006-03-24
I just experienced a similar problem after installing Ubuntu and not knowing it didn't have g++, etc with it.

```
sudo apt-get install g++
```

```
sudo apt-get install build-essential
```

```
sudo apt-get install anjuta
```

And it worked like a charm.


I find Anjuta to be a great IDE. I use MS Visual C++ Express on Win2k, and have no gripes with using Anjuta as an alternative.

---

### Post by jan on 2006-03-25
Right,

installing build-essential worked out for me...

---

